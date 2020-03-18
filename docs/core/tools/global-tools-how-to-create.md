---
title: 'Kurz: Vytvoření nástroje .NET Core'
description: Přečtěte si, jak vytvořit nástroj .NET Core. Nástroj je konzolová aplikace, která je nainstalována pomocí rozhraní CLI jádra .NET.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156722"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Kurz: Vytvoření nástroje .NET Core pomocí rozhraní CLI jádra .NET

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

Tento kurz vás naučí, jak vytvořit a zabalit nástroj .NET Core. Rozhraní .NET Core CLI umožňuje vytvořit konzolovou aplikaci jako nástroj, který mohou ostatní instalovat a spouštět. Nástroje .NET Core jsou balíčky NuGet, které jsou nainstalovány z rozhraní CLI jádra .NET. Další informace o nástrojích naleznete v [tématu Přehled nástrojů .NET Core](global-tools.md).

Nástroj, který vytvoříte, je konzolová aplikace, která přebírá zprávu jako vstup a zobrazuje zprávu spolu s řádky textu, které vytvářejí obraz robota.

Toto je první ze série tří výukových programů. V tomto kurzu vytvoříte a zabalíte nástroj. V dalších dvou kurzech [použijete nástroj jako globální nástroj](global-tools-how-to-use.md) a nástroj [použijete jako místní nástroj](local-tools-how-to-use.md).

## <a name="prerequisites"></a>Požadavky

