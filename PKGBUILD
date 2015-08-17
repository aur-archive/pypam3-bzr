pkgname=pypam3-bzr
pkgver=20
pkgrel=2
arch=('any')
license=('GPL')
makedepends=('bzr')
depends=('pam' 'python3')
url="https://launchpad.net/ubuntu/precise/+source/python-pam"
pkgdesc="A Python interface to the PAM library (configured to build for python3)"
source=('2and3compat.patch')
md5sums=('7b30d36545f6ca0c68145340dbdf5f56')

_bzrtrunk="https://code.launchpad.net/~vorlon/ubuntu/quantal/python-pam/python3"
_bzrmod=python-pam

build()
{
	cd "${srcdir}"
	if [[ -d "$_bzrmod" ]]; then
		cd "$_bzrmod" && bzr --no-plugins pull "$_bzrtrunk" -r "$pkgver"
		msg "The local files are updated."
	else
		bzr --no-plugins branch "$_bzrtrunk" "$_bzrmod" -q -r "$pkgver"
		cd python-pam
	fi
	patch -Np1 -i "${srcdir}/2and3compat.patch"
	python3 setup.py build 
}

package()
{
	cd "${srcdir}/python-pam"
	python3 setup.py install --root="${pkgdir}"
}
