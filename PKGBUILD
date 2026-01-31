# Maintainer: Felix Kröhnert <kroehnert@cy-core.de>
pkgname=brother-mfc-l8390cdw
pkgver=3.5.1
pkgrel=1
pkgdesc="LPR and CUPS drivers for Brother MFC-L8390CDW"
arch=('i686' 'x86_64')
url="https://support.brother.com/g/b/producttop.aspx?c=de&lang=de&prod=mfcl8390cdw_eu_as"
license=('custom:brother' 'GPL')
install=brother-mfc-l8390cdw.install
depends=('cups' 'poppler' 'ghostscript')
makedepends=('tar' 'perl')
source=("https://download.brother.com/welcome/dlf105766/mfcl8390cdwpdrv-3.5.1-1.i386.deb")
md5sums=('2810ef7fe4a81360f650032a02d1c5c0')
package() {
        ar x mfcl8390cdwpdrv-3.5.1-1.i386.deb && tar xzvf data.tar.gz

	# Patch filenames to work on Arch
	cd $srcdir
	cd opt/brother/Printers/mfcl8390cdw
	find . -type f -exec perl -i -pe 's#/etc/init.d#/etc/rc.d#g; s#printcap\.local#printcap#g' {} +

	# Patch the filepath as we are not adding it to path
	find . -type f -exec perl -i -pe 's#\$LPDCONFIGEXE\=\"brprintconf_\"#\$LPDCONFIGEXE\=\$basedir.\"lpd/brprintconf_"#g' {} +

	# Add proper renderer to ppd
	#sed -i "/\*\%==== Media Selection/i \*OpenUI *pdftops-renderer/PDF Renderer: PickOne\n*Defaultpdftops-renderer: pdftocairo\n*pdftops-renderer pdftocairo/Poppler pdftocairo: \"\"\n*pdftops-renderer pdftops/Poppler pdftops: \"\"\n*pdftops-renderer gs/Ghostscript: \"\"\n*CloseUI: *pdftops-renderer\n" "./cupswrapper/brother_mfcl8390cdw_printer_en.ppd"
	
	cp -rf $srcdir/opt/ $pkgdir/

	ln -s ${CARCH}/brmfcl8390cdwfilter ${pkgdir}/opt/brother/Printers/mfcl8390cdw/lpd/brmfcl8390cdwfilter
  	ln -s ${CARCH}/brprintconf_mfcl8390cdw ${pkgdir}/opt/brother/Printers/mfcl8390cdw/lpd/brprintconf_mfcl8390cdw
}
