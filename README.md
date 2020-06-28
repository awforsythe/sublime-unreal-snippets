# Unreal Snippets

A collection of Sublime Text 3 snippets for writing Unreal Engine 4 game code.

Some of these snippets assume that your project's source modules follow the convention of splitting source files into _Public_ and _Private_ subdirectories.

### Available Snippets

**Project (.uproject)**

- **uuproj** - Boilerplate .uproject file (e.g. `Project.uproject`)

**Module (C#)**

- **umt** - Define a project-level target rules file (e.g. `Source/Project.Target.cs`)
- **umb** - Define a module-level build rules files (e.g. `Source/ProjectCore/ProjectCore.Build.cs`)
- **umh** - Declare a module in its public header file (e.g. `Source/ProjectCore/Public/ProjectCore.h`)
- **umc** - Define a module in its private cpp file (e.g. `Source/ProjectCore/Private/ProjectCore.cpp`)
- **umcp** - Define the _primary_ game module implementation (one per project)

**Logging (C++)**

- **ulh** - Declare a module-level log category in a module-private header (e.g. `Source/ProjectCore/Private/Log.h`)
- **ulc** - Define a module-level log category in a cpp file (e.g. `Source/ProjectCore/Private/Log.cpp`)
- **ull** - Write a single UE_LOG line using the module-level log category
- **ulf** - Write a single UE_LOG line at Fatal severity

**Classes (C++)**

- **uco** - Declare a UObject subclass
- **ucc** - Declare a UActorComponent subclass
- **uca** - Declare an AActor subclass

**Properties (C++)**

- **upc** - Declare a component UPROPERTY (Visible/ReadOnly in "Components" category)
- **upe** - Declare an editable UPROPERTY (Editable/ReadWrite in "<ModuleName>" category)
- **upv** - Declare a visible UPROPERTY (Visible/ReadOnly in "<ModuleName>" category)

**Functions (C++)**

- **ufc** - Declare a constructor that accepts a const FObjectInitializer reference (in a class header)
- **ufr** - Define the implementation of GetLifetimeReplicatedProps (in an actor source file)

### Creating a Project

Example setup steps for creating a new Unreal C++ project from scratch:

- Create a root Unreal project directory: replace `Project` with your project name
- Add `Project.uproj`, run `uuproj`, populate with primary module name (e.g. `ProjectCore`)
- Add a `Source` directory
- Within that directory, add `Project.Target.cs`, run `umt`, enter primary module name
- Add `ProjectEditor.Target.cs` the same way, set _Type_ to `TargetType.Editor`
- If desired, add `ProjectServer.Target.cs`, set _Type_ to `TargetType.Server`
- Add a subdirectory for the primary module, e.g. `ProjectCore`
- Within that directory, add `ProjectCore.Build.cs`, run `umb`
- Add two subdirectories, `Public` and `Private`
- Within Public, add `ProjectCore.h`, run `umh`
- Within Private, add `ProjectCore.cpp`, run `umcp`
- Within Private, add `Log.h`, run `ulh`
- Within Private, add `Log.cpp`, run `ulc`

At this point, you should be able to build your project and open it with the version of UE4Editor that you've built against.
