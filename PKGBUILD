# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=sqitch
_srcname=App-Sqitch
pkgver=0.996
pkgrel=1
pkgdesc="Sane database change management"
arch=('i686' 'x86_64')
depends=('perl' 'perl-class-xsaccessor' 'perl-clone' 'perl-config-gitlike' 'perl-datetime' 'perl-dbd-sqlite' 'perl-devel-stacktrace' 'perl-digest-sha1' 'perl-encode-locale' 'perl-file-homedir' 'perl-hash-merge' 'perl-io-pager' 'perl-ipc-run3' 'perl-ipc-system-simple' 'perl-libintl-perl' 'perl-list-moreutils' 'perl-moose' 'perl-mouse' 'perl-mousex-nativetraits' 'perl-mousex-types-path-class' 'perl-namespace-autoclean' 'perl-path-class' 'perl-perlio-utf8-strict' 'perl-role-hasmessage' 'perl-role-identifiable' 'perl-string-formatter' 'perl-string-shellquote' 'perl-sub-exporter' 'perl-template-tiny' 'perl-throwable' 'perl-try-tiny' 'perl-type-tiny' 'perl-type-tiny-xs' 'perl-uri-db' 'sqlite')
checkdepends=('perl-test-dir' 'perl-test-file' 'perl-test-file-contents' 'perl-test-mockmodule' 'perl-test-deep' 'perl-test-exception' 'perl-test-nowarnings')
makedepends=('perl-module-build')
optdepends=('postgresql: PostgreSQL'
            'libfbclient: FirebirdSQL'
            'mariadb: MySQL'
            'oracle: Oracle DB')
url="http://sqitch.org"
license=('MIT')
source=($pkgname-$pkgver.tar.gz::https://cpan.metacpan.org/authors/id/D/DW/DWHEELER/$_srcname-$pkgver.tar.gz)
sha256sums=('5ea0f742ba066a62512664f60528b57d1ee6577c88fdd51e5f73b070e37c9b72')
options=('!emptydirs')
provides=('sqitch' 'perl-app-sqitch')
conflicts=('perl-app-sqitch')

build() {
  cd "${srcdir}/${_srcname}-${pkgver}"

  msg 'Building...'
  perl Build.PL INSTALLDIRS=vendor
  ./Build installdeps
  ./Build
}

check() {
  cd "${srcdir}/${_srcname}-${pkgver}"

  msg 'Testing...'
  ./Build test
}

package() {
  cd "${srcdir}/${_srcname}-${pkgver}"

  msg 'Installing...'
  ./Build prefix="$pkgdir/usr" install
  mv "$pkgdir/usr/etc" "$pkgdir/etc"
}
