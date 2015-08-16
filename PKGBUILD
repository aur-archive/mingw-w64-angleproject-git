# Contributor: Filip Brcic <brcha@gna.org>
# Contributor: jellysheep <max DOT mail AT dameweb DOT de>

pkgname=mingw-w64-angleproject-git
pkgver=2.1.r3427.30d6c25
pkgrel=3
pkgdesc='Angle project built from git source (mingw-w64)'
arch=('any')
url='http://code.google.com/p/angleproject/'
license=('BSD')
groups=('mingw-w64')
depends=()
makedepends=('mingw-w64-gcc' 'gyp-svn' 'git' 'python')
provides=('mingw-w64-angleproject')
conflicts=('mingw-w64-angleproject')
options=('!strip' '!buildflags' 'staticlibs')
source=('angleproject::git+https://chromium.googlesource.com/angle/angle#commit=30d6c25'
        'libGLESv2_mingw32.def'
        'libEGL_mingw32.def'
        '0000-General-fixes-for-ANGLE-2.1.patch'
        '0004-Make-it-possible-to-link-ANGLE-statically-for-single.patch'
        '0008-ANGLE-Dynamically-load-D3D-compiler-from-a-list-or-t.patch'
        '0009-ANGLE-Support-WinRT.patch'
        '0010-ANGLE-Enable-D3D11-for-feature-level-9-cards.patch'
        '0012-ANGLE-fix-semantic-index-lookup.patch'
        '0013-ANGLE-Add-support-for-querying-platform-device.patch'
        '0014-Let-ANGLE-use-multithreaded-devices-if-necessary.patch'
        '0015-ANGLE-Fix-angle-d3d11-on-MSVC2010.patch'
        '0016-ANGLE-Fix-compilation-with-MinGW-D3D11.patch'
        '0017-ANGLE-Fix-compilation-with-D3D9.patch'
        '0018-ANGLE-Fix-releasing-textures-after-we-kill-D3D11.patch'
        'angleproject-undo-mingw-org-compatibility.patch'
        'angleproject-undo-mingw-org-compatibility2.patch'
        'angleproject-disable-debug-annotations.patch'
        'angleproject-undo-shader-renames.patch'
        'angleproject-prevent-multiple-definition-errors.patch'
        'commit-4de44cb'
        'commit-409078f'
        'angleproject-include-import-library-and-use-def-file.patch'
        'angleproject-export-shader-symbols.patch')
sha1sums=('SKIP'
          '7e16a61fbfa6502a87ce1602aabd2274d990bb08'
          'f5bc457abec785245230afce670d5de992196507'
          'e53d9a8e978c95eded3779a2a572aec5831d4785'
          'd8caa3d2c6a5ce96834fbdd38d45f6a1aac89cac'
          '69416b0a83d6ecbbb88a52524e5a3db3fc62b6f8'
          '2224a2b109b994c6c593dabf3b4d4f2b988edf6a'
          'b744cd3dd4d88deb63ebb481f17a8d536fb7b10e'
          '0bdaa75ff30dd1be166205321a23507f95bb9ef2'
          '541075ede625b7db96102deadcfa7d1ddc874ddf'
          'e76a1ad268dbae4466e79cd7e72eae12afee3801'
          'ab7f2dfe67d25b1d346b733564e3bfbf6264e3ac'
          '2a9f710409c4ffa0e7b95f4ec0aa3bba116f5e18'
          '2e15fdfb6749f68cc723289045f4d16ad8ad4626'
          '1ae568414591a4e319b02259a1ab8ca915ba0a42'
          'c6e8e358b21b8ac494dbbac6db37aa214d9b0766'
          'aba1c8180e30e040f3efe8ab40ecd69efa5fcae4'
          '68c9828568c8ed9f1aac3f56283a1e2f3a27889a'
          'd0c45e1a11d9cd2916b36a2d1d696ebf4aa2c8f3'
          '4eb3356e6ab3d2cbd6f5c0d7c5db9e6a5cfcbf30'
          'c889119b1fdd2e3f5bcbc9ce965979c26b5b3bbf'
          '0a7a1eaef478ae31f328dea2be432f6fad814bc7'
          'f199910e90f3978e39f4b6234ebfd689edf165f4'
          'ed30c584a7df2fbb9247192ca69443180627d596')

_architectures="i686-w64-mingw32 x86_64-w64-mingw32"

