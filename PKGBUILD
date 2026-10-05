# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributors:
#   Biswapriyo Nath
#     <nathbappai@gmail.com>
#   Amin Vakil
#     <info AT aminvakil DOT com>
#   xgdgsc
#     <xgdgsc @t gmail dot com>
#   mynacol
#     <dc07d át mynacol dót xyz>

_os="$(
  uname \
    -o)"
if [[ "${_os}" == "Android" ]]; then
  _compiler="clang"
  _libcompiler="libc++"
  _libc="ndk-sysroot"
elif [[ "${_os}" == "GNU/Linux" ]]; then
  _compiler="gcc"
  _libc="gcc-libs"
  _libcompiler="libgcc"
elif [[ "${_os}" == "Msys" ]]; then
  _libc="msys2-w32api-runtime"
  _libc_headers="msys2-w32api-headers"
  _compiler="gcc"
  _libcompiler="gcc-libs"
  _sh="sh"
  _mailcap="winpty"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_git_service" ]]; then
  _git_service="gitlab"
  _git_service="github"
fi
if [[ ! -v "_archive_format" ]]; then
  if [[ "${_git}" == "true" ]]; then
    if [[ "${_evmfs}" == "true" ]]; then
      _archive_format="bundle"
    elif [[ "${_evmfs}" == "false" ]]; then
      _archive_format="git"
    fi
  elif [[ "${_git}" == "false" ]]; then
    if [[ "${_git_service}" == "github" ]]; then
      _archive_format="zip"
    elif [[ "${_git_service}" == "gitlab" ]]; then
      _archive_format="tar.gz"
    fi
  fi
fi
if [[ ! -v "_ns" ]]; then
  _ns="termux"
  _ns="themartiancompany"
fi
if [[ ! -v "_proj" ]]; then
  _proj=android
fi
_sdk=${_proj}
_pkg=aapt
_pkg_alt="${_proj}-build-tools"
pkgbase="${_pkg}"
pkgname=(
  "${_pkg}"
)
# _ver="$(
#   cat \
#     "${srcdir}/$_android/source.properties" |
#     grep \
#       ^Pkg.Revision= |
#       sed \
#         's/Pkg.Revision=\([0-9.]*\).*/\1/')"
# if [[ "${_os}" == "GNU/Linux" ]]; then
#   _major=34
#   _minor=0
#   _micro=0
#   _mini=0
#   _android_ver="14"
#   _displayversion=34
# elif [[ "${_os}" == "GNU/Linux" ]]; then
   _major=16
   _minor=0
   _micro=0
   _mini=4
   _android_ver="14"
   _displayversion=34
# fi
_ver="${_major}.${_minor}.${_micro}"
if [[ "${_mini}" != "" ]]; then
  _ver="${_ver}.${_mini}"
fi
_android="${_proj}-${_android_ver}"
_pkgver="r${_ver}"
pkgver="${_ver}"
_commit="c4edf8539a34a8600538e6642c1ecb170452a79e"
pkgrel=7
_pkgdesc=(
  'Build-Tools for Google Android SDK'
  '(aapt, aidl, dexdump, dx, llvm-rs-cc)'
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'aarch64'
  'arm'
  'armv7l'
  'armv8l'
  'i686'
  'x86_64'
)
# Android SDK is proprietary
# so while The Martian Company can
# publish a CI-compatible repository,
# no binary packages can be distributed.
# This package is one of the open-source
# distributable programs which are
# also part of Android SDK.
_http="https://${_git_service}.com"
_url="${_http}/${_ns}/${_pkg_alt}"
url="${_url}"
license=(
  "Apache2"
)
_expat="expat"
_gtest="gtest"
_zopfli="zopfli"
if [[ "${_os}" == "Android" ]]; then
  # To keep compatibility
  # with Termux Debian-based
  # tree, but really it's
  # optional and you should
  # move from Termux altogether
  # because up so far they've
  # said themselves unavailable
  # to ditch the
  # Debian nomenclature and
  # adopt one which is compatible
  # with the Arch/MSys2/MinGW64 one
  # as well.
  _expat="libexpat"
  _gtest="googletest"
  _zopfli="libzopfli"
