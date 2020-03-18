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
# <a name="create-a-net-core-application-with-plugins"></a>Vytvoření aplikace .NET Core pomocí modulů plug-in

Tento kurz vám ukáže, <xref:System.Runtime.Loader.AssemblyLoadContext> jak vytvořit vlastní načíst pluginy. A <xref:System.Runtime.Loader.AssemblyDependencyResolver> se používá k vyřešení závislosti pluginu. Výukový program správně izoluje závislosti pluginu z hostitelské aplikace. Dozvíte se, jak provést tyto akce:

- Strukturujte projekt na podporu pluginů.
- Vytvořte <xref:System.Runtime.Loader.AssemblyLoadContext> vlastní načíst každý plugin.
- Pomocí <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> typu povolte moduly plug-in mít závislosti.
- Autor pluginy, které lze snadno nasadit pouhým zkopírováním artefakty sestavení.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte sadu [.NET Core 3.0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření aplikace:

1. Vytvořte novou složku a v této složce spusťte následující příkaz:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Chcete-li usnadnit vytváření projektu, vytvořte soubor řešení sady Visual Studio ve stejné složce. Spusťte následující příkaz:

    ```dotnetcli
    dotnet new sln
    ```

3. Chcete-li přidat projekt aplikace do řešení, spusťte následující příkaz:

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

Nyní můžeme vyplnit kostru naší žádosti. Nahraďte kód v souboru *AppWithPlugin/Program.cs* následujícím kódem:

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

## <a name="create-the-plugin-interfaces"></a>Vytvoření rozhraní pluginu

Dalším krokem při vytváření aplikace s pluginy je definování rozhraní, které pluginy potřebují implementovat. Doporučujeme vytvořit knihovnu tříd, která obsahuje všechny typy, které chcete použít pro komunikaci mezi aplikací a pluginy. Tato divize umožňuje publikovat rozhraní pluginu jako balíček, aniž byste museli odesílat plnou aplikaci.

V kořenové složce projektu `dotnet new classlib -o PluginBase`spusťte . Také spusťte `dotnet sln add PluginBase/PluginBase.csproj` přidat projekt do souboru řešení. Odstraňte `PluginBase/Class1.cs` soubor a vytvořte nový `PluginBase` soubor `ICommand.cs` ve složce s názvem s následující definicí rozhraní:

[!code-csharp[the-plugin-interface](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/PluginBase/ICommand.cs)]

Toto `ICommand` rozhraní je rozhraní, které budou implementovat všechny pluginy.

Nyní, `ICommand` když je definováno rozhraní, může být projekt aplikace vyplněn o něco více. Přidejte odkaz `AppWithPlugin` z projektu `PluginBase` do `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` projektu pomocí příkazu z kořenové složky.

Nahraďte `// Load commands from plugins` komentář následujícím fragmentem kódu, který mu umožní načítat pluginy z daných cest k souborům:

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

Potom komentář `// Output the loaded commands` nahraďte následujícím fragmentem kódu:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Nahraďte `// Execute the command with the name passed as an argument` komentář následujícím fragmentem:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

A nakonec přidejte statické `Program` metody `LoadPlugin` `CreateCommands`do třídy s názvem a , jak je znázorněno zde:

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

## <a name="load-plugins"></a>Načtení pluginů

Nyní aplikace může správně načíst a vytvořit instanci příkazů z načtených sestavení pluginů, ale stále není schopna načíst sestavení pluginů. Vytvořte soubor s názvem *PluginLoadContext.cs* ve složce *AppWithPlugin* s následujícím obsahem:

[!code-csharp[loading-plugins](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/AppWithPlugin/PluginLoadContext.cs)]

Typ `PluginLoadContext` je odvozen <xref:System.Runtime.Loader.AssemblyLoadContext>od . Typ `AssemblyLoadContext` je zvláštní typ v běhu, který umožňuje vývojářům izolovat načtená sestavení do různých skupin, aby se zajistilo, že verze sestavení nejsou v konfliktu. Kromě toho vlastní `AssemblyLoadContext` můžete zvolit různé cesty k načtení sestavení z a přepsat výchozí chování. Používá `PluginLoadContext` instanci `AssemblyDependencyResolver` typu zavedeného v rozhraní .NET Core 3.0 k překladu názvů sestavení na cesty. Objekt `AssemblyDependencyResolver` je vytvořen s cestou do knihovny tříd .NET. Řeší sestavení a nativní knihovny na jejich relativní cesty založené na souboru *.deps.json* `AssemblyDependencyResolver` pro knihovnu tříd, jejíž cesta byla předána konstruktoru. Vlastní `AssemblyLoadContext` umožňuje pluginy mít své vlastní závislosti `AssemblyDependencyResolver` a usnadňuje správné načtení závislostí.

Nyní, `AppWithPlugin` když projekt `PluginLoadContext` má typ, aktualizujte metodu `Program.LoadPlugin` s následujícím tělem:

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

Použitím jiné `PluginLoadContext` instance pro každý plugin mohou mít pluginy různé nebo dokonce konfliktní závislosti bez problémů.

## <a name="simple-plugin-with-no-dependencies"></a>Jednoduchý plugin bez závislostí

Zpět v kořenové složce postupujte takto:

1. Spusťte následující příkaz a vytvořte `HelloPlugin`nový projekt knihovny tříd s názvem :

    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Chcete-li přidat projekt do `AppWithPlugin` řešení, spusťte následující příkaz:

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

3. Nahraďte soubor *HelloPlugin/Class1.cs* souborem s názvem *HelloCommand.cs* s následujícím obsahem:

[!code-csharp[the-hello-plugin](~/samples/snippets/core/tutorials/creating-app-with-plugin-support/csharp/HelloPlugin/HelloCommand.cs)]

Nyní otevřete soubor *HelloPlugin.csproj.* Mělo by to vypadat nějak takto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

Mezi značky `<Project>` přidejte následující prvky:

```xml
<ItemGroup>
    <ProjectReference Include="..\PluginBase\PluginBase.csproj">
        <Private>false</Private>
        <ExcludeAssets>runtime</ExcludeAssets>
    </ProjectReference>
</ItemGroup>
```

Prvek `<Private>false</Private>` je důležitý. To říká MSBuild nekopírovat *PluginBase.dll* do výstupního adresáře pro HelloPlugin. Pokud je ve výstupním adresáři k dispozici `PluginLoadContext` sestavení *PluginBase.dll,* najdete sestavení a načte ho při načtení sestavení *HelloPlugin.dll.* V tomto okamžiku `HelloPlugin.HelloCommand` bude typ `ICommand` implementovat rozhraní z *PluginBase.dll* `HelloPlugin` ve výstupním `ICommand` adresáři projektu, nikoli rozhraní, které je načteno do výchozího kontextu zatížení. Vzhledem k tomu, že runtime vidí tyto dva `AppWithPlugin.Program.CreateCommands` typy jako různé typy z různých sestavení, metoda nenajde příkazy. V důsledku toho `<Private>false</Private>` metadata je vyžadována pro odkaz na sestavení obsahující rozhraní pluginu.

Podobně `<ExcludeAssets>runtime</ExcludeAssets>` prvek je také důležité, `PluginBase` pokud odkazuje na jiné balíčky. Toto nastavení má `<Private>false</Private>` stejný účinek jako ale `PluginBase` funguje na odkazy na balíček, které může zahrnovat projekt nebo jedna z jeho závislostí.

Nyní, `HelloPlugin` když je projekt dokončen, `AppWithPlugin` měli byste `HelloPlugin` aktualizovat projekt, abyste věděli, kde lze plugin nalézt. Za `// Paths to plugins to load` komentář, `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` přidejte jako `pluginPaths` prvek pole.

## <a name="plugin-with-library-dependencies"></a>Plugin se závislostmi knihovny

Téměř všechny pluginy jsou složitější než jednoduchý "Hello World" a mnoho pluginů má závislosti na jiných knihovnách. A `JsonPlugin` `OldJson` plugin projekty v ukázce zobrazit dva příklady `Newtonsoft.Json`pluginů s NuGet balíček závislosti na . Samotné soubory projektu nemají žádné speciální informace pro odkazy na projekt a (po `pluginPaths` přidání cest pluginu do pole) pluginy běží perfektně, i když běží ve stejném provádění aplikace AppWithPlugin. Tyto projekty však nekopírují odkazovaná sestavení do jejich výstupního adresáře, takže sestavení musí být přítomna v počítači uživatele, aby moduly plug-in fungovaly. Existují dva způsoby, jak tento problém vyřešit. První možností je použití `dotnet publish` příkazu k publikování knihovny tříd. Případně, pokud chcete mít možnost použít výstup `dotnet build` pro váš plugin, `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` můžete přidat `<PropertyGroup>` vlastnost mezi značky v souboru projektu pluginu. Podívejte `XcopyablePlugin` se na plugin projekt pro příklad.

## <a name="other-examples-in-the-sample"></a>Další příklady ve vzorku

Kompletní zdrojový kód pro tento kurz naleznete v [úložišti dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Dokončená ukázka obsahuje několik `AssemblyDependencyResolver` dalších příkladů chování. Objekt může `AssemblyDependencyResolver` například také vyřešit nativní knihovny, stejně jako lokalizované satelitní sestavení zahrnuté v balíčcích NuGet. A `UVPlugin` `FrenchPlugin` v úložišti ukázky ukazují tyto scénáře.

## <a name="reference-a-plugin-interface-from-a-nuget-package"></a>Odkaz na rozhraní pluginu z balíčku NuGet

Řekněme, že existuje aplikace A, která má rozhraní plugindefinované `A.PluginBase`v balíčku NuGet s názvem . Jak správně odkazujete na balíček v projektu pluginu? Pro odkazy na projekt, použití `<Private>false</Private>` `ProjectReference` metadat na prvek v souboru projektu zabránit dll zkopírovat do výstupu.

Chcete-li `A.PluginBase` správně odkazovat na `<PackageReference>` balíček, chcete změnit prvek v souboru projektu na následující:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Tím zabráníte `A.PluginBase` kopírování sestavení do výstupního adresáře pluginu a zajistíte, že váš `A.PluginBase`plugin bude používat verzi aplikace .

## <a name="plugin-target-framework-recommendations"></a>Doporučení cílového rámce pluginů

Vzhledem k tomu, že načítání závislostí pluginů používá soubor *.deps.json,* existuje gotcha související s cílovým rámcem pluginu. Konkrétně by vaše pluginy měly cílit na modul runtime, například .NET Core 3.0, namísto verze standardu .NET. Soubor *.deps.json* je generován na základě toho, na jakém rámci se projekt zaměřuje, a protože mnoho balíčků .NET Standard kompatibilních s ship reference sestavení pro sestavení proti .NET Standard a implementační sestavení pro konkrétní runtimes, *.deps.json* nemusí správně zobrazit sestavení implementace nebo může uchopit verzi .NET Standard sestavení namísto verze .NET Core, kterou očekáváte.

## <a name="plugin-framework-references"></a>Odkazy na rozhraní pluginů

V současné době pluginy nemohou zavést nové rámce do procesu. Například nelze načíst plugin, který `Microsoft.AspNetCore.App` používá rozhraní do aplikace, `Microsoft.NETCore.App` která používá pouze kořenový rámec. Hostitelská aplikace musí deklarovat odkazy na všechny rámce potřebné pro pluginy.
