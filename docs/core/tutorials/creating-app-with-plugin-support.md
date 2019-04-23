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
# <a name="create-a-net-core-application-with-plugins"></a>Vytvoření aplikace .NET Core s moduly plug-in

V tomto kurzu se dozvíte, jak do:

- Strukturování projektu pro podporu modulů plug-in.
- Vytvoření vlastní <xref:System.Runtime.Loader.AssemblyLoadContext> načtení modulu plug-in.
- Použití `System.Runtime.Loader.AssemblyDependencyResolver` typ povolit moduly plug-in k závislostmi.
- Autor moduly plug-in, který je možné snadno nasadit pomocí pouhé kopírování artefaktů sestavení.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte [sady SDK .NET Core 3.0 ve verzi Preview 2](https://www.microsoft.com/net/core) nebo novější verze.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření aplikace:

1. Vytvořte novou složku a v této složce spusťte `dotnet new console -o AppWithPlugin`. 
2. Chcete-li sestavení projektu jednodušší, vytvořte soubor řešení sady Visual Studio. Spustit `dotnet new sln` ve stejné složce. 
3. Spustit `dotnet sln add AppWithPlugin/AppWithPlugin.csproj` přidat do řešení projekt aplikace.

Nyní jsme můžete vyplnit kostra naši aplikaci. Nahraďte kód v *AppWithPlugin/Program.cs* souboru následujícím kódem:

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

## <a name="create-the-plugin-interfaces"></a>Vytvoření modulu plug-in rozhraní

Dalším krokem při sestavování aplikace s moduly plug-in definuje rozhraní, které moduly plug-in je nutné implementovat. Doporučujeme, abyste vytvořili knihovnu tříd, který obsahuje všechny typy, které budete používat pro komunikaci mezi aplikací a moduly plug-in. Můžeme vám umožňuje publikovat rozhraní modulu plug-in jako balíček není přitom nutné dodávat celou aplikaci.

V kořenové složce projektu, spusťte `dotnet new classlib -o PluginBase`. Také spustit `dotnet sln add PluginBase/PluginBase.csproj` přidání projektu do souboru řešení. Odstranit `PluginBase/Class1.cs` souboru a vytvořte nový soubor v `PluginBase` složku s názvem `ICommand.cs` s následující definice rozhraní:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

To `ICommand` rozhraní je rozhraní, že všechny moduly plug-in implementovat.

Teď, když `ICommand` rozhraní je definováno, může být vyplněno projekt aplikace o něco víc. Přidat odkaz z `AppWithPlugin` projektu `PluginBase` projekt se `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` příkazů z kořenové složky.

Nahradit `// Load commands from plugins` komentář pomocí následujícího fragmentu kódu, který umožňuje načíst pluginy ze zadané cesty k souborům:

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

Potom nahraďte `// Output the loaded commands` komentáře následujícím fragmentem kódu:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Nahradit `// Execute the command with the name passed as an argument` komentáře následujícím fragmentem kódu:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

A nakonec statické metody pro přidání `Program` třídu s názvem `LoadPlugin` a `CreateCommands`, jak je znázorněno zde:

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

## <a name="load-plugins"></a>Načítání modulů plug-in

Nyní můžete načíst a vytvořit instanci příkazy ze sestavení načíst modul plug-in aplikace správně, ale je stále nelze načíst sestavení modulu plug-in. Vytvořte soubor s názvem *PluginLoadContext.cs* v *AppWithPlugin* složka s následujícím obsahem:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

`PluginLoadContext` Typ je odvozen od <xref:System.Runtime.Loader.AssemblyLoadContext>. `AssemblyLoadContext` Typ je speciální typ v modulu runtime, která umožňuje vývojářům izolovat načtená sestavení do různých skupin, ujistěte se, že verze sestavení nejsou v konfliktu. Kromě toho vlastní `AssemblyLoadContext` můžete změnit výchozí chování a načítat sestavení z různých cest. `PluginLoadContext` Používá instanci `AssemblyDependencyResolver` typu zavedeného do .NET Core 3.0 k překladu názvů sestavení na cesty. `AssemblyDependencyResolver` Objekt je vytvořen s cestou k knihovny tříd .NET. Přeloží sestavení a nativních knihoven na jejich relativní cesty na základě *deps.json* soubor pro knihovnu tříd, jejichž cesty byl předán `AssemblyDependencyResolver` konstruktoru. Vlastní `AssemblyLoadContext` umožňuje mají svoje vlastní závislosti modulů plug-in a `AssemblyDependencyResolver` usnadňuje správně načíst závislosti.

Teď, když `AppWithPlugin` projekt má `PluginLoadContext` zadejte, aktualizujte `Program.LoadPlugin` metoda spolu s následujícím textem:

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

Pomocí jiného `PluginLoadContext` instance pro každý modul plug-in, moduly plug-in může mít různé nebo dokonce konfliktní závislosti bez problému.

## <a name="create-a-simple-plugin-with-no-dependencies"></a>Vytvořte jednoduchý modul plug-in bez závislostí

Zpět v kořenové složce postupujte takto:

1. Spustit `dotnet new classlib -o HelloPlugin` vytvoříte nový projekt knihovny tříd s názvem `HelloPlugin`.
2. Spustit `dotnet sln add HelloPlugin/HelloPlugin.csproj` přidat projekt tak, aby `AppWithPlugin` řešení. 
3. Nahradit *HelloPlugin/Class1.cs* soubor se soubor s názvem *HelloCommand.cs* s následujícím obsahem:

[!code-csharp[the-hello-plugin](~/samples/core/extensions/AppWithPlugin/HelloPlugin/HelloCommand.cs)]

Nyní, otevřete *HelloPlugin.csproj* souboru. By měl vypadat nějak takto:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>

```

Mezi `<Project>` značky, přidejte následující prvky:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

`<Private>false</Private>` Element je velmi důležité. To říká MSBuild k nekopíruje *PluginBase.dll* do výstupního adresáře pro HelloPlugin. Pokud *PluginBase.dll* se nachází v adresáři výstupu sestavení `PluginLoadContext` se najít sestavení existuje a načtěte ho po načtení *HelloPlugin.dll* sestavení. V tomto okamžiku `HelloPlugin.HelloCommand` typ implementuje `ICommand` rozhraní z *PluginBase.dll* v adresáři výstupu `HelloPlugin` projekt není `ICommand` rozhraní, který je načten do Výchozí kontext načtení. Vzhledem k tomu, že modul runtime považuje tyto dva typy různých typů z různých sestavení `AppWithPlugin.Program.CreateCommands` metoda nenajde příkazy. V důsledku toho `<Private>false</Private>` metadat pro se vyžaduje odkaz na sestavení obsahující rozhraní modulu plug-in.

Teď, když `HelloPlugin` dokončení projektu, by měl aktualizujeme `AppWithPlugin` projekt tak, aby věděli, kde `HelloPlugin` najdete modulu plug-in. Po `// Paths to plugins to load` komentář, přidání `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako prvek sady `pluginPaths` pole.

## <a name="create-a-plugin-with-library-dependencies"></a>Vytvořit modul plug-in s závislé položky knihoven

Téměř všechny moduly plug-in jsou složitější než jednoduché "Hello World" a mnoha modulů plug-in mají závislosti na dalších knihovnách. `JsonPlugin` a `OldJson` modulu plug-in projekty v ukázce zobrazit dva příklady moduly plug-in s závislosti balíčku NuGet na `Newtonsoft.Json`. Soubory projektu samy nemají žádné speciální informace pro projektové odkazy a (po přidání modulu plug-in cesty k `pluginPaths` pole) na moduly plug-in spuštění, i v případě, že spuštění v rámci stejné AppWithPlugin aplikace. Ale tyto projekty nekopírovat odkazovaná sestavení do výstupního adresáře, aby sestavení musí být na počítači uživatele pro moduly plug-in pro práci. Existují dva způsoby, jak tento problém vyřešit. První možností je použít `dotnet publish` příkaz pro publikování knihovny tříd. Případně pokud budete chtít použít výstup `dotnet build` pro váš modul plug-in, můžete přidat `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` vlastnost mezi `<PropertyGroup>` značky v souboru modulu plug-in projektu. Zobrazit `XcopyablePlugin` projekt modulu plug-in pro příklad.

## <a name="other-plugin-examples-in-the-sample"></a>Další příklady modul plug-in v ukázce

Úplný zdrojový kód pro účely tohoto kurzu můžete najít v [úložišti dotnet/samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Je hotová ukázka obsahuje několik příkladů scénářů `AssemblyDependencyResolver` chování. Například `AssemblyDependencyResolver` objektu můžete také vyřešit nativních knihoven, jakož i lokalizovaná satelitní sestavení v balíčcích NuGet. `UVPlugin` a `FrenchPlugin` v úložišti ukázek ukazují tyto scénáře.

## <a name="how-to-reference-a-plugin-interface-assembly-defined-in-a-nuget-package"></a>Způsob vytvoření odkazu na sestavení rozhraní modulu plug-in definovaných v balíčku NuGet

Řekněme, že je aplikace A, který má modul plug-in rozhraní definované v balíček NuGet s názvem `A.PluginBase`. Jak můžete odkázat na balíček správně v projektu pro modul plug-in? Pro projektové odkazy pomocí `<Private>false</Private>` metadat na `ProjectReference` element v souboru projektu zabránily knihovny dll byly zkopírovány na výstupu.

Chcete-li správně odkazovat `A.PluginBase` balíčku, kterou chcete změnit `<PackageReference>` element v souboru projektu následující:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Díky tomu `A.PluginBase` sestavení jsou zkopírovány do výstupního adresáře vašeho modulu plug-in a zajistí, že váš modul plug-in použije příslušné verzi `A.PluginBase`.

## <a name="plugin-target-framework-recommendations"></a>Modul plug-in cílové rozhraní framework doporučení

Vzhledem k tomu používá načítání závislost modulu plug-in *deps.json* souboru, je gotcha související se modul plug-in cílovou architekturu. Konkrétně váš moduly plug-in zaměřit modulu runtime, jako je .NET Core 3.0 místo verze .NET Standard. `deps.json` Soubor se generuje založená na platformě pro které projekt cílí, a protože mnoho balíčků kompatibilním s technologií .NET Standard dodávat referenční sestavení pro sestavení proti sestavení .NET Standard a implementaci pro konkrétní moduly runtime, `deps.json` možná není správně sestavení implementace viz nebo ji může vzít .NET Standard verzi sestavení namísto očekáváte, že verze .NET Core.
