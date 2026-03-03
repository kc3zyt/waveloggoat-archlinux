#template taken from here:
#https://wiki.archlinux.org/title/Go_package_guidelines
pkgname_=WaveLogGoat
pkgname=waveloggoat
pkgver=0.0.5
pkgrel=1
pkgdesc='Go PKGBUILD Example'
arch=('x86_64')
url="https://github.com/johnsonm/$pkgname_"
license=('GPL')
#makedepends=('go' 'goreleaser')
makedepends=('go')
source=("$url/archive/refs/tags/v$pkgver.tar.gz")
sha256sums=('c91926fb15d4a992f64da5c6ebfa7e3304236a261e230228a6afa9dadaaadc3b')

prepare(){
	cd "$pkgname_-$pkgver"
#	mkdir -p build/
}

build() {
	cd "$pkgname_-$pkgver"
	export CGO_CPPFLAGS="${CPPFLAGS}"
	export CGO_CFLAGS="${CFLAGS}"
	export CGO_CXXFLAGS="${CXXFLAGS}"
	#export CGO_LDeeFLAGS="${LDFLAGS}"
	#export GOFLAGS="-buildmode=pie -trimpath -ldflags=-linkmode=external -mod=readonly -modcacherw"
	go mod tidy
	go build -o "$pkgname"
}

check() {
	cd "$pkgname_-$pkgver"
	go test ./...
}

package() {
	cd "$pkgname_-$pkgver"
	install -Dm755 "$pkgname" "$pkgdir"/usr/bin/$pkgname
}
