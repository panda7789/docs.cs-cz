---
title: 'Kurz: Vytvoření nástroje .NET Core'
description: Naučte se vytvořit nástroj .NET Core. Nástroj je Konzolová aplikace, která je nainstalována pomocí .NET Core CLI.
ms.date: 02/12/2020
ms.openlocfilehash: 88cc3be7b149834ace0c5f3ba8ac8c039199908f
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156722"
---
# <a name="tutorial-create-a-net-core-tool-using-the-net-core-cli"></a>Kurz: Vytvoření nástroje .NET Core pomocí .NET Core CLI

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

V tomto kurzu se naučíte, jak vytvořit a zabalit nástroj .NET Core. .NET Core CLI umožňuje vytvořit konzolovou aplikaci jako nástroj, který mohou nainstalovat a spustit další. Nástroje .NET Core jsou balíčky NuGet, které jsou nainstalované z .NET Core CLI. Další informace o nástrojích najdete v tématu [Přehled nástrojů .NET Core](global-tools.md).

Nástroj, který vytvoříte, je Konzolová aplikace, která jako vstup převezme zprávu, a zobrazí zprávu spolu s řádky textu, které vytvoří obrázek robota.

Toto je první v sérii tří kurzů. V tomto kurzu vytvoříte a zabalíte nástroj. V následujících dvou kurzech používáte [Nástroj jako globální nástroj](global-tools-how-to-use.md) a [nástroj použijete jako místní nástroj](local-tools-how-to-use.md).

## <a name="prerequisites"></a>Předpoklady

- [.NET Core SDK 3,1](https://dotnet.microsoft.com/download) nebo novější verze.

  Tento kurz a následující [kurz pro globální nástroje](global-tools-how-to-use.md) se vztahují na .NET Core SDK 2,1 a novější verze, protože v této verzi jsou dostupné globální nástroje. Ale v tomto kurzu se předpokládá, že máte nainstalovaný 3,1 nebo novější, abyste měli možnost pokračovat na [místní kurzy k nástrojům](local-tools-how-to-use.md). K dispozici jsou místní nástroje od .NET Core SDK 3,0. Postupy pro vytvoření nástroje jsou stejné, ať už používáte jako globální nástroj, nebo jako místní nástroj.
  
- Textový editor nebo editor kódu podle vašeho výběru.

## <a name="create-a-project"></a>Vytvoření projektu

1. Otevřete příkazový řádek a vytvořte složku s názvem *úložiště*.

1. Přejděte do složky *úložiště* a zadejte následující příkaz:

   ```dotnetcli
   dotnet new console -n microsoft.botsay
   ```

   Příkaz vytvoří novou složku s názvem *Microsoft. botsay* ve složce *úložiště* .

1. Přejděte do složky *Microsoft. botsay* .

   ```console
   cd microsoft.botsay
   ```

## <a name="add-the-code"></a>Přidání kódu

1. Otevřete `Program.cs` soubor pomocí editoru kódu.

1. Do horní části souboru přidejte následující direktivu `using`:

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

   Pokud nejsou předány žádné argumenty, zobrazí se krátká zpráva help. V opačném případě jsou všechny argumenty zřetězeny do jednoho řetězce a vytištěny voláním metody `ShowBot`, kterou vytvoříte v následujícím kroku.

1. Přidejte novou metodu s názvem `ShowBot`, která přijímá řetězcový parametr. Metoda vytiskne zprávu a obrázek robota s použitím řádků textu.

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

Spusťte projekt a podívejte se na výstup. Zkuste tyto variace na příkazovém řádku pro zobrazení různých výsledků:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- Hello from the bot
```

Všechny argumenty po `--` oddělovači jsou předány do aplikace.

## <a name="package-the-tool"></a>Zabalení nástroje

Předtím, než budete moci zabalit a distribuovat aplikaci jako nástroj, je nutné upravit soubor projektu.

1. Otevřete soubor *Microsoft. botsay. csproj* a přidejte tři nové uzly XML na konec `<PropertyGroup>` uzlu:

   ```xml
   <PackAsTool>true</PackAsTool>
   <ToolCommandName>botsay</ToolCommandName>
   <PackageOutputPath>./nupkg</PackageOutputPath>
   ```

   `<ToolCommandName>` je volitelný prvek, který určuje příkaz, který nástroj vyvolá po jeho instalaci. Pokud tento prvek není k dispozici, název příkazu pro nástroj je název souboru projektu bez přípony *. csproj* .

   `<PackageOutputPath>` je volitelný prvek, který určuje, kde bude vytvořen balíček NuGet. Balíček NuGet je to, co .NET Core CLI používá k instalaci nástroje.

   Soubor projektu teď vypadá jako v následujícím příkladu:

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

1. Vytvořte balíček NuGet spuštěním příkazu [dotnet Pack](dotnet-pack.md) :

   ```dotnetcli
   dotnet pack
   ```

   Soubor *Microsoft. botsay. 1.0.0. nupkg* se vytvoří ve složce určené hodnotou `<PackageOutputPath>` ze souboru *Microsoft. botsay. csproj* , který je v tomto příkladu složkou *./nupkg* .
  
   Pokud chcete veřejně vydávat nástroj, můžete ho nahrát na `https://www.nuget.org`. Jakmile je nástroj k dispozici v NuGet, mohou vývojáři nainstalovat nástroj pomocí příkazu pro [instalaci nástroje dotnet](dotnet-tool-install.md) . V tomto kurzu nainstalujete balíček přímo z místní složky *nupkg* , takže není potřeba balíček nahrát do NuGet.

## <a name="troubleshoot"></a>Řešení potíží

Pokud se vám zobrazí chybová zpráva s postupem v tomto kurzu, přečtěte si téma [řešení potíží s používáním nástrojů .NET Core](troubleshoot-usage-issues.md).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste vytvořili konzolovou aplikaci a zabalíte ji jako nástroj. Pokud se chcete dozvědět, jak nástroj používat jako globální nástroj, přejděte k dalšímu kurzu.

> [!div class="nextstepaction"]
> [Instalace a použití globálního nástroje](global-tools-how-to-use.md)

Pokud chcete, můžete přeskočit kurz globálních nástrojů a přejít přímo do kurzu místních nástrojů.

> [!div class="nextstepaction"]
> [Instalace a použití místního nástroje](local-tools-how-to-use.md)
