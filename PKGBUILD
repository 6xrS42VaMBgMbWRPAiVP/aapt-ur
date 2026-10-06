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
_evmfs_available="$(
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
_git="true"
if [[ ! -v "_git_advice_merge_conflict" ]]; then
  _git_advice_merge_conflict="false"
fi
if [[ ! -v "_git_service" ]]; then
  _git_service="gitlab"
  _git_service="github"
fi
if [[ ! -v "_submodule_update" ]]; then
  _submodule_update="true"
fi
if [[ ! -v "_depth1" ]]; then
  _depth1="true"
fi
if [[ ! -v "_aidl" ]]; then
  _aidl="true"
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
if [[ ! -v "_base_ns" ]]; then
  _base_ns="themartiancompany"
  _base_ns="lineageos"
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
_frameworks_base_commit="45034f0663f960d9ee5fb0a101a4732b71f6e2f4"
pkgrel=68
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
if [[ "${_git}" == "true" ]]; then
  makedepends+=(
    "git"
  )
fi
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
  'sysprop'
)
if [[ "${_aidl}" == "true" ]]; then
  provides+=(
    "aidl"
  )
fi
_android_repo="https://dl.google.com/${_proj}/repository"
_googlesource="https://${_proj}.googlesource.com"
# _android_uri="${_android_repo}/build-tools_r${_displayversion}-linux.zip"
# _android_512sum='c28dd52f8eca82996726905617f3cb4b0f0aee1334417b450d296991d7112cab1288f5fd42c48a079ba6788218079f81caa3e3e9108e4a6f27163a1eb7f32bd7'
_vendor_build_url="${_googlesource}/platform/build"
_zopfli_uri="${_googlesource}/platform/external/zopfli"
_vendor_base_uri="${_googlesource}/platform/frameworks/base"
_vendor_base_url="${_http}/${_base_ns}/${_proj}_frameworks_base"
_vendor_native_uri="${_googlesource}/platform/frameworks/native"
_vendor_core_uri="${_googlesource}/platform/system/core"
_vendor_incremental_delivery="${_googlesource}/platform/system/incremental_delivery"
_vendor_libbase="${_googlesource}/platform/system/libbase"
_vendor_libziparchive="${_googlesource}/platform/system/libziparchive"
_vendor_logging="${_googlesource}/platform/system/logging"
_vendor_aidl="${_googlesource}/platform/system/tools/aidl"
_vendor_sysprop="${_googlesource}/platform/system/tools/sysprop"
_tarname="${_pkg_alt}-${_commit}"
_tarfile="${_tarname}.${_archive_format}"
_base_tarname="base-${_frameworks_base_commit}"
_sum="adb484320ed6fb0265469b10f320f6c71a7eaa3c39279fc06c61e1d60b3b11a6"
_base_sum="boh"
if [[ "${_git}" == "false" ]]; then
  _uri="${_url}/archive/${_commit}.${_archive_format}"
  _src="${_tarfile}::${_uri}"
  _vendor_base_uri="${_vendor_base_url}/archive/${_frameworks_base_commit}.${_archive_format}"
  _vendor_base_src="${_base_tarfile}::${_vendor_base_uri}"
elif [[ "${_git}" == "true" ]]; then
  _uri="git+${_url}#commit=${_commit}"
  _sum="SKIP"
  _src="${_tarname}::${_uri}"
  _vendor_base_uri="git+${_vendor_base_url}#commit=${_frameworks_base_commit}"
  _vendor_base_src="${_base_tarname}::${_vendor_base_uri}"
fi
source=(
  "${_src}"
)
# sha512sums=(
#   "${_android_512sum}"
# )
sha256sums=(
  "${_sum}"
  # "${_base_sum}"
)
if [[ "${_depth1}" == "false" ]]; then
  source+=(
    "${_vendor_base_src}"
  )
  sha256sums=(
    "${_base_sum}"
  )