pkgver() {
    cd "$srcdir/angleproject"
    grep -E "^#define ANGLE_M..OR_VERSION [0-9]+$" src/common/version.h | sed 's/#define ANGLE_M..OR_VERSION //' | tr '\n' '.'
    printf "r%s.%s\n" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
    cd "${srcdir}"/angleproject

    # Install additional .def files
    cp "${srcdir}/libGLESv2_mingw32.def" "src/libGLESv2/"
    cp "${srcdir}/libEGL_mingw32.def" "src/libEGL/"

    # Patches taken from Qt5
    # https://qt.gitorious.org/qt/qtbase/source/2302d386c7a1aa1a96658f79c236d6b8a59db7ac:src/angle/patches
    patch -p4 -i "${srcdir}/0000-General-fixes-for-ANGLE-2.1.patch"
    patch -p4 -i "${srcdir}/0004-Make-it-possible-to-link-ANGLE-statically-for-single.patch"
    patch -p4 -i "${srcdir}/0008-ANGLE-Dynamically-load-D3D-compiler-from-a-list-or-t.patch"
    patch -p4 -i "${srcdir}/0009-ANGLE-Support-WinRT.patch"
    patch -p4 -i "${srcdir}/0010-ANGLE-Enable-D3D11-for-feature-level-9-cards.patch"
    patch -p4 -i "${srcdir}/0012-ANGLE-fix-semantic-index-lookup.patch"
    patch -p4 -i "${srcdir}/0013-ANGLE-Add-support-for-querying-platform-device.patch"
    patch -p4 -i "${srcdir}/0014-Let-ANGLE-use-multithreaded-devices-if-necessary.patch"
    patch -p4 -i "${srcdir}/0015-ANGLE-Fix-angle-d3d11-on-MSVC2010.patch"
    patch -p4 -i "${srcdir}/0016-ANGLE-Fix-compilation-with-MinGW-D3D11.patch"
    patch -p4 -i "${srcdir}/0017-ANGLE-Fix-compilation-with-D3D9.patch"
    patch -p4 -i "${srcdir}/0018-ANGLE-Fix-releasing-textures-after-we-kill-D3D11.patch"

    # Undo a change from 0016-ANGLE-Fix-compilation-with-MinGW-D3D11.patch which
    # implements some missing stuff from the mingw.org toolchain, but which already
    # exists in the mingw-w64 toolchain (and causes breakage)
    patch -p1 -i "${srcdir}/angleproject-undo-mingw-org-compatibility.patch"

    # Same as above but introduced by a change from 0015-ANGLE-Fix-angle-d3d11-on-MSVC2010.patch
    patch -p1 -i "${srcdir}/angleproject-undo-mingw-org-compatibility2.patch"

    # Disable some debug code as it depends on the ID3DUserDefinedAnnotation
    # interface which isn't available in mingw-w64 yet
    # Patch for this is currently pending at http://source.winehq.org/patches/data/108405
    patch -p1 -i "${srcdir}/angleproject-disable-debug-annotations.patch"

    # Undo a change from 0000-General-fixes-for-ANGLE-2.1.patch which renames
    # some shader references, but which doesn't rename the precompiled shaders
    patch -p1 -i "${srcdir}/angleproject-undo-shader-renames.patch"

    # Prevent multiple definition errors during the final link of libGLESv2
    patch -p1 -i "${srcdir}/angleproject-prevent-multiple-definition-errors.patch"

    # Revert commit 4de44cb and commit 409078f as qt5-qtwebkit still depends on it
    patch -p1 -R -i "${srcdir}/commit-4de44cb"
    patch -p1 -R -i "${srcdir}/commit-409078f"

    # Make sure an import library is created and the correct .def file is used during the build
    patch -p1 -i "${srcdir}/angleproject-include-import-library-and-use-def-file.patch"

    # WebKit depends on symbols which are used in the static library called translator_hlsl
    # This static library is linked into the libGLESv2 shared library
    # To allow building WebKit export the required symbols in the libGLESv2 shared library
    patch -p1 -i "${srcdir}/angleproject-export-shader-symbols.patch"

    # Executing .bat scripts on Linux is a no-go so make this a no-op
    echo "" > src/copy_compiler_dll.bat
    chmod +x src/copy_compiler_dll.bat
}

