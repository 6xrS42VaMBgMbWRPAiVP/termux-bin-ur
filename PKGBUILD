# SPDX-License-Identifier: AGPL-3.0

#    -----------------------------------------------------
#    Copyright © 2024, 2025, 2026  Pellegrino Prevete
#
#    All rights reserved
#    -----------------------------------------------------
#
#    This program is free software: you can redistribute
#    it and/or modify it under the terms of the
#    GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of
#    the License, or (at your option) any later version.
#
#    This program is distributed in the hope that it
#    will be useful, but WITHOUT ANY WARRANTY;
#    without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
#    See the GNU Affero General Public License for
#    more details.
#
#    You should have received a copy of the
#    GNU Affero General Public License
#    along with this program.
#    If not, see <https://www.gnu.org/licenses/>.

# Maintainers:
#   Truocolo
#     <truocolo@aol.com>
#     <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
#   Pellegrino Prevete (dvorak)
#     <pellegrinoprevete@gmail.com>
#     <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

if [[ ! -v "_os" ]]; then
  _os="$(
    uname \
    -o)"
fi
_arch="$(
  uname \
    -m)"
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
if [[ ! -v "_fdroid" ]]; then
  _fdroid="false"
fi
if [[ ! -v "_github" ]]; then
  _github="true"
fi
if [[ ! -v "_system_install" ]]; then
  _system_install="false"
fi
if [[ ! -v "_user_install" ]]; then
  _user_install="false"
fi
if [[ "${_system_install}" == "true" ]]; then
  _install_type="system"
elif [[ "${_user_install}" == "true" ]]; then
  _install_type="user"
fi
if [[ ! -v "_offline" ]]; then
  _offline="false"
fi
if [[ ! -v "_git" ]]; then
  _git="false"
fi
if [[ ! -v "_git_service" ]]; then
  _git_service="github"
fi
if [[ ! -v "_cmd" ]]; then
  _cmd="true"
  if [[ "${_evmfs}" == "true" ]]; then
    _cmd="false"
  fi
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
if [[ ! -v "_docs" ]]; then
  _docs="true"
  if [[ "${_arch}" == "armv8l" ]]; then
    _docs="false"
  fi
fi
_py="python"
_pkgname=termux
_pkg="com.${_pkgname}"
_Pkg="Termux"
pkgbase="${_pkgname}-bin"
pkgname=(
  "${pkgbase}"
)
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkgname}-docs"
  )
fi
pkgver=0.118.1
# For building source on-device
_commit="e117ccae32d5a7d75479b61f034000122fe9fa24"
_cmd_commit="871a50c11278990214d684d39ac592f0401a5df9"
_cmd_man_commit="7ffa116f99599f027e1a371e92ded76b6b7462a9"
pkgrel=31
_fdroid_pkgrel=1000
if [[ "${_fdroid}" == "true" ]]; then
  pkgrel="${_fdroid_pkgrel}"
fi
_pkgdesc=(
  "Terminal emulator application"
  "for Android OS extendible by"
  "variety of packages."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'arm'
  "armv7l"
  "armv8l"
  'aarch64'
  'i686'
  "pentium4"
  'x86_64'
)
_aarch="${_arch}"
if [[ "${_arch}" == "armv7l" || \
      "${_arch}" == "armv8l" || \
      "${_arch}" == "arm" ]]; then
  _aarch="armeabi-v7a"
elif [[ "${_arch}" == "aarch64" ]]; then
  _aarch="arm64-v8a"
elif [[ "${_arch}" == "i686" ]]; then
  _aarch="x86"
fi
url="${_pkgname}.dev"
license=(
  'GPL3'
)
depends=(
)
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
    'inteppacman'
  )
fi
optdepends=(
)
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  optdepends+=(
  )
