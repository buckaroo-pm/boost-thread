include_defs('//BUCKAROO_DEPS')

posix_srcs = glob([
  'src/pthread/**/*.cpp', 
])

windows_srcs = glob([
  'src/win32/**/*.cpp', 
])

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
  deps = BUCKAROO_DEPS, 
  visibility = [
    'PUBLIC', 
  ], 
)
