# Klick Plugin Development Guideline

## Naming Conventions

### Project Name
The form of project name should be like this:

    com.helloklick.plugin[.<company-name>][.<country-name>].<plugin-name>

For example:

    com.helloklick.plugin.qihoo.tw.mobilesafe // with company name and country name

    com.helloklick.plugin.kankun.smartplug // with company name, no country name

### Package Name
The package name should be the same as project name, for example:

    package com.helloklick.plugin.camera;

### Action Class Name
The action class name should be started with plugin name and followed by the suffix 'Action', for example:

    package com.helloklick.plugin.camera;

    public class CameraAction extends AbstractAction<CameraSetting> {
        ...
    }

### Action Setting Class Name
The action setting class name is similar with action class name, it should be started with plugin name and followed by the suffix 'Setting', for example:

    package com.helloklick.plugin.camera;

    public class CameraSetting implements ActionSetting {
        ...
    }

### Action Setting Fragment Class Name
The action setting fragment class name is also similar with action class name, and it should be started with plugin name and followed by the suffix 'Fragment', for example:

    package com.helloklick.plugin.camera;

    public class CameraFragment extends ActionFragment<CameraSetting> {
        ...
    }

### Drawable Resource Name
Each resource name should be started with a prefix, such as 'ic_', 'bg_', and then followed by 'action_', and then followed by plugin name, for example:

    ic_action_camera_active.png
    ic_action_camera_inactive.png

### Action Setting Fragment Layout Resource Name
The layout resource name should be started with prefix 'fragment_', and then followed by 'action_', and ended in plugin name, for example:

    fragment_action_camera.xml

### String Resource Name
Each string resource name should be started with prefix 'action_', and then followed by plugin name, for example:

    <string name="action_camera_title">Camera</string>

### View ID
The id of view declared in layout xml should be started with the layout xml file name, for example:

    <ImageButton
        android:id="@+id/fragment_action_select_phone_number"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_weight="0"
        android:contentDescription="@string/empty"
        android:background="@drawable/selector_action_phone_number" />