- [Sada .NET Core SDK 3.1](https://dotnet.microsoft.com/download) nebo novější verze.

  Tento kurz a následující [kurz pro globální nástroje](global-tools-how-to-use.md) platí pro .NET Core SDK 2.1 a novější verze, protože globální nástroje jsou k dispozici od této verze. Ale tento výukový program předpokládá, že jste nainstalovali 3.1 nebo novější, takže máte možnost pokračovat na [místní nástroje tutorial](local-tools-how-to-use.md). Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0. Postupy pro vytvoření nástroje jsou stejné, ať už jej používáte jako globální nástroj nebo jako místní nástroj.
  
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete příkazový řádek a vytvořte složku s názvem *repozitář*.

1. Přejděte do složky *úložiště* a zadejte následující příkaz:

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   Příkaz vytvoří novou složku s názvem *microsoft.botsay* pod složkou *úložiště.*

1. Přejděte do složky *microsoft.botsay.*

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Přidání kódu

1. Otevřete `Program.cs` soubor pomocí editoru kódu.

1. Do horní `using` části souboru přidejte následující direktivu:

   ```csharp
   using System.Reflection;
   ```

1. Nahraďte metodu `Main` následujícím kódem pro zpracování argumentů příkazového řádku pro aplikaci.

   ```csharp
   static void Main(string[] args)
   {
       if (args.Length == 0)
       {
           var versionString = Assembly.GetEntryAssembly()
                                   .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                   .InformationalVersion
                                   .ToString();

           Console.WriteLine($"botsay v{versionString}");
           Console.WriteLine("-------------");
           Console.WriteLine("\nUsage:");
           Console.WriteLine("  botsay <message>");
           return;
       }

       ShowBot(string.Join(' ', args));
   }
   ```

   Pokud nejsou předány žádné argumenty, zobrazí se krátká zpráva nápovědy. V opačném případě jsou všechny argumenty zřetězeny do jednoho `ShowBot` řetězce a vytištěny voláním metody, kterou vytvoříte v dalším kroku.

1. Přidejte novou `ShowBot` metodu s názvem, která přebírá parametr řetězce. Metoda vytiskne zprávu a obrázek robota pomocí řádků textu.

   ```csharp
   static void ShowBot(string message)
   {
       string bot = $"\n        {message}";
       bot += @"
       __________________
                         \
                          \
                             ....
                             ....'
                              ....
                           ..........
                       .............'..'..
                    ................'..'.....
                  .......'..........'..'..'....
                 ........'..........'..'..'.....
                .'....'..'..........'..'.......'.
                .'..................'...   ......
                .  ......'.........         .....
                .    _            __        ......
               ..    #            ##        ......
              ....       .                 .......
              ......  .......          ............
               ................  ......................
               ........................'................
              ......................'..'......    .......
           .........................'..'.....       .......
        ........    ..'.............'..'....      ..........
      ..'..'...      ...............'.......      ..........
     ...'......     ...... ..........  ......         .......
    ...........   .......              ........        ......
   .......        '...'.'.              '.'.'.'         ....
   .......       .....'..               ..'.....
      ..       ..........               ..'........
             ............               ..............
            .............               '..............
           ...........'..              .'.'............
          ...............              .'.'.............
         .............'..               ..'..'...........
         ...............                 .'..............
          .........                        ..............
           .....
   ";
       Console.WriteLine(bot);
   }
   ```

1. Uložte provedené změny.

## <a name="test-the-application"></a>Testování aplikace

Spusťte projekt a podívejte se na výstup. Chcete-li zobrazit různé výsledky, vyzkoušejte tyto varianty na příkazovém řádku:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Všechny argumenty `--` po oddělovač jsou předány do aplikace.

## <a name="package-the-tool"></a>Balení nástroje

Před balením a distribucí aplikace jako nástroje je třeba upravit soubor projektu.

1. Otevřete soubor *microsoft.botsay.csproj* a přidejte tři nové `<PropertyGroup>` uzly XML na konec uzlu:

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>`je volitelný prvek, který určuje příkaz, který bude nástroj vyvolat po jeho instalaci. Pokud tento prvek není k dispozici, název příkazu pro nástroj je název souboru projektu bez přípony *.csproj.*

   `<PackageOutputPath>`je volitelný prvek, který určuje, kde bude vytvořen balíček NuGet. Balíček NuGet je to, co rozhraní .NET Core CLI používá k instalaci nástroje.

   Soubor projektu nyní vypadá jako následující příklad:

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">
  
     <PropertyGroup>

       <OutputType>Exe</OutputType>
       <TargetFramework>netcoreapp3.1</TargetFramework>
  
       <PackAsTool>true</PackAsTool>
       <ToolCommandName>botsay</ToolCommandName>
       <PackageOutputPath>./nupkg</PackageOutputPath>
  
     </PropertyGroup>

   </Project>
   ```

1. Vytvořte balíček NuGet spuštěním příkazu [dotnet pack:](dotnet-pack.md)

   ```dotnetcli
   dotnet pack
   ```

   Soubor *microsoft.botsay.1.0.0.nupkg* je vytvořen ve složce identifikované `<PackageOutputPath>` hodnotou ze souboru *microsoft.botsay.csproj,* což je v tomto příkladu složka *./nupkg.*
  
   Chcete-li nástroj vydat veřejně, můžete jej `https://www.nuget.org`odeslat do aplikace . Jakmile je nástroj k dispozici na NuGet, vývojáři můžete nainstalovat nástroj pomocí příkazu [dotnet nástroj nainstalovat.](dotnet-tool-install.md) Pro tento kurz nainstalujete balíček přímo z místní složky *nupkg,* takže není třeba nahrát balíček do NuGet.

## <a name="troubleshoot"></a>Řešení potíží

Pokud se při sledování kurzu zobrazí chybová zpráva, [přečtěte si článek Poradce při potížích s používáním nástroje .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili konzolovou aplikaci a zabalili ji jako nástroj. Chcete-li se dozvědět, jak používat nástroj jako globální nástroj, přejdete k dalšímu kurzu.

> [!div class="nextstepaction"]
> [Instalace a použití globálního nástroje](global-tools-how-to-use.md)

Pokud dáváte přednost, můžete přeskočit globální nástroje tutorial a přejít přímo do kurzu místnínástroje.

> [!div class="nextstepaction"]
> [Instalace a použití místního nástroje](local-tools-how-to-use.md)
