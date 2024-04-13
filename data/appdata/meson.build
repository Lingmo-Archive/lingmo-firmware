metainfo_file = i18n.merge_file(
  input: 'org.lingmo.Firmware.metainfo.xml.in',
  output: 'org.lingmo.Firmware.metainfo.xml',
  type: 'xml',
  po_dir: join_paths(meson.source_root(), 'po'),
  install: true,
  install_dir: join_paths(prefixed_datadir, 'metainfo'),
)

# Validate Appdata
appstreamcli = find_program('appstreamcli', required: false)
if appstreamcli.found()
  test(
    'validate-metainfo', appstreamcli,
    args: [
      'validate', '--no-net', '--explain', metainfo_file,
    ],
    depends: metainfo_file,
  )
endif