fi
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
_patches_sums=(
  "339b89d651b972af9007207ebf57d72c296e4aac2282d8ed8eb1a351c7b6f749"
  "9b028802105cc1fef7b7bcd9f7aa4d39bf55e00fc7839a784b464ddfd22d4a2d"
  "9fadc5183cc016d15adf8300b7ea6133f6e186cf7c20ac6df7881d1dd7a029f6"
  "8733ec6cf100bfcd329e9a593331748d2dd0db8d5d77eb0f2daf94401f6f7715"
  "12c5cc8b61c7151ffa907a3b7dd3e6e9f80f1beffbfba4a01628c2aee084653e"
  "f11c788d1bb9da3148750b31966b87eb889293c1870e82f5257cb3c3754074c8"
  "03bc33b7bc880fbeb6596c2a07e76e1f5a99439816a6ffed0b3d7f3f704b7fb5"
  "38e906d632f1a7f8501e4dafae8dbf8e9811851ef2adbdda2510936e7ac4aac7"
  "39a3f19a88ea7f7302fdb59990873be504cd864875c5ec2e3f73a5a062e82491"
  "7e88f30df4ea10151d1c626eff2b9616b552efc86b75f81e42259a201d742db1"
  "c5dc53674307a36a83972259234fab57cce06ed36e7fa075e1334386576e785d"
  "180deb68b94f4c0e4cb0835aebbf26143ea3db7b9fc56c2e274caecd5d76512c"
  "59a0c5041dd6bf58d6cdf54f29aab7d2a46ce29907be365a9b9f2eb2e915f845"
  "01b77100ecfc857b47091f6ffdbe24ba8399ad4374c32cb9e786c982e89af01d"
  "dfeede569e08782bf1cc5354da4dc6bfbba9ce0453d9cbbdfb3467937a9bd8df"
  "80a2cc9c9f2ec00233d75449684bdef21fd757b8ea5cf3341912dfb86b8df0dd"
  "e3bdeb93d9f86bd0348864c5eaef6b31cf3ad3f9ef58ce7b89b1b1db654db34e"
  "56c5d73f3c8efe7a21167def9492c3c199bd1ef2a7d466e3a15603708140ab64"
)
_index=0
for _patch \
  in "${_patches[@]}"; do
  source+=(
    "${_patch}"
  )
  sha256sums+=(
    "${_patches_sums["${_index}"]}"
  )
  _index=$((
    _index + 1))
done

