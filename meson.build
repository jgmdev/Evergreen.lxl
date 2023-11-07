project('Evergreen',
    version : '2.0.0',
    license : 'MIT',
    meson_version : '>= 0.56'
)

if get_option('arch_tuple') != ''
    arch_tuple = get_option('arch_tuple')
else
    arch_tuple = '@0@-@1@'.format(target_machine.cpu_family(), target_machine.system())
endif

data_dir = get_option('data_dir')

if get_option('ltreesitter')
    if not get_option('plugin_api')
        subproject('ltreesitter', default_options: [
            'arch_tuple='+arch_tuple,
            'data_dir='+data_dir,
            'use_system_lua='+get_option('use_system_lua').to_string(),
            'jit='+get_option('jit').to_string(),
        ])
    else
        subproject('ltreesitter_plugin_api', default_options: [
            'arch_tuple='+arch_tuple,
            'data_dir='+data_dir,
            'prefer_static=true',
        ])
    endif
endif

if get_option('parsers')
    subproject('tree-sitter-c', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-cpp', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-d', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-diff', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-go', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-go-mod', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-javascript', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-julia', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-lua', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-rust', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
    subproject('tree-sitter-zig', default_options: ['arch_tuple='+arch_tuple, 'data_dir='+data_dir])
endif

install_subdir('plugins/evergreen',
    install_dir: join_paths(get_option('data_dir'), 'plugins')
)
