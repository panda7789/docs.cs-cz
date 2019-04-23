---
title: Vytvoření aplikace .NET Core s moduly plug-in
description: Zjistěte, jak vytvořit aplikaci .NET Core, která podporuje moduly plug-in.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: a9431ee28c7df21a8688f845be20e062eca21887
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773425"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="47934-103">Vytvoření aplikace .NET Core s moduly plug-in</span><span class="sxs-lookup"><span data-stu-id="47934-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="47934-104">V tomto kurzu se dozvíte, jak do:</span><span class="sxs-lookup"><span data-stu-id="47934-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="47934-105">Strukturování projektu pro podporu modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="47934-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="47934-106">Vytvoření vlastní <xref:System.Runtime.Loader.AssemblyLoadContext> načtení modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="47934-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="47934-107">Použití `System.Runtime.Loader.AssemblyDependencyResolver` typ povolit moduly plug-in k závislostmi.</span><span class="sxs-lookup"><span data-stu-id="47934-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="47934-108">Autor moduly plug-in, který je možné snadno nasadit pomocí pouhé kopírování artefaktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="47934-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="47934-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="47934-109">Prerequisites</span></span>

- <span data-ttu-id="47934-110">Nainstalujte [sady SDK .NET Core 3.0 ve verzi Preview 2](https://www.microsoft.com/net/core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="47934-110">Install the [.NET Core 3.0 Preview 2 SDK](https://www.microsoft.com/net/core) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="47934-111">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="47934-111">Create the application</span></span>

<span data-ttu-id="47934-112">Prvním krokem je vytvoření aplikace:</span><span class="sxs-lookup"><span data-stu-id="47934-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="47934-113">Vytvořte novou složku a v této složce spusťte `dotnet new console -o AppWithPlugin`.</span><span class="sxs-lookup"><span data-stu-id="47934-113">Create a new folder, and in that folder run `dotnet new console -o AppWithPlugin`.</span></span> 
2. <span data-ttu-id="47934-114">Chcete-li sestavení projektu jednodušší, vytvořte soubor řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="47934-114">To make building the project easier, create a Visual Studio solution file.</span></span> <span data-ttu-id="47934-115">Spustit `dotnet new sln` ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="47934-115">Run `dotnet new sln` in the same folder.</span></span> 
3. <span data-ttu-id="47934-116">Spustit `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` přidat do řešení projekt aplikace.</span><span class="sxs-lookup"><span data-stu-id="47934-116">Run `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` to add the app project to the solution.</span></span>

<span data-ttu-id="47934-117">Nyní jsme můžete vyplnit kostra naši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47934-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="47934-118">Nahraďte kód v *AppWithPlugin/Program.cs* souboru následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="47934-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

```csharp
using PluginBase;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Reflection;

namespace AppWithPlugin
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length == 1 && args[0] == "/d")
                {
                    Console.WriteLine("Waiting for any key...");
                    Console.ReadLine();
                }

                // Load commands from plugins.

                if (args.Length == 0)
                {
                    Console.WriteLine("Commands: ");
                    // Output the loaded commands.
                }
                else
                {
                    foreach (string commandName in args)
                    {
                        Console.WriteLine($"-- {commandName} --");

                        // Execute the command with the name passed as an argument.

                        Console.WriteLine();
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex);
            }
        }
    }
}

```

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="47934-119">Vytvoření modulu plug-in rozhraní</span><span class="sxs-lookup"><span data-stu-id="47934-119">Create the plugin interfaces</span></span>

<span data-ttu-id="47934-120">Dalším krokem při sestavování aplikace s moduly plug-in definuje rozhraní, které moduly plug-in je nutné implementovat.</span><span class="sxs-lookup"><span data-stu-id="47934-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="47934-121">Doporučujeme, abyste vytvořili knihovnu tříd, který obsahuje všechny typy, které budete používat pro komunikaci mezi aplikací a moduly plug-in.</span><span class="sxs-lookup"><span data-stu-id="47934-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="47934-122">Můžeme vám umožňuje publikovat rozhraní modulu plug-in jako balíček není přitom nutné dodávat celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="47934-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="47934-123">V kořenové složce projektu, spusťte `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="47934-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="47934-124">Také spustit `dotnet sln add PluginBase/PluginBase.csproj` přidání projektu do souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="47934-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="47934-125">Odstranit `PluginBase/Class1.cs` souboru a vytvořte nový soubor v `PluginBase` složku s názvem `ICommand.cs` s následující definice rozhraní:</span><span class="sxs-lookup"><span data-stu-id="47934-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="47934-126">To `ICommand` rozhraní je rozhraní, že všechny moduly plug-in implementovat.</span><span class="sxs-lookup"><span data-stu-id="47934-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="47934-127">Teď, když `ICommand` rozhraní je definováno, může být vyplněno projekt aplikace o něco víc.</span><span class="sxs-lookup"><span data-stu-id="47934-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="47934-128">Přidat odkaz z `AppWithPlugin` projektu `PluginBase` projekt se `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` příkazů z kořenové složky.</span><span class="sxs-lookup"><span data-stu-id="47934-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="47934-129">Nahradit `// Load commands from plugins` komentář pomocí následujícího fragmentu kódu, který umožňuje načíst pluginy ze zadané cesty k souborům:</span><span class="sxs-lookup"><span data-stu-id="47934-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

```csharp
string[] pluginPaths = new string[]
{
    // Paths to plugins to load.
};

IEnumerable<ICommand> commands = pluginPaths.SelectMany(pluginPath =>
{
    Assembly pluginAssembly = LoadPlugin(pluginPath);
    return CreateCommands(pluginAssembly);
}).ToList();
```

<span data-ttu-id="47934-130">Potom nahraďte `// Output the loaded commands` komentáře následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="47934-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="47934-131">Nahradit `// Execute the command with the name passed as an argument` komentáře následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="47934-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="47934-132">A nakonec statické metody pro přidání `Program` třídu s názvem `LoadPlugin` a `CreateCommands`, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="47934-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    throw new NotImplementedException();
}

