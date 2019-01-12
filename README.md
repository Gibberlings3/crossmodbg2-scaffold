# crossmodbg2-scaffold
A (hopefully) easy way to help CPB get updated faster


## Oh hi there!

Over the years this mod has had some amazing and dedicated people maintaining it. Having mod NPCs banter with each other is pretty much one of the coolest things ever. 

But maintaining this mod is NOT easy. The Crossmod Banter Pack has grown in size by a staggering amount over the years and with EE there are more NPC mods than ever.

So, as the maintainers of this mod, we ask for your (the modder) help! If you wish for your crossmod content to be included in this pack, we ask that the creators of the mods make the effort to structure their crossmod content in a way that helps us, the maintainers, update the master files quickly and with as little bugs as possible.

**NOTE**: These steps should be followed AFTER you've tested your code (you did test it, right?)

This template will get you started. Download this repository and extract the zip somewhere. Take a look at the folders in here. You're going to be putting your crossmod content in there. When you're ready to submit, send it off to a Gibberlings 3 moderator or admin and we'll get it into the mod.

**NOTE**:
- All dialogue must be tra-fied
- Every crossmod must have its own folder (see below for example)
- Remember, **don't write crossmod with another modder's NPC if you don't have their permission**.

```soa
|--banters
   |--soa_auren-sarah
      |--soa_auren-sarah.d   <- This is where the banters live for this SoA crossmod

tob
|--banters
   |--tob_auren-sarah
      |--tob_auren-sarah.d   <- This is where the banters live for this ToB crossmod

tra
|--soa_auren-sarah.tra
|--tob_auren-sarah.tra  <-  These are the TRA files for your crossmod
```

A TRA file for one of these would look something like this:
```
@0    = ~I like red.~
@1    = ~Red is lame! I like green.~
@2    = ~Sounds suspicious.~
```

```
setup
|--setup.tra  <- Don't worry about numbering these...we have to add them to the master list so leave them at 000.

   @000  = ~Adding SoA banters between Auren and Sarah...~
   @000  = ~k#aurenb.dlg and/or k#sarahb.dlg not detected. Skipping these particular SoA banters.~
```

Let's not forget the ToB ones too
```
   @000  = ~Adding ToB banters between Auren and Sarah...~
   @000  = ~k#aurenb.dlg and/or k#sarahb.dlg not detected. Skipping these particular ToB banters.~
```
```
|--setup.tp2
/* Auren - Sarah SoA Material */    // # of banters
ACTION_IF FILE_EXISTS_IN_GAME ~k#aurenb.dlg~ AND FILE_EXISTS_IN_GAME ~k#sarahb.dlg~
THEN BEGIN
    PRINT @000 /* Adding SoA banters between Auren and Sarah... */
    APPEND_OUTER ~crossmodbg2/crossmod_0_debug.log~ ~Adding SoA banters between Auren and Sarah..~
    COMPILE ~crossmodbg2/soa/banters/soa_auren-sarah/soa_elaryn-auren-sarah.d~
END ELSE BEGIN
    PRINT @000 /* k#aurenb.dlg and/or k#sarahb.dlg not detected. Skipping these particular SoA banters. */
    APPEND_OUTER ~crossmodbg2/crossmod_0_debug.log~ ~K#AurenB.dlg and/or K#SarahB.dlg not detected. Skipping these particular SoA banters.~
END
```

Finally, we ask that you compile a list of the banters so that we can update readmes and announcements.

- 5 banters between theacefes' Auren and theacefes' Sarah
- 6 unnecessary banters between theacefes' Banana! and theacefes' Skooter
