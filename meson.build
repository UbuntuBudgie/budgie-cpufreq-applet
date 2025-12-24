project('budgie-cpufreq-applet',
    ['c', 'vala'],
    version: '1.0.3',
    license: 'GPL-2.0',
    default_options: [
        'c_std=c11',
    ],
)

# Vala generates bad C code and missing these on gcc 14 will cause FTBFS
# Additionally, Meson 1.4 unhides warnings from valac-generated C code,
# which causes unreadable logspam. Reenables prior behavior.
am_cflags = [
    '-w',
    '-Wno-incompatible-pointer-types',
    '-Wno-implicit-function-declaration',
]
add_global_arguments(am_cflags, language: 'c')

add_project_arguments(
    '-DGETTEXT_PACKAGE="@0@"'.format(meson.project_name()),
    language:'c'
)

dep_gtk3 = dependency('gtk+-3.0', version: '>=3.18')
dep_glib = dependency('glib-2.0', version: '>= 2.46.0')
dep_peas = dependency('libpeas-2', version: '>= 2.0.0')
dep_budgie = dependency('budgie-3.0', version: '>= 3')
dep_gobject = dependency('gobject-2.0')
dep_polkit = dependency('polkit-gobject-1')

vala_version_required = '0.40.0'
vala = meson.get_compiler('vala')

LIB_INSTALL_DIR = join_paths(get_option('prefix'), get_option('libdir'), 'budgie-desktop', 'plugins', meson.project_name())
VAPI_DIR = join_paths(meson.project_source_root(),
                      'vapi')

conf = configuration_data()
conf.set_quoted('PACKAGE_LIBDIR', LIB_INSTALL_DIR)

config_h = configure_file(
	output: 'config.h',
	configuration: conf
)

config_dep = declare_dependency(
	dependencies: vala.find_library('config', dirs: VAPI_DIR),
	sources: config_h
)

config_inc_dir = include_directories('.')


subdir('data')
subdir('src')

meson.add_install_script('meson/meson_post_install.py')
