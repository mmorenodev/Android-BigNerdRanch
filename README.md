# Android-BigNerdRanch
Learning about Android with Big Nerd Ranch

Jetpack Compose is the future or Android development. 
There are many ways to write asynchronous code on Android, but in this book we focus exclusively using Kotlin coroutines as they are baked directly into Jetpack Compose's API as well as being excellent tools to interact with UI written with Android's existing UI toolkit. 

Reworked projects to follow the UNIDIRECTIONAL data flow architecture pattern. **The unidirectional data flow pattern is essential to building apps with Jetpack Compose- and it also helps organize code when building apps with Android's existing UI toolkit.**


## Activity
An activity is a class in the Android SDK. It is an entry point into your application and is responsible for managing user interaction with a screen of information. 

- You write subclasses of Activity to implement the functionality your app requires. A simple application may need only one subclass; a complex application may have many. 
- A layout defines a set of UI objects and the object's positions on the scren. A layout is made up of definitions written in XML. Each definition is used to **create an object that appears onscreen,** like a button or some text. 

<img width="674" alt="image" src="https://user-images.githubusercontent.com/66931789/184678372-8b9c09d7-7808-4c84-bedf-f1fcfea8b379.png">

Notice that the package name uses a "reverse DNS" convention: the domain name of your organization is reversed and suffixed with further identifiers. **This convention keeps package names unique and distinguishes applications from each other on a device and in the Google Play Store.**

**TAKE INTO ACCOUNT THAT CERTAIN TOOLS AND LIBRARIES ONLY SUPPORT KOTLIN -SUCH AS JETPACK COMPOSE**

## Navigating in Android Studio

Project tool window: by default, Android Studio displays the Android project view in the project tool window. **This view hides the true directory structure of your Android project so that you can focus on the files and folders that you need MOST OFTEN**. To see the files and folders in your project as they actually are, locate the dropdown at the top of the project tool window and click to expand it. 

<img width="671" alt="image" src="https://user-images.githubusercontent.com/66931789/184681141-38f87af3-4c46-4cf3-b8e3-33d623e1bf37.png">

**Adding the suffix 'Activity' on the class name when it is an activity is not required, but IT IS AN EXCELLENT CONVENTION TO FOLLOW.**

## Laying Out the UI 
By convention, a layout file is named based on the activity it is associated with: its name begins with 'activity_', and the rest of the activity name folows in all lowercase, using underscores to separate words (a style called "snake_case"). So for example, your layout file's name is 'activity_main.xml', and the layout file for an activity called **SplashScreenActivity** would be named 'activity_splash_screen'. This naming style is recommended for layouts as well as other resources. 

The Android SDK includes many views that you can configure to get the appearance and behavior you want. Each is an instance of the 'View' class or one of its subclasses (such as TextView or Button).
Something has to tell the views where they belong onscreen. A 'ViewGroup' is kind of a 'View' that contains and arranges other views. A **ViewGroup** does not display content itself. Rather, it orchestrates where other views' content is displayed. **ViewGroups are often referred to as layouts.**

Each element in a layout has a set of XML 'attributes'. Each attribute is an instruction about how the view should be configured. 

## The view hierarchy
Your views exist in a hierarchy of View objects called the 'view hierarchy'. 

<img width="717" alt="image" src="https://user-images.githubusercontent.com/66931789/184684099-3f01712c-8f9d-4659-ba0a-9115ccc4b4b3.png">

The root element of this layout's view hierarchy is a LinearLayout. As the root element, the 'LinearLayout' must specify the Android resource XML namespace at 'http://schemas.android.com/apk/res/android'. 
When a view is contained by a ViewGroup, that view is said to be a 'child' of the ViewGroup. 

**The LinearLayout is the root element, but it still has a parent - THE VIEW THAT ANDROID PROVIDES FOR YOUR APP'S VIEW HIERARCHY TO LIVE IN.**

## android:orientation
The android:orientation attribute on the LinearLayout views determines whether their children will appear vertically or horizontally. The order in which children are defined determines the order they appear onscreen. In a vertical LinearLayout, the first child defined will appear topmost. In a horizontal LinearLayout, the first child defined will be leftmost. 

## String resources
A string resource is a string that lives in a separate XML file called a 'strings file'. 
Although the default strings file is named 'strings.xml', you can name a strings file anything you want. You can also have multiple strings files in a project. As long as the file is located in 'res/values/', has a 'resources' root element, and contains child 'string' elements, your strings will be found and used. 