makedepends=(
  'coreutils'
  "make"
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
checkdepends=(
)
provides=(
  "${_pkgname}=${pkgver}"
)
conflicts=(
  "${_pkgname}"
)
if [[ "${_cmd}" == "true" ]]; then
  provides+=(
    "termux-cmd=${pkgver}"
    "termux-cli=${pkgver}"
  )
  conflicts+=(
    "termux-cmd"
    "termux-cli"
  )
fi
source=()
sha256sums=()
_fdroid_url="https://f-droid.org/repo"
_http="https://github.com"
_ns="${_pkgname}"
_cmd_ns="themartiancompany"
_github_url="${_http}/${_ns}/${_pkgname}-app"
_cmd_url="${_http}/${_cmd_ns}/${_pkgname}"
_cmd_man_url="${_http}/${_cmd_ns}/${_pkgname}-man"
if [[ ! -v "_tag_name" ]]; then
  if [[ "${_fdroid}" == "true" ]]; then
    _tag_name="pkgrel"
  fi
  if [[ "${_github}" == "true" ]]; then
    _tag_name="pkgver"
  fi
fi
if [[ ! -v "_tag" ]]; then
  if [[ "${_fdroid}" == "true" ]]; then
    _tag="${pkgrel}"
  fi
  if [[ "${_github}" == "true" ]]; then
    _tag="{pkgver}"
  fi
fi
_tarname="${_pkgname}-${pkgver}-${pkgrel}"
if [[ ! -v "_cmd_tag_name" ]]; then
  _cmd_tag_name="commit"
fi
if [[ ! -v "_cmd_tag" ]]; then
  _cmd_tag="${_cmd_commit}"
fi
if [[ ! -v "_cmd_man_tag_name" ]]; then
  _cmd_man_tag_name="commit"
fi
if [[ ! -v "_cmd_man_tag" ]]; then
  _cmd_man_tag="${_cmd_man_commit}"
fi
_cmd_tarname="${_pkgname}-cmd-${_cmd_tag}"
_cmd_tarfile="${_cmd_tarname}.${_archive_format}"
_cmd_man_tarname="${_pkgname}-cmd-man-${_cmd_man_tag}"
_cmd_man_tarfile="${_cmd_man_tarname}.${_archive_format}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
source=()
sha256sums=()
_cmd_github_sum="a3568c1fdd79cfaae6aa63ed117683fbbfdc0df59d7dd55a98b9bd3f2ab4d989"
_cmd_man_github_sum="e04d018b68bd5f5f7598d17d9eaf8a318986c89031f439abe7ea4ba5ef6d9f15"
if [[ "${_git}" == true ]]; then
  _url="${_github_url}"
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_fdroid}" == "true" ]]; then
    _url="${_fdroid_url}"
    _sum="SKIP"
    if [[ "${_tag_name}" == 'pkgrel' ]]; then
      _src="${_tarname}.apk::${_url}/${_pkg}_${pkgrel}.apk"
      _sig="${_tarname}.apk.sig::${_url}/${_pkg}_${pkgrel}.apk.asc"
      source+=(
        "${_sig}"
      )
      sha256sums+=(
        "SKIP"
      )
      _sum="f137958392a800fca583bfc00f191b8edb29b77c705fddf27dffb6c26ca5d413"
    fi
  elif [[ "${_github}" == "true" ]]; then
    _sum="SKIP"
    _url="${_github_url}"
    if [[ "${_tag_name}" == "pkgver" ]]; then
      _dl_name="${_pkgname}-app_v${pkgver}+github-debug_${_aarch}.apk"
      _src="${_tarname}.apk::${_url}/releases/download/v${pkgver}/${_dl_name}"
      if [[ "${_aarch}" == "arm64-v8a" ]]; then
        _sum="72c8d3cf7cb12d8c550a6b2750bd00bc99ad084c70f8ff0d2ffa9189e685ce4f"
      elif [[ "${_aarch}" == "armeabi-v7a" ]]; then
        _sum="925a169cfafa2181066bb52c58da7b3514110dfd5f9b8f6d84df897842988e93"
      elif [[ "${_aarch}" == "x86" ]]; then
        _sum="084ada98b58d28e9df38b234afb8653a53e37a237e7446e3e3077c68c5281b7c"
      elif [[ "${_aarch}" == "x86_64" ]]; then
        _sum="cc63b1cda554adf84a152f99703847871790943fb0ce492ec6d200bd0bec2dc6"
      fi
    elif [[ "${_tag_name}" == "commit" ]]; then
      _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
      _sum="dacf4a05e8dab38c49034e5d58deb477c36d005fe81324cf7973ba5487d87eb7"
    fi
  fi
