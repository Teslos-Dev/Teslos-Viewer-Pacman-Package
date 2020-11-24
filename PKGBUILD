# Maintainer: Triplehx3 <ginge264@gmail.com>

pkgname=TeslosViewer
pkgver=1.0.0.10
_pkgver=1_0_0_10
pkgrel=1
pkgdesc="A Second Life (secondlife) protocol compatible client application, used to access its service as well as a number of other such as those based upon OpenSim platform"
url="https://github.com/Teslos-Dev/Teslos-Viewer"
license=('custom')
arch=('x86_64')
depends=('apr' 'apr-util' 'gtk2' 'libgl' 'libidn' 'mesa' 'nss' 'sdl' 'libxss' 'lib32-libidn' 'lib32-libsndfile' 'lib32-zlib' 'gconf' 'lib32-util-linux' 'openal' 'expat' 'freealut')
optdepends=('libpulse: for PulseAudio support'
	'alsa-lib: for ALSA support'
	'nvidia-utils: for NVIDIA support'
	'flashplugin: for inworld Flash support'
	'gstreamer0.10: for video support, may need good, bad and ugly plugins'
	'libxtst'
	'pangox-compat: for media_plugin_webkit to work'
	'lib32-alsa-plugins: for voice')

source=("https://github.com/Teslos-Dev/Teslos-Viewer/releases/download/tv-${pkgver}/Teslos_${_pkgver}_x86_64.tar.xz"
	"teslosviewer.desktop"
	"teslosviewer.launcher")
md5sums=('2c6c188f852934f1aee65f51a20ecd33'
         '3317de28c6a3a21f332a3bcd96b3b9b5'
         '78235f9b14d682a1b7c02c374cf98d45')

package() {
cd $srcdir

# Rename Data Directory
mv Teslos_${_pkgver}_$CARCH teslosviewer

# Remove old libraries
#cd $srcdir
#cd singularityviewer/
#cd lib64/
#rm *SDL*
#rm *openal*
#rm *expat*
#rm *apr*
#rm *alut*
#rm *freetype*

# Install Desktop File
install -D -m644 $srcdir/teslosviewer.desktop \
    $pkgdir/usr/share/applications/teslosviewer.desktop
  
# Install Icon File
install -D -m644 $srcdir/teslosviewer/viewer_icon.png \
  $pkgdir/usr/share/pixmaps/teslosviewer.png
  
# Install Launcher
install -D -m755 $srcdir/teslosviewer.launcher \
    $pkgdir/usr/bin/teslosviewer

# Install License file
install -D -m755 $srcdir/teslosviewer/licenses.txt \
    $pkgdir/usr/share/licenses/$pkgname/LICENSE
    
# Move Data to Destination Directory
install -d $pkgdir/opt
mv $srcdir/teslosviewer $pkgdir/opt/
  
# Change Permissions of files to root:games
chown -R root:games $pkgdir/opt/teslosviewer
chmod -R g+rw $pkgdir/opt/teslosviewer

# Make Binary Group-Executable
chmod g+x $pkgdir/opt/teslosviewer/teslos

# Do not re-register the application with the desktop system at every launch, saves from locally installed desktop files.
sed -i 's|./refresh_desktop_app_entry.sh|#./refresh_desktop_app_entry.sh|' $pkgdir/opt/teslosviewer/teslos


}
