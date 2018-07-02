include_defs('//BUCKAROO_DEPS')

posix_flags = [
  '-DBOOST_THREAD_POSIX',
]

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
    ('default', glob(['src/pthread/**/*.cpp'])),
    ('^iphoneos.*', glob(['src/pthread/**/*.cpp'])),
    ('^macos.*', glob(['src/pthread/**/*.cpp'])),
    ('^linux.*', glob(['src/pthread/**/*.cpp'])),
    ('^windows.*', glob(['src/win32/**/*.cpp'])),
  ],
  compiler_flags = [
    '-DBOOST_THREAD_STATIC_LINK=1',
    '-DBOOST_THREAD_DYN_LINK=1',
    '-DBOOST_THREAD_BUILD_LIB=1',
    '-DBOOST_THREAD_BUILD_DLL=1',
  ],
  platform_compiler_flags = [
    ('default', posix_flags),
    ('^iphoneos.*', posix_flags),
    ('^macos.*', posix_flags),
    ('^linux.*', posix_flags),
  ],
  visibility = [
    'PUBLIC',
  ],
  deps = BUCKAROO_DEPS,
)
