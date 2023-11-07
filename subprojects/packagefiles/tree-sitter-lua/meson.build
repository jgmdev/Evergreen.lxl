project('tree-sitter-lua',
    ['c'],
    version : 'GIT',
    license : 'MIT',
    meson_version : '>= 0.56',
    default_options : ['c_std=c11']
)

if get_option('arch_tuple') != ''
    arch_tuple = get_option('arch_tuple')
else
    arch_tuple = '@0@-@1@'.format(target_machine.cpu_family(), target_machine.system())
endif

library_suffix = []

# On macOS the default suffix is .dylib but we need .so
if host_machine.system() == 'darwin'
    library_suffix = 'so'
endif

shared_library('tree-sitter-lua.'+arch_tuple,
    [
        'src/parser.c', 'src/scanner.c'
    ],
    name_suffix: library_suffix,
    include_directories: [include_directories('src')],
    install_dir: join_paths(get_option('data_dir'), 'libraries', 'tree-sitter-lua'),
    install: true,
)
