project('io.elementary.sideload', 'vala', 'c')

gnome = import('gnome')
i18n = import('i18n')

add_global_arguments('-DGETTEXT_PACKAGE="@0@"'.format (meson.project_name()), language:'c')

vapi_dir = join_paths(meson.current_source_dir(), 'vapi')
add_project_arguments(['--vapidir', vapi_dir], language: 'vala')

resources = gnome.compile_resources(
    'resources', 'data/sideload.gresource.xml',
    source_dir: 'data',
    c_name: 'resources'
)

executable(
    meson.project_name(),
    resources,
    'src/Utils/AsyncMutex.vala',
    'src/Views/AbstractView.vala',
    'src/Views/ErrorView.vala',
    'src/Views/MainView.vala',
    'src/Views/ProgressView.vala',
    'src/Views/SuccessView.vala',
    'src/Application.vala',
    'src/MainWindow.vala',
    'src/FlatpakRefFile.vala',
    dependencies: [
        dependency ('flatpak'),
        dependency ('glib-2.0'),
        dependency ('gobject-2.0'),
        dependency ('granite', version: '>=0.5'),
        dependency ('gtk+-3.0'),
        dependency ('libxml-2.0'),
    ],
    install : true
)

subdir('data')
subdir('po')

meson.add_install_script('meson/post_install.py')

