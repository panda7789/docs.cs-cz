---
title: 'DotNet. Spusťte příkaz: .NET Core rozhraní příkazového řádku'
description: Dotnet, spusťte příkaz poskytuje vhodnou možnost pro spuštění aplikace ze zdrojového kódu.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 82c6e44e52aa6af7044edf72fd6e57b7614a70f3
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696309"
---
# <a name="dotnet-run"></a>Spustit DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet run` -Běží zdrojový kód bez jakýchkoli explicitní kompilace nebo spusťte příkazy.

## <a name="synopsis"></a>Stručný obsah

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
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet run` Příkaz poskytuje vhodnou možnost pro spuštění aplikace ze zdrojového kódu se jeden příkaz. Je vhodné pro rychlé iterativní vývoj z příkazového řádku. Příkaz závisí na [ `dotnet build` ](dotnet-build.md) k vytvoření kód. Všechny požadavky pro sestavení, jako je například, je nutné obnovit projekt nejprve použít `dotnet run` také.

Výstupní soubory se zapisují do výchozího umístění, což je `bin/<configuration>/<target>`. Například pokud máte `netcoreapp1.0` aplikace a můžete spustit `dotnet run`, se umístí výstup v `bin/Debug/netcoreapp1.0`. Soubory jsou přepsány podle potřeby. Dočasné soubory jsou umístěny v `obj` adresáře.

Pokud projekt určuje více rozhraní, provádění `dotnet run` vede k chybě, pokud `-f|--framework <FRAMEWORK>` možnost slouží k určení rozhraní.

`dotnet run` Příkaz se používá v souvislosti s projekty, Nevytvořen sestavení. Pokud se pokoušíte spustit framework závislé aplikace DLL místo, musíte použít [dotnet](dotnet.md) bez příkaz. Chcete-li například spustit `myapp.dll`, použijte:

```console
dotnet myapp.dll
```

Další informace o `dotnet` ovladač, najdete v článku [.NET Core příkazového řádku nástroje (CLI)](index.md) tématu.

Ke spuštění aplikace, `dotnet run` příkaz vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet. Protože se používá v mezipaměti závislosti, nedoporučujeme používat `dotnet run` ke spouštění aplikací v provozním prostředí. Místo toho [vytvořit nasazení](../deploying/index.md) pomocí [ `dotnet publish` ](dotnet-publish.md) příkazů a nasadit publikované výstup.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--`

Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty po této oddělovač jsou předány aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`--force`

Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné. Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--launch-profile <NAME>`

Název spuštění profilu (pokud existuje) pro použití při spuštění aplikace. Spuštění profily jsou definovány v *launchSettings.json* souborů a jsou obvykle nazývá `Development`, `Staging`, a `Production`. Další informace najdete v tématu [práce s několika prostředí](/aspnet/core/fundamentals/environments).

`--no-build`

Není sestavení projektu dřív, než spustíte. Také implicitní nastaví `--no-restore` příznak.

`--no-dependencies`

Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.

`--no-launch-profile`

Nebude pokoušet použít *launchSettings.json* konfigurace aplikace.

`--no-restore`

Implicitní obnovení není spustit, když spustíte příkaz.

`-p|--project <PATH>`

Určuje cestu k souboru projektu ke spuštění (úplná cesta nebo název). Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.

`--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovení balíčků pro. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--`

Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty po této oddělovač jsou předány aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`--force`

Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné. Zadáním tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--launch-profile <NAME>`

Název spuštění profilu (pokud existuje) pro použití při spuštění aplikace. Spuštění profily jsou definovány v *launchSettings.json* souborů a jsou obvykle nazývá `Development`, `Staging`, a `Production`. Další informace najdete v tématu [práce s několika prostředí](/aspnet/core/fundamentals/environments).

`--no-build`

Není sestavení projektu dřív, než spustíte. Také implicitní nastaví `--no-restore` příznak.

`--no-dependencies`

Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.

`--no-launch-profile`

Nebude pokoušet použít *launchSettings.json* konfigurace aplikace.

`--no-restore`

Implicitní obnovení není spustit, když spustíte příkaz.

`-p|--project <PATH>`

Určuje cestu k souboru projektu ke spuštění (úplná cesta nebo název). Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.

`--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovení balíčků pro. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`--`

Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty po této oddělovač jsou předány aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-p|--project <PATH/PROJECT.csproj>`

Určuje cestu a název souboru projektu. (Viz poznámka.) Pokud není zadáno, výchozí hodnoty k aktuálnímu adresáři.

> [!NOTE]
> Použijte cestu a název souboru projektu s `-p|--project` možnost. Regrese v rozhraní příkazového řádku brání poskytuje cestu ke složce s .NET Core SDK 1.x. Další informace o tomto problému najdete v tématu [dotnet. Spusťte -p, nelze spustit projekt (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Příklady

Spusťte projekt v aktuálním adresáři:

`dotnet run`

Spusťte zadaného projektu:

`dotnet run --project /projects/proj1/proj1.csproj`

Spusťte projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, protože `--` použit argument):

`dotnet run --configuration Release -- --help`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři jen s minimální výstup a spusťte projekt: (.NET Core SDK 2.0 a novější):

`dotnet run --verbosity m`