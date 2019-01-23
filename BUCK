load('//:buckaroo_macros.bzl', 'buckaroo_deps')
load('//:subdir_glob.bzl', 'subdir_glob')

macos_srcs = glob([
  'Release/src/**/*apple.cpp',
])

windows_srcs = glob([
  'Release/src/**/*httpsys.cpp',
  'Release/src/**/*win.cpp',
  'Release/src/**/*_winhttp.cpp',
  'Release/src/**/*_win32.cpp',
])

winrt_srcs = glob([
  'Release/src/**/*_winrt.cpp',
])

platform_srcs = macos_srcs + windows_srcs + winrt_srcs

cxx_library(
  name = 'cpprestsdk',
  header_namespace = '',
  exported_headers = subdir_glob([
    ('Release/include', '**/*.h'),
    ('Release/include', '**/*.hpp'),
    ('Release/include', '**/*.dat'),
  ]),
  headers = subdir_glob([
    ('Release/src/pch', '**/*.h'),
  ]),
  srcs = glob([
    'Release/src/**/*.cpp',
  ], exclude = platform_srcs),
  platform_srcs = [
    ('macos.*', macos_srcs),
    ('windows.*', windows_srcs),
    ('winrt.*', winrt_srcs),
  ],
  licenses = [
    'license.txt',
  ],
  deps = buckaroo_deps(),
  visibility = [
    'PUBLIC',
  ],
)
