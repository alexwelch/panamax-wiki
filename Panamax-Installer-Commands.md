## Commands
### init 
First time installing Panamax! - Downloads CoreOS VM and installs latest Panamax version.

**Alias**: install/init,-op=install

**Parameters**: -ppUi=UI Port, -ppApi=Api Port, --dev/–stable (dev: nightly build, stable:  stable release), --cpu=cores, --memory=MemoryinMB

**Example usage**: ``$ panamax init --ppUi=3000 --ppApi=3001 --stable --cpu=2 --memory=2048``

**Actions**:  Downloads a pre-tested version of CoreOS, and tar of images.vdi containing Panamax UI & API images, google/cadvisor:0.1.0 images. This disk is attached to the VM with a disk labeled images and will be mapped to /var/lib/docker folder.  
 
If a dev/stable version of Panamax is selected during install/reinstall/update, all subsequent Panamax install/reinstall/updates will be on that branch of Panamax. It needs to be overwritten by passing --dev/stable. To check which version you're on, run "panamax -v".

### pause
Stops Panamax

**Alias**: pause/stop/-op=stop

**Parameters**: none 

**Example usage**: ``$ panamax pause``

**Actions**: Stops Panamax CoreOS VM. Any running apps inside CoreOS will also stop. State of Panamax is maintained. 

### up
Starts Panamax

**Alias**: up/start/-op=start

**Parameters**: none 

**Example usage**: ``$ panamax up``

**Actions**: Starts Panamax CoreOS VM. Any running apps that were tagged to be auto-restarted should come back up.

### restart
Stops and Starts Panamax.

**Alias**: restart/-op=restart

**Parameters**: none

**Example usage**: ``$ panamax restart``

**Actions**: Same as Stop & Start. State of apps should be maintained.  DB will be rehydrated with latest templates when Panamax is restarted. 

### reinstall
Deletes your applications and CoreOS VM; reinstalls to latest Panamax version.

**Alias**: reinstall/-op=reinstall

**Parameters**: -ppUi=UI Port, -ppApi=Api Port, --dev/–stable (dev: nightly build, stable:  stable release), --cpu=cores, --memory=MemoryinMB, vd=Y/N: If Y, redownloads the Vagrant Box.

**Example usage**: ``$ panamax reinstall --cpu=2 --memory=2048``

**Actions**:
Shut downs the VM, detaches images.vdi and deletes the Virtualbox VM. Creates a new VM. (optionally downloads a new coreOS Vagrant Box if there's an updated CoreOS version specified in settings), re-attaches images.vdi to VM and updates Panamax images. All existing user images will still be available. Panamax Containers/DB is dropped off and recreated, so all items stored in the DB/Container will have to be re-initialized. DB is rehydrated with latest templates when Panamax is reinstalled. 

*Note*:    If dev/stable version of Panamax is selected during install/reinstall/update, all sub-sequent Panamax install/reinstall/updates will be on that branch of Panamax. It needs to be overwritten by passing --dev/stable.

###info
Displays version of your local Panamax install.

**Alias**: info/--version/-v

**Parameters**: none

**Example usage**: ``$ panamax info``

**Actions**: Display UI, API and Installer Versions

###check
Checks for available updates for Panamax.

**Alias**: check

**Parameters**: none

**Example usage**: ``$ panamax check``

**Actions**: checks for updates to setup or Panamax images. If running dev version, displays message that new builds are pushed nightly.

###download
Updates to latest Panamax version.

**Alias**: download/update/-op=update

**Parameters**:-ppUi=UI Port, -ppApi=Api Port, --dev/–stable (dev: nightly build, stable:  stable release), --cpu=cores, --memory=MemoryinMB

**Example usage**: ``$ panamax download --cpu=2 --memory=2048``

**Actions**: Updates Panamax images to latest version and drops and recreates Panamax Containers. DB volume is left behind, so all settings in DB remain intact, (apps/git config etc is preserved). DB is rehydrated with latest templates when Panamax is reinstalled. 

*Note*: If dev/stable version of Panamax is selected during install/reinstall/update, all subsequent Panamax install/reinstall/updates will be on that branch of Panamax. It needs to be overwritten by passing --dev/stable.

###delete
Uninstalls Panamax, deletes applications and CoreOS VM.

**Alias**: delete/uninstall/-op=uninstall

**Parameters**: none

**Example usage**: ``$ panamax delete``

**Actions**: Deletes the CoreOS VM and deletes the associated Vagrant Box. Everything else is left intact (brew & the folders created by brew setup on Mac OS X installations).

###ssh 
ssh into Panamax CoreOS VM.

**Alias**: ssh

**Parameters**: none

**Example usage**: ``$ panamax ssh``

**Actions**: Shortcut to ssh into panamax-vm.
