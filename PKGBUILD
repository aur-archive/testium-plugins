# Maintainer: ava1ar <mail(at)ava1ar(dot)info>

pkgbase=testium-plugins
pkgname=(testium-libpdf testium-pepper-flash)
pkgdesc="Google Chrome's plugins for Chromium (libpdf and pepper-flash, stable versions)"
pkgver=36.0.1985.143
pkgrel=1
epoch=1
_verbld=${pkgver}-1
_channel='stable'
arch=('i686' 'x86_64')
url="http://www.google.com/chrome"
license=('custom:chrome')
source=(license.html::http://www.google.com/chrome/intl/en/eula_text.html)
sha1sums=('SKIP')
if [ "$CARCH" == x86_64 ]; then
	source+=(https://dl.google.com/linux/chrome/rpm/stable/x86_64/google-chrome-${_channel}-${_verbld}.x86_64.rpm)
	sha1sums+=('7f47121c38c2051f7c7072f67701520582a998e9')
elif [ "$CARCH" == i686 ]; then
	source+=(https://dl.google.com/linux/chrome/rpm/stable/i386/google-chrome-${_channel}-${_verbld}.i386.rpm)
	sha1sums+=('4ca7a54f6e8f5df061c6b18c06d6247303afcd06')
fi

package_testium-libpdf() {
	pkgdesc="Google Chrome's PDF plugin for Chromium (stable version)"
	conflicts=('chromium-libpdf-dev')
	install=chromium-libpdf.install

	install -d "${pkgdir}/usr/lib/chromium"
	install -m644 opt/google/chrome/libpdf.so "${pkgdir}/usr/lib/chromium"
	# License
	install -Dm644 "${srcdir}/license.html" "${pkgdir}/usr/share/licenses/${pkgname}/license.html"
}

package_testium-pepper-flash() {
	pkgdesc="Google Chrome's Pepper Flash plugin for Chromium (stable version)"
	pkgver=14.0.0.177
	conflicts=('chromium-pepper-flash-dev')
	install=chromium-pepper-flash.install

	install -d "${pkgdir}/usr/lib/PepperFlash"
	install -m644 opt/google/chrome/PepperFlash/* "${pkgdir}/usr/lib/PepperFlash"
	sed -i "s/flashver=.*/flashver=${pkgver}/" "${startdir}/chromium-pepper-flash.install"
	# License
	install -Dm644 "${srcdir}/license.html" "${pkgdir}/usr/share/licenses/${pkgname}/license.html"
}
