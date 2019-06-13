# OTB provider for QGIS Processing

**OTB provider will be available in processing core starting from qgis 3.8.**


## Version
* QGIS : 3.2.0 or later
* OTB  : 6.6.0 or later


## Requirements

Make sure you don't have reference to clone of this repository in your QGIS_PLUGINPATH. 

### Download and Install OTB

OTB is not distributed with qgis-otb-plugin. It is a seperate project and has its own git repository.

Download OTB: https://www.orfeo-toolbox.org/download/

Git repository: https://gitlab.orfeo-toolbox.org/orfeotoolbox/otb

## Installation

Install through QGIS plugin manager. This plugin is available in OTB's plugin repository located at orfeo-toolbox.org/qgis/

#### Start QGIS

* Open plugin manager through menu. `Plugins -> Manage and Install Plugins `
* Select `Settings` on left pane and then click `Add..` button to add our plugin repository

![QGIS Plugin Manager](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_plugins_settings.png)

* Write `Name` for repository. eg: `CNES plugin repository`
* Write `URL` as `http://orfeo-toolbox.org/qgis/plugins.xml`
* Click `OK` to add repository.

![Add cnes plugin repo 1](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_plugins_add_repo.png)

* Once list of plugins are fetched from our repository. It will show status as `connected`

![Add cnes plugin repo 2](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_plugins_add_otb_1.png)

* Select `New` or `Upgradable` from left pane. You can now see `Processing OTB Provider` in the list of plugins
* Select `Processing OTB Provider` and click on `Install plugin` to download and install otb processing

![intall plugin ](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_plugins_install_1.png)

* It show "Plugin installed Sucessfully" message afer installation is finished.
 
![install plugin done ](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_plugins_install_done.png)


#### Verify otb plugin installation

`Plugins -> Manage and Install Plugins `

Click on `Installed` tab on left and make sure box next to `Processing OTB provider` is checked.

![ verify plugin installation ](http://orfeo-toolbox.org/qgis/otb_plugin_readme/verify_plugin_install.png)

#### Open processing settings
  
`Settings -> Options -> Processing (left panel)`

You can see OTB under "Providers".

* Expand `OTB` tab
* Tick `Activate` box
* Set `OTB folder`. This is location of your OTB installation.
* Set `OTB application folder`. This is location of your OTB applications. `<OTB_FOLDER>/lib/otb/applications`
* Click `ok` to save settings and close dialog. If settings are correct, you will have OTB algorithms loaded in QGIS Processing toolbox

![configure otb provider ](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_processing_configure_otb.png)

![install finished ](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_processing_configure_done.png)

****Installation finished!****

#### OTB Haralick texture extraction Algorithm in QGIS processing

![OTB Algorithm ](http://orfeo-toolbox.org/qgis/otb_plugin_readme/qgis_processing_otb_haralick.png)

------

#### Documenation of OTB settings available in QGIS Processing.

##### Activate
This is a checkbox to activate or deactivate OTB provider. Any invalid settings in OTB folder will uncheck this when saved.

##### OTB folder
This is the directory where OTB is available. Valid values are list below.
* OTB build folder (for source builds), 
* Folder in which OTB is installed using `make install`, package managers or official binary packages

##### OTB application folder
This is the location(s) of OTB applications.

Multiple paths are allowed to use custom/proprietary OTB applications.

##### Logger level (optional)
Level of logger to use by OTB applications. level of logging control amount of details printed during algorithm execution.

Possible values for logger level are INFO, WARNING, CRITICAL, DEBUG. you can refer to otb::Logger documentation for more on this values

*This value is INFO by default.*

**This is an advanced user configuration.**

##### Maximum RAM to use (optional)

By default otb application use system RAM as available. you can however instruct otb to use specific amount of RAM from available using this option. 

*A value of `128` is ignored by OTB processing provider.*

**This is an advanced user configuration.**

##### Geoid file (optional)
Path to geoid file. 

Value of this options is set for `elev.dem.geoid` and `elev.geoid` parameters in OTB applications.

Setting this value globally help users to share it across multiple processing algorithms. 

*This value is empty by default.*


##### SRTM tiles folder (optional)
Directory where SRTM tiles are available.

SRTM data can be stored locally to avoid connecting to downloading of files during processing.

Value of this options is set for `elev.dem.path` and `elev.dem` parameters in OTB applications.

Setting this value globally help users to share it across multiple processing algorithms.

*This value is empty by default.*

See OTB issue for a related feature request in OTB QtWidget wrapper. https://gitlab.orfeo-toolbox.org/orfeotoolbox/otb/issues/1560

