---
title: Vytvoření aplikace .NET Core pomocí modulů plug-in
description: Naučte se, jak vytvořit aplikaci .NET Core, která podporuje moduly plug-in.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 10/16/2019
ms.openlocfilehash: 16fc9d3c721ddd0618c980c7dc406b7ad7864ff5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739697"
---
# <a name="create-a-net-core-application-with-plugins"></a>Vytvoření aplikace .NET Core pomocí modulů plug-in

V tomto kurzu se dozvíte, jak vytvořit vlastní <xref:System.Runtime.Loader.AssemblyLoadContext> pro načtení modulů plug-in. K vyřešení závislostí modulu plug-in se používá <xref:System.Runtime.Loader.AssemblyDependencyResolver>. Kurz správně izoluje závislosti modulu plug-in z hostující aplikace. Naučíte se:

- Vytvořte strukturu projektu pro podporu modulů plug-in.
- Vytvořením vlastního <xref:System.Runtime.Loader.AssemblyLoadContext> načtete jednotlivé modul plug-in.
- Pokud chcete, aby moduly plug-in měly závislosti, použijte <xref:System.Runtime.Loader.AssemblyDependencyResolver?displayProperty=fullName> typ.
- Vytváření modulů plug-in, které lze snadno nasadit pouhým zkopírováním artefaktů sestavení.

## <a name="prerequisites"></a>Požadavky