# Previewing 
<img width="699" alt="image" src="https://user-images.githubusercontent.com/66931789/184689095-8cc93bce-a8d8-44ef-a84f-88ef5d83e639.png">

Previous image shows the two kinds of preview available. 
The preview on the left is the 'Design' preview. This shows **how the layout would look on a device, INCLUDING THEMING.**

The preview on the right is the 'Blueprint' preview. This preview focuses on the size of the views and the relationships between them. 
The design view also allows you to see how your layout looks on different device configurations. At the top of the preview window, you can specify the type of device, the version of Android to simulate, the device theme, AND THE LOCALE to use when rendering your layout. 

**It's important to test your app using the different localizations, themes, configuration, etc**

The next image shows the preview with 'layout decorations' the device status bar, app bar with GeoQuiz label, and virtual device button bar. **To see these decorations, click the eye-shaped button in the toolbar just above the preview and select *Show System UI***

<img width="898" alt="image" src="https://user-images.githubusercontent.com/66931789/184690137-2bab0359-657a-4679-987e-f4a9d82aaa77.png">

A quick aside about the directory src/main/*java*. This directory is called 'java' because Android originally supported only Java code. In your project, when you configure it to use Kotlin, the 'java' directory is where the Kotlin code lives. You could create a 'kotlin' directory and place your Kotlin files there, but that would provide no real benefits and requires additional configuration, so most developers just place their Kotlin files in the 'java' directory. 

**AppCompatActivity is a subclass of Android's Activity class that provides compatibility support for older versions of Android.**

**When a layout is inflated, each view in the layout file is instantiated as defined by its attributes.**


**Resources and resource IDs**
A layout is a resource. A resource is a piece of your application that is not code -things like image files, audio files, and XML files. 

Resources for your project live in a subdirectory of the app/res directory. 

To access a resource in code, you use its resource ID. You don't define the 'R.layout.resource_id' yourself. As a part of compiling your app, the build process automatically generates that resource ID for you. In fact, the build process generates resource IDs *for all the resources in your project*. 

During the compilation and packaging of your app, the build tools generate a class known as the **R** class. This class contains a long list of IDs as integer constants, allowing you to access and use your resources in your application. When referencing 'R.layout.activity_main', you are actually referencing an integer constant named 'activity_main' within the **layout** inner class of **R**.
_As you add, remove, and change resources, the build process will automatically update the file in order to maintain the correct mapping between resources and their IDs._

Your strings also have resource IDs. Android generates a resource ID for the entire layout and for each string resource. 
To generate a resource ID for a view, you include an 'android:id' attribute in the view's definition. 

<img width="348" alt="image" src="https://user-images.githubusercontent.com/66931789/184692212-7bd6f9f9-8a5a-4114-852f-094c9b73e21f.png">

Notice that there is a + sign in the values for 'android:id' but not in the values for 'android:text'. This is because you are _creating_ the resource IDs and only _referencing_ the strings. 

## lateinit
You use 'lateinit' on your property declarations to indicate to the compiler that you WILL PROVIDE A NON-NULL value before you attempt to use the contents of the property. 


## Listeners
Android applications are typically EVENT DRIVEN. Unlike command-line programs or scripts, event-driven applications start and then wait for an event, such as the user pressing a button. (Events can also be initiated by the OS or another application, but user-initiated events are the most obvious)

When your application is waiting for a specific event, we say that it is 'listening for' that event. The object that you create to respond to an event is called a _listener_, and the listener implements a _listener interface_ for that event. 

The Android SDK comes with listener interfaces for various events, so you do not have to write your own. In this case, the event you want to listen for is a button being pressed (or "clicked"), so your listener will implement the 'View.OnClickListener' interface. 

The Android framework defines **View.OnClickListener** as a Java interface with a single method, **onClick(View).** Interfaces with a _single abstract method_ are common enough in Java that the pattern has a pet name, _SAM_. 

**Kotlin has special support for this pattern as part of its Java interoperability layer. It lets you write a function literal, and it takes care of turning that into an object implementing the interface. This behind-the-scenes process is called _SAM conversion_.**

## Toasts
A toast is a short message that informs the user of something but does not require any input or action. 

**When you use code completion, YOU DO NOT HAVE TO DO ANYTHING TO IMPORT THE MISSING/NEW CLASS. When you accept a code completion suggestion, the necessary classes are imported automatically.**
