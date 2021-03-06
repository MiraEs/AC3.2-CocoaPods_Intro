# AC3.2-CocoaPods_Intro
---

### Readings/Videos:
1. [An Introduction to Cocoapods (Route85/Google via Youtube)](https://www.youtube.com/watch?v=iEAjvNRdZa0)
1. [A Brief Intro to Cocoapods - grokswift](https://grokswift.com/cocoapods/)
2. [Getting an OAuth2.0 Token with Alamofire - grokswift](https://grokswift.com/alamofire-OAuth2/) 
3. [Cocoapods: Getting Started - Cocoapods](https://guides.cocoapods.org/using/getting-started.html)

### Reference: 
1. [Cocoapods](https://cocoapods.org/)
2. [Podfile Syntax Referece](https://guides.cocoapods.org/syntax/podfile.html)
3. [`pod` Command Line Reference](https://guides.cocoapods.org/terminal/commands.html)

### Optional: 
1. [Why I Use Libraries like Alamofire - grokswift](https://grokswift.com/i-like-libraries/)
2. [Cocoapods and the Case of the Squiggly Arrow](https://www.youtube.com/watch?v=x4ARXyovvPc)
3. [CocoaPods and Pod Try - (Route85/Google via Youtube)](https://www.youtube.com/watch?annotation_id=annotation_4056188601&feature=iv&index=18&list=PLOU2XLYxmsIKGQekfmV0Qk52qLG5LU2jO&src_vid=x4ARXyovvPc&v=tKm105KJPjQ)

### Advanced:
3. [Using a Router to Organize your API calls in Alamofire](https://grokswift.com/router/)
4. [Semantic Versioning](http://semver.org/)

---
### Installation 

#### Pre-Requisites: Installing [RubyGems](https://rubygems.org/pages/download)
1. Download package from site
2. Unpack into any directory, and `cd` to that directory in Terminal
3. Install with `ruby setup.rb`

> Note: `ruby` is built in to every Macbook. Type `ruby -v` in terminal to verify

Installing RubyGems will allow you to install [gem files](http://guides.rubygems.org/what-is-a-gem/), which are 3rd party libraries that are managed by the RubyGem org (written in Ruby). This type of library manager is called a dependancy management system, or dependancy manager for short. 

#### [Installing CocoaPods](https://guides.cocoapods.org/using/getting-started.html)
1. type `sudo gem install cocoapods` into terminal and wait for everything to download & install
2. (Optional) type `pod setup` next to download the podspec for all pods. What's a podspec, what's a pod? If you're asking, you haven't read the homework. So go do that. Right meow. 

> If you're having issues, running `sudo gem install -n /usr/local/bin cocoapods` instead may help

> If you prefer video installation: [An Introduction to Cocoapods (Route 85)](https://www.youtube.com/watch?v=iEAjvNRdZa0&spfreload=10) (cringe-worthy at times, but creative and informative).

---
### [Using Cocoapods](https://guides.cocoapods.org/using/using-cocoapods.html)
1. Create a new repository on git and clone the project locally
2. Create a new .xcodeproj in the directory of the cloned repo
3. Quit Xcode, and navigate to that same directory in Terminal
4. Type in `pod init` and wait a moment
  - This will generate some of the basic components you'll need to use/install pods, include the all important `Podfile`
5. Open the `Podfile` in the text editor of your choice
6. Add the cocoapods of your choosing, and save your changes
7. Type `pod install` in terminal and let cocoapods download the pods listed in your Podfile. 
8. When finished, it will inform you that you need to now use your project's `xcworkspace` instead of the `xcproject`
9. Open your project's `.xcworkspace` and try to Build
10. Refer to the pod's documentation or header files to determine what functions are available. 

> Note: What the heck is happening behind the scenes with all of this code running in terminal?!? Check [this](https://guides.cocoapods.org/using/using-cocoapods.html#what-is-happening-behind-the-scenes) out for info

#### [Other Considerations](https://guides.cocoapods.org/using/using-cocoapods.html#should-i-check-the-pods-directory-into-source-control): 
1. Sometimes it's good practice to add the actual `Pod/` directory to your `.gitignore` so that your repo doesn't get bloated with all of your dependancies. Committing just the [`Podfile`](https://guides.cocoapods.org/using/using-cocoapods.html#what-is-podfilelock) and `Podfile.lock` will allow other developers to pull down your code and run `pod install` on their own if they so choose. 

---
### [Updating your Pods](https://guides.cocoapods.org/using/using-cocoapods.html#when-to-use-pod-install-vs-pod-update)
1. Go into the same directory as your repo's `xcworkspace` and `Podfile` 
2. Type `pod update` in terminal

> Note: This will attemp to update your pods to the latest version. `pod install` will simply install the pods specified by your `Podfile` or in your `Podfile.lock` if you've already run `pod install` before. 

> Note: Knowing when to properly use [`install`](https://guides.cocoapods.org/using/pod-install-vs-update.html#pod-install) vs. `update` is a bit of a nuanced topic, so if you're interested you can read about it here: [`pod install` vs. `pod update`](https://guides.cocoapods.org/using/pod-install-vs-update.html)
The tl;dr (from the guide): 
 - Use pod install to install new pods in your project. Even if you already have a Podfile and ran pod install before; so even if you are just adding/removing pods to a project already using CocoaPods.
 - Use pod update [PODNAME] only when you want to update pods to a newer version.
 
 --- 
 ### [The Podfile](https://guides.cocoapods.org/using/the-podfile.html)
 
 > _The Podfile is a specification that describes the dependencies of the targets of one or more Xcode projects. The file should simply be named Podfile._
 
Podfiles usually end up being pretty simple, containing just the names of the pods you'll need, along with you minimum supported version of iOS:

> For a full list of usable syntax and examples, see the [Podfile Syntax Reference](https://guides.cocoapods.org/syntax/podfile.html)

```ruby
# Uncomment this line to define a global platform for your project
platform :ios, '9.0'

target 'CatPColoralettes' do
	use_frameworks!

	pod 'SnapKit'
	pod 'RESideMenu'
	# pod 'SwiftHSVColorPicker'

end
```

Another common practice is specifying version numbers for each of the pods using the notation `pod '<PodName>', '~> <version>': 

```ruby
# Uncomment this line to define a global platform for your project
platform :ios, '9.0'

target 'CatPColoralettes' do
	use_frameworks!

	pod 'SnapKit' , '~> 0.21.0'
	pod 'RESideMenu', '~> 4.0.7'
	# pod 'SwiftHSVColorPicker', '~> 1.0.9'

end
```

__Q: Where do you find out a pod's version number?__

A: A couple of places. You can find a pod's version number:

#### Searching for it on the Cocoapod's site.
![Version No. Listed in Cocoapods.org](./Images/version_number_on_site.png)

#### Searching through terminal.
![Version No. Listed in Terminal](./Images/version_number_on_terminal_search.png)

#### Searching the Github repo via its tags.
![Version No. Listed in Github Repo](./Images/version_number_on_github_tag.png)

---

### Exercises:

__Setup__
Using this repo to practice working with Pods, perform the following:

1. Fork this repo, clone it locally, and add a new Xcode project. Name it `CatPods`
2. Initialize you pods setup by running `pod init`
3. Open the `Podfile`

__Adding Pods__
After each step, verify you were able to complete the exercise by opening your `xcworkspace` and inspecting the `pod` project and your `Podfile.lock`. Then close Xcode before the next step

1. Add Alamofire to your project, do not specify the version
2. Now, specify that you want to use version `4.0.1`
3. Now, specify that you'd like to use any version higher than `3.5`
4. Now, specify that you'd like to use any version less than or equal to `4.0.0`
5. Now, specify that you'd like to use any version `3.0` and higher, not including `4.0`
6. Now, specify that you'd like to use any version `4.0` and higher, not including `4.1`
7. Finally, specify that you'd like to use any version `4.2` and higher, not including `5.0`

__Trying Pods__
See video linked above and try out Alamofire.

---

### (Brief) [Semantic Versioning](http://semver.org/), or, "What do all those version numbers mean?"

Given a version number `MAJOR.MINOR.PATCH`, increment the:

1. `MAJOR` version when you make incompatible API changes,
2. `MINOR` version when you add functionality in a backwards-compatible manner, and
3. `PATCH` version when you make backwards-compatible bug fixes.

Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

---

### Using AlamoFire to make web requests


