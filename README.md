# Import FlatLaf library to NetBeans(17)

There are ways to import library on NetBeans.

First, if you are creating a project with ***Maven*** java, you don't need to download the `JAR` file of ***FlatLaf*** library, you have to copy the `dependency` on their website, first go to [FlatLaf](https://www.formdev.com/flatlaf/) page, press the `maven central`.

![image](images/FlatLafPage.png)

after pressing, the button should deliver you to download page, but instead of downloading the `JAR` file, you copy the dependency of ***FlatLaf***.

![image](images/dependencyPage.png)

then paste it on your `pom.xml` file:

![image](images/pomXml.png)

After pasting it, go to you Main frame, then clear all the extras on the `main` method, and replace it with 

```java
UIManager.setLookAndFeel(new FlatDarkLaf());
```

after putting this line of code, the IDE still cannot recognize the ***FlatLaf*** library, so you should **Search Dependency at Maven Repositories for FlatLaf**

![image](images/searchDependency.png)

>to show this hint, Alt + Enter at the error

after searching dependency you should see the `com.formdev` artifact, and then add the `JAR` file under that artifact. 


![image](images/artifact.png)

You should now able to import the library for ***FlatLaf***.
```java
    import com.formdev.flatlaf.FlatDarkLaf;
```

Then, your code will ask you to surround it with `try-catch` statement, so your code should look like this:

```java
    public static void main(String args[]) {
            try {
                UIManager.setLookAndFeel(new FlatDarkLaf());
            } catch (UnsupportedLookAndFeelException ex) {
                Logger.getLogger(FlatLafDemo.class.getName()).log(Level.SEVERE, null, ex);
            }

            java.awt.EventQueue.invokeLater(new Runnable() {
                public void run() {
                    new FlatLafDemo().setVisible(true);
                }
            });
    }
```

And now, your title bar and other components is customized by ***FlatLaf*** theme.

![image](images/frame.png)

***
If you're using java ***Ant*** you need to download the `JAR` file

![image](images/downloadJar.png)

after creating a java ***Ant*** file, there should be a library folder in the project, you right-click that library folder and choose the ***Add JAR/Folder*** menu.

![image](images/addJar.png)

after that, find the `JAR` file that you download and choose it.

then, call again the ***FLatLaf***  declaration:
```java
    UIManager.setLookAndFeel(new FlatDarkLaf());
```

and this should run:

![image](images/javaAnt.png)