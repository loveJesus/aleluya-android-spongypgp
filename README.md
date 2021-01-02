# Jesus Christ is Lord

This is an adaptation of Bouncy Castle PGP for use with Android. Android already has a version of bouncy castle, but doesn't work with certain features like some with OpenPGP. An updated Bouncy Castle cannot be included with the same namespaces as the one included with android. Spongy castle is a version of Bouncy Castle with a new name to avoid this. This is an old version of openpgp from bouncy castle meant to work with Spongy Castle, however Spongy Castle is outdated at the moment.

The currently recommended route is to compile the current version of Bouncy Castle modified using https://github.com/jbuhacoff/nodejs-mybc-util to compile it with different names, which you can choose. Make sure to have Ant, Maven, Java 8 already installed, and do everything in order. The steps are not that difficult but if you make a mistake within the folder do a git reset --hard and start over. This should also compile the .jar to use openpgp without the need to use this package. Make sure if you are security conscious to check the nodejs scripts tha they don't modify things other than package names/etc.

Blessings unto Christ Jesus
