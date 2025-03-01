# Deepin Tweak

Tweak 是一个基于 dtkdeclarative 的高级设置工具，Tweak 仅维护很少的内建功能，大部分功能将由符合开发规范的插件提供，通常这些插件由社区开发者提供。

[英文文档](README.md)

## 为什么需要这个工具

deepin 是一个用户群体广泛的发行版，其中囊括普通用户、开发者用户、极客等，对于使用 deepin 的用户而言，对桌面环境及操作系统的个性化管理能力有着强烈诉求。当前，deepin 为平衡普通用户和开发者用户之间的差异，更多的选择了相对稳定性、易操作、规则更为固定的管理方式，将产品提供给用户使用。但对于开发者或极客用户而言，期望对操作系统和桌面环境有着更加灵活的个性化和自定义管理能力，而目前的产品则无法满足这样的需求。
     开发者和极客用户一直以来是我们所关注的重要用户群体，因此计划在社区独立开发一款面向于开发者和极客用户的高级设置管理软件，以图形化界面的形式为广大对系统有更多个性化定制需求的高级用户提供更强大、便捷的管理能力，未来它可能会涵盖（窗管口管理器、桌面环境、文管、内核等）各方面的全局化高级自定义能力，以此来满足更多不同类型用户的高级自定义管理诉求。

## 它与控制中心的区别是什么

在控制中心中添加的设置项一般会具备以下特点：

* 基础性。属于系统中必备的基础功能，如日期设置
* 普适性。适用于大多数的用户，如网络设置

并且，往控制中心添加一个新的设置项时还必须要考虑它的`副作用`，因此往往不会提供很灵活的设置手段，以`个性化`模块里的`窗口圆角`这一项设置为例，控制中心里提供了“小”、“中”、“大”三个选项，而不是直接提供一个输入框由用户自由设置像素值，这样做是因为我们需要保证无论用户如何设置，都不会带来很严重的后果。因此控制中心可以适用于大多数用户，不必担心用户的误操作导致系统出现非常严重的问题。但是，这同时也局限了在控制中心添加设置项的范围，提高了增加功能的门槛，而本工具就是为了弥补这类问题而创建。

在本工具中添加的设置项一般会具备以下特点：

* 无法添加到控制中心，且没有其它更合适的产品可以承载。即不符合控制中心产品定位的系统设置类功能，如无限制地设置系统环境变量
* 需要它的人局限于某类单一的群体中，不适用于大多数人。如开启程序的 Debug 日志

本工具与控制中心的一些理念相反且功能互补，它不考虑增加设置项时的`副作用`，我们将假定使用此工具的用户都有能力解决使用它所带来的任何问题，即便无法解决也有觉悟接受它所带来的不良后果！基于以上原则，为此工具添加选项将变得较为简单，因为开发者不需要考虑用户的行为会导致怎样的后果，可以以最简单的方式添加最灵活的设置。还是以控制中心里的`窗口圆角`这一项设置为例，如果将其添加到此工具中，开发者可以直接提供一个输入框，用户可以精确定义圆角大小，但是如果使用者将其设置为 10000，由此带来的严重后果将自己承担（注：此处只是举例，不表示将其设置为10000一定会出现非常严重的后果）。即使用此工具所带来的收益和风险皆归使用者自身所有，此项目不会受理此类问题。

## 准备怎样开发和发布

本项目将提供一个独立的应用程序，而不是将其作为控制中心的插件或者是其它产品的附属品提供，因为它定位的独特性，我们必须严格地将其与其它产品划清界限，避免使用者产生误会。本工具将不会预装到系统中，而是单独在应用商店提供，由需要它的人自行下载，亦或下载源代码自行编译使用。

本项目的期望是尽量减少其“官方”基因，虽然由官方人员发起，但是主要由社区人员参与后续的开发和迭代。项目的功能和发展也主要由开发者决定，不强制依赖于产品和设计人员。在技术结构方面，当前的想法是：本项目只作为设置的 GUI 入口，所添加的功能都在具体的项目中提供配置项或 DBus 接口，本工具不需要后台，在设置完毕后即可推出，不影响功能的生效和后续的使用。因此，若要提供强大的个性化和自定义能力，仅有设置工具是不够的，它需要 DDE 桌面环境的各个组件能提供个性化定制的能力，再由本工具将相关的功能以界面设置的形式呈现给用户。我们希望能以此项目作为一个桥梁，使得参与到本项目开发中的社区伙伴更加方便和深入的了解 DDE 的各项细节，也希望在项目的开发过程中，能一并推进 DDE 本身的演进，使得 DDE 变得更加强大，能符合更多用户的高端需求。

## 未来的畅想

为了更灵活的支持功能扩展，本项目计划支持插件，自身主要提供插件的运行环境，在 GUI 方面使用 qml，其它方面提供 js 的接口，目标是能满足大部分插件的开发需求。因为不涉及二进制文件，插件可以更容易分发，甚至可以专门提供一个网站允许自由发布和下载这些插件。

## 运行依赖

* dtkdeclarative

## 构建依赖

* cmake
* libdtkdeclarative-dev
* qtdeclarative5-dev
* qtbase5-dev-tools
* qtquickcontrols2-5-dev
* libdtkgui-dev
* libdtkcore-dev
* libgsettings-qt-dev

## 安装

### 从源码构建

1. 请确保已安装全部构建依赖
2. 获取源码

    ```shell
    $ git clone https://github.com/linuxdeepin/deepin-tweak.git
    cmake -B build -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr
    cmake --build build
    ```

3. 安装

    ```shell
    $ sudo cmake --install build
    ```

## 获取帮助

* 如果您遇到任何问题，请随时报告问题
* 在 [Deepin 论坛](https://bbs.deepin.org/) 获取通用帮助

## 参与

我们鼓励您参与问题报告和项目贡献

* [开发者贡献指南](https://github.com/linuxdeepin/developer-center/wiki/Contribution-Guidelines-for-Developers)

## 许可

deepin-tweak 使用 [LGPL-3.0-or-later](LICENSE)
