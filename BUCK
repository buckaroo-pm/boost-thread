load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps')

posix_srcs = glob([
  'src/pthread/**/*.cpp',
])

windows_srcs = glob([
  'src/win32/**/*.cpp',
])

prebuilt_cxx_library(
  name = 'pthread',
  header_only = True,
  exported_linker_flags = [
    '-lpthread',
  ],
)

cxx_library(
  name = 'thread',
  header_namespace = 'boost',
  exported_headers = subdir_glob([
    ('include/boost', '**/*.hpp'),
  ]),
  srcs = glob([
    'src/*.cpp',
  ]),
  platform_srcs = [
    ('linux.*', posix_srcs),
    ('android.*', posix_srcs),
    ('macos.*', posix_srcs),
    ('iphone.*', posix_srcs),
    ('windows.*', windows_srcs),
  ],
  deps = buckaroo_deps(),
  platform_deps = [
    ('linux.*', [ ':pthread' ]),
  ],
  visibility = [
    'PUBLIC',
  ],
)