build() {
    cd "${srcdir}"/angleproject

    export CFLAGS="-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions --param=ssp-buffer-size=4"
    export CXXFLAGS="-O2 -g -pipe -Wall -Wp,-D_FORTIFY_SOURCE=2 -fexceptions --param=ssp-buffer-size=4"
    unset LDFLAGS

    for _arch in ${_architectures}
    do
        mkdir -p build-${_arch} && pushd build-${_arch}

        export CXX="${_arch}-g++"
        export AR="${_arch}-ar"

        if [ "${_arch}" = "i686-w64-mingw32" ]
        then
            target="win32"
        else
            target="win64"
        fi

        gyp -D OS=win -D TARGET=$target -D MSVS_VERSION="" --depth . -I ../build/common.gypi ../src/angle.gyp

        # Make sure the correct libraries are linked in
        sed -i s@'^LIBS :='@'LIBS := -ld3d9 -ldxguid'@ ../src/libGLESv2.target.mk
        sed -i s@'^LIBS :='@'LIBS := -ld3d9 -ldxguid -L. -lGLESv2'@ ../src/libEGL.target.mk

        make V=1 CXXFLAGS="-std=c++11 -msse2 -DUNICODE -D_UNICODE -g"

        # Also build static libraries (which are needed by the static Qt build)
        ${AR} rcs libGLESv2.a \
            out/Debug/obj.target/src/common/*.o \
            out/Debug/obj.target/src/common/win32/*.o \
            out/Debug/obj.target/src/compiler/translator/*.o \
            out/Debug/obj.target/src/compiler/translator/depgraph/*.o \
            out/Debug/obj.target/src/compiler/translator/timing/*.o \
            out/Debug/obj.target/src/compiler/preprocessor/*.o \
            out/Debug/obj.target/src/third_party/compiler/*.o \
            out/Debug/obj.target/src/third_party/murmurhash/*.o \
            out/Debug/obj.target/src/third_party/systeminfo/*.o \
            out/Debug/obj.target/src/libGLESv2/*.o \
            out/Debug/obj.target/src/libGLESv2/renderer/*.o \
            out/Debug/obj.target/src/libGLESv2/renderer/d3d/*.o \
            out/Debug/obj.target/src/libGLESv2/renderer/d3d/d3d9/*.o \
            out/Debug/obj.target/src/libGLESv2/renderer/d3d/d3d11/*.o

        ${AR} rcs libEGL.a \
            out/Debug/obj.target/libEGL/../src/common/RefCountObject.o \
            out/Debug/obj.target/libEGL/../src/common/angleutils.o \
            out/Debug/obj.target/libEGL/../src/common/debug.o \
            out/Debug/obj.target/libEGL/../src/common/event_tracer.o \
            out/Debug/obj.target/libEGL/../src/common/mathutil.o \
            out/Debug/obj.target/libEGL/../src/common/tls.o \
            out/Debug/obj.target/libEGL/../src/common/utilities.o \
            out/Debug/obj.target/libEGL/../src/libEGL/AttributeMap.o \
            out/Debug/obj.target/libEGL/../src/libEGL/Config.o \
            out/Debug/obj.target/libEGL/../src/libEGL/Display.o \
            out/Debug/obj.target/libEGL/../src/libEGL/Error.o \
            out/Debug/obj.target/libEGL/../src/libEGL/Surface.o \
            out/Debug/obj.target/libEGL/../src/libEGL/libEGL.o \
            out/Debug/obj.target/libEGL/../src/libEGL/main.o \
            out/Debug/obj.target/libEGL/../src/common/win32/NativeWindow.o

        popd
    done
}

package() {
    cd "${srcdir}"/angleproject

    for _arch in ${_architectures}
    do
        pushd build-${_arch}

        mkdir -p "${pkgdir}"/usr/${_arch}/{bin,lib,include}

        install out/Debug/src/libGLESv2.so "${pkgdir}"/usr/${_arch}/bin/libGLESv2.dll
        install out/Debug/src/libEGL.so "${pkgdir}"/usr/${_arch}/bin/libEGL.dll

        ${_arch}-strip --strip-unneeded "${pkgdir}"/usr/${_arch}/bin/*.dll

        install libGLESv2.a "${pkgdir}"/usr/${_arch}/lib/
        install libEGL.a "${pkgdir}"/usr/${_arch}/lib/

        ${_arch}-strip --strip-debug "${pkgdir}"/usr/${_arch}/lib/libEGL.a
        install libEGL.dll.a "${pkgdir}"/usr/${_arch}/lib/
        install libGLESv2.dll.a "${pkgdir}"/usr/${_arch}/lib/
        ${_arch}-strip --strip-unneeded "${pkgdir}"/usr/${_arch}/lib/*.dll.a

        cp -Rv ../include/* "${pkgdir}"/usr/${_arch}/include/

        popd
    done
}