static IEnumerable<ICommand> CreateCommands(Assembly assembly)
{
    int count = 0;

    foreach (Type type in assembly.GetTypes())
    {
        if (typeof(ICommand).IsAssignableFrom(type))
        {
            ICommand result = Activator.CreateInstance(type) as ICommand;
            if (result != null)
            {
                count++;
                yield return result;
            }
        }
    }

    if (count == 0)
    {
        string availableTypes = string.Join(",", assembly.GetTypes().Select(t => t.FullName));
        throw new ApplicationException(
            $"Can't find any type which implements ICommand in {assembly} from {assembly.Location}.\n" +
            $"Available types: {availableTypes}");
    }
}
```

## <a name="load-plugins"></a><span data-ttu-id="47934-133">Načítání modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="47934-133">Load plugins</span></span>

<span data-ttu-id="47934-134">Nyní můžete načíst a vytvořit instanci příkazy ze sestavení načíst modul plug-in aplikace správně, ale je stále nelze načíst sestavení modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="47934-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="47934-135">Vytvořte soubor s názvem *PluginLoadContext.cs* v *AppWithPlugin* složka s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="47934-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="47934-136">`PluginLoadContext` Typ je odvozen od <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="47934-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="47934-137">`AssemblyLoadContext` Typ je speciální typ v modulu runtime, která umožňuje vývojářům izolovat načtená sestavení do různých skupin, ujistěte se, že verze sestavení nejsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="47934-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="47934-138">Kromě toho vlastní `AssemblyLoadContext` můžete změnit výchozí chování a načítat sestavení z různých cest.</span><span class="sxs-lookup"><span data-stu-id="47934-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="47934-139">`PluginLoadContext` Používá instanci `AssemblyDependencyResolver` typu zavedeného do .NET Core 3.0 k překladu názvů sestavení na cesty.</span><span class="sxs-lookup"><span data-stu-id="47934-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="47934-140">`AssemblyDependencyResolver` Objekt je vytvořen s cestou k knihovny tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="47934-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="47934-141">Přeloží sestavení a nativních knihoven na jejich relativní cesty na základě *deps.json* soubor pro knihovnu tříd, jejichž cesty byl předán `AssemblyDependencyResolver` konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="47934-141">It resolves assemblies and native libraries to their relative paths based on the *deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="47934-142">Vlastní `AssemblyLoadContext` umožňuje mají svoje vlastní závislosti modulů plug-in a `AssemblyDependencyResolver` usnadňuje správně načíst závislosti.</span><span class="sxs-lookup"><span data-stu-id="47934-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="47934-143">Teď, když `AppWithPlugin` projekt má `PluginLoadContext` zadejte, aktualizujte `Program.LoadPlugin` metoda spolu s následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="47934-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

```csharp
static Assembly LoadPlugin(string relativePath)
{
    // Navigate up to the solution root
    string root = Path.GetFullPath(Path.Combine(
        Path.GetDirectoryName(
            Path.GetDirectoryName(
                Path.GetDirectoryName(
                    Path.GetDirectoryName(
                        Path.GetDirectoryName(typeof(Program).Assembly.Location)))))));

    string pluginLocation = Path.GetFullPath(Path.Combine(root, relativePath.Replace('\\', Path.DirectorySeparatorChar)));
    Console.WriteLine($"Loading commands from: {pluginLocation}");
    PluginLoadContext loadContext = new PluginLoadContext(pluginLocation);
    return loadContext.LoadFromAssemblyName(new AssemblyName(Path.GetFileNameWithoutExtension(pluginLocation)));
}
```

<span data-ttu-id="47934-144">Pomocí jiného `PluginLoadContext` instance pro každý modul plug-in, moduly plug-in může mít různé nebo dokonce konfliktní závislosti bez problému.</span><span class="sxs-lookup"><span data-stu-id="47934-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="47934-145">Vytvořte jednoduchý modul plug-in bez závislostí</span><span class="sxs-lookup"><span data-stu-id="47934-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="47934-146">Zpět v kořenové složce postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="47934-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="47934-147">Spustit `dotnet new classlib -o HelloPlugin` vytvoříte nový projekt knihovny tříd s názvem `HelloPlugin`.</span><span class="sxs-lookup"><span data-stu-id="47934-147">Run `dotnet new classlib -o HelloPlugin` to create a new class library project named `HelloPlugin`.</span></span>
2. <span data-ttu-id="47934-148">Spustit `dotnet sln add HelloPlugin/HelloPlugin.csproj` přidat projekt tak, aby `AppWithPlugin` řešení.</span><span class="sxs-lookup"><span data-stu-id="47934-148">Run `dotnet sln add HelloPlugin/HelloPlugin.csproj` to add the project to the `AppWithPlugin` solution.</span></span> 
3. <span data-ttu-id="47934-149">Nahradit *HelloPlugin/Class1.cs* soubor se soubor s názvem *HelloCommand.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="47934-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="47934-150">Nyní, otevřete *HelloPlugin.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="47934-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="47934-151">By měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="47934-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="47934-152">Mezi `<Project>` značky, přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="47934-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="47934-153">`<Private>false</Private>` Element je velmi důležité.</span><span class="sxs-lookup"><span data-stu-id="47934-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="47934-154">To říká MSBuild k nekopíruje *PluginBase.dll* do výstupního adresáře pro HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="47934-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="47934-155">Pokud *PluginBase.dll* se nachází v adresáři výstupu sestavení `PluginLoadContext` se najít sestavení existuje a načtěte ho po načtení *HelloPlugin.dll* sestavení.</span><span class="sxs-lookup"><span data-stu-id="47934-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="47934-156">V tomto okamžiku `HelloPlugin.HelloCommand` typ implementuje `ICommand` rozhraní z *PluginBase.dll* v adresáři výstupu `HelloPlugin` projekt není `ICommand` rozhraní, který je načten do Výchozí kontext načtení.</span><span class="sxs-lookup"><span data-stu-id="47934-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="47934-157">Vzhledem k tomu, že modul runtime považuje tyto dva typy různých typů z různých sestavení `AppWithPlugin.Program.CreateCommands` metoda nenajde příkazy.</span><span class="sxs-lookup"><span data-stu-id="47934-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="47934-158">V důsledku toho `<Private>false</Private>` metadat pro se vyžaduje odkaz na sestavení obsahující rozhraní modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="47934-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="47934-159">Teď, když `HelloPlugin` dokončení projektu, by měl aktualizujeme `AppWithPlugin` projekt tak, aby věděli, kde `HelloPlugin` najdete modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="47934-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="47934-160">Po `// Paths to plugins to load` komentář, přidání `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako prvek sady `pluginPaths` pole.</span><span class="sxs-lookup"><span data-stu-id="47934-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="47934-161">Vytvořit modul plug-in s závislé položky knihoven</span><span class="sxs-lookup"><span data-stu-id="47934-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="47934-162">Téměř všechny moduly plug-in jsou složitější než jednoduché "Hello World" a mnoha modulů plug-in mají závislosti na dalších knihovnách.</span><span class="sxs-lookup"><span data-stu-id="47934-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="47934-163">`JsonPlugin` a `OldJson` modulu plug-in projekty v ukázce zobrazit dva příklady moduly plug-in s závislosti balíčku NuGet na `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="47934-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="47934-164">Soubory projektu samy nemají žádné speciální informace pro projektové odkazy a (po přidání modulu plug-in cesty k `pluginPaths` pole) na moduly plug-in spuštění, i v případě, že spuštění v rámci stejné AppWithPlugin aplikace.</span><span class="sxs-lookup"><span data-stu-id="47934-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="47934-165">Ale tyto projekty nekopírovat odkazovaná sestavení do výstupního adresáře, aby sestavení musí být na počítači uživatele pro moduly plug-in pro práci.</span><span class="sxs-lookup"><span data-stu-id="47934-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="47934-166">Existují dva způsoby, jak tento problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="47934-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="47934-167">První možností je použít `dotnet publish` příkaz pro publikování knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="47934-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="47934-168">Případně pokud budete chtít použít výstup `dotnet build` pro váš modul plug-in, můžete přidat `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` vlastnost mezi `<PropertyGroup>` značky v souboru modulu plug-in projektu.</span><span class="sxs-lookup"><span data-stu-id="47934-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="47934-169">Zobrazit `XcopyablePlugin` projekt modulu plug-in pro příklad.</span><span class="sxs-lookup"><span data-stu-id="47934-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="47934-170">Další příklady modul plug-in v ukázce</span><span class="sxs-lookup"><span data-stu-id="47934-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="47934-171">Úplný zdrojový kód pro účely tohoto kurzu můžete najít v [úložišti dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="47934-171">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="47934-172">Je hotová ukázka obsahuje několik příkladů scénářů `AssemblyDependencyResolver` chování.</span><span class="sxs-lookup"><span data-stu-id="47934-172">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="47934-173">Například `AssemblyDependencyResolver` objektu můžete také vyřešit nativních knihoven, jakož i lokalizovaná satelitní sestavení v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="47934-173">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="47934-174">`UVPlugin` a `FrenchPlugin` v úložišti ukázek ukazují tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="47934-174">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="47934-175">Způsob vytvoření odkazu na sestavení rozhraní modulu plug-in definovaných v balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="47934-175">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="47934-176">Řekněme, že je aplikace A, který má modul plug-in rozhraní definované v balíček NuGet s názvem `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="47934-176">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="47934-177">Jak můžete odkázat na balíček správně v projektu pro modul plug-in?</span><span class="sxs-lookup"><span data-stu-id="47934-177">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="47934-178">Pro projektové odkazy pomocí `<Private>false</Private>` metadat na `ProjectReference` element v souboru projektu zabránily knihovny dll byly zkopírovány na výstupu.</span><span class="sxs-lookup"><span data-stu-id="47934-178">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="47934-179">Chcete-li správně odkazovat `A.PluginBase` balíčku, kterou chcete změnit `<PackageReference>` element v souboru projektu následující:</span><span class="sxs-lookup"><span data-stu-id="47934-179">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="47934-180">Díky tomu `A.PluginBase` sestavení jsou zkopírovány do výstupního adresáře vašeho modulu plug-in a zajistí, že váš modul plug-in použije příslušné verzi `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="47934-180">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="47934-181">Modul plug-in cílové rozhraní framework doporučení</span><span class="sxs-lookup"><span data-stu-id="47934-181">Plugin target framework recommendations</span></span>

<span data-ttu-id="47934-182">Vzhledem k tomu používá načítání závislost modulu plug-in *deps.json* souboru, je gotcha související se modul plug-in cílovou architekturu.</span><span class="sxs-lookup"><span data-stu-id="47934-182">Because plugin dependency loading uses the *deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="47934-183">Konkrétně váš moduly plug-in zaměřit modulu runtime, jako je .NET Core 3.0 místo verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="47934-183">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="47934-184">`deps.json` Soubor se generuje založená na platformě pro které projekt cílí, a protože mnoho balíčků kompatibilním s technologií .NET Standard dodávat referenční sestavení pro sestavení proti sestavení .NET Standard a implementaci pro konkrétní moduly runtime, `deps.json` možná není správně sestavení implementace viz nebo ji může vzít .NET Standard verzi sestavení namísto očekáváte, že verze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="47934-184">The `deps.json` file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the `deps.json` may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
