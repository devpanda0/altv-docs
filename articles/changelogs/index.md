# 15.0-Release

> [!WARNING]
> This update is the latest.

> [!TIP]
> This update was released on 20.10.2023

> [!div class="nohljsln"]
> ```yaml
> - 15.1:
>    - Fixed serverlist player count sort
> - 15.2:
>    - UI Fixes
> - 15.3:
>    - Fixes if alt:V path included invalid characters
> - 15.4:
>    - Fixed config parsing
> - 15.5:
>    - Temporary disabled backup
> - 15.6:
>    - print stacktrace on crash
> - 15.7:
>    - Fixed disconnect messages
> - 15.19:
>    - Improved startup
> - 15.20:
>    - Improved cloudauth
> - 15.21:
>    - added removeHeadBlendData method to player
>    - Improved cloudauth
> - 15.22:
>    - Improved model loading
> - 15.24:
>    - Crashes on game starting
> - 15.28:
>    - Localizitation for crash reporter
> - 15.31:
>    - Print error on asset errror
> - 15.32:
>    - Fix Voice chat dimensions
> - 15.33:
>    - Fix distorsion with noise suppression enabled
> - 15.36:
>    - Fix voicechat crackles with louad sounds and normalization enabled
> - 15.37:
>    - Fix vehicle pools
> - 15.38:
>    - Improve asia region support
> - 15.40:
>    - Fix colshape delete & create in same tick
> - 15.41:
>    - Fix infinite sprint
>    - Improve modelloading
>    - Fix total events received
> - 15.48:
>    - Fix Stream synced meta script event delete new value
> - 15.49:
>    - Increase weapon component info pool
> - 15.57:
>    - Always reconnect to masterlist on failure

## Client

### <span style="color: red;">Breaking changes</span>

> [!div class="nohljsln"]
> ```yaml
> - Renamed Object to LocalObject
> - .id represents local id now, if you need same id as on server use .remoteID
> - getPermissionState returns bool now
> - setArtificialLightsState has no effect anymore, use DisableEmissiveLightsRendering config flag instead
> - Weapons no more be synced clienside, use server side methods instead. Ammo set by the server will override ammo set by client.
> - client to server events can't be more then 8kb
> ```

### Added

> [!div class="nohljsln"]
> ```yaml
> - mute loading music
> - DISABLE_VEHICLE_ENGINE_SHUTDOWN_ON_LEAVE configflag to keep engines on when leaving a vehicle
> - FORCE_RENDER_SNOW configflag to enable snow on any weather
> - FORCE_HIDE_NIGHT_PROPS & FORCE_SHOW_NIGHT_PROPS
> - DISABLE_EMISSIVE_LIGHTS_RENDERING configflag to enable / disable emissive lights
> - audio, checkpoint, webview all getter
> - audio, webview, httpclient, websocketclient id getter
> - audio, blip remoteid getter
> - worldObjectPositionChange, worldObjectStreamIn & worldObjectStreamOut event
> - entityHitEntity event
> - audio filter, colshape, textlabel, weaponObject api
> - dimension getter, position & rotation setter for localplayer
> - httpclient, rmldocument, websocketclient, webview, checkpoint getbyID method
> - blip getByScriptID method
> - multiple webviews can be focused
> - resource config getter
> - vehicle rpm setter
> - warning if gta systems have performance issues
> - overwrite all game meta & dat files
> - DISABLE_SP_ENTER_VEHICLE_CLIPSET flag (true by default)
> - extendet texture budget
> - new setter & getter for object, checkpoint
> - localPed & localVehicle api
> - activityInputEnabled, activationLevel, noiseSuppressionEnabled, toggleInput methods
> - Extended Voice API Permission
> - isFullScreen method
> - cef hardware acceleration
> - improve resource loading speed
> - downloadspeed settings
> - entity frozen setter/getter
> - startEnteringVehicle & startLeavingVehicle events
> - webview reload method
> - sourceentity parameter to weaponDamage event
> - gpuAccelerationActive webview getter
> - playerBulletHit event
> - checkpoint icon color getter/setter
> - extend audio api by output classes
> - audiocategory data api
> - all getter for weapondata api
> - gta v backup system
> - resetMinimapComponentPosition method
> - localstorage has method
> - suspensionHeight setter & getter
> - 3d audio output for webview
> - alt.getVersion, alt.getBranch, alt.getLocale in webviews
> - player IsStealthy & IsCrouching getter
> - weaponTintIndex & currentWeapontintindex getter
> - vehicle steeringAngle setter
> - Discord Rich Presence can be deactivated/activated
> - getNetTime method
> - markers api
> - player taskData getter
> - playerStartTalking & playerStopTalking event
> ```

### Fixed

> [!div class="nohljsln"]
> ```yaml
> - minimap textures couldn't be replaced
> - ap1_* ytds, vehshare.ytd, hud.ytd, minimap.ytd couldn't be replaced
> - gfx couldn't be replaced
> - cef flickering while marker is visible (native.drawRect(0, 0, 0, 0, 0, 0, 0, 0) workaround is no longer needed)
> - weapon dlc addon crashed the game on connect to the server
> - cef locale detection
> - webview didnt get destroyed
> - wrong reported resource downloadspeed
> - optional permissions
> - cancel button crashed client
> - voiceInputVolume sets volume in reverse
> - ladder sync
> - localplayer micLevel & isTalking getter
> - mouse cursor stucked in the middle of the screen if input was not set to raw
> - crash on invalid rml document input
> - multiple fixes related to the audio api
> - carmodcols can be loaded to use gta v chameleon colors
> - possible crash in getWheelSurfaceMaterial
> - wrong vehicle position on streamin after few restreams
> - playing animation directly after another one wasnt synced
> - entity models are not freed from memory
> - taskSynchronizedScene wasnt synced
> - tattoos disappeared randomly
> - (max)health, (max)armor getter from remoteplayers wasn't always correct
> - parachute sync
> - connect to server via ipv6 adress
> - position of towtruck hook on streamin
> - loadCloudHat native
> - custom numberplate limit
> - vehicle dirt rendering
> ```

## Server

### <span style="color: red;">Breaking changes</span>

> [!div class="nohljsln"]
> ```yaml
> - Removed PlayerBeforeConnect event
> - Removed id support for entityinstreamingrange method
> - Removed entityWorkerCount server option
> - playerWeaponChange is not cancable anymore
> ```

### Added

> [!div class="nohljsln"]
> ```yaml
> - unreliable events
> - vehicleHorn event (cancable)
> - vehicleSiren, playerSpawn event
> - getEntitiesInDimension, getEntitiesInRange, getClosestEntities methods
> - support for singleplayer rpf files
> - extend limit to 65.000 entities (players, vehicles, etc.)
> - colshape & blip, voicechannel id getter
> - checkpoint all getter
> - extend resource limit to 4GB
> - added priority, filter getter & setter for voiceserver
> - player playAnimation, clearTasks, playScenario method
> - streamsyncedmeta for checkpoints
> - vehicle quaternion setter & getter
> - objects Api
> - player socialClubName getter
> - socialClubName info in connectioInfo
> - option (spawnAfterConnect = true) to spawn player automatically at position 0,0,71
> - no-regenerate-rpf-cache cmd line arg
> - error message if justpack gets used without valid host config
> - possible to enable only specific gta dlcs with the dlcWhitelist config option
> - player streamedEntities getter
> - hashClientResourceName server option
> - Modify gamepool size via server config
> - prometheus support
> - Missing maxDistance & isSpatial voicechannel getter
> - streamer, migration, syncSend, syncReceive thread count can be configured in server.toml
> - resource wildcard support in server.toml
> - getWeaponModelInfoByHash method, getAmmoHashForWeaponHash method & weaponmodels.bin file
> - ammo getter & setter method
> - canAttachCars & handlingNameHash to vehicleModelInfo
> - timestamp for entitys
> - hasWeapon, AmmoSpecialType, ammoFlags, ammoMax method for player
> - removeAllAmmo parameter for removeAllWeapons
> - blip dimension setter, blips can be shown to specific players
> - addDecoration, removeDecoration, clearDecorations, getDecorations method for player
> - setVoiceExternalPublic & setVoiceExternal method
> - player netOwnershipDisabled property
> - vehicle brakeLevel, accelerationLevel getter
> - requestSyncedScene, startSyncedScene, stopSyncedScene, updateSyncedScene events
> - vehicle hornActive getter
> - clientDeleteObject & clientRequestObject event
> - connectioninfo text to display text while in queue
> - entities limit can be increased in server.toml
> - playerheal event
> - setter & getter to set streaminglimits & threadcounts
> - vehicle passenger getter
> - cloudauth api
> - givePedScriptedTask event
> - attach api for objects
> - pedDamage, pedDeath, pedHeal events
> - every entity can have its own streaming distance
> - maxClientScriptEventSize & maxServerScriptEventSize config option
> - getLoadedVehicleModels method
> - allowUnknownRPCEvents server config option
> - blooddamage getter & setter
> ```

### Fixed

> [!div class="nohljsln"]
> ```yaml
> - Dead body position sync
> - vehicle angular interpolator
> - vehicle flickers when the netowner changes
> - player model setter removed all weapons
> - setting health directly after model change, left hp at 200
> - maxArmour resetted when player died
> - entity attachto api didnt accept all bone ids
> - voiceserver port config did not apply
> - attachTo was desync on netowner change
> - projectile sync
> - netownerChange event wasnt called when netowner got null
> ```

## Server & Client

### <span style="color: red;">Breaking changes</span>

> [!div class="nohljsln"]
> ```yaml
> - Removed alt.Entity.getByID method
> ```

### Added
> [!div class="nohljsln"]
> ```yaml
> - getByID & getByRemoteID method for baseobjects
> - getMetaKeys & getSyncedMetaKeys methods
> - ped's Api
> - virtual entitys api
> - isEnteringVehicle, isLeavingVehicle, isOnLadder, isInCover, isInMelee, isParachuting player getter
> - metachange event
> - voiceConnection event
> - getVoiceConnectionState method
> - new blip api methods
> - vehicle steeringAngle getter
> - player hasWeaponComponent method
> - server <-> client rpc api
> ```

### Fixed
> [!div class="nohljsln"]
> ```yaml
> - radius blip wasn't visible
> - radius blip size property
> ```

## JS Module

### <span style="color: red;">Breaking changes</span>

> [!div class="nohljsln"]
> ```yaml
> - Removed deprecated null in emitClient & emitClientRaw as target parameter
> ```

### Added
> [!div class="nohljsln"]
> ```yaml
> - (Client) toggleStrictChecks for natives
> - (Server|Client) baseObjectCreate & baseObjectRemove event
> ```


## C# Module

### <span style="color: red;">Breaking changes</span>

> [!div class="nohljsln"]
> ```yaml
> - Removed deprecated Alt.Server property
> - All element constructors are deprecated. Please only use Alt.Create* or AltAsync.Create* instead. In one of the next updates the constructors will be removed.
> - (server) ScriptEvents must now set the required return type. Otherwise a log will be output to the console and the event will not be registered
> ```

### Fixed

> [!div class="nohljsln"]
> ```yaml
> - Fix OnRmlEvent Event
> ```