fi
depends=(
  "abseil-cpp"
  "${_libc}"
  "${_libcompiler}"
  'bash'
  "fmt"
  "libpng"
  # sysprof-specific
  "protobuf"
  'zlib'
  "${_zopfli}"
)
makedepends=(
  "cmake"
  "${_compiler}"
  "${_gtest}"
  "fmt"
  "libpng"
  "protobuf"
)
_zopfli_optdepends=(
  "zopfli:"
    "For the compression algorithm support."
)
optdepends=(
  'lib32-gcc-libs'
  'lib32-zlib'
  'java-runtime'
  "${_zopfli_optdepends[*]}"
)
provides=(
  'aapt'
  'aapt2'
  'aidl'
  'sysprop'
)
_android_repo="https://dl.google.com/${_proj}/repository"
# _android_uri="${_android_repo}/build-tools_r${_displayversion}-linux.zip"
# _android_512sum='c28dd52f8eca82996726905617f3cb4b0f0aee1334417b450d296991d7112cab1288f5fd42c48a079ba6788218079f81caa3e3e9108e4a6f27163a1eb7f32bd7'
if [[ "${_git}" == "false" ]]; then
  _uri="${_url}/archive/${_commit}.${_archive_format}"
fi
_tarname="${_pkg_alt}-${_commit}"
_tarfile="${_tarname}.${_archive_format}"
_sum="adb484320ed6fb0265469b10f320f6c71a7eaa3c39279fc06c61e1d60b3b11a6"
_src="${_tarfile}::${_uri}"
source=(
  "${_src}"
)
# sha512sums=(
#   "${_android_512sum}"
# )
sha256sums=(
  "${_sum}"
)
options=(
  '!strip'
)

_patches=(
  "aidl-aidl_language.cpp.patch"
  "aidl-aidl_language.h.patch"
  "androidfw-Asset.cpp.patch"
  "androidfw-AssetManager.cpp.patch"
  "androidfw-ResourceTypes.cpp.patch"
  "incfs-util-map_ptr.cpp.patch"
  "include-android-base-unique_fd.h.patch"
  "libbase-properties.cpp.patch"
  "libcutils-native_handle.cpp.patch"
  "libcutils-properties.cpp.patch"
  "libcutils-sockets_unix.cpp.patch"
  "liblog-android-log.h.patch"
  "liblog-logger_write.cpp.patch"
  "libutils-Threads.cpp.patch"
  "libutils-misc.cpp.patch"
  "libziparchive-zip_archive.cc.patch"
  "libziparchive-zip_archive_stream_entry.cc.patch"
  "libziparchive-zip_writer.cc.patch"
)

prepare() {
  cd \
    "${_tarname}"
  if [[ "${_os}" == "Android" ]]; then
    for _patch \
      in "${_patches[@]}"; do
      patch \
        -Np1 \
        -i \
        "${srcdir}/${_patch}"
    done
  fi
  true
}

