---
title: Vytvoření aplikace .NET Core s moduly plug-in
description: Naučte se, jak vytvořit aplikaci .NET Core, která podporuje moduly plug-in.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: 54f616a7b2b20b7682963e9f5d503878bb512c90
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250165"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="84c14-103">Vytvoření aplikace .NET Core s moduly plug-in</span><span class="sxs-lookup"><span data-stu-id="84c14-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="84c14-104">V tomto kurzu se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="84c14-104">This tutorial shows you how to:</span></span>

- <span data-ttu-id="84c14-105">Vytvořte strukturu projektu pro podporu modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-105">Structure a project to support plugins.</span></span>
- <span data-ttu-id="84c14-106">Vytvořením vlastního <xref:System.Runtime.Loader.AssemblyLoadContext> načtete jednotlivé modul plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-106">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="84c14-107">Pomocí typu `System.Runtime.Loader.AssemblyDependencyResolver` povolíte, aby moduly plug-in měly závislosti.</span><span class="sxs-lookup"><span data-stu-id="84c14-107">Use the `System.Runtime.Loader.AssemblyDependencyResolver` type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="84c14-108">Vytváření modulů plug-in, které lze snadno nasadit pouhým zkopírováním artefaktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="84c14-108">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84c14-109">Požadované součásti</span><span class="sxs-lookup"><span data-stu-id="84c14-109">Prerequisites</span></span>

