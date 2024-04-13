cargs = ['-DG_LOG_DOMAIN="Gfu"']

lingmo_firmware_resources = lingmo.compile_resources(
  'lingmo-firmware-resources',
  'lingmo-firmware.gresource.xml',
  source_dir : '.',
  c_name : 'gfu',
)

lingmo_firmware = executable(
  'lingmo-firmware',
  lingmo_firmware_resources,
  sources : [
    'gfu-main.c',
    'gfu-common.c',
    'gfu-device-row.c',
    'gfu-release-row.c',
  ],
  include_directories : [
    include_directories('..'),
  ],
  dependencies : [
    libgtk,
    libfwupd,
    libxmlb,
    libadwaita,
  ],
  c_args : cargs,
  install : true,
)

if get_option('man')
  help2man = find_program('help2man')
  custom_target('lingmo-firmware-man',
    input : lingmo_firmware,
    output : 'lingmo-firmware.1',
    command : [
      help2man, '@INPUT@',
      '--no-info',
      '--output', '@OUTPUT@',
      '--name', 'lingmo-firmware',
      '--manual', 'User Commands',
      '--version-string', meson.project_version(),
    ],
    install : true,
    install_dir : join_paths(prefixed_mandir, 'man1'),
  )
endif
