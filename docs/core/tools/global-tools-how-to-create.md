---
title: Vytvoření globální nástroje .NET Core
description: Popisuje, jak vytvořit globální nástroj. Nástroj globální je konzolová aplikace, která se instaluje prostřednictvím rozhraní příkazového řádku .NET Core.
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 3d0a64d0473f51d73892cd40633e2982c1130469
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61647941"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>Vytvoření globální nástroje .NET Core pomocí rozhraní příkazového řádku .NET Core

V tomto článku se naučíte, jak vytvořit a balíček globální nástroje .NET Core. Rozhraní příkazového řádku .NET Core umožňuje vytvořit konzolovou aplikaci jako globální nástroj, který ostatní snadno nainstalovat a spustit. Globální nástroje .NET core jsou balíčky NuGet, které jsou instalovány z rozhraní příkazového řádku .NET Core. Další informace o těchto nástrojích, globální, naleznete v tématu [globální nástroje .NET Core přehled](global-tools.md).

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>Vytvoření projektu

Tento článek používá rozhraní příkazového řádku .NET Core k vytváření a správě projektu.

Náš příklad nástroj bude konzolovou aplikaci, která generuje bot ASCII a vytiskne zprávu. Nejprve vytvořte novou konzolovou aplikaci .NET Core.

```console
dotnet new console -o botsay
```

Přejděte `botsay` adresář vytvořený v předchozím příkazu.

## <a name="add-the-code"></a>Přidejte kód

Otevřít `Program.cs` souboru v oblíbeném textovém editoru, jako například `vim` nebo [Visual Studio Code](https://code.visualstudio.com/).

Přidejte následující `using` směrnice do horní části souboru, to pomáhá zkrátit kódu zobrazíte informace o verzi aplikace.

```csharp
using System.Reflection;
```

Dále přejděte dolů `Main` metody. Metoda nahraďte následující kód pro zpracování argumentů příkazového řádku pro vaši aplikaci. Pokud byly předány žádné argumenty, zobrazí se krátký nápovědu. V opačném případě všechny tyto argumenty jsou transformuje na řetězec a vytisknout s roboty.

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

### <a name="create-the-bot"></a>Vytvořte robota

V dalším kroku přidejte novou metodu s názvem `ShowBot` , která použije parametr řetězce. Tato metoda vytiskne zprávu a ASCII bot. Kód ASCII bot byla získána z [dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) vzorku.

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

### <a name="test-the-tool"></a>Testovací nástroje

Spusťte projekt a zobrazit výstup. Vyzkoušejte tyto odchylky z příkazového řádku, pokud chcete zobrazit odlišné výsledky:

```csharp
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

Všechny argumenty po `--` oddělovače jsou předány do vaší aplikace.

## <a name="setup-the-global-tool"></a>Instalační program nástroje global

Před aktualizací Service pack a distribuce aplikace jako globální nástroj, budete muset upravit soubor projektu. Otevřít `botsay.csproj` a přidejte tři nové uzly XML k `<Project><PropertyGroup>` uzlu:

- `<PackAsTool>`\
[POVINNÉ] Označuje, že aplikace se zabalí pro instalaci jako globální nástroj.

- `<ToolCommandName>`\
[VOLITELNÉ] Alternativní název pro nástroj, jinak název příkazu pro nástroj bude mít název souboru projektu. Může mít několik nástrojů v balíčku, při výběru že jedinečný a popisný název pomáhá odlišil od jiných nástrojů ve stejném balíku.

- `<PackageOutputPath>`\
[VOLITELNÉ] Kde se budou vytvářet balíček NuGet. Balíček NuGet je globální nástroje .NET Core CLI používá k instalaci nástroj.

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

I když `<PackageOutputPath>` je volitelný, jeho použití v tomto příkladu. Ujistěte se, že ji nastavíte: `<PackageOutputPath>./nupkg</PackageOutputPath>`.

Dále vytvořte balíček NuGet pro vaši aplikaci.

```console
dotnet pack
```

`botsay.1.0.0.nupkg` Vytvoří soubor ve složce identifikován `<PackageOutputPath>` hodnotu XML z `botsay.csproj` soubor, který v tomto příkladu je `./nupkg` složky. To usnadňuje instalaci a testování. Pokud chcete uvolnit nástroj veřejně, nahrajte ho do <https://www.nuget.org>. Až nástroj je k dispozici na webu NuGet, vývojáři můžete provést instalaci celou uživatele pomocí nástroje `--global` možnost [instalace nástrojů dotnet](dotnet-tool-install.md) příkazu.

Teď, když máte balíček, nainstalujte nástroj z tohoto balíčku:

```console
dotnet tool install --global --add-source ./nupkg botsay
```

`--add-source` Určuje parametr příkazového řádku .NET Core pro dočasně použití `./nupkg` složky (naše `<PackageOutputPath>` složky) jako další zdroj datového kanálu pro balíčky NuGet. Další informace o instalaci nástrojů pro globální, naleznete v tématu [globální nástroje .NET Core přehled](global-tools.md).

Pokud je instalace úspěšná, zobrazí se zpráva zobrazující příkazu používaný k volání nástroje a verze nainstalovaná, podobně jako v následujícím příkladu:

```
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

Nyní byste měli být schopni zadejte `botsay` a získat odpověď z nástroje.

> [!NOTE]
> Pokud byla instalace úspěšná, ale nemůžete použít `botsay` příkazu, budete muset otevřít nové zařízení k aktualizaci cesty.

## <a name="remove-the-tool"></a>Odeberte nástroj

Jakmile budete mít experimentování s nástroji, můžete ho odebrat pomocí následujícího příkazu:

```console
dotnet tool uninstall -g botsay
```
