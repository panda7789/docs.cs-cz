---
title: Vytvoření aplikace .NET Core pomocí modulů plug-in
description: Naučte se, jak vytvořit aplikaci .NET Core, která podporuje moduly plug-in.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 4c03c70edcdba52c4e6029402b92d5478a0d312c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156644"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="1ac76-103">Vytvoření aplikace .NET Core pomocí modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="1ac76-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="1ac76-104">V tomto kurzu se dozvíte, jak vytvořit vlastní <xref:System.Runtime.Loader.AssemblyLoadContext> pro načtení modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="1ac76-105">K vyřešení závislostí modulu plug-in se používá <xref:System.Runtime.Loader.AssemblyDependencyResolver>.</span><span class="sxs-lookup"><span data-stu-id="1ac76-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="1ac76-106">Kurz správně izoluje závislosti modulu plug-in z hostující aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ac76-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="1ac76-107">Dozvíte se, jak provést tyto akce:</span><span class="sxs-lookup"><span data-stu-id="1ac76-107">You'll learn how to:</span></span>

- <span data-ttu-id="1ac76-108">Vytvořte strukturu projektu pro podporu modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="1ac76-109">Vytvořte vlastní <xref:System.Runtime.Loader.AssemblyLoadContext> pro načtení každého modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="1ac76-110">Pokud chcete, aby moduly plug-in měly závislosti, použijte <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> typ.</span><span class="sxs-lookup"><span data-stu-id="1ac76-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="1ac76-111">Vytváření modulů plug-in, které lze snadno nasadit pouhým zkopírováním artefaktů sestavení.</span><span class="sxs-lookup"><span data-stu-id="1ac76-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ac76-112">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="1ac76-112">Prerequisites</span></span>

