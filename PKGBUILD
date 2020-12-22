#Maintainer: Andrzej Giniewicz <gginiu@gmail.com>

pkgname='fbx-sdk'
pkgver=2020.0.1
pkgrel=1
pkgdesc='Platform and API toolkit to transfer existing content into the FBX format.'
arch=('i686' 'x86_64')
url='http://www.autodesk.com/products/fbx/overview'
license=('custom')
install='fbx-sdk.install'
_verstr=`echo ${pkgver:0:4}${pkgver:5} | sed 's/\./_/g'`
source=("https://www.autodesk.com/content/dam/autodesk/www/adn/fbx/2020-0-1/fbx202001_fbxsdk_linux.tar.gz")
md5sums=('4771622b5a55fcbf9ff26a140e2e110d')

build() {
  cd "$srcdir"

  rm -rf "fbx-sdk"
  mkdir "fbx-sdk"
  chmod +x "./fbx202001_fbxsdk_linux"
  printf "yes\nn\n" | "./fbx202001_fbxsdk_linux" "$srcdir/fbx-sdk"
}

package() {
  cd "$srcdir/fbx-sdk"

  if [ "$CARCH" = "x86_64" ]; then
    fbxarch="x64"
  else
    fbxarch="x86"
  fi
  install -D "lib/gcc/$fbxarch/release/libfbxsdk.so" "$pkgdir/usr/lib/libfbxsdk.so"

  cp -r include "$pkgdir/usr"

  install -d "$pkgdir/usr/share/doc/$pkgname"
  cp -r samples "$pkgdir/usr/share/doc/$pkgname"
  install -D "FBX_SDK_Online_Documentation.html" "$pkgdir/usr/share/doc/$pkgname/FBX_SDK_Online_Documentation.html"
  install -D "License.txt" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

