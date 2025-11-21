# GSettings schema
install_data('org.mate.clipman.gschema.xml',
  install_dir: join_paths(get_option('datadir'), 'glib-2.0', 'schemas')
)

# Desktop files
desktop_conf = configuration_data()
desktop_conf.set('bindir', join_paths(get_option('prefix'), get_option('bindir')))

desktop_in = configure_file(
  input: 'mate-clipman.desktop.in',
  output: 'mate-clipman.desktop.in',
  configuration: desktop_conf
)

i18n.merge_file(
  input: desktop_in,
  output: 'mate-clipman.desktop',
  po_dir: join_paths(meson.source_root(), 'po'),
  install: true,
  install_dir: join_paths(get_option('datadir'), 'applications'),
  type: 'desktop'
)

autostart_in = configure_file(
  input: 'mate-clipman-autostart.desktop.in',
  output: 'mate-clipman-autostart.desktop.in',
  configuration: desktop_conf
)

i18n.merge_file(
  input: autostart_in,
  output: 'mate-clipman-autostart.desktop',
  po_dir: join_paths(meson.source_root(), 'po'),
  install: true,
  install_dir: join_paths(get_option('sysconfdir'), 'xdg', 'autostart'),
  type: 'desktop'
)

# Panel applet files (if building with MATE panel support)
if mate_panel_dep.found()
  applet_conf = configuration_data()
  applet_conf.set('LIBDIR', join_paths(get_option('prefix'), get_option('libdir')))

  applet_keyfile_in = configure_file(
    input: 'org.mate.panel.ClipmanApplet.mate-panel-applet.desktop.in',
    output: 'org.mate.panel.ClipmanApplet.mate-panel-applet.in',
    configuration: applet_conf
  )

  i18n.merge_file(
    input: applet_keyfile_in,
    output: 'org.mate.panel.ClipmanApplet.mate-panel-applet',
    po_dir: join_paths(meson.source_root(), 'po'),
    install: true,
    install_dir: join_paths(get_option('datadir'), 'mate-panel', 'applets'),
    type: 'desktop'
  )

  configure_file(
    input: 'org.mate.panel.applet.ClipmanAppletFactory.service.in',
    output: 'org.mate.panel.applet.ClipmanAppletFactory.service',
    configuration: applet_conf,
    install: true,
    install_dir: join_paths(get_option('datadir'), 'dbus-1', 'services')
  )
endif
