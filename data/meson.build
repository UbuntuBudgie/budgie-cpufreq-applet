install_data('CpuFreqApplet.plugin',
             install_dir: LIB_INSTALL_DIR)

install_data(
             'budgie-cpufreq-modifier',
             install_mode: 'r-xr--r--',
             install_dir: LIB_INSTALL_DIR
)

configdata= configuration_data()
configdata.set('PLUGIN', LIB_INSTALL_DIR)

policyinstall = configure_file(
    input: 'budgie.cpufreq.policy.in',
    output: 'budgie.cpufreq.policy',
    configuration: configdata
)

install_data(policyinstall,
    install_dir: join_paths(get_option('datadir'), 'polkit-1', 'actions')
)

install_data('com.github.dirli.budgie-cpufreq-applet.gschema.xml',
    install_dir: join_paths(get_option('datadir'), 'glib-2.0/schemas')
)
