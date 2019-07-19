---
title: Vytvoření aplikace .NET Core pomocí modulů plug-in
description: Naučte se, jak vytvořit aplikaci .NET Core, která podporuje moduly plug-in.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/28/2019
ms.openlocfilehash: 308fd2f853261e87da71892c42e17e36984d1978
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68330977"
---
# <a name="create-a-net-core-application-with-plugins"></a>Vytvoření aplikace .NET Core pomocí modulů plug-in

V tomto kurzu se dozvíte, jak:

- Vytvořte strukturu projektu pro podporu modulů plug-in.
- Vytvořte vlastní <xref:System.Runtime.Loader.AssemblyLoadContext> , který načte jednotlivé modul plug-in.
- `System.Runtime.Loader.AssemblyDependencyResolver` Typ použijte, pokud chcete, aby moduly plug-in měly závislosti.
- Vytváření modulů plug-in, které lze snadno nasadit pouhým zkopírováním artefaktů sestavení.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte [sadu SDK .NET Core 3,0 Preview 2](https://www.microsoft.com/net/core) nebo novější verzi.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření aplikace:

1. Vytvořte novou složku a v této složce spusťte `dotnet new console -o AppWithPlugin`. 
2. Aby bylo možné sestavit projekt snadněji, vytvořte soubor řešení sady Visual Studio. Spusťte `dotnet new sln` ve stejné složce. 
3. Spusťte `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` aplikaci a přidejte do řešení projekt aplikace.

Teď můžeme vyplnit kostru naší aplikace. Nahraďte kód v souboru *AppWithPlugin/program. cs* následujícím kódem:

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

## <a name="create-the-plugin-interfaces"></a>Vytvoření rozhraní modulů plug-in

Dalším krokem při sestavování aplikace pomocí modulů plug-in je definování rozhraní, které moduly plug-in potřebují k implementaci. Doporučujeme vytvořit knihovnu tříd, která obsahuje všechny typy, které plánujete použít pro komunikaci mezi aplikací a moduly plug-in. Tato divize vám umožní publikovat rozhraní modulu plug-in jako balíček bez nutnosti dodávat celou aplikaci.

V kořenové složce projektu spusťte `dotnet new classlib -o PluginBase`. Také spusťte příkaz `dotnet sln add PluginBase/PluginBase.csproj` pro přidání projektu do souboru řešení. Odstraňte soubor a `PluginBase` ve složce s názvem `ICommand.cs` pomocí následující definice rozhraní vytvořte nový soubor: `PluginBase/Class1.cs`

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Toto `ICommand` rozhraní je rozhraní, které budou všechny moduly plug-in implementovat.

Teď, `ICommand` když je rozhraní definované, může být projekt aplikace vyplněný o něco dalšího. Přidejte odkaz z `AppWithPlugin` projektu `PluginBase` do projektu pomocí `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` příkazu z kořenové složky.

Nahraďte `// Load commands from plugins` komentář následujícím fragmentem kódu, aby mohl načíst moduly plug-in z daných cest k souborům:

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

Pak nahraďte `// Output the loaded commands` komentář následujícím fragmentem kódu:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Nahraďte `// Execute the command with the name passed as an argument` komentář následujícím fragmentem kódu:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

A nakonec přidejte statické metody do `Program` třídy s názvem `LoadPlugin` a `CreateCommands`, jak je znázorněno zde:

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

## <a name="load-plugins"></a>Načtení modulů plug-in

Aplikace nyní může správně načíst a vytvořit instanci příkazů z načtených sestavení modulu plug-in, ale stále nemůže načíst sestavení modulu plug-in. Ve složce *AppWithPlugin* vytvořte soubor s názvem *PluginLoadContext.cs* s následujícím obsahem:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

Typ je odvozen z <xref:System.Runtime.Loader.AssemblyLoadContext>. `PluginLoadContext` `AssemblyLoadContext` Typ je speciální typ v modulu runtime, který umožňuje vývojářům izolovat načtená sestavení do různých skupin, aby se zajistilo, že verze sestavení nejsou v konfliktu. Kromě toho může vlastní `AssemblyLoadContext` možnost zvolit různé cesty pro načtení sestavení a přepsat výchozí chování. `PluginLoadContext` Používá instanci`AssemblyDependencyResolver` typu představenou v .NET Core 3,0 k překladu názvů sestavení na cesty. `AssemblyDependencyResolver` Objekt je vytvořen s cestou k knihovně tříd .NET. Překládá sestavení a nativní knihovny na jejich relativní cesty založené na souboru *. DEPS. JSON* pro knihovnu tříd, jejíž cesta byla předána `AssemblyDependencyResolver` konstruktoru. Vlastní `AssemblyLoadContext` moduly plug-in umožňují používat vlastní závislosti `AssemblyDependencyResolver` a usnadňuje správné načtení závislostí.

Teď, `AppWithPlugin` když `PluginLoadContext` má projekt typ, aktualizujte `Program.LoadPlugin` metodu s následujícím textem:

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

Při použití jiné `PluginLoadContext` instance pro každý modul plug-in můžou mít moduly plug-in různé nebo dokonce konfliktní závislosti bez problémů.

## <a name="create-a-simple-plugin-with-no-dependencies"></a>Vytvoření jednoduchého modulu plug-in bez závislostí

Zpět v kořenové složce proveďte následující kroky:

1. Spusťte `dotnet new classlib -o HelloPlugin` , chcete-li vytvořit nový projekt knihovny `HelloPlugin`tříd s názvem.
2. Spusťte `dotnet sln add HelloPlugin/HelloPlugin.csproj` , chcete-li přidat projekt `AppWithPlugin` do řešení. 
3. Soubor *HelloPlugin/Class1. cs* nahraďte souborem s názvem *HelloCommand.cs* s následujícím obsahem:

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

Nyní otevřete soubor *HelloPlugin. csproj* . Měl by vypadat nějak takto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

V mezi `<Project>` značkami přidejte následující prvky:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

`<Private>false</Private>` Element je velmi důležitý. Nástroj MSBuild nezkopíruje *PluginBase. dll* do výstupního adresáře pro HelloPlugin. Pokud se ve výstupním adresáři nachází sestavení *PluginBase. dll* , aplikace `PluginLoadContext` nalezne sestavení a načte ho při načtení sestavení *HelloPlugin. dll* . V tomto `HelloPlugin.HelloCommand` okamžiku typ bude `ICommand` implementovat rozhraní z *knihovny PluginBase. dll* ve výstupním `HelloPlugin` `ICommand` adresáři projektu, nikoli rozhraní, které je načteno do výchozího kontextu načtení. Vzhledem k tomu, že modul runtime tyto dva typy považuje za různé typy `AppWithPlugin.Program.CreateCommands` z různých sestavení, metoda tyto příkazy nenajde. Výsledkem je, že `<Private>false</Private>` metadata jsou vyžadována pro odkaz na sestavení obsahující rozhraní modulů plug-in.

Teď, `HelloPlugin` když je projekt hotový, měl by `AppWithPlugin` projekt aktualizovat, aby věděli, `HelloPlugin` kde se modul plug-in našel. Za komentář přidejte `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako prvek pole.`pluginPaths` `// Paths to plugins to load`

## <a name="create-a-plugin-with-library-dependencies"></a>Vytvoření modulu plug-in se závislostmi knihovny

Téměř všechny moduly plug-in jsou složitější než jednoduché "Hello World" a mnohé moduly plug-in mají závislosti na jiných knihovnách. Projekty modulů `OldJson` plug-in `Newtonsoft.Json`avukázce znázorňují dva příklady modulů plug-in s závislostmi balíčku NuGet v. `JsonPlugin` Samotné soubory projektu neobsahují žádné zvláštní informace pro odkazy na projekt a (po přidání cest modulu plug-in do `pluginPaths` pole) jsou moduly plug-in spouštěny dokonale, i když je spustíte ve stejném provedení aplikace AppWithPlugin. Tyto projekty však nekopírují odkazovaná sestavení do jejich výstupního adresáře, takže sestavení musí být přítomna v počítači uživatele, aby mohly fungovat moduly plug-in. Existují dva způsoby, jak tento problém obejít. První možností je použít `dotnet publish` příkaz pro publikování knihovny tříd. Případně, pokud chcete mít možnost použít výstup `dotnet build` pro modul plug-in, můžete `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` přidat vlastnost mezi `<PropertyGroup>` značkami v souboru projektu modulu plug-in. Příklad najdete v projektu moduluplug-in.`XcopyablePlugin`

## <a name="other-plugin-examples-in-the-sample"></a>Další příklady modulů plug-in v ukázce

Úplný zdrojový kód pro tento kurz najdete v [úložišti dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Hotová ukázka obsahuje několik dalších příkladů `AssemblyDependencyResolver` chování. Například `AssemblyDependencyResolver` objekt může také překládat nativní knihovny a také lokalizovaná satelitní sestavení obsažená v balíčcích NuGet. Tyto scénáře `FrenchPlugin` předvádí avúložištiukázek.`UVPlugin`

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a>Postup odkazu na sestavení rozhraní modulu plug-in definované v balíčku NuGet

Řekněme, že existuje aplikace, která má rozhraní modulu plug-in definované v balíčku NuGet s názvem `A.PluginBase`. Jak v projektu modulu plug-in správně odkazovat na balíček? V případě odkazů na projekt, `<Private>false</Private>` použití metadat `ProjectReference` na elementu v souboru projektu zabránilo zkopírování knihovny DLL do výstupu.

Pro správné odkazování `A.PluginBase` na balíček chcete `<PackageReference>` změnit prvek v souboru projektu na následující:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

To brání `A.PluginBase` zkopírování sestavení do výstupního adresáře vašeho modulu plug-in a zajistí, že bude modul plug-in používat `A.PluginBase`verzi.

## <a name="plugin-target-framework-recommendations"></a>Doporučení pro cílové rozhraní modulu plug-in

Vzhledem k tomu, že načítání závislostí modulu plug-in používá soubor *. DEPS. JSON* , existuje gotcha související s cílovým rozhraním modulu plug-in. Moduly plug-in by konkrétně měly cílit na modul runtime, jako je .NET Core 3,0, namísto verze .NET Standard. Soubor *. DEPS. JSON* je vygenerován na základě toho, na které architektuře je projekt cílen, a vzhledem k tomu, že mnoho balíčků kompatibilních s .NET Standard dodává referenční sestavení pro sestavení .NET Standard a implementační sestavení pro konkrétní moduly runtime, *. DEPS. JSON* nemusí správně zobrazovat implementační sestavení nebo může místo očekávané verze .NET Core použít .NET Standard verzi sestavení.
