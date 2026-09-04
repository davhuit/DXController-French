```bash
# Prérequis (une fois par PC) : WSL2 + Ubuntu, Nix, Git, Visual Studio Build Tools (avec "Développement Desktop en C++")

# 1. Cloner les deux dépôts
mkdir -p /mnt/c/dev
cd /mnt/c/dev
git clone https://github.com/davhuit/DxController-Davhuit.git
git clone https://github.com/davhuit/DeusEx-BuildTools-Davhuit.git

# 2. Relier gamedir
cd /mnt/c/dev/DxController-Davhuit
rm -f gamedir
ln -s /mnt/c/dev/DeusEx-BuildTools-Davhuit gamedir

# 3. Localiser MSBuild (depuis cmd.exe)
dir /s /b "C:\Program Files (x86)\Microsoft Visual Studio\*MSBuild.exe" 2>nul

# 4. Build
export MSBUILD="/mnt/c/Program Files (x86)/Microsoft Visual Studio/18/BuildTools/MSBuild/Current/Bin/MSBuild.exe"
nix run .#sync-and-build

# 5. Installer dans le jeu
cp gamedir/System/DeusEx.u gamedir/System/DXController.u gamedir/System/DeusEx.exe gamedir/System/SDL3.dll "/mnt/c/Program Files (x86)/Steam/steamapps/common/Deus Ex/System/"
