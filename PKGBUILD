pkgname=deadbeef-plugins-infobar-hg
pkgver=20140130
pkgrel=1
pkgdesc="Infobar plugin for DeadBeeF audio player. Shows lyrics and artist's biography for the current track. The stable version."
arch=(i686 x86_64)
url="https://bitbucket.org/dsimbiriatin/deadbeef-infobar"
license=('LGPL' 'MPL')
depends=('deadbeef>=0.6.0' 'libxml2')
makedepends=('mercurial')

_hgmod="deadbeef-infobar"

build() {
  cd $srcdir
  msg "Getting source..."
  if [ -d $_hgmod/.hg ]; then
    (cd $_hgmod && hg pull -u) || return 1
  else
    hg clone https://bitbucket.org/dsimbiriatin/$_hgmod || return 1
  fi

  msg "Building..."
  cd $_hgmod
  make || return 1
}

package() {
  install -D -m644 $srcdir/$_hgmod/gtk2/ddb_infobar_gtk2.so $pkgdir/usr/lib/deadbeef/ddb_infobar_gtk2.so
  install -D -m644 $srcdir/$_hgmod/gtk3/ddb_infobar_gtk3.so $pkgdir/usr/lib/deadbeef/ddb_infobar_gtk3.so
}

