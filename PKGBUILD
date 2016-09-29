# Maintainer:  Giovanni Santini "ItachiSan" <giovannisantini93@yahoo.it>
# Previous maintainer:  agnotek <agnostic.sn [at]gmail.com>
# Contributor: agnotek <agnostic.sn [at]gmail.com>

pkgname=telegram-desktop-bin
pkgver=0.10.8
pkgrel=1
pkgdesc="Official desktop version of Telegram messaging app - Static binaries"
arch=('i686' 'x86_64')
url="https://desktop.telegram.org"
license=('GPL3')
depends=(
	'glib2'
	'hicolor-icon-theme'
	'libdbus'
	'libx11'
)
optdepends=(
	'libappindicator-gtk2: to hide Telegram in the tray bar (GTK2-based desktop environment)'
	'libappindicator-gtk3: to hide Telegram in the tray bar (GTK3-based desktop environment)'
	'libappindicator-sharp: to hide Telegram in the tray bar (Unity-based desktop environment)'
)
conflicts=('telegram-desktop')
provides=('telegram-desktop')
replaces=('telegram-bin')

# Sources
source=(
	"$pkgname.desktop"
	"$pkgname.png"
	tg.protocol
	https://github.com/telegramdesktop/tdesktop/raw/master/Telegram/Resources/art/icon{16,32,48,64,128,256,512}.png
)
source_i686=('https://updates.tdesktop.com/tlinux32/tsetup32.'$pkgver'.tar.xz')
source_x86_64=('https://updates.tdesktop.com/tlinux/tsetup.'$pkgver'.tar.xz')
# Checksums
sha256sums=('32d1597d67a7ef519367e499fcc978da4cce104e370b3787853446d93b1533d6'
            '4226167b476a75e844ddf0d429068e7e901bbde516810a7d4ca90f8405c01eef'
            'd4cdad0d091c7e47811d8a26d55bbee492e7845e968c522e86f120815477e9eb'
            'cf079b341461e2ed439b7c6ff13d6a31b09e3840df07e9811823fc4b12a23831'
            '0ff2bd9d21a4a265cf414778321623ca92d37d8285e2ce81941bf742a40e1a64'
            '9d6d999cbb9d711f36840256b7704593d77c470f22f367b80bf501a0dc155887'
            'e9570cc49fa66ebabe250598671ffab7bcdbd9875b36763481d9f796b360cf92'
            '94e21d6e7c30ae4f09a42937c46836454b955944ca565e0427f6d7494d034f6d'
            '4226167b476a75e844ddf0d429068e7e901bbde516810a7d4ca90f8405c01eef'
            '2339e94c159975c81a14b6df67a5fad1be02cf032ffb953215d895d1343a3ecb')
sha256sums_i686=('33d5c8556ebbc6582352f3566bcbdeb18d6223a14a075659a9c5d38704aaff84')
sha256sums_x86_64=('4379d406a79f9579f55a14f61fe999229618d481131fa18e43b6e273adfeca70')
# Some installation information
install="$pkgname.install"

package() {

	cd "$srcdir/"

	# Creating needed directories
	install -dm755 "$pkgdir/usr/bin"
	install -dm755 "$pkgdir/usr/share/pixmaps/"
	install -dm755 "$pkgdir/usr/share/applications/"

	# Program
	install -Dm755 "$srcdir/Telegram/Telegram" "$pkgdir/usr/bin/telegram-desktop"

	# Desktop launcher
	install -Dm755 "$srcdir/$pkgname.png" "$pkgdir/usr/share/pixmaps/telegram.png"
	install -Dm755 "$srcdir/$pkgname.desktop" "$pkgdir/usr/share/applications/telegramdesktop.desktop"

	# KDE4 protocol file
	install -d "$pkgdir/usr/share/kde4/services"
	install -m644 "$srcdir/tg.protocol" "$pkgdir/usr/share/kde4/services/tg.protocol"

	# Icons
	local icon_size icon_dir
	for icon_size in 16 32 48 64 128 256 512; do
		icon_dir="$pkgdir/usr/share/icons/hicolor/${icon_size}x${icon_size}/apps"
		install -d "$icon_dir"
		install -m644 "$srcdir/icon${icon_size}.png" "$icon_dir/telegram-desktop.png"
	done
}
sha256sums=('32d1597d67a7ef519367e499fcc978da4cce104e370b3787853446d93b1533d6'
            '4226167b476a75e844ddf0d429068e7e901bbde516810a7d4ca90f8405c01eef'
            'd4cdad0d091c7e47811d8a26d55bbee492e7845e968c522e86f120815477e9eb'
            'cf079b341461e2ed439b7c6ff13d6a31b09e3840df07e9811823fc4b12a23831'
            '0ff2bd9d21a4a265cf414778321623ca92d37d8285e2ce81941bf742a40e1a64'
            '9d6d999cbb9d711f36840256b7704593d77c470f22f367b80bf501a0dc155887'
            'e9570cc49fa66ebabe250598671ffab7bcdbd9875b36763481d9f796b360cf92'
            '94e21d6e7c30ae4f09a42937c46836454b955944ca565e0427f6d7494d034f6d'
            '4226167b476a75e844ddf0d429068e7e901bbde516810a7d4ca90f8405c01eef'
            '2339e94c159975c81a14b6df67a5fad1be02cf032ffb953215d895d1343a3ecb')
sha256sums_i686=('b3b713eca3937d654cd8b2d1184096576d653042fe5ea420a4afa16e18db7893')
sha256sums_x86_64=('416e8c43be1a099395bdbcf14810094f8f9498800084e36fa4246d4404653e0a')