- Nainstalujte [sadu .NET Core 3,0 SDK](https://dotnet.microsoft.com/download) nebo novější verzi.

## <a name="create-the-application"></a>Vytvoření aplikace

Prvním krokem je vytvoření aplikace:

1. Vytvořte novou složku a v této složce spusťte následující příkaz:

    ```dotnetcli
    dotnet new console -o AppWithPlugin
    ```

2. Aby bylo možné projekt sestavit snadněji, vytvořte soubor řešení sady Visual Studio ve stejné složce. Spusťte následující příkaz:

    ```dotnetcli
    dotnet new sln
    ```

3. Spusťte následující příkaz pro přidání projektu aplikace do řešení:

    ```dotnetcli
    dotnet sln add AppWithPlugin/AppWithPlugin.csproj
    ```

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

V kořenové složce projektu spusťte `dotnet new classlib -o PluginBase`. K přidání projektu do souboru řešení také spusťte `dotnet sln add PluginBase/PluginBase.csproj`. Odstraňte soubor `PluginBase/Class1.cs` a ve složce `PluginBase` s názvem `ICommand.cs` vytvořte nový soubor s následující definicí rozhraní:

[!code-csharp[the-plugin-interface](~/samples/core/extensions/AppWithPlugin/PluginBase/ICommand.cs)]

Toto rozhraní `ICommand` je rozhraní, které budou všechny moduly plug-in implementovat.

Teď, když je definováno rozhraní `ICommand`, může být projekt aplikace vyplněný o něco dalšího. Přidejte odkaz z projektu `AppWithPlugin` do projektu `PluginBase` s příkazem `dotnet add AppWithPlugin\AppWithPlugin.csproj reference PluginBase\PluginBase.csproj` z kořenové složky.

Nahraďte komentář `// Load commands from plugins` následujícím fragmentem kódu, aby mohl načíst moduly plug-in z daných cest k souborům:

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

Potom nahraďte komentář `// Output the loaded commands` následujícím fragmentem kódu:

```csharp
foreach (ICommand command in commands)
{
    Console.WriteLine($"{command.Name}\t - {command.Description}");
}
```

Nahraďte komentář `// Execute the command with the name passed as an argument` následujícím fragmentem kódu:

```csharp
ICommand command = commands.FirstOrDefault(c => c.Name == commandName);
if (command == null)
{
    Console.WriteLine("No such command is known.");
    return;
}

command.Execute();
```

A nakonec přidejte statické metody do třídy `Program` s názvem `LoadPlugin` a `CreateCommands`, jak je znázorněno zde:

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

Nyní může aplikace správně načíst a vytvořit instanci příkazů z načtených sestavení modulu plug-in, ale nelze načíst sestavení modulu plug-in. Ve složce *AppWithPlugin* vytvořte soubor s názvem *PluginLoadContext.cs* s následujícím obsahem:

[!code-csharp[loading-plugins](~/samples/core/extensions/AppWithPlugin/AppWithPlugin/PluginLoadContext.cs)]

Typ `PluginLoadContext` je odvozen z <xref:System.Runtime.Loader.AssemblyLoadContext>. `AssemblyLoadContext` typ je speciální typ v modulu runtime, který umožňuje vývojářům izolovat načtená sestavení do různých skupin, aby se zajistilo, že verze sestavení nejsou v konfliktu. Navíc vlastní `AssemblyLoadContext` může zvolit různé cesty pro načtení sestavení a přepsat výchozí chování. `PluginLoadContext` používá instanci `AssemblyDependencyResolver` typu představenou v .NET Core 3,0 k překladu názvů sestavení na cesty. Objekt `AssemblyDependencyResolver` je vytvořen s cestou k knihovně tříd .NET. Přeloží sestavení a nativní knihovny na jejich relativní cesty založené na souboru *. DEPS. JSON* pro knihovnu tříd, jehož cesta byla předána konstruktoru `AssemblyDependencyResolver`. Vlastní `AssemblyLoadContext` umožňuje modulům plug-in používat vlastní závislosti a `AssemblyDependencyResolver` usnadňuje správné načtení závislostí.

Teď, když má projekt `AppWithPlugin` typ `PluginLoadContext`, aktualizujte metodu `Program.LoadPlugin` s následujícím textem:

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

Při použití jiné instance `PluginLoadContext` pro každý modul plug-in můžou mít moduly plug-in různé nebo dokonce konfliktní závislosti bez problémů.

## <a name="simple-plugin-with-no-dependencies"></a>Jednoduchý modul plug-in bez závislostí

Zpět v kořenové složce proveďte následující kroky:

1. Spusťte následující příkaz, který vytvoří nový projekt knihovny tříd s názvem `HelloPlugin`:
    
    ```dotnetcli
    dotnet new classlib -o HelloPlugin
    ```

2. Spuštěním následujícího příkazu přidejte projekt do řešení `AppWithPlugin`:

    ```dotnetcli
    dotnet sln add HelloPlugin/HelloPlugin.csproj
    ```

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

Do mezi značkami `<Project>` přidejte následující prvky:

```xml
<ItemGroup>
<ProjectReference Include="..\PluginBase\PluginBase.csproj">
    <Private>false</Private>
</ProjectReference>
</ItemGroup>
```

Element `<Private>false</Private>` je důležitý. Nástroj MSBuild nezkopíruje *PluginBase. dll* do výstupního adresáře pro HelloPlugin. Pokud se ve výstupním adresáři nachází sestavení *PluginBase. dll* , `PluginLoadContext` nalezne sestavení a načte ho při načtení sestavení *HelloPlugin. dll* . V tomto okamžiku typ `HelloPlugin.HelloCommand` implementuje rozhraní `ICommand` z *knihovny PluginBase. dll* ve výstupním adresáři projektu `HelloPlugin`, nikoli rozhraní `ICommand`, které je načteno do výchozího kontextu načtení. Vzhledem k tomu, že modul runtime tyto dva typy považuje za různé typy z různých sestavení, metoda `AppWithPlugin.Program.CreateCommands` nenajde příkazy. V důsledku toho je potřeba metadata `<Private>false</Private>` pro odkaz na sestavení obsahující rozhraní modulů plug-in.

Teď, když je projekt `HelloPlugin` dokončený, doporučujeme aktualizovat projekt `AppWithPlugin`, aby věděli, kde je možné najít modul plug-in `HelloPlugin`. Po komentáři `// Paths to plugins to load` přidejte `@"HelloPlugin\bin\Debug\netcoreapp3.0\HelloPlugin.dll"` jako prvek pole `pluginPaths`.

## <a name="plugin-with-library-dependencies"></a>Modul plug-in se závislostmi knihovny

Téměř všechny moduly plug-in jsou složitější než jednoduché "Hello World" a mnohé moduly plug-in mají závislosti na jiných knihovnách. Projekty modulu plug-in `JsonPlugin` a `OldJson` v ukázce znázorňují dva příklady modulů plug-in s závislostmi balíčku NuGet v `Newtonsoft.Json`. Samotné soubory projektu neobsahují žádné zvláštní informace pro odkazy na projekt a (po přidání cest modulu plug-in do pole `pluginPaths`) jsou moduly plug-in spouštěny dokonale, a to i v případě, že jsou spuštěny ve stejném provedení aplikace AppWithPlugin. Tyto projekty však nekopírují odkazovaná sestavení do výstupního adresáře, takže sestavení musí být přítomna v počítači uživatele, aby mohly fungovat moduly plug-in. Existují dva způsoby, jak tento problém obejít. První možností je použít příkaz `dotnet publish` pro publikování knihovny tříd. Případně, pokud chcete mít možnost použít výstup `dotnet build` pro modul plug-in, můžete přidat vlastnost `<CopyLocalLockFileAssemblies>true</CopyLocalLockFileAssemblies>` mezi značkami `<PropertyGroup>` v souboru projektu modulu plug-in. Příklad naleznete v projektu modulu plug-in `XcopyablePlugin`.

## <a name="other-examples-in-the-sample"></a>Další příklady v ukázce

Úplný zdrojový kód pro tento kurz najdete v [úložišti dotnet/Samples](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin). Hotová ukázka obsahuje několik dalších příkladů chování `AssemblyDependencyResolver`. Například objekt `AssemblyDependencyResolver` může také překládat nativní knihovny a také lokalizovaná satelitní sestavení obsažená v balíčcích NuGet. Tyto scénáře předvádí `UVPlugin` a `FrenchPlugin` v úložišti ukázek.

## <a name="reference-a-plugin-from-a-nuget-package"></a>Odkazování na modul plug-in z balíčku NuGet

Řekněme, že existuje aplikace, která má rozhraní modulu plug-in definované v balíčku NuGet s názvem `A.PluginBase`. Jak v projektu modulu plug-in správně odkazovat na balíček? V případě odkazů na projekt, použití metadat `<Private>false</Private>` u prvku `ProjectReference` v souboru projektu zabránilo zkopírování knihovny DLL do výstupu.

Pro správné odkazování na balíček `A.PluginBase` chcete změnit prvek `<PackageReference>` v souboru projektu na následující:

```xml
<PackageReference Include="A.PluginBase" Version="1.0.0">
    <ExcludeAssets>runtime</ExcludeAssets>
</PackageReference>
```

Tím zabráníte tomu, aby se sestavení `A.PluginBase` zkopírovala do výstupního modulu plug-in a zajistilo, že bude modul plug-in používat verzi `A.PluginBase`.

## <a name="plugin-target-framework-recommendations"></a>Doporučení pro cílové rozhraní modulu plug-in

Vzhledem k tomu, že načítání závislostí modulu plug-in používá soubor *. DEPS. JSON* , existuje gotcha související s cílovým rozhraním modulu plug-in. Moduly plug-in by konkrétně měly cílit na modul runtime, jako je .NET Core 3,0, namísto verze .NET Standard. Soubor *. DEPS. JSON* je vygenerován na základě toho, na které architektuře je projekt cílen, a vzhledem k tomu, že mnoho balíčků kompatibilních s .NET Standard dodává referenční sestavení pro sestavení .NET Standard a implementační sestavení pro konkrétní moduly runtime, *. DEPS. JSON* nemusí správně zobrazovat implementační sestavení nebo může místo očekávané verze .NET Core použít .NET Standard verzi sestavení.

## <a name="plugin-framework-references"></a>Odkazy na rozhraní modulů plug-in

Moduly plug-in v současné době nemůžou do procesu zavádět nová rozhraní. Například nelze načíst modul plug-in, který používá `Microsoft.AspNetCore.App` Framework do aplikace, která používá pouze kořenové rozhraní `Microsoft.NETCore.App`. Hostitelská aplikace musí deklarovat odkazy na všechny architektury, které vyžadují moduly plug-in.
