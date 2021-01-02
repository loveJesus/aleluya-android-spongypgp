# Jesus Christ is Lord

This is an adaptation of Bouncy Castle PGP for use with Android. Android already has a version of bouncy castle, but doesn't work with certain features like some with OpenPGP. An updated Bouncy Castle cannot be included with the same namespaces as the one included with android. Spongy castle is a version of Bouncy Castle with a new name to avoid this. This is an old version of openpgp from bouncy castle meant to work with Spongy Castle, however Spongy Castle is outdated at the moment.

The currently recommended route is to compile the current version of Bouncy Castle modified using https://github.com/jbuhacoff/nodejs-mybc-util to compile it with different names, which you can choose. Make sure to have Ant, Maven, Java 8 already installed, and do everything in order. The steps are not that difficult but if you make a mistake within the folder do a git reset --hard and start over. This should also compile the .jar to use openpgp without the need to use this package. Make sure if you are security conscious to check the nodejs scripts tha they don't modify things other than package names/etc.

Once you complete the steps, a simple way of using the file in android is to include 
```bcpg-jdk15on-168-shaded.jar```
and
```bcprov-jdk15on-168-shaded.jar```
in your libs folder, right click and add library
then you can run ```Security.addProvider(BouncyCastleProvider())``` on the initial onCreate with the BouncyCastleProvider you created.

Here is an example usage of the project with their ```openpgp.examples.ByteArrayHandler``` in Kotlin
```
var ba1_aleluya = "Jesus Christ is Lord".toByteArray()
var arr1_aleluya = ByteArrayHandler.encrypt(
    ba1_aleluya,
    "passwordleluya".toCharArray(),
    "placeholder_filename_aleluya",
    SymmetricKeyAlgorithmTags.AES_256,
    true
)
var str_aleluya = ByteArrayHandler.decrypt(arr1_aleluya, "passwordleluya".toCharArray());
```

Blessings unto Christ Jesus
