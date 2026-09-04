
# 1. Cloner les deux dépôts
mkdir -p /mnt/c/dev
cd /mnt/c/dev
git clone https://github.com/davhuit/DxController-Davhuit.git
git clone https://github.com/davhuit/DeusEx-BuildTools-Davhuit.git

# 2. Relier gamedir à l'environnement de build
cd /mnt/c/dev/DxController-Davhuit
rm -f gamedir
ln -s /mnt/c/dev/DeusEx-BuildTools-Davhuit gamedir

# 3. Vérifications rapides
ls gamedir/System/ucc.exe
ls launcher/games/DeusEx/Engine/Inc/Engine.h

# 4. Localiser MSBuild (le chemin peut varier selon la version VS installée)
dir "C:\Program Files (x86)\Microsoft Visual Studio\*MSBuild.exe" 2>nul   # depuis cmd.exe

# 5. Build
export MSBUILD="/mnt/c/Program Files (x86)/Microsoft Visual Studio/<VERSION>/BuildTools/MSBuild/Current/Bin/MSBuild.exe"
nix run .#sync-and-build

# 6. Installer dans le jeu
cp gamedir/System/DeusEx.u gamedir/System/DXController.u gamedir/System/DeusEx.exe gamedir/System/SDL3.dll "/chemin/vers/Deus Ex/System/"
