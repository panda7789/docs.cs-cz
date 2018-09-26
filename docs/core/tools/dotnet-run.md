---
title: 'DotNet spusťte příkaz: rozhraní příkazového řádku .NET Core'
description: Spusťte příkaz dotnet poskytuje vhodnou možnost ke spuštění aplikace ze zdrojového kódu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f560e6f795f00488818647a4b5c711dcf9d59dcd
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078477"
---
# <a name="dotnet-run"></a>Spusťte příkaz DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet run` -Spuštění zdrojový kód bez žádné explicitní kompilace a spuštění příkazů.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet run` Příkaz poskytuje vhodnou možnost ke spuštění aplikace ze zdrojového kódu pomocí jednoho příkazu. To je užitečné pro rychlé iterativní vývoj z příkazového řádku. Příkaz závisí [ `dotnet build` ](dotnet-build.md) příkaz sestavení kódu. Všechny požadavky pro sestavení, jako je projekt, je potřeba obnovit nejdřív použijte k `dotnet run` také.

Výstupní soubory jsou zapsány do výchozího umístění, což je `bin/<configuration>/<target>`. Například pokud máte `netcoreapp2.1` aplikace a spusťte `dotnet run`, výstup je umístěn v `bin/Debug/netcoreapp2.1`. Soubory jsou přepsány, podle potřeby. Dočasné soubory jsou umístěny v `obj` adresáře.

Pokud projekt určuje více platforem, provádí `dotnet run` způsobí chybu, pokud `-f|--framework <FRAMEWORK>` možnost slouží k určení rozhraní framework.

`dotnet run` Příkaz se používá v rámci projektů nejsou vytvořená sestavení. Pokud se snažíte místo něj spustí aplikace závisí na architektuře knihovny DLL, je nutné použít [dotnet](dotnet.md) bez příkaz. Chcete-li například spustit `myapp.dll`, použijte:

```console
dotnet myapp.dll
```

Další informace o `dotnet` ovladač, najdete v článku [.NET Core příkazového řádku nástroje (CLI)](index.md) tématu.

Ke spuštění aplikace, `dotnet run` příkaz řeší závislosti aplikace, které se nachází mimo sdílený modul runtime z mezipaměti NuGet. Protože ho používá uložené v mezipaměti závislosti, se nedoporučuje používat `dotnet run` ke spouštění aplikací v produkčním prostředí. Místo toho [vytvořit nasazení](../deploying/index.md) pomocí [ `dotnet publish` ](dotnet-publish.md) příkazů a nasaďte publikovaný výstup.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--`

Odděluje citaci argumenty `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty za tento oddělovač jsou předány do aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikaci pomocí zadaného [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`--force`

Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--launch-profile <NAME>`

Název spuštění profilu (pokud existuje) má použít při spuštění aplikace. Profily spuštění, které jsou definovány v *launchSettings.json* a souborů jsou běžně označována jako `Development`, `Staging`, a `Production`. Další informace najdete v tématu [práce v různých prostředích](/aspnet/core/fundamentals/environments).

`--no-build`

Nelze sestavit projekt před provozováním. Také implicitní nastaví `--no-restore` příznak.

`--no-dependencies`

Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.

`--no-launch-profile`

Nebude se pokusí použít *launchSettings.json* konfigurace aplikace.

`--no-restore`

Při spuštění příkazu se nebude spouštět implicitní obnovení.

`-p|--project <PATH>`

Určuje cestu k souboru projektu pro spuštění (název složky nebo úplná cesta). Pokud není zadán, použije se výchozí do aktuálního adresáře.

`--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovování balíčků pro. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--`

Odděluje citaci argumenty `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty za tento oddělovač jsou předány do aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikaci pomocí zadaného [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`--force`

Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--launch-profile <NAME>`

Název spuštění profilu (pokud existuje) má použít při spuštění aplikace. Profily spuštění, které jsou definovány v *launchSettings.json* a souborů jsou běžně označována jako `Development`, `Staging`, a `Production`. Další informace najdete v tématu [práce v různých prostředích](/aspnet/core/fundamentals/environments).

`--no-build`

Nelze sestavit projekt před provozováním. Také implicitní nastaví `--no-restore` příznak.

`--no-dependencies`

Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.

`--no-launch-profile`

Nebude se pokusí použít *launchSettings.json* konfigurace aplikace.

`--no-restore`

Při spuštění příkazu se nebude spouštět implicitní obnovení.

`-p|--project <PATH>`

Určuje cestu k souboru projektu pro spuštění (název složky nebo úplná cesta). Pokud není zadán, použije se výchozí do aktuálního adresáře.

`--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovování balíčků pro. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--`

Odděluje citaci argumenty `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty za tento oddělovač jsou předány do aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikaci pomocí zadaného [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`-p|--project <PATH/PROJECT.csproj>`

Určuje cestu a název souboru projektu. (Viz poznámky). Pokud není zadán, použije se výchozí do aktuálního adresáře.

> [!NOTE]
> Použít cestu a název souboru projektu se `-p|--project` možnost. Zabraňuje Regrese v rozhraní příkazového řádku .NET Core SDK poskytuje cestu ke složce 1.x. Další informace o tomto problému najdete v tématu [dotnet spustit -p, nelze spustit projekt (.NET/cli #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Příklady

Spusťte projekt v aktuálním adresáři:

`dotnet run`

Spusťte zadaný projekt:

`dotnet run --project ./projects/proj1/proj1.csproj`

Spusťte projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, od prázdnou `--` možnost se používá):

`dotnet run --configuration Release -- --help`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři jenom minimální výstupní a spuštění projektu: (.NET Core SDK 2.0 a novější):

`dotnet run --verbosity m`