- <span data-ttu-id="1ac76-113">Nainstalujte [sadu .NET Core 3,0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="1ac76-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1ac76-114">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="1ac76-114">Create the application</span></span>

<span data-ttu-id="1ac76-115">Prvním krokem je vytvoření aplikace:</span><span class="sxs-lookup"><span data-stu-id="1ac76-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="1ac76-116">Vytvořte novou složku a v této složce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1ac76-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="1ac76-117">Aby bylo možné projekt sestavit snadněji, vytvořte soubor řešení sady Visual Studio ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="1ac76-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="1ac76-118">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="1ac76-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="1ac76-119">Spusťte následující příkaz pro přidání projektu aplikace do řešení:</span><span class="sxs-lookup"><span data-stu-id="1ac76-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="1ac76-120">Teď můžeme vyplnit kostru naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ac76-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="1ac76-121">Nahraďte kód v souboru *AppWithPlugin/program. cs* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1ac76-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="1ac76-122">Vytvoření rozhraní modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="1ac76-122">Create the plugin interfaces</span></span>

<span data-ttu-id="1ac76-123">Dalším krokem při sestavování aplikace pomocí modulů plug-in je definování rozhraní, které moduly plug-in potřebují k implementaci.</span><span class="sxs-lookup"><span data-stu-id="1ac76-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="1ac76-124">Doporučujeme vytvořit knihovnu tříd, která obsahuje všechny typy, které plánujete použít pro komunikaci mezi aplikací a moduly plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="1ac76-125">Tato divize vám umožní publikovat rozhraní modulu plug-in jako balíček bez nutnosti dodávat celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1ac76-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="1ac76-126">V kořenové složce projektu spusťte `dotnet new classlib -o PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="1ac76-127">Také spusťte `dotnet sln add PluginBase/PluginBase.csproj` pro přidání projektu do souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="1ac76-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="1ac76-128">Odstraňte soubor `PluginBase/Class1.cs` a ve složce `PluginBase` s názvem `ICommand.cs` vytvořte nový soubor s následující definicí rozhraní:</span><span class="sxs-lookup"><span data-stu-id="1ac76-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

<span data-ttu-id="1ac76-129">Toto `ICommand` rozhraní je rozhraní, které budou všechny moduly plug-in implementovat.</span><span class="sxs-lookup"><span data-stu-id="1ac76-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="1ac76-130">Nyní, když je definováno rozhraní `ICommand`, může být projekt aplikace vyplněný o něco dalšího.</span><span class="sxs-lookup"><span data-stu-id="1ac76-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="1ac76-131">Přidejte odkaz z `AppWithPlugin` projektu do projektu `PluginBase` pomocí příkazu `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` z kořenové složky.</span><span class="sxs-lookup"><span data-stu-id="1ac76-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="1ac76-132">Nahraďte `// Load commands from plugins` komentář následujícím fragmentem kódu, aby mohl načíst moduly plug-in z daných cest k souborům:</span><span class="sxs-lookup"><span data-stu-id="1ac76-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="1ac76-133">Pak nahraďte `// Output the loaded commands` komentář následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="1ac76-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="1ac76-134">Nahraďte `// Execute the command with the name passed as an argument` komentář následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="1ac76-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="1ac76-135">A nakonec přidejte statické metody do třídy `Program` s názvem `LoadPlugin` a `CreateCommands`, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="1ac76-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="1ac76-136">Načtení modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="1ac76-136">Load plugins</span></span>

<span data-ttu-id="1ac76-137">Nyní může aplikace správně načíst a vytvořit instanci příkazů z načtených sestavení modulu plug-in, ale nelze načíst sestavení modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="1ac76-138">Ve složce *AppWithPlugin* vytvořte soubor s názvem *PluginLoadContext.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="1ac76-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="1ac76-139">Typ `PluginLoadContext` je odvozen z <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="1ac76-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="1ac76-140">`AssemblyLoadContext` typ je speciální typ v modulu runtime, který umožňuje vývojářům izolovat načtená sestavení do různých skupin, aby se zajistilo, že verze sestavení nejsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="1ac76-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="1ac76-141">Kromě toho může vlastní `AssemblyLoadContext` zvolit různé cesty pro načtení sestavení a přepsat výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="1ac76-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="1ac76-142">`PluginLoadContext` používá instanci `AssemblyDependencyResolver` typu představenou v .NET Core 3,0 k překladu názvů sestavení na cesty.</span><span class="sxs-lookup"><span data-stu-id="1ac76-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="1ac76-143">Objekt `AssemblyDependencyResolver` je vytvořen s cestou k knihovně tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="1ac76-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="1ac76-144">Překládá sestavení a nativní knihovny na jejich relativní cesty založené na souboru *. DEPS. JSON* pro knihovnu tříd, jehož cesta byla předána konstruktoru `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="1ac76-145">Vlastní `AssemblyLoadContext` umožňuje modulům plug-in používat vlastní závislosti a `AssemblyDependencyResolver` usnadňuje správné načtení závislostí.</span><span class="sxs-lookup"><span data-stu-id="1ac76-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="1ac76-146">Teď, když `AppWithPlugin` projekt má `PluginLoadContext` typ, aktualizujte `Program.LoadPlugin` metodu s následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="1ac76-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="1ac76-147">Při použití jiné instance `PluginLoadContext` pro každý modul plug-in můžou mít moduly plug-in různé nebo dokonce konfliktní závislosti bez problémů.</span><span class="sxs-lookup"><span data-stu-id="1ac76-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="1ac76-148">Jednoduchý modul plug-in bez závislostí</span><span class="sxs-lookup"><span data-stu-id="1ac76-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="1ac76-149">Zpět v kořenové složce proveďte následující kroky:</span><span class="sxs-lookup"><span data-stu-id="1ac76-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="1ac76-150">Spusťte následující příkaz, který vytvoří nový projekt knihovny tříd s názvem `HelloPlugin`:</span><span class="sxs-lookup"><span data-stu-id="1ac76-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="1ac76-151">Spusťte následující příkaz pro přidání projektu do řešení `AppWithPlugin`:</span><span class="sxs-lookup"><span data-stu-id="1ac76-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="1ac76-152">Soubor *HelloPlugin/Class1. cs* nahraďte souborem s názvem *HelloCommand.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="1ac76-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="1ac76-153">Nyní otevřete soubor *HelloPlugin. csproj* .</span><span class="sxs-lookup"><span data-stu-id="1ac76-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="1ac76-154">Mělo by to vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="1ac76-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="1ac76-155">Do mezi značkami `<Project>` přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="1ac76-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="1ac76-156">Element `<Private>false</Private>` je důležitý.</span><span class="sxs-lookup"><span data-stu-id="1ac76-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="1ac76-157">Nástroj MSBuild nezkopíruje *PluginBase. dll* do výstupního adresáře pro HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="1ac76-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="1ac76-158">Pokud se ve výstupním adresáři nachází sestavení *PluginBase. dll* , `PluginLoadContext` nalezne sestavení a načte ho při načtení sestavení *HelloPlugin. dll* .</span><span class="sxs-lookup"><span data-stu-id="1ac76-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="1ac76-159">V tomto okamžiku `HelloPlugin.HelloCommand` typ implementuje rozhraní `ICommand` z *knihovny PluginBase. dll* ve výstupním adresáři projektu `HelloPlugin`, nikoli `ICommand` rozhraní, které je načteno do výchozího kontextu načtení.</span><span class="sxs-lookup"><span data-stu-id="1ac76-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="1ac76-160">Vzhledem k tomu, že modul runtime tyto dva typy považuje za různé typy z různých sestavení, metoda `AppWithPlugin.Program.CreateCommands` nenajde příkazy.</span><span class="sxs-lookup"><span data-stu-id="1ac76-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="1ac76-161">V důsledku toho se `<Private>false</Private>` metadata vyžadují pro odkaz na sestavení obsahující rozhraní modulů plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="1ac76-162">Podobně, `<ExcludeAssets>runtime</ExcludeAssets>` prvek je také důležité, pokud `PluginBase` odkazuje na jiné balíčky.</span><span class="sxs-lookup"><span data-stu-id="1ac76-162">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="1ac76-163">Toto nastavení má stejný účinek jako `<Private>false</Private>`, ale funguje na odkazech na balíčky, které mohou zahrnovat `PluginBase` projekt nebo jedna z jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="1ac76-163">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="1ac76-164">Teď, když je projekt `HelloPlugin` dokončený, byste měli aktualizovat projekt `AppWithPlugin`, aby věděli, kde se modul plug-in `HelloPlugin` najít.</span><span class="sxs-lookup"><span data-stu-id="1ac76-164">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="1ac76-165">Po `// Paths to plugins to load` komentář přidejte `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako prvek pole `pluginPaths`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-165">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="1ac76-166">Modul plug-in se závislostmi knihovny</span><span class="sxs-lookup"><span data-stu-id="1ac76-166">Plugin with library dependencies</span></span>

<span data-ttu-id="1ac76-167">Téměř všechny moduly plug-in jsou složitější než jednoduché "Hello World" a mnohé moduly plug-in mají závislosti na jiných knihovnách.</span><span class="sxs-lookup"><span data-stu-id="1ac76-167">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="1ac76-168">Projekty modulu plug-in `JsonPlugin` a `OldJson` v ukázce znázorňují dva příklady modulů plug-in s závislostmi balíčku NuGet v `Newtonsoft.Json`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-168">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="1ac76-169">Samotné soubory projektu neobsahují žádné zvláštní informace pro odkazy na projekt a (po přidání cest modulu plug-in do pole `pluginPaths`) jsou moduly plug-in spouštěny dokonale, a to i v případě, že jsou spuštěny ve stejném provedení aplikace AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="1ac76-169">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="1ac76-170">Tyto projekty však nekopírují odkazovaná sestavení do výstupního adresáře, takže sestavení musí být přítomna v počítači uživatele, aby mohly fungovat moduly plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-170">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="1ac76-171">Existují dva způsoby, jak tento problém obejít.</span><span class="sxs-lookup"><span data-stu-id="1ac76-171">There are two ways to work around this problem.</span></span> <span data-ttu-id="1ac76-172">První možností je použít příkaz `dotnet publish` pro publikování knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="1ac76-172">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="1ac76-173">Případně, pokud chcete mít možnost použít výstup `dotnet build` pro modul plug-in, můžete přidat vlastnost `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` mezi značky `<PropertyGroup>` v souboru projektu modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-173">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="1ac76-174">Příklad najdete v projektu modulu plug-in `XcopyablePlugin`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-174">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="1ac76-175">Další příklady v ukázce</span><span class="sxs-lookup"><span data-stu-id="1ac76-175">Other examples in the sample</span></span>

<span data-ttu-id="1ac76-176">Úplný zdrojový kód pro tento kurz najdete v [úložišti dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="1ac76-176">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="1ac76-177">Hotová ukázka obsahuje několik dalších příkladů chování `AssemblyDependencyResolver`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-177">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="1ac76-178">Například objekt `AssemblyDependencyResolver` může také překládat nativní knihovny a také lokalizovaná satelitní sestavení obsažená v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="1ac76-178">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="1ac76-179">Tyto scénáře předvádí `UVPlugin` a `FrenchPlugin` v úložišti ukázek.</span><span class="sxs-lookup"><span data-stu-id="1ac76-179">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="1ac76-180">Odkazování na rozhraní modulu plug-in z balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="1ac76-180">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="1ac76-181">Řekněme, že existuje aplikace, která má rozhraní modulu plug-in definované v balíčku NuGet s názvem `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-181">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="1ac76-182">Jak v projektu modulu plug-in správně odkazovat na balíček?</span><span class="sxs-lookup"><span data-stu-id="1ac76-182">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="1ac76-183">V případě odkazů na projekt pomocí `<Private>false</Private>` metadat v elementu `ProjectReference` v souboru projektu zabránilo zkopírování knihovny DLL do výstupu.</span><span class="sxs-lookup"><span data-stu-id="1ac76-183">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="1ac76-184">Chcete-li správně odkazovat na balíček `A.PluginBase`, je třeba změnit prvek `<PackageReference>` v souboru projektu na následující:</span><span class="sxs-lookup"><span data-stu-id="1ac76-184">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="1ac76-185">Tím zabráníte zkopírování `A.PluginBase` sestavení do výstupního adresáře vašeho modulu plug-in a tím zajistíte, že bude modul plug-in používat verzi `A.PluginBase`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-185">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="1ac76-186">Doporučení pro cílové rozhraní modulu plug-in</span><span class="sxs-lookup"><span data-stu-id="1ac76-186">Plugin target framework recommendations</span></span>

<span data-ttu-id="1ac76-187">Vzhledem k tomu, že načítání závislostí modulu plug-in používá soubor *. DEPS. JSON* , existuje gotcha související s cílovým rozhraním modulu plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-187">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="1ac76-188">Moduly plug-in by konkrétně měly cílit na modul runtime, jako je .NET Core 3,0, namísto verze .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="1ac76-188">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="1ac76-189">Soubor *. DEPS. JSON* je vygenerován na základě toho, na které architektuře cílí projekt, a vzhledem k tomu, že mnoho balíčků s podporou .NET Standard dodává referenční sestavení pro sestavení .NET Standard a implementace pro konkrétní moduly runtime, soubor *. DEPS. JSON* nemusí správně zobrazit implementační sestavení nebo může místo očekávané verze rozhraní .NET Core použít .NET Standard verzi sestavení.</span><span class="sxs-lookup"><span data-stu-id="1ac76-189">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="1ac76-190">Odkazy na rozhraní modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="1ac76-190">Plugin framework references</span></span>

<span data-ttu-id="1ac76-191">Moduly plug-in v současné době nemůžou do procesu zavádět nová rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1ac76-191">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="1ac76-192">Například nelze načíst modul plug-in, který používá `Microsoft.AspNetCore.App` Framework do aplikace, která používá pouze kořenové rozhraní `Microsoft.NETCore.App`.</span><span class="sxs-lookup"><span data-stu-id="1ac76-192">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="1ac76-193">Hostitelská aplikace musí deklarovat odkazy na všechny architektury, které vyžadují moduly plug-in.</span><span class="sxs-lookup"><span data-stu-id="1ac76-193">The host application must declare references to all frameworks needed by plugins.</span></span>
