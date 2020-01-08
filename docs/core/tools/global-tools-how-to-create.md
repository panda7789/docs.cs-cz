---
title: Postup vytvoření globálního nástroje .NET Core
description: Popisuje, jak vytvořit globální nástroj. Globální nástroj je Konzolová aplikace, která je nainstalována prostřednictvím .NET Core CLI.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 1daecf7234f02a5fe0dcf25cf7edbb0af327b8c1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343525"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Vytvoření globálního nástroje .NET Core pomocí .NET Core CLI

V tomto článku se naučíte, jak vytvořit a zabalit globální nástroj .NET Core. .NET Core CLI umožňuje vytvořit konzolovou aplikaci jako globální nástroj, který mohou uživatelé snadno nainstalovat a spustit. Globální nástroje .NET Core jsou balíčky NuGet, které jsou nainstalované z .NET Core CLI. Další informace o globálních nástrojích najdete v tématu [Přehled globálních nástrojů .NET Core](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Vytvoření projektu

Tento článek používá .NET Core CLI k vytvoření a správě projektu.

Náš ukázkový nástroj bude Konzolová aplikace, která generuje robota ASCII a vytiskne zprávu. Nejprve vytvořte novou konzolovou aplikaci .NET Core.

```dotnetcli
dotnet new console -o botsay
```

Přejděte do adresáře `botsay` vytvořeného předchozím příkazem.

## <a name="add-the-code"></a>Přidání kódu

Otevřete `Program.cs` soubor pomocí oblíbeného textového editoru, jako je například `vim` nebo [Visual Studio Code](https://code.visualstudio.com/).

Do horní části souboru přidejte následující direktivu `using`, což pomáhá zkrátit kód pro zobrazení informací o verzi aplikace.

```csharp
using System.Reflection;
```

Potom přejděte dolů k metodě `Main`. Nahraďte metodu následujícím kódem pro zpracování argumentů příkazového řádku pro vaši aplikaci. Pokud nebyly předány žádné argumenty, zobrazí se krátká zpráva help. V opačném případě jsou všechny tyto argumenty transformovány do řetězce a vytištěny s robotem.

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

### <a name="create-the-bot"></a>Vytvoření robota

Dále přidejte novou metodu s názvem `ShowBot`, která převezme řetězcový parametr. Tato metoda vytiskne zprávy a robota ASCII. Z ukázky [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) byl vytvořen kód bot standardu ASCII.

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

### <a name="test-the-tool"></a>Otestování nástroje

Spusťte projekt a podívejte se na výstup. Zkuste tyto variace na příkazovém řádku pro zobrazení různých výsledků:

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Všechny argumenty po `--` oddělovači jsou předány do aplikace.

## <a name="set-up-the-global-tool"></a>Nastavení globálního nástroje

Předtím, než budete moci zabalit a distribuovat aplikaci jako globální nástroj, je nutné upravit soubor projektu. Otevřete soubor `botsay.csproj` a přidejte do uzlu `<Project><PropertyGroup>` tři nové uzly XML:

- `<PackAsTool>`\
POŽADOVANOU Označuje, že aplikace bude zabalena pro instalaci jako globální nástroj.

- `<ToolCommandName>`\
VOLITELNÉ Alternativní název nástroje, jinak bude název příkazu pro nástroj pojmenován za souborem projektu. V balíčku můžete mít několik nástrojů, přičemž volba jedinečného a popisného názvu pomůže odlišit od ostatních nástrojů ve stejném balíčku.

- `<PackageOutputPath>`\
VOLITELNÉ Kde bude vytvořen balíček NuGet. Balíček NuGet je to, co .NET Core CLI globální nástroje používají k instalaci vašeho nástroje.

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

I když je `<PackageOutputPath>` nepovinná, použijte ji v tomto příkladu. Ujistěte se, že jste ji nastavili: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Dále vytvořte balíček NuGet pro vaši aplikaci.

```dotnetcli
dotnet pack
```

Soubor `botsay.1.0.0.nupkg` se vytvoří ve složce určené hodnotou `<PackageOutputPath>` XML ze souboru `botsay.csproj`, který je v tomto příkladu složkou `./nupkg`. To usnadňuje instalaci a testování. Pokud chcete veřejně vydávat nástroj, nahrajte ho do <https://www.nuget.org>. Jakmile je nástroj k dispozici v NuGet, vývojáři můžou provést instalaci nástroje na úrovni uživatele pomocí možnosti `--global` příkazu pro [instalaci nástroje dotnet](dotnet-tool-install.md) .

Teď, když máte balíček, nainstalujte nástroj z tohoto balíčku:

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

Parametr `--add-source` přikáže .NET Core CLI k dočasnému použití složky `./nupkg` (naše `<PackageOutputPath>` složka) jako dalšího zdrojového kanálu pro balíčky NuGet. Další informace o instalaci globálních nástrojů najdete v tématu [Přehled globálních nástrojů .NET Core](global-tools.md).

Pokud je instalace úspěšná, zobrazí se zpráva s příkazem použitým pro volání nástroje a nainstalované verze, podobně jako v následujícím příkladu:

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Nyní byste měli být schopni zadat `botsay` a získat odpověď z nástroje.

> [!NOTE]
> Pokud byla instalace úspěšná, ale nemůžete použít příkaz `botsay`, možná budete muset otevřít nový terminál, aby se cesta aktualizovala.

## <a name="remove-the-tool"></a>Odebrat nástroj

Až budete s nástrojem hotovi, můžete ho odebrat pomocí následujícího příkazu:

```dotnetcli
dotnet tool uninstall -g botsay
```