prepare() {
  local \
    _cmd=() \
    _cmd_shallow=() \
    _git_submodule_config \
    _gitconfig=() \
    _email \
    _user=() \
    _msg=() \
    _patch_opts=() \
    _patch_pattern \
    _patch_repl \
    _git_patch_pattern \
    _git_patch_repl \
    _submodule_path \
    _submodules_paths=()
  _patch_opts+=(
    -Np1
    -i
  )
  if [[ ! -e "${HOME}/.gitconfig" ]]; then
    _msg=(
      "WARNING: This package requires"
      "to have configured a global"
      "git user configuration"
      "in '${HOME}/.gitconfig'."
    )
    echo \
      "${_msg[*]}" \
      1>&2
  fi
  _email="PKGBUILD@${_pkg}.${_ns}"
  _user=(
    "The Martian Company's"
    "Aapt Universal Recipe"
  )
  _gitconfig+=(
    "[user]"
    "  email = ${_email}"
    "  name = ${_user[*]}"
  )
  printf \
    "%s\n" \
    "${_gitconfig[@]}" >> \
    "${srcdir}/${_tarname}/.git/config"
  if [[ "${_depth1}" == "true" ]]; then
    git \
      -C \
        "${srcdir}/${_tarname}" \
      submodule \
        init
    git \
      init \
        "${_base_tarname}"
    git \
      -C \
        "${_base_tarname}" \
      remote \
        add \
          origin \
          "${_vendor_base_url}"
    _msg=(
      "Fetching commit"
      "${_base_tarname_commit}"
      "for repository '${_base_tarname}'."
    )
    echo \
      "${_msg[*]}"
    git \
      -C \
        "${_base_tarname}" \
      fetch \
        "origin" \
        --depth \
          1 \
        "${_frameworks_base_commit}" || \
   true
    _msg=(
      "Checking out commit"
      "${_base_tarname_commit}"
      "for repository '${_base_tarname}'."
    )
    echo \
      "${_msg[*]}"
    # git \
    #   -C \
    #     "${_base_tarname}" \
    #   checkout \
    #     "origin" \
    #     "${_frameworks_base_commit}" || \
    #   true
    _msg=(
      "Updating submodule"
      "'${srcdir}/${_tarname}/vendor/base'."
    )
    echo \
      "${_msg[*]}"
    git \
      -C \
      "${_tarname}" \
      config \
        --local \
          "submodule.vendor/base.url" \
         "${srcdir}/${_base_tarname}"
    git \
      -C \
      "${_tarname}" \
      config \
        -f \
        ".gitmodules" \
          "submodule.vendor/base.shallow" \
          "true"
    echo \
      "Repository '${_tarname}'" \
      "'.gitmodules' file:"
    cat \
      "${_tarname}/.gitmodules"
    git \
      -C \
        "${_tarname}" \
      -c \
        protocol.file.allow='always' \
      -c \
        submodule.vendor/base.shallow='true' \
      submodule \
        update \
	  --init \
          --recommend-shallow \
          "vendor/base" || \
    true
    git \
      -C \
        "${_tarname}" \
      -c \
        protocol.file.allow='always' \
      -c \
        submodule.vendor/base.shallow='true' \
      submodule \
        update \
          --recommend-shallow \
          "vendor/base" || \
    true
  fi
  cd \
    "${srcdir}/${_tarname}"
  _cmd=(
    "execute_process(COMMAND"
      "git"
        "submodule"
          "--quiet"
            "update)"
  )
  _cmd_shallow=(
    "execute_process(COMMAND"
      "git"
        "submodule"
          "--quiet"
            "update"
              "--init"
              "--recommend-shallow)"
  )
  sed \
    "s/${_cmd[*]}/${_cmd_shallow[*]}/g" \
    -i \
    "vendor/CMakeLists.txt"
  _patch_pattern='${CMAKE_CURRENT_SOURCE_DIR}/${v} -p1 -i ${patch}'
  _patch_repl='${CMAKE_CURRENT_SOURCE_DIR}/${v} -p1 -i ${patch} || true'
  # sed \
  #   "s%${_patch_pattern}%${_patch_repl}%g" \
  #   -i \
  #   "vendor/CMakeLists.txt"
  _git_patch_pattern='${CMAKE_CURRENT_SOURCE_DIR}/${v} am ${patches}'
  _git_patch_repl='${CMAKE_CURRENT_SOURCE_DIR}/${v} am ${patches} || true'
  # sed \
  #   "s%${_git_patch_pattern}%${_git_patch_repl}%g" \
  #   -i \
  #   "vendor/CMakeLists.txt"
  sed \
    -e \
      "30d;
       31d;
       32d;
       38d;
       39d;
       40d" \
    -i \
    "vendor/CMakeLists.txt"
  _msg=(
    "New vendor/CMakeLists.txt:"
  )
  echo \
    "${_msg[*]}"
  cat \
    "vendor/CMakeLists.txt"
  if [[ "${_git}" == "true" ]]; then
    if [[ "${_submodule_update}" == "true" ]]; then
      git \
        submodule \
          update \
            --init \
            --recursive \
            --recommend-shallow || \
      true
      _submodules_paths+=( $(
        cat \
          ".gitmodules" |
          grep \
            -e \
              "^\[submodule \"" |
            sed \
              "s/^\[submodule \"//g;
               s/\"\]$//g")
      )
      for _submodule_path \
        in "${_submodules_paths[@]}"; do
          _git_submodule_config="${srcdir}/${_tarname}/.git/modules/${_submodule_path}/config"
        if [[ -e "${_git_submodule_config}" ]]; then
          printf \
            "%s\n" \
            "${_gitconfig[@]}" >> \
            "${srcdir}/${_tarname}/.git/modules/${_submodule_path}/config"
        else
          echo \
            "File '${_git_submodule_config}'" \
            "does not exist." \
            1>&2
        fi
        git \
          -C \
            "${PWD}/${_path}" \
          config \
            "user.email" \
              "${_email}" || \
        true
        git \
          -C \
            "${PWD}/${_path}" \
          config \
            "user.name" \
              "${_user[*]}" || \
        true
        if [[ "${_git_advice_merge_conflict}" == "false" ]]; then
          git \
            -C \
              "${PWD}/${_path}" \
            config \
              set \
                "advice.mergeConfict" \
                  "false"
        fi
      done
    fi
  elif [[ "${_git}" == "false" ]]; then
    _msg=(
      "Not supported."
    )
    echo \
      "${_msg[*]}" \
      1>&2
    exit \
      1
  fi
  if [[ "${_os}" == "Android" ]]; then
    for _patch \
      in "${_patches[@]}"; do
      patch \
        "${_patch_opts[@]}" \
        "${srcdir}/${_patch}"
    done
  elif [[ "${_os}" == "Msys" ]]; then
    for _patch \
      in "${_patches[@]}"; do
      patch \
        "${_patch_opts[@]}" \
        "${srcdir}/${_patch}"
    done
  fi
  # git \
  #   config \
  #     --global \
  #     "user.email" \
  #       "${_email}" || \
  # true
  # git \
  #   config \
  #     --global \
  #     "user.name" \
  #       "${_user[*]}" || \
  # true
  git \
    config \
      "user.email" \
        "${_email}" || \
  true
  git \
    config \
      "user.name" \
        "${_user[*]}" || \
  true
  if [[ "${_git_advice_merge_conflict}" == "false" ]]; then
    _msg=(
      "Setting 'advice.mergeConfict'"
      "to 'false'."
    )
    echo \
      "${_msg[*]}"
    git \
      config \
        set \
          "advice.mergeConfict" \
            "false"
  fi
}

build() {
  local \
    _cflags=() \
    _cmake_opts=() \
    _cppflags=() \
    _cxxflags=() \
    _protoc
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
  DESTDIR="${pkgdir}" \
  cmake \
    --install \
      "${srcdir}/${_tarname}/build/"
  if [[ "${_aidl}" == "false" ]]; then
    rm \
      -vrf \
      "${pkgdir}/usr/bin/aidl"
  fi
}