build() {
  local \
    _cflags=() \
    _cmake_opts=() \
    _cppflags=() \
    _cxxflags=() \
    _protoc
  rm \
    "${HOME}/.gitconfig.lock"
  git \
    config \
      "user.email" \
        "PKGBUILD@${_pkg}.${_ns}" || \
  true
  rm \
    "${HOME}/.gitconfig.lock"
  _cppflags+=(
    -DNDEBUG
    -D__ANDROID_SDK_VERSION__="__ANDROID_API"
    -D_FILE_OFFSET_BITS="64"
    -DPROTOBUF_USE_DLLS
    -DANDROID_BUILD_TOOLS_DEV_MODE="ON"
  )
  _cflags+=(
    "${CFLAGS}"
    -fPIC
  )
  _cxxflags=(
    "${CXXFLAGS}"
    -fPIC
  )
  _protoc="$(
    command \
      -v \
      "protoc")"
  _cmake_opts+=(
    # --trace-expand 
    # -G
    #   "Ninja"
    -D
      CMAKE_BUILD_TYPE="Release"
    -D
      CMAKE_INSTALL_PREFIX="/usr/"
    -D
      protobuf_generate_PROTOC_EXE="${_protoc}"
    # -D
    #   CMAKE_VERBOSE_MAKEFILE:BOOL="ON"
    -S
      "${srcdir}/${_tarname}/"
  )
  _flags+=(
    CC="${_cc}"
    CXX="${_cxx}"
    CXXFLAGS="${_cxxflags[*]}"
  )
  CFLAGS="${_cflags[*]}" \
  CPPFLAGS="${_cppflags[*]}" \
  CXXFLAGS="${_cxxflags[*]}" \
  cmake \
    -B \
      "${srcdir}/${_tarname}/build/" \
    "${_cmake_opts[@]}"
  CFLAGS="${_cflags[*]}" \
  CPPFLAGS="${_cppflags[*]}" \
  CXXFLAGS="${_cxxflags[*]}" \
  cmake \
    --build \
      "${srcdir}/${_tarname}/build/"
}

_root_get() {
  local \
    _bin \
    _env \
    _root \
    _usr
  _env="$(
    command \
      -v \
      "env")"
  _bin="$(
    dirname \
      "${_env}")"
  _usr="$(
    dirname \
      "${_bin}")"
  _root="$(
    dirname \
      "${_usr}")"
  if [[ "${_root}" == "/" ]]; then
    _root=""
  fi
  echo \
    "${_root}"
}

package() {
  local \
    _binaries=() \
    _f \
    _target \
    _root
  _root="$(
    _root_get)"
  cd \
    "${_tarname}"
  cmake \
    --install \
      "${srcdir}/${_tarname}/build/"
  # install \
  #   -d \
  #   "usr/share/licenses/${pkgname}/"
  # ln \
  #   -s \
  #   "${_root}/opt/${_sdk}/build-tools/${_ver}/NOTICE.txt" \
  #   "usr/share/licenses/${pkgname}/NOTICE.txt"
  # sed \
  #   -i \
  #   "s/@major@/${_major}/g;
  #    s/@minor@/${_minor}/g;
  #    s/@micro@/${_micro}/g;
  #    s/@displayv@/${_displayversion}/g;
  #    s/@pathv@/${_ver}/g" \
  #    "${srcdir}/package.xml"
  # install \
  #   -Dm644 \
  #   "${srcdir}/package.xml" \
  #   "opt/${_sdk}/build-tools/${_ver}/package.xml"
  # ln \
  #   -s \
  #   "${_root}/opt/${_sdk}/build-tools/${_ver}/package.xml" \
  #   "usr/share/licenses/${pkgname}/package.xml"
  # _target="opt/${_sdk}/build-tools/${_ver}"
  # mkdir \
  #   -p \
  #   "${_target}"
  # cp \
  #   -r \
  #   "${srcdir}/${_android}/"* \
  #   "${_target}"
  # chmod \
  #   +Xr \
  #   -R \
  #   "${_target}"
  # Add symlinks to binaries to usr/bin/
  # mkdir \
  #   -p \
  #   "usr/bin/"
  # lld is also provided by
  # extra/lld, not creating symlink
  # _binaries=( $(
  #   find \
  #     "${_target}" \
  #     -maxdepth \
  #       1 \
  #     -type \
  #       "f" \
  #     -executable \
  #     -not \
  #     -iname \
  #       "lld" \
  #     -printf \
  #       "%f\n")
  # )
  # for _f in ${_binaries[@]}; do
  #   ln \
  #     -s \
  #     "${_root}/${_target}/${_f}" \
  #     "usr/bin/${_f}"
  # done
}