- <span data-ttu-id="84c14-110">Nainstalujte [rozhraní .NET Core 3,0](https://dotnet.microsoft.com/download) nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="84c14-110">Install the [.NET Core 3.0](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="84c14-111">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="84c14-111">Create the application</span></span>

<span data-ttu-id="84c14-112">Prvním krokem je vytvoření aplikace:</span><span class="sxs-lookup"><span data-stu-id="84c14-112">The first step is to create the application:</span></span>

1. <span data-ttu-id="84c14-113">Vytvořte novou složku a v této složce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="84c14-113">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="84c14-114">Aby bylo možné projekt sestavit snadněji, vytvořte soubor řešení sady Visual Studio ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="84c14-114">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="84c14-115">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="84c14-115">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="84c14-116">Spusťte následující příkaz pro přidání projektu aplikace do řešení:</span><span class="sxs-lookup"><span data-stu-id="84c14-116">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="84c14-117">Teď můžeme vyplnit kostru naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="84c14-117">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="84c14-118">Nahraďte kód v souboru *AppWithPlugin/program. cs* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="84c14-118">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="84c14-119">Vytvoření rozhraní modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="84c14-119">Create the plugin interfaces</span></span>

<span data-ttu-id="84c14-120">Dalším krokem při sestavování aplikace pomocí modulů plug-in je definování rozhraní, které moduly plug-in potřebují k implementaci.</span><span class="sxs-lookup"><span data-stu-id="84c14-120">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="84c14-121">Doporučujeme vytvořit knihovnu tříd, která obsahuje všechny typy, které plánujete použít pro komunikaci mezi aplikací a moduly plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-121">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="84c14-122">Tato divize vám umožní publikovat rozhraní modulu plug-in jako balíček bez nutnosti dodávat celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="84c14-122">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="84c14-123">V kořenové složce projektu spusťte `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="84c14-123">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="84c14-124">K přidání projektu do souboru řešení také spusťte `dotnet sln add PluginBase/PluginBase.csproj`.</span><span class="sxs-lookup"><span data-stu-id="84c14-124">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="84c14-125">Odstraňte soubor `PluginBase/Class1.cs` a ve složce `PluginBase` s názvem `ICommand.cs` vytvořte nový soubor s následující definicí rozhraní:</span><span class="sxs-lookup"><span data-stu-id="84c14-125">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="84c14-126">Toto rozhraní `ICommand` je rozhraní, které budou všechny moduly plug-in implementovat.</span><span class="sxs-lookup"><span data-stu-id="84c14-126">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="84c14-127">Teď, když je definováno rozhraní `ICommand`, může být projekt aplikace vyplněný o něco dalšího.</span><span class="sxs-lookup"><span data-stu-id="84c14-127">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="84c14-128">Přidejte odkaz z projektu `AppWithPlugin` do projektu `PluginBase` s příkazem `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` z kořenové složky.</span><span class="sxs-lookup"><span data-stu-id="84c14-128">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="84c14-129">Nahraďte komentář `// Load commands from plugins` následujícím fragmentem kódu, aby mohl načíst moduly plug-in z daných cest k souborům:</span><span class="sxs-lookup"><span data-stu-id="84c14-129">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="84c14-130">Potom nahraďte komentář `// Output the loaded commands` následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="84c14-130">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="84c14-131">Nahraďte komentář `// Execute the command with the name passed as an argument` následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="84c14-131">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="84c14-132">A nakonec přidejte statické metody do třídy `Program` s názvem `LoadPlugin` a `CreateCommands`, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="84c14-132">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="84c14-133">Načtení modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="84c14-133">Load plugins</span></span>

<span data-ttu-id="84c14-134">Aplikace nyní může správně načíst a vytvořit instanci příkazů z načtených sestavení modulu plug-in, ale stále nemůže načíst sestavení modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-134">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it is still unable to load the plugin assemblies.</span></span> <span data-ttu-id="84c14-135">Ve složce *AppWithPlugin* vytvořte soubor s názvem *PluginLoadContext.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="84c14-135">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="84c14-136">Typ `PluginLoadContext` je odvozen z <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="84c14-136">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="84c14-137">Typ `AssemblyLoadContext` je speciální typ v modulu runtime, který umožňuje vývojářům izolovat načtená sestavení do různých skupin, aby se zajistilo, že verze sestavení nejsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="84c14-137">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions do not conflict.</span></span> <span data-ttu-id="84c14-138">Navíc vlastní `AssemblyLoadContext` může zvolit různé cesty pro načtení sestavení a přepsat výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="84c14-138">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="84c14-139">@No__t-0 používá instanci typu `AssemblyDependencyResolver` představenou v .NET Core 3,0 k překladu názvů sestavení na cesty.</span><span class="sxs-lookup"><span data-stu-id="84c14-139">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="84c14-140">Objekt `AssemblyDependencyResolver` je vytvořen s cestou k knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="84c14-140">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="84c14-141">Přeloží sestavení a nativní knihovny na jejich relativní cesty založené na souboru *. DEPS. JSON* pro knihovnu tříd, jehož cesta byla předána konstruktoru `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="84c14-141">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="84c14-142">Vlastní `AssemblyLoadContext` umožňuje modulům plug-in používat vlastní závislosti a `AssemblyDependencyResolver` usnadňuje správné načtení závislostí.</span><span class="sxs-lookup"><span data-stu-id="84c14-142">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="84c14-143">Teď, když má projekt `AppWithPlugin` typ `PluginLoadContext`, aktualizujte metodu `Program.LoadPlugin` s následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="84c14-143">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="84c14-144">Při použití jiné instance `PluginLoadContext` pro každý modul plug-in můžou mít moduly plug-in různé nebo dokonce konfliktní závislosti bez problémů.</span><span class="sxs-lookup"><span data-stu-id="84c14-144">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="create-a-simple-plugin-with-no-dependencies"></a><span data-ttu-id="84c14-145">Vytvoření jednoduchého modulu plug-in bez závislostí</span><span class="sxs-lookup"><span data-stu-id="84c14-145">Create a simple plugin with no dependencies</span></span>

<span data-ttu-id="84c14-146">Zpět v kořenové složce proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="84c14-146">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="84c14-147">Spusťte následující příkaz, který vytvoří nový projekt knihovny tříd s názvem `HelloPlugin`:</span><span class="sxs-lookup"><span data-stu-id="84c14-147">Run the following command to create a new class library project named `HelloPlugin`:</span></span>
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="84c14-148">Spuštěním následujícího příkazu přidejte projekt do řešení `AppWithPlugin`:</span><span class="sxs-lookup"><span data-stu-id="84c14-148">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="84c14-149">Soubor *HelloPlugin/Class1. cs* nahraďte souborem s názvem *HelloCommand.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="84c14-149">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="84c14-150">Nyní otevřete soubor *HelloPlugin. csproj* .</span><span class="sxs-lookup"><span data-stu-id="84c14-150">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="84c14-151">Měl by vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="84c14-151">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="84c14-152">Do mezi značkami `<Project>` přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="84c14-152">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

<span data-ttu-id="84c14-153">Element `<Private>false</Private>` je velmi důležitý.</span><span class="sxs-lookup"><span data-stu-id="84c14-153">The `<Private>false</Private>` element is very important.</span></span> <span data-ttu-id="84c14-154">Nástroj MSBuild nezkopíruje *PluginBase. dll* do výstupního adresáře pro HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="84c14-154">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="84c14-155">Pokud se ve výstupním adresáři nachází sestavení *PluginBase. dll* , `PluginLoadContext` nalezne sestavení a načte ho při načtení sestavení *HelloPlugin. dll* .</span><span class="sxs-lookup"><span data-stu-id="84c14-155">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="84c14-156">V tomto okamžiku typ `HelloPlugin.HelloCommand` implementuje rozhraní `ICommand` z *knihovny PluginBase. dll* ve výstupním adresáři projektu `HelloPlugin`, nikoli rozhraní `ICommand`, které je načteno do výchozího kontextu načtení.</span><span class="sxs-lookup"><span data-stu-id="84c14-156">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="84c14-157">Vzhledem k tomu, že modul runtime tyto dva typy považuje za různé typy z různých sestavení, metoda `AppWithPlugin.Program.CreateCommands` nenajde příkazy.</span><span class="sxs-lookup"><span data-stu-id="84c14-157">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method will not find the commands.</span></span> <span data-ttu-id="84c14-158">V důsledku toho je potřeba metadata `<Private>false</Private>` pro odkaz na sestavení obsahující rozhraní modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-158">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="84c14-159">Teď, když je projekt `HelloPlugin` dokončený, doporučujeme aktualizovat projekt `AppWithPlugin`, aby věděli, kde je možné najít modul plug-in `HelloPlugin`.</span><span class="sxs-lookup"><span data-stu-id="84c14-159">Now that the `HelloPlugin` project is complete, we should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="84c14-160">Po komentáři `// Paths to plugins to load` přidejte `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako prvek pole `pluginPaths`.</span><span class="sxs-lookup"><span data-stu-id="84c14-160">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="create-a-plugin-with-library-dependencies"></a><span data-ttu-id="84c14-161">Vytvoření modulu plug-in se závislostmi knihovny</span><span class="sxs-lookup"><span data-stu-id="84c14-161">Create a plugin with library dependencies</span></span>

<span data-ttu-id="84c14-162">Téměř všechny moduly plug-in jsou složitější než jednoduché "Hello World" a mnohé moduly plug-in mají závislosti na jiných knihovnách.</span><span class="sxs-lookup"><span data-stu-id="84c14-162">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="84c14-163">Projekty modulu plug-in `JsonPlugin` a `OldJson` v ukázce znázorňují dva příklady modulů plug-in s závislostmi balíčku NuGet v `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="84c14-163">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="84c14-164">Samotné soubory projektu nemají žádné speciální informace pro odkazy na projekt a (po přidání cest modulu plug-in do pole `pluginPaths`) jsou moduly plug-in spouštěny dokonale, a to i v případě, že jsou spuštěny ve stejném spuštění aplikace AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="84c14-164">The project files themselves do not have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="84c14-165">Tyto projekty však nekopírují odkazovaná sestavení do jejich výstupního adresáře, takže sestavení musí být přítomna v počítači uživatele, aby mohly fungovat moduly plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-165">However, these projects do not copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="84c14-166">Existují dva způsoby, jak tento problém obejít.</span><span class="sxs-lookup"><span data-stu-id="84c14-166">There are two ways to work around this problem.</span></span> <span data-ttu-id="84c14-167">První možností je použít příkaz `dotnet publish` pro publikování knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="84c14-167">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="84c14-168">Případně, pokud chcete mít možnost použít výstup `dotnet build` pro modul plug-in, můžete přidat vlastnost `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` mezi značkami `<PropertyGroup>` v souboru projektu modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-168">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="84c14-169">Příklad naleznete v projektu modulu plug-in `XcopyablePlugin`.</span><span class="sxs-lookup"><span data-stu-id="84c14-169">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-plugin-examples-in-the-sample"></a><span data-ttu-id="84c14-170">Další příklady modulů plug-in v ukázce</span><span class="sxs-lookup"><span data-stu-id="84c14-170">Other plugin examples in the sample</span></span>

<span data-ttu-id="84c14-171">Úplný zdrojový kód pro tento kurz najdete v [úložišti dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="84c14-171">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="84c14-172">Hotová ukázka obsahuje několik dalších příkladů chování @no__t 0.</span><span class="sxs-lookup"><span data-stu-id="84c14-172">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="84c14-173">Například objekt `AssemblyDependencyResolver` může také překládat nativní knihovny a také lokalizovaná satelitní sestavení obsažená v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="84c14-173">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="84c14-174">Tyto scénáře předvádí `UVPlugin` a `FrenchPlugin` v úložišti ukázek.</span><span class="sxs-lookup"><span data-stu-id="84c14-174">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a><span data-ttu-id="84c14-175">Postup odkazu na sestavení rozhraní modulu plug-in definované v balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="84c14-175">How to reference a plugin interface assembly defined in a NuGet package</span></span>

<span data-ttu-id="84c14-176">Řekněme, že existuje aplikace, která má rozhraní modulu plug-in definované v balíčku NuGet s názvem `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="84c14-176">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="84c14-177">Jak v projektu modulu plug-in správně odkazovat na balíček?</span><span class="sxs-lookup"><span data-stu-id="84c14-177">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="84c14-178">V případě odkazů na projekt, použití metadat `<Private>false</Private>` u prvku `ProjectReference` v souboru projektu zabránilo zkopírování knihovny DLL do výstupu.</span><span class="sxs-lookup"><span data-stu-id="84c14-178">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="84c14-179">Pro správné odkazování na balíček `A.PluginBase` chcete změnit prvek `<PackageReference>` v souboru projektu na následující:</span><span class="sxs-lookup"><span data-stu-id="84c14-179">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="84c14-180">Tím zabráníte tomu, aby se sestavení `A.PluginBase` zkopírovala do výstupního modulu plug-in a zajistilo, že bude modul plug-in používat verzi `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="84c14-180">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="84c14-181">Doporučení pro cílové rozhraní modulu plug-in</span><span class="sxs-lookup"><span data-stu-id="84c14-181">Plugin target framework recommendations</span></span>

<span data-ttu-id="84c14-182">Vzhledem k tomu, že načítání závislostí modulu plug-in používá soubor *. DEPS. JSON* , existuje gotcha související s cílovým rozhraním modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="84c14-182">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="84c14-183">Moduly plug-in by konkrétně měly cílit na modul runtime, jako je .NET Core 3,0, namísto verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="84c14-183">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="84c14-184">Soubor *. DEPS. JSON* je vygenerován na základě toho, na které architektuře je projekt cílen, a vzhledem k tomu, že mnoho balíčků kompatibilních s .NET Standard dodává referenční sestavení pro sestavení .NET Standard a implementační sestavení pro konkrétní moduly runtime, *. DEPS. JSON* nemusí správně zobrazovat implementační sestavení nebo může místo očekávané verze .NET Core použít .NET Standard verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="84c14-184">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>
