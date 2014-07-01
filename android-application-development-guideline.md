# Android Development Guideline

## Development Environment

>- [Java SDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
>- [Android SDK]()
>- [Android NDK]()
>- [Android Development Tools]()
>- [Apache Ant](http://ant.apache.org)
>- [jd-gui](http://jd.benow.ca)
>- [dex2jar](https://code.google.com/p/dex2jar/)
>- [bakjava](https://code.google.com/p/bakjava/)
>- [AXMLPrinter2](https://code.google.com/p/android4me)

## ADT Preferences

### Editor
> Displayd tab width : 4

> Show print margin
>> Print margin column : 80

> Show line number

### Workspace
> Text file encoding
>> Default : UTF-8

## 代码规范
所有的代码规范以Java编程语言代码规范为参考，并在其基础之上做了更严格的约束

### 命名
约定俗成采用Java的命名规范，包括单词的大小写、缩进、断行、注释等，所有的命名要做到顾名思义，禁止使用C/C++或者其它语言的命名习惯！例如：

    private Context context;  // 首选
    private Context mContext; // 错误！不要使用前缀'm'，尽管Android源代码中采用了这种命名习惯

#### 包名
参考Java包名命名规范

#### 类名
类名必须以名词来命名，首字母大写，采用驼峰标识

#### 成员方法名
成员方法名必须以动词为前缀来命名，首字母小写，采用驼峰标识，如果是override的方法必须加上@Override注解

#### 成员变量名
成员变量名必须以名词来命名，首字母小写，采用驼峰标识，尽可能的不使用缩写，变量长度控制在32个字符以内，对于不需要修改其引用的成员变量，应当声明为final，在类中访问成员变量时，尽可能使用this关键字，以避免命名冲突和作用域问题，例如：

    public class FooActivity extends Activity {
        private final List<Bar> bars = new ArrayList<Bar>();

        public List<Bar> getBars() {
            return this.bars;
        }

    }

#### 常量
常量必须冠以static final的修饰符，而且必须为大写，单词之间用下划线分隔，例如：

    public static final int EXTRA_GESTURE_SIGNATURE = "gesture_signature";

    private static final int SESSION_TIMEOUT = 5000L;

#### 局部变量
为了控制每行不超过80列，局部变量可以使用缩写，例如：

    Resources res = getResources();
    XmlResourceParser xrp = res.getXml(R.xml.config);

    try {
        while (XmlResourceParser.END_DOCUMENT != xrp.getEventType()) {
            // TODO
        }
    } catch (Exception e) {
        e.printStackTrace();
    }

#### 内部类
内部类一般声明为private static final，除非有其它的需要

#### 资源文件命名
资源文件的命名必须以前缀或后缀做标识

对于res/layout下的资源文件，常用的前缀有：
>- activity_
>- fragment_
>- notification_
>- menu_
>- menu_item_

对于res/drawable-xxx下的资源文件，常用的前缀有：
>- ic_
>- bg_

#### 资源ID的命名
View的id必须以其所在的资源文件的名称为前缀，例如：

    <TextView
        android:width="wrap_content"
        android:height="wrap_content"
        android:id="@+id/activity_home_action_bar_icon" />

String的name尽可能的使用前缀做标识，常用的前缀有：
>- msg_
>- toast_
>- title_
>- label_
>- notification_

    <string name="msg_xxx_xxx_xxx">...</string>
    <string name="toast_xxx_xxx_xxx">...</string>

## 缩进
代码的缩进统一使用TAB，显示宽度为4个字符

## 空格
适当的使用空格，提高代码的可读性

    for (int i = 0; i < n; i++) {
        // TODO
    }

    if (a > b) {
        // TODO
    } else if (a > c) {
        // TODO
    } else if (a > d) {
        // TODO
    } else {
        // TODO
    }

    try {
        method.invoke(obj, arg1, arg2, arg3, arg4, arg5, arg6);
    } catch (Exception e) {
        e.printStackTrace();
    }

## 空行
适当的使用空行，提高代码的可读性
>- 代码块与代码块之间
>- 不同的逻辑单元之间
>- 类成员与类成员之间

## 代码结构
一般来说，一个java文件的结构如下：
>- 文件注释
>- package语句
>- import语句
>- 类注释
>- 类声明

### 类的结构
一般来说，类的结构如下：
>- 常量
>- 类的变量
>- 类的方法
>- 成员变量
>- 构造方法
>- 成员方法

成员变量总是在类的头部声明，成员方法的声明顺序首先按照访问修饰符的级别从高到低，即public -> protected -> default -> private，其次按照是否是override进行排序，最后按照字母表顺序进行排序，通常，private的成员在最后
