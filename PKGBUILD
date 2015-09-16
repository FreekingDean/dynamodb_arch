# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Your Name <youremail@domain.com>
pkgname=dynamodb
pkgver=1.0
pkgrel=1
pkgdesc="Package to create a service that will run DynamoDB locally."
arch=('x86_64')
url="http://docs.aws.amazon.com/amazondynamodb/latest/developerguide/Tools.DynamoDBLocal.html"
license=('custom:DynamoDB Local License Agreement')
depends=('java-runtime')
install=dynamodb.install
source=("dynamodb.service" "config.cfg" "dynamodb" "http://dynamodb-local.s3-website-us-west-2.amazonaws.com/dynamodb_local_latest.tar.gz")
md5sums=('bffad98b32691ace89bed3cd95817ae1' '6f3dec74c425a20d35dde96de2517cad' '8e180068df12e2714898335fb916a951' 'c8f797919053a34ac34b5204a09f551e')

package() {
  cd "$pkgdir"

  mkdir -p "usr/bin" "var/lib/dynamodb" "etc/dynamodb" "usr/share/dynamodb" "usr/lib/systemd/system"
  install -Dm755 "$srcdir/dynamodb" "./usr/bin"
  install -Dm755 "$srcdir/config.cfg" "./etc/dynamodb/"
  cp -dr --no-preserve=ownership "$srcdir/DynamoDBLocal_lib/" "./usr/share/dynamodb"
  install -Dm644 "$srcdir/DynamoDBLocal.jar" "./usr/share/dynamodb"
  install -Dm644 "$srcdir/dynamodb.service" "./usr/lib/systemd/system/dynamodb.service"
}