fi
if [[ "${_cmd}" == "true" ]]; then
  if [[ "${_evmfs}" == "true" ]]; then
    if [[ "${_git}" == "false" ]]; then
      _src="${_evmfs_cmd_src}"
      _cmd_sum="SKIP"
      source+=(
        "${_cmd_sig_src}"
      )
      sha256sums+=(
        "${_cmd_sig_sum}"
      )
    fi
  elif [[ "${_evmfs}" == "false" ]]; then
    if [[ "${_git}" == true ]]; then
      _cmd_src="${_cmd_tarname}::git+${_cmd_url}#${_cmd_tag_name}=${_cmd_tag}?signed"
      _cmd_sum="SKIP"
    elif [[ "${_git}" == false ]]; then
      _uri=""
      if [[ "${_git_service}" == "github" ]]; then
        if [[ "${_cmd_tag_name}" == "commit" ]]; then
          _cmd_uri="${_cmd_url}/archive/${_cmd_tag}.${_archive_format}"
          _cmd_sum="${_cmd_github_sum}"
        fi
      elif [[ "${_git_service}" == "gitlab" ]]; then
        if [[ "${_cmd_tag_name}" == "commit" ]]; then
          _cmd_uri="${_cmd_url}/-/archive/${_cmd_tag}/${_cmd_tag}.${_archive_format}"
        fi
      fi
      _cmd_src="${_cmd_tarfile}::${_cmd_uri}"
    fi
  fi
  source+=(
    "${_cmd_src}"
  )
  sha256sums+=(
    "${_cmd_sum}"
  )
fi
if [[ "${_docs}" == "true" ]]; then
  if [[ "${_evmfs}" == "true" ]]; then
    if [[ "${_git}" == "false" ]]; then
      _src="${_evmfs_cmd_man_src}"
      source+=(
        "${_cmd_man_sig_src}"
      )
      sha256sums+=(
        "${_cmd_man_sig_sum}"
      )
    fi
  elif [[ "${_evmfs}" == "false" ]]; then
    if [[ "${_git}" == true ]]; then
      _cmd_man_src="${_cmd_man_tarname}::git+${_cmd_man_url}#${_cmd_man_tag_name}=${_cmd_man_tag}"
      _cmd_man_sum="SKIP"
    elif [[ "${_git}" == false ]]; then
      if [[ "${_git_service}" == "github" ]]; then
        if [[ "${_cmd_tag_name}" == "commit" ]]; then
          _cmd_man_uri="${_cmd_url}-man/archive/${_cmd_man_tag}.${_archive_format}"
          _cmd_man_sum="${_cmd_man_github_sum}"
        fi
      elif [[ "${_git_service}" == "gitlab" ]]; then
        if [[ "${_cmd_tag_name}" == "commit" ]]; then
          _cmd_uri="${_cmd_url}-man/-/archive/${_cmd_man_tag}/${_cmd_man_tag}.${_archive_format}"
        fi
      fi
      _cmd_man_src="${_cmd_man_tarfile}::${_cmd_man_uri}"
    fi
  fi
  source+=(
    "${_cmd_man_src}"
  )
  sha256sums+=(
    "${_cmd_man_sum}"
  )
fi

source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)

noextract=(
  "${_src}"
)
validgpgkeys=(
  # F-droid binary releases
  "37D2C98789D8311948394E3E41E7044E1DBA2E89"
)

package_termux-bin() {
  local \
    _dest_dir \
    _dest \
    _extra_libs=() \
    _make_opts=() \
    _manifest \
    _manifests=() \
    _lib
  _dest_dir="/usr/bin"
  _dest="${_pkgname}.apk"
  if [[ "${_os}" == "Android" ]]; then
    if [[ "${_install_type}" == "system" ]]; then
      _dest_dir="/system/app/${_Pkg}"
    elif [[ "${_install_type}" == "user" ]]; then
      _dest_dir="/data/app/${_pkg}"
    fi
    _dest="base.apk"
  fi
  install \
    -vdm755 \
    "${pkgdir}${_dest_dir}"
  install \
    -vDm644 \
    "${srcdir}/${_tarname}.apk" \
    "${pkgdir}${_dest_dir}/${_dest}"
  if [[ "${_cmd}" == "true" ]]; then
    _make_opts+=(
      DESTDIR="${pkgdir}"
      PREFIX="/usr"
    )
    cd \
      "${_pkgname}-${_cmd_tag}"
    make \
      "${_make_opts[@]}" \
      install-scripts
    install \
      -vDm644 \
      "COPYING" \
      -t \
      "${pkgdir}/usr/share/licenses/${pkgname}/"
  fi || \
  true
}

package_termux-docs() {
  arch=(
    "any"
  )
  if [[ "${_cmd}" == "true" ]]; then
    _make_opts+=(
      DESTDIR="${pkgdir}"
      PREFIX="/usr"
    )
    cd \
      "${_pkgname}-man-${_cmd_man_tag}"
    make \
      "${_make_opts[@]}" \
      install
  install \
    -vDm644 \
    "COPYING" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}/"
  fi || \
  true
}

# vim: ft=sh syn=sh et
