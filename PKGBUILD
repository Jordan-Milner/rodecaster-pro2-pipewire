# Maintainer: Jordan Milner <jordan.l.milner@gmail.com>
pkgname=rodecaster-pro2-pipewire
pkgver=1.0.0
pkgrel=1
pkgdesc="PipeWire/WirePlumber configuration for RODE RODECaster Pro II with proper channel names"
arch=('any')
url="https://github.com/jmilnz/rodecaster-pro2-pipewire"
license=('MIT')
depends=('pipewire' 'wireplumber')
source=(
    '50-rodecaster-pro2.conf'
    '51-rodecaster-pro2-rename.conf'
    'LICENSE'
)
sha256sums=('b156e671a98137920477f25aee0ee2ff861d8a16f7c74df30493fbcbb74c95f9'
            '3765a0880a7d9b05fcc0ffcc96fd5e778eda82810691aaafd2c699b890d474d6'
            'cfa77bfffb8256eec180f2b9b478b8e40e5cebcf7e9ad18f834beb64c716d719')

package() {
    # PipeWire config for pro-audio profile
    install -Dm644 "$srcdir/50-rodecaster-pro2.conf" \
        "$pkgdir/usr/share/pipewire/pipewire.conf.d/50-rodecaster-pro2.conf"

    # WirePlumber config for device renaming
    install -Dm644 "$srcdir/51-rodecaster-pro2-rename.conf" \
        "$pkgdir/usr/share/wireplumber/wireplumber.conf.d/51-rodecaster-pro2-rename.conf"

    # License
    install -Dm644 "$srcdir/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
