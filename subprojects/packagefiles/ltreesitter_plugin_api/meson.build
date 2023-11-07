project('ltreesitter-plugin-api',
    ['c'],
    version : 'GIT',
    license : 'MIT',
    meson_version : '>= 0.56',
    default_options : ['c_std=c11', 'prefer_static=true']
)

if get_option('arch_tuple') != ''
    arch_tuple = get_option('arch_tuple')
else
    arch_tuple = '@0@-@1@'.format(target_machine.cpu_family(), target_machine.system())
endif

cc = meson.get_compiler('c')

library_suffix = []

# On macOS the default suffix is .dylib but we need .so
if host_machine.system() == 'darwin'
    library_suffix = 'so'
endif

ltreesitter = shared_library('ltreesitter.'+arch_tuple,
    [
        'csrc/dynamiclib.c',
        'csrc/ltreesitter.c',
        'csrc/luautils.c',
        'csrc/node.c',
        'csrc/object.c',
        'csrc/parser.c',
        'csrc/query.c',
        'csrc/query_cursor.c',
        'csrc/tree.c',
        'csrc/tree_cursor.c',
        'csrc/types.c'
    ],
    name_prefix: '',
    name_suffix: library_suffix,
    include_directories: [
        include_directories('include'),
        include_directories('lite-xl-plugin-api/include')
    ],
    dependencies: [
        dependency('tree-sitter'),
        cc.find_library('m', required: false),
        cc.find_library('dl', required: false)
    ],
    install_dir: join_paths(get_option('data_dir'), 'plugins', 'evergreen'),
    install: true,
)
