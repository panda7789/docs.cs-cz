---
title: Vytvoření aplikace .NET Core pomocí modulů plug-in
description: Zjistěte, jak vytvořit aplikaci .NET Core, která podporuje pluginy.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: eae792ddaa6655bfdcd932d3cb695f9dafa68130
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240841"
---
# <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="d4139-103">Vytvoření aplikace .NET Core pomocí modulů plug-in</span><span class="sxs-lookup"><span data-stu-id="d4139-103">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="d4139-104">Tento kurz vám ukáže, <xref:System.Runtime.Loader.AssemblyLoadContext> jak vytvořit vlastní načíst pluginy.</span><span class="sxs-lookup"><span data-stu-id="d4139-104">This tutorial shows you how to create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load plugins.</span></span> <span data-ttu-id="d4139-105">A <xref:System.Runtime.Loader.AssemblyDependencyResolver> se používá k vyřešení závislosti pluginu.</span><span class="sxs-lookup"><span data-stu-id="d4139-105">An <xref:System.Runtime.Loader.AssemblyDependencyResolver> is used to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="d4139-106">Výukový program správně izoluje závislosti pluginu z hostitelské aplikace.</span><span class="sxs-lookup"><span data-stu-id="d4139-106">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span> <span data-ttu-id="d4139-107">Dozvíte se, jak provést tyto akce:</span><span class="sxs-lookup"><span data-stu-id="d4139-107">You'll learn how to:</span></span>

- <span data-ttu-id="d4139-108">Strukturujte projekt na podporu pluginů.</span><span class="sxs-lookup"><span data-stu-id="d4139-108">Structure a project to support plugins.</span></span>
- <span data-ttu-id="d4139-109">Vytvořte <xref:System.Runtime.Loader.AssemblyLoadContext> vlastní načíst každý plugin.</span><span class="sxs-lookup"><span data-stu-id="d4139-109">Create a custom <xref:System.Runtime.Loader.AssemblyLoadContext> to load each plugin.</span></span>
- <span data-ttu-id="d4139-110">Pomocí <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> typu povolte moduly plug-in mít závislosti.</span><span class="sxs-lookup"><span data-stu-id="d4139-110">Use the <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> type to allow plugins to have dependencies.</span></span>
- <span data-ttu-id="d4139-111">Autor pluginy, které lze snadno nasadit pouhým zkopírováním artefakty sestavení.</span><span class="sxs-lookup"><span data-stu-id="d4139-111">Author plugins that can be easily deployed by just copying the build artifacts.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4139-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4139-112">Prerequisites</span></span>

