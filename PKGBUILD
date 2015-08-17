# Maintainer: Guten Ye

pkgname="rutorrent-saber-git"
pkgver=20120911
pkgrel=1
pkgdesc="a rutorrent plugin to auto download files from seedbox."
arch=("i686" "x86_64")
url="https://github.com/GutenYe/saber"
license=("MIT")
depends=("rutorrent")
makedepends=("git")
provides=("rutorrent-saber")

_gitroot="git://github.com/GutenYe/saber.git"
_gitname="saber"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"
}

package() {
  cd "$srcdir/$_gitname-build"

  mkdir -p "$pkgdir/usr/share/webapps/rutorrent/plugins/saber"
  cp -r rutorrent/* "$pkgdir/usr/share/webapps/rutorrent/plugins/saber"
}

# vim:set ts=2 sw=2 et:
md5sums=()
