vala_compiler = meson.get_compiler('vala')

ValaArgs = [
    '--pkg=config',
    '--vapidir=' + VAPI_DIR,
    '--target-glib=2.38',
]


bcfa_sources = [
    'CpuFreqApplet.vala',
    'Utils.vala',
    'Services/FreqManager.vala',
    'Widgets/CpuView.vala'
]

bcfa_deps = [
    dep_gtk3,
    dep_glib,
    dep_peas,
    dep_budgie,
    dep_gobject,
    dep_polkit
]

shared_library('budgiecpufreqapplet',
    bcfa_sources,
    vala_args: ValaArgs,
    dependencies: [
        bcfa_deps,
        vala_compiler.find_library('posix'),
    ],
    include_directories: config_inc_dir,
    install: true,
    install_dir: LIB_INSTALL_DIR,
)