- <span data-ttu-id="d4139-113">Nainstalujte sadu [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.</span><span class="sxs-lookup"><span data-stu-id="d4139-113">Install the [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) or a newer version.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="d4139-114">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="d4139-114">Create the application</span></span>

<span data-ttu-id="d4139-115">Prvním krokem je vytvoření aplikace:</span><span class="sxs-lookup"><span data-stu-id="d4139-115">The first step is to create the application:</span></span>

1. <span data-ttu-id="d4139-116">Vytvořte novou složku a v této složce spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d4139-116">Create a new folder, and in that folder run the following command:</span></span>

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. <span data-ttu-id="d4139-117">Chcete-li usnadnit vytváření projektu, vytvořte soubor řešení sady Visual Studio ve stejné složce.</span><span class="sxs-lookup"><span data-stu-id="d4139-117">To make building the project easier, create a Visual Studio solution file in the same folder.</span></span> <span data-ttu-id="d4139-118">Spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d4139-118">Run the following command:</span></span>

    ```dotnetcli
    dotnet new sln
    ```

3. <span data-ttu-id="d4139-119">Chcete-li přidat projekt aplikace do řešení, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d4139-119">Run the following command to add the app project to the solution:</span></span>

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

<span data-ttu-id="d4139-120">Nyní můžeme vyplnit kostru naší žádosti.</span><span class="sxs-lookup"><span data-stu-id="d4139-120">Now we can fill in the skeleton of our application.</span></span> <span data-ttu-id="d4139-121">Nahraďte kód v souboru *AppWithPlugin/Program.cs* následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d4139-121">Replace the code in the *AppWithPlugin/Program.cs* file with the following code:</span></span>

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

## <a name="create-the-plugin-interfaces"></a><span data-ttu-id="d4139-122">Vytvoření rozhraní pluginu</span><span class="sxs-lookup"><span data-stu-id="d4139-122">Create the plugin interfaces</span></span>

<span data-ttu-id="d4139-123">Dalším krokem při vytváření aplikace s pluginy je definování rozhraní, které pluginy potřebují implementovat.</span><span class="sxs-lookup"><span data-stu-id="d4139-123">The next step in building an app with plugins is defining the interface the plugins need to implement.</span></span> <span data-ttu-id="d4139-124">Doporučujeme vytvořit knihovnu tříd, která obsahuje všechny typy, které chcete použít pro komunikaci mezi aplikací a pluginy.</span><span class="sxs-lookup"><span data-stu-id="d4139-124">We suggest that you make a class library that contains any types that you plan to use for communicating between your app and plugins.</span></span> <span data-ttu-id="d4139-125">Tato divize umožňuje publikovat rozhraní pluginu jako balíček, aniž byste museli odesílat plnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d4139-125">This division allows you to publish your plugin interface as a package without having to ship your full application.</span></span>

<span data-ttu-id="d4139-126">V kořenové složce projektu `dotnet new classlib -o PluginBase`spusťte .</span><span class="sxs-lookup"><span data-stu-id="d4139-126">In the root folder of the project, run `dotnet new classlib -o PluginBase`.</span></span> <span data-ttu-id="d4139-127">Také spusťte `dotnet sln add PluginBase/PluginBase.csproj` přidat projekt do souboru řešení.</span><span class="sxs-lookup"><span data-stu-id="d4139-127">Also, run `dotnet sln add PluginBase/PluginBase.csproj` to add the project to the solution file.</span></span> <span data-ttu-id="d4139-128">Odstraňte `PluginBase/Class1.cs` soubor a vytvořte nový `PluginBase` soubor `ICommand.cs` ve složce s názvem s následující definicí rozhraní:</span><span class="sxs-lookup"><span data-stu-id="d4139-128">Delete the `PluginBase/Class1.cs` file, and create a new file in the `PluginBase` folder named `ICommand.cs` with the following interface definition:</span></span>

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

<span data-ttu-id="d4139-129">Toto `ICommand` rozhraní je rozhraní, které budou implementovat všechny pluginy.</span><span class="sxs-lookup"><span data-stu-id="d4139-129">This `ICommand` interface is the interface that all of the plugins will implement.</span></span>

<span data-ttu-id="d4139-130">Nyní, `ICommand` když je definováno rozhraní, může být projekt aplikace vyplněn o něco více.</span><span class="sxs-lookup"><span data-stu-id="d4139-130">Now that the `ICommand` interface is defined, the application project can be filled in a little more.</span></span> <span data-ttu-id="d4139-131">Přidejte odkaz `AppWithPlugin` z projektu `PluginBase` do `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` projektu pomocí příkazu z kořenové složky.</span><span class="sxs-lookup"><span data-stu-id="d4139-131">Add a reference from the `AppWithPlugin` project to the `PluginBase` project with the `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj`  command from the root folder.</span></span>

<span data-ttu-id="d4139-132">Nahraďte `// Load commands from plugins` komentář následujícím fragmentem kódu, který mu umožní načítat pluginy z daných cest k souborům:</span><span class="sxs-lookup"><span data-stu-id="d4139-132">Replace the `// Load commands from plugins` comment with the following code snippet to enable it to load plugins from given file paths:</span></span>

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

<span data-ttu-id="d4139-133">Potom komentář `// Output the loaded commands` nahraďte následujícím fragmentem kódu:</span><span class="sxs-lookup"><span data-stu-id="d4139-133">Then replace the `// Output the loaded commands` comment with the following code snippet:</span></span>

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

<span data-ttu-id="d4139-134">Nahraďte `// Execute the command with the name passed as an argument` komentář následujícím fragmentem:</span><span class="sxs-lookup"><span data-stu-id="d4139-134">Replace the `// Execute the command with the name passed as an argument` comment with the following snippet:</span></span>

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

<span data-ttu-id="d4139-135">A nakonec přidejte statické `Program` metody `LoadPlugin` `CreateCommands`do třídy s názvem a , jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="d4139-135">And finally, add static methods to the `Program` class named `LoadPlugin` and `CreateCommands`, as shown here:</span></span>

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

## <a name="load-plugins"></a><span data-ttu-id="d4139-136">Načtení pluginů</span><span class="sxs-lookup"><span data-stu-id="d4139-136">Load plugins</span></span>

<span data-ttu-id="d4139-137">Nyní aplikace může správně načíst a vytvořit instanci příkazů z načtených sestavení pluginů, ale stále není schopna načíst sestavení pluginů.</span><span class="sxs-lookup"><span data-stu-id="d4139-137">Now the application can correctly load and instantiate commands from loaded plugin assemblies, but it's still unable to load the plugin assemblies.</span></span> <span data-ttu-id="d4139-138">Vytvořte soubor s názvem *PluginLoadContext.cs* ve složce *AppWithPlugin* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="d4139-138">Create a file named *PluginLoadContext.cs* in the *AppWithPlugin* folder with the following contents:</span></span>

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

<span data-ttu-id="d4139-139">Typ `PluginLoadContext` je odvozen <xref:System.Runtime.Loader.AssemblyLoadContext>od .</span><span class="sxs-lookup"><span data-stu-id="d4139-139">The `PluginLoadContext` type derives from <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="d4139-140">Typ `AssemblyLoadContext` je zvláštní typ v běhu, který umožňuje vývojářům izolovat načtená sestavení do různých skupin, aby se zajistilo, že verze sestavení nejsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="d4139-140">The `AssemblyLoadContext` type is a special type in the runtime that allows developers to isolate loaded assemblies into different groups to ensure that assembly versions don't conflict.</span></span> <span data-ttu-id="d4139-141">Kromě toho vlastní `AssemblyLoadContext` můžete zvolit různé cesty k načtení sestavení z a přepsat výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="d4139-141">Additionally, a custom `AssemblyLoadContext` can choose different paths to load assemblies from and override the default behavior.</span></span> <span data-ttu-id="d4139-142">Používá `PluginLoadContext` instanci `AssemblyDependencyResolver` typu zavedeného v rozhraní .NET Core 3.0 k překladu názvů sestavení na cesty.</span><span class="sxs-lookup"><span data-stu-id="d4139-142">The `PluginLoadContext` uses an instance of the `AssemblyDependencyResolver` type introduced in .NET Core 3.0 to resolve assembly names to paths.</span></span> <span data-ttu-id="d4139-143">Objekt `AssemblyDependencyResolver` je vytvořen s cestou do knihovny tříd .NET.</span><span class="sxs-lookup"><span data-stu-id="d4139-143">The `AssemblyDependencyResolver` object is constructed with the path to a .NET class library.</span></span> <span data-ttu-id="d4139-144">Řeší sestavení a nativní knihovny na jejich relativní cesty založené na souboru *.deps.json* `AssemblyDependencyResolver` pro knihovnu tříd, jejíž cesta byla předána konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d4139-144">It resolves assemblies and native libraries to their relative paths based on the *.deps.json* file for the class library whose path was passed to the `AssemblyDependencyResolver` constructor.</span></span> <span data-ttu-id="d4139-145">Vlastní `AssemblyLoadContext` umožňuje pluginy mít své vlastní závislosti `AssemblyDependencyResolver` a usnadňuje správné načtení závislostí.</span><span class="sxs-lookup"><span data-stu-id="d4139-145">The custom `AssemblyLoadContext` enables plugins to have their own dependencies, and the `AssemblyDependencyResolver` makes it easy to correctly load the dependencies.</span></span>

<span data-ttu-id="d4139-146">Nyní, `AppWithPlugin` když projekt `PluginLoadContext` má typ, aktualizujte metodu `Program.LoadPlugin` s následujícím tělem:</span><span class="sxs-lookup"><span data-stu-id="d4139-146">Now that the `AppWithPlugin` project has the `PluginLoadContext` type, update the `Program.LoadPlugin` method with the following body:</span></span>

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

<span data-ttu-id="d4139-147">Použitím jiné `PluginLoadContext` instance pro každý plugin mohou mít pluginy různé nebo dokonce konfliktní závislosti bez problémů.</span><span class="sxs-lookup"><span data-stu-id="d4139-147">By using a different `PluginLoadContext` instance for each plugin, the plugins can have different or even conflicting dependencies without issue.</span></span>

## <a name="simple-plugin-with-no-dependencies"></a><span data-ttu-id="d4139-148">Jednoduchý plugin bez závislostí</span><span class="sxs-lookup"><span data-stu-id="d4139-148">Simple plugin with no dependencies</span></span>

<span data-ttu-id="d4139-149">Zpět v kořenové složce postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="d4139-149">Back in the root folder, do the following:</span></span>

1. <span data-ttu-id="d4139-150">Spusťte následující příkaz a vytvořte `HelloPlugin`nový projekt knihovny tříd s názvem :</span><span class="sxs-lookup"><span data-stu-id="d4139-150">Run the following command to create a new class library project named `HelloPlugin`:</span></span>

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. <span data-ttu-id="d4139-151">Chcete-li přidat projekt do `AppWithPlugin` řešení, spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="d4139-151">Run the following command to add the project to the `AppWithPlugin` solution:</span></span>

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. <span data-ttu-id="d4139-152">Nahraďte soubor *HelloPlugin/Class1.cs* souborem s názvem *HelloCommand.cs* s následujícím obsahem:</span><span class="sxs-lookup"><span data-stu-id="d4139-152">Replace the *HelloPlugin/Class1.cs* file with a file named *HelloCommand.cs* with the following contents:</span></span>

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

<span data-ttu-id="d4139-153">Nyní otevřete soubor *HelloPlugin.csproj.*</span><span class="sxs-lookup"><span data-stu-id="d4139-153">Now, open the *HelloPlugin.csproj* file.</span></span> <span data-ttu-id="d4139-154">Mělo by to vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="d4139-154">It should look similar to the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

<span data-ttu-id="d4139-155">Mezi značky `<Project>` přidejte následující prvky:</span><span class="sxs-lookup"><span data-stu-id="d4139-155">In between the `<Project>` tags, add the following elements:</span></span>

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

<span data-ttu-id="d4139-156">Prvek `<Private>false</Private>` je důležitý.</span><span class="sxs-lookup"><span data-stu-id="d4139-156">The `<Private>false</Private>` element is important.</span></span> <span data-ttu-id="d4139-157">To říká MSBuild nekopírovat *PluginBase.dll* do výstupního adresáře pro HelloPlugin.</span><span class="sxs-lookup"><span data-stu-id="d4139-157">This tells MSBuild to not copy *PluginBase.dll* to the output directory for HelloPlugin.</span></span> <span data-ttu-id="d4139-158">Pokud je ve výstupním adresáři k dispozici `PluginLoadContext` sestavení *PluginBase.dll,* najdete sestavení a načte ho při načtení sestavení *HelloPlugin.dll.*</span><span class="sxs-lookup"><span data-stu-id="d4139-158">If the *PluginBase.dll* assembly is present in the output directory, `PluginLoadContext` will find the assembly there and load it when it loads the *HelloPlugin.dll* assembly.</span></span> <span data-ttu-id="d4139-159">V tomto okamžiku `HelloPlugin.HelloCommand` bude typ `ICommand` implementovat rozhraní z *PluginBase.dll* `HelloPlugin` ve výstupním `ICommand` adresáři projektu, nikoli rozhraní, které je načteno do výchozího kontextu zatížení.</span><span class="sxs-lookup"><span data-stu-id="d4139-159">At this point, the `HelloPlugin.HelloCommand` type will implement the `ICommand` interface from the *PluginBase.dll* in the output directory of the `HelloPlugin` project, not the `ICommand` interface that is loaded into the default load context.</span></span> <span data-ttu-id="d4139-160">Vzhledem k tomu, že runtime vidí tyto dva `AppWithPlugin.Program.CreateCommands` typy jako různé typy z různých sestavení, metoda nenajde příkazy.</span><span class="sxs-lookup"><span data-stu-id="d4139-160">Since the runtime sees these two types as different types from different assemblies, the `AppWithPlugin.Program.CreateCommands` method won't find the commands.</span></span> <span data-ttu-id="d4139-161">V důsledku toho `<Private>false</Private>` metadata je vyžadována pro odkaz na sestavení obsahující rozhraní pluginu.</span><span class="sxs-lookup"><span data-stu-id="d4139-161">As a result, the `<Private>false</Private>` metadata is required for the reference to the assembly containing the plugin interfaces.</span></span>

<span data-ttu-id="d4139-162">Podobně `<ExcludeAssets>runtime</ExcludeAssets>` prvek je také důležité, `PluginBase` pokud odkazuje na jiné balíčky.</span><span class="sxs-lookup"><span data-stu-id="d4139-162">Similarly, the `<ExcludeAssets>runtime</ExcludeAssets>` element is also important if the `PluginBase` references other packages.</span></span> <span data-ttu-id="d4139-163">Toto nastavení má `<Private>false</Private>` stejný účinek jako ale `PluginBase` funguje na odkazy na balíček, které může zahrnovat projekt nebo jedna z jeho závislostí.</span><span class="sxs-lookup"><span data-stu-id="d4139-163">This setting has the same effect as `<Private>false</Private>` but works on package references that the `PluginBase` project or one of its dependencies may include.</span></span>

<span data-ttu-id="d4139-164">Nyní, `HelloPlugin` když je projekt dokončen, `AppWithPlugin` měli byste `HelloPlugin` aktualizovat projekt, abyste věděli, kde lze plugin nalézt.</span><span class="sxs-lookup"><span data-stu-id="d4139-164">Now that the `HelloPlugin` project is complete, you should update the `AppWithPlugin` project to know where the `HelloPlugin` plugin can be found.</span></span> <span data-ttu-id="d4139-165">Za `// Paths to plugins to load` komentář, `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` přidejte jako `pluginPaths` prvek pole.</span><span class="sxs-lookup"><span data-stu-id="d4139-165">After the `// Paths to plugins to load` comment, add `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` as an element of the `pluginPaths` array.</span></span>

## <a name="plugin-with-library-dependencies"></a><span data-ttu-id="d4139-166">Plugin se závislostmi knihovny</span><span class="sxs-lookup"><span data-stu-id="d4139-166">Plugin with library dependencies</span></span>

<span data-ttu-id="d4139-167">Téměř všechny pluginy jsou složitější než jednoduchý "Hello World" a mnoho pluginů má závislosti na jiných knihovnách.</span><span class="sxs-lookup"><span data-stu-id="d4139-167">Almost all plugins are more complex than a simple "Hello World", and many plugins have dependencies on other libraries.</span></span> <span data-ttu-id="d4139-168">A `JsonPlugin` `OldJson` plugin projekty v ukázce zobrazit dva příklady `Newtonsoft.Json`pluginů s NuGet balíček závislosti na .</span><span class="sxs-lookup"><span data-stu-id="d4139-168">The `JsonPlugin` and `OldJson` plugin projects in the sample show two examples of plugins with NuGet package dependencies on `Newtonsoft.Json`.</span></span> <span data-ttu-id="d4139-169">Samotné soubory projektu nemají žádné speciální informace pro odkazy na projekt a (po `pluginPaths` přidání cest pluginu do pole) pluginy běží perfektně, i když běží ve stejném provádění aplikace AppWithPlugin.</span><span class="sxs-lookup"><span data-stu-id="d4139-169">The project files themselves don't have any special information for the project references, and (after adding the plugin paths to the `pluginPaths` array) the plugins run perfectly, even if run in the same execution of the AppWithPlugin app.</span></span> <span data-ttu-id="d4139-170">Tyto projekty však nekopírují odkazovaná sestavení do jejich výstupního adresáře, takže sestavení musí být přítomna v počítači uživatele, aby moduly plug-in fungovaly.</span><span class="sxs-lookup"><span data-stu-id="d4139-170">However, these projects don't copy the referenced assemblies to their output directory, so the assemblies need to be present on the user's machine for the plugins to work.</span></span> <span data-ttu-id="d4139-171">Existují dva způsoby, jak tento problém vyřešit.</span><span class="sxs-lookup"><span data-stu-id="d4139-171">There are two ways to work around this problem.</span></span> <span data-ttu-id="d4139-172">První možností je použití `dotnet publish` příkazu k publikování knihovny tříd.</span><span class="sxs-lookup"><span data-stu-id="d4139-172">The first option is to use the `dotnet publish` command to publish the class library.</span></span> <span data-ttu-id="d4139-173">Případně, pokud chcete mít možnost použít výstup `dotnet build` pro váš plugin, `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` můžete přidat `<PropertyGroup>` vlastnost mezi značky v souboru projektu pluginu.</span><span class="sxs-lookup"><span data-stu-id="d4139-173">Alternatively, if you want to be able to use the output of `dotnet build` for your plugin, you can add the `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` property between the `<PropertyGroup>` tags in the plugin's project file.</span></span> <span data-ttu-id="d4139-174">Podívejte `XcopyablePlugin` se na plugin projekt pro příklad.</span><span class="sxs-lookup"><span data-stu-id="d4139-174">See the `XcopyablePlugin` plugin project for an example.</span></span>

## <a name="other-examples-in-the-sample"></a><span data-ttu-id="d4139-175">Další příklady ve vzorku</span><span class="sxs-lookup"><span data-stu-id="d4139-175">Other examples in the sample</span></span>

<span data-ttu-id="d4139-176">Kompletní zdrojový kód pro tento kurz naleznete v [úložišti dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="d4139-176">The complete source code for this tutorial can be found in [the dotnet/samples repository](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span> <span data-ttu-id="d4139-177">Dokončená ukázka obsahuje několik `AssemblyDependencyResolver` dalších příkladů chování.</span><span class="sxs-lookup"><span data-stu-id="d4139-177">The completed sample includes a few other examples of `AssemblyDependencyResolver` behavior.</span></span> <span data-ttu-id="d4139-178">Objekt může `AssemblyDependencyResolver` například také vyřešit nativní knihovny, stejně jako lokalizované satelitní sestavení zahrnuté v balíčcích NuGet.</span><span class="sxs-lookup"><span data-stu-id="d4139-178">For example, the `AssemblyDependencyResolver` object can also resolve native libraries as well as localized satellite assemblies included in NuGet packages.</span></span> <span data-ttu-id="d4139-179">A `UVPlugin` `FrenchPlugin` v úložišti ukázky ukazují tyto scénáře.</span><span class="sxs-lookup"><span data-stu-id="d4139-179">The `UVPlugin` and `FrenchPlugin` in the samples repository demonstrate these scenarios.</span></span>

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a><span data-ttu-id="d4139-180">Odkaz na rozhraní pluginu z balíčku NuGet</span><span class="sxs-lookup"><span data-stu-id="d4139-180">Reference a plugin interface from a NuGet package</span></span>

<span data-ttu-id="d4139-181">Řekněme, že existuje aplikace A, která má rozhraní plugindefinované `A.PluginBase`v balíčku NuGet s názvem .</span><span class="sxs-lookup"><span data-stu-id="d4139-181">Let's say that there is an app A that has a plugin interface defined in the NuGet package named `A.PluginBase`.</span></span> <span data-ttu-id="d4139-182">Jak správně odkazujete na balíček v projektu pluginu?</span><span class="sxs-lookup"><span data-stu-id="d4139-182">How do you reference the package correctly in your plugin project?</span></span> <span data-ttu-id="d4139-183">Pro odkazy na projekt, použití `<Private>false</Private>` `ProjectReference` metadat na prvek v souboru projektu zabránit dll zkopírovat do výstupu.</span><span class="sxs-lookup"><span data-stu-id="d4139-183">For project references, using the `<Private>false</Private>` metadata on the `ProjectReference` element in the project file prevented the dll from being copied to the output.</span></span>

<span data-ttu-id="d4139-184">Chcete-li `A.PluginBase` správně odkazovat na `<PackageReference>` balíček, chcete změnit prvek v souboru projektu na následující:</span><span class="sxs-lookup"><span data-stu-id="d4139-184">To correctly reference the `A.PluginBase` package, you want to change the `<PackageReference>` element in the project file to the following:</span></span>

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

<span data-ttu-id="d4139-185">Tím zabráníte `A.PluginBase` kopírování sestavení do výstupního adresáře pluginu a zajistíte, že váš `A.PluginBase`plugin bude používat verzi aplikace .</span><span class="sxs-lookup"><span data-stu-id="d4139-185">This prevents the `A.PluginBase` assemblies from being copied to the output directory of your plugin and ensures that your plugin will use A's version of `A.PluginBase`.</span></span>

## <a name="plugin-target-framework-recommendations"></a><span data-ttu-id="d4139-186">Doporučení cílového rámce pluginů</span><span class="sxs-lookup"><span data-stu-id="d4139-186">Plugin target framework recommendations</span></span>

<span data-ttu-id="d4139-187">Vzhledem k tomu, že načítání závislostí pluginů používá soubor *.deps.json,* existuje gotcha související s cílovým rámcem pluginu.</span><span class="sxs-lookup"><span data-stu-id="d4139-187">Because plugin dependency loading uses the *.deps.json* file, there is a gotcha related to the plugin's target framework.</span></span> <span data-ttu-id="d4139-188">Konkrétně by vaše pluginy měly cílit na modul runtime, například .NET Core 3.0, namísto verze standardu .NET.</span><span class="sxs-lookup"><span data-stu-id="d4139-188">Specifically, your plugins should target a runtime, such as .NET Core 3.0, instead of a version of .NET Standard.</span></span> <span data-ttu-id="d4139-189">Soubor *.deps.json* je generován na základě toho, na jakém rámci se projekt zaměřuje, a protože mnoho balíčků .NET Standard kompatibilních s ship reference sestavení pro sestavení proti .NET Standard a implementační sestavení pro konkrétní runtimes, *.deps.json* nemusí správně zobrazit sestavení implementace nebo může uchopit verzi .NET Standard sestavení namísto verze .NET Core, kterou očekáváte.</span><span class="sxs-lookup"><span data-stu-id="d4139-189">The *.deps.json* file is generated based on which framework the project targets, and since many .NET Standard-compatible packages ship reference assemblies for building against .NET Standard and implementation assemblies for specific runtimes, the *.deps.json* may not correctly see implementation assemblies, or it may grab the .NET Standard version of an assembly instead of the .NET Core version you expect.</span></span>

## <a name="plugin-framework-references"></a><span data-ttu-id="d4139-190">Odkazy na rozhraní pluginů</span><span class="sxs-lookup"><span data-stu-id="d4139-190">Plugin framework references</span></span>

<span data-ttu-id="d4139-191">V současné době pluginy nemohou zavést nové rámce do procesu.</span><span class="sxs-lookup"><span data-stu-id="d4139-191">Currently, plugins can't introduce new frameworks into the process.</span></span> <span data-ttu-id="d4139-192">Například nelze načíst plugin, který `Microsoft.AspNetCore.App` používá rozhraní do aplikace, `Microsoft.NETCore.App` která používá pouze kořenový rámec.</span><span class="sxs-lookup"><span data-stu-id="d4139-192">For example, you can't load a plugin that uses the `Microsoft.AspNetCore.App` framework into an application that only uses the root `Microsoft.NETCore.App` framework.</span></span> <span data-ttu-id="d4139-193">Hostitelská aplikace musí deklarovat odkazy na všechny rámce potřebné pro pluginy.</span><span class="sxs-lookup"><span data-stu-id="d4139-193">The host application must declare references to all frameworks needed by plugins.</span></span>
