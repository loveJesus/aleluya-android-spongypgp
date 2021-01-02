# Jesus Christ is Lord

### Please read below for updated instructions instead of using this source

This is an adaptation of Bouncy Castle PGP for use with Android. Android already has a version of bouncy castle, but doesn't work with certain features like some with OpenPGP. An updated Bouncy Castle cannot be included with the same namespaces as the one included with android. Spongy castle is a version of Bouncy Castle with a new name to avoid this. This is an old version of openpgp from bouncy castle meant to work with Spongy Castle, however Spongy Castle is outdated at the moment.

The currently recommended route is to compile the current version of Bouncy Castle modified using https://github.com/jbuhacoff/nodejs-mybc-util to compile it with different names, which you can choose. Make sure to have Ant, Maven, Java 8 already installed, and do everything in order. The steps are not that difficult but if you make a mistake within the folder do a ```git reset --hard``` or redownload the bouncy castle source and start over. This should also compile the .jar to use openpgp without the need to use this package. Make sure if you are security conscious to check the nodejs scripts tha they don't modify things other than package names/etc.

Once you complete the steps, a simple way of using the file in android is to include the generated
```bcpg-jdk15on-168-shaded.jar```
and
```bcprov-jdk15on-168-shaded.jar```
in your app/libs folder. Go into Project Files view on the right side and drag them in. The right click on each of them and click "Add as Library".
You will then have ```my.bouncycastle.openpgp.*``` available (or whatever name you used, like ```us.xjes.bouncyleluya```) for the package hierarchy.

Here are the mybc commands for my usage
```
sudo apt install -y openjdk-8-jdk maven ant npm
sudo update-alternatives --config java
# Find the directory there too
export JAVA_HOME="(dir from above after selecting)"
sudo npm install -g @jbuhacoff/mybc
git clone https://github.com/bcgit/bc-java && cd bc-java
git checkout -b mybc-1.68-aleluya tags/r1rv68
mybc prebuild --providerName BCleluya --packageName us.xjes.bouncyleluya --displayName BouncyCastleAleluya
export JDKPATH="$JAVA_HOME"
sh ./build15+
mybc postbuild --groupId us.xjes.bouncyleluya
# -shaded libs to copy now in build
```

It is important to include the new Security provider. Run ```Security.addProvider(BouncyCastleProvider())``` on the initial onCreate with using the imported BouncyCastleProvider you created as one method of doing it.

For an example of symmetrical encryption with their ```openpgp.examples.ByteArrayHandler``` in Kotlin

On top place
```
import us.xjes.bouncyleluya.bcpg.SymmetricKeyAlgorithmTags
import us.xjes.bouncyleluya.jce.provider.BouncyCastleProvider
import us.xjes.bouncyleluya.openpgp.examples.ByteArrayHandler
import java.security.Security
```

And then in the source

Here is an example usage of the project 
```
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        Security.addProvider(BouncyCastleProvider())
        var message_aleluya = "Jesus Christ is Lord".toByteArray()
        var encrypted_aleluya = ByteArrayHandler.encrypt(
            message_aleluya,
            "passwordleluya".toCharArray(),
            "placeholder_filename_aleluya",
            SymmetricKeyAlgorithmTags.AES_256,
            true
        )
        var str_decrypted_aleluya = String(ByteArrayHandler.decrypt(encrypted_aleluya, "passwordleluya".toCharArray()));
       // etc...        
```

Thanks to @Neustradamus For helping me to be encouraged to write this up.

Blessings unto Christ Jesus https://www.jesusfilm.org/watch/jesus.html/english.html
