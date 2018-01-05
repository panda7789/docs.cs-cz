---
title: "DotNet. Spusťte příkaz: .NET Core rozhraní příkazového řádku"
description: "Dotnet, spusťte příkaz poskytuje vhodnou možnost pro spuštění aplikace ze zdrojového kódu."
author: mairaw
ms.author: mairaw
ms.date: 09/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 1f5a3927859f89bef6c50d3d31b73de43cd1cd31
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-run"></a>Spustit DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet run`-Běží zdrojový kód bez jakýchkoli explicitní kompilace nebo spusťte příkazy.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
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

```
dotnet myapp.dll
```

Další informace o `dotnet` ovladač, najdete v článku [.NET Core příkazového řádku nástroje (CLI)](index.md) tématu.

Aby bylo možné spustit aplikaci `dotnet run` příkaz vyřeší závislosti aplikace, které jsou mimo sdílený modul runtime z mezipaměti NuGet. Protože se používá v mezipaměti závislosti, nedoporučujeme používat `dotnet run` ke spouštění aplikací v provozním prostředí. Místo toho [vytvořit nasazení](../deploying/index.md) pomocí [ `dotnet publish` ](dotnet-publish.md) příkazů a nasadit publikované výstup.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

`--`

Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty po touto jsou předány aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`--force`

Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné. Jde o ekvivalent odstraňování *project.assets.json*.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--launch-profile <NAME>`

Název spuštění profilu (pokud existuje) pro použití při spuštění aplikace. Spuštění profily jsou definovány v *launchSettings.json* souborů a jsou obvykle nazývá `Development`, `Staging` a `Production`. Další informace najdete v tématu [práce s několika prostředí](/aspnet/core/fundamentals/environments).

`--no-build`

Není sestavení projektu dřív, než spustíte.

`--no-dependencies`

Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.

`--no-launch-profile`

Není pokus o použití *launchSettings.json* konfigurace aplikace.

`--no-restore`

Neprovede implicitní obnovení, při spuštění příkazu.

`-p|--project <PATH>`

Určuje cestu k souboru projektu ke spuštění (úplná cesta nebo název). Pokud není zadaný, výchozí se k aktuálnímu adresáři.

`--runtime <RUNTIME_IDENTIFIER>`

Určuje cílový modul runtime pro obnovení balíčků pro. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`--`

Vymezuje argumenty, které mají `dotnet run` z argumentů pro aplikace spuštěna. Všechny argumenty po touto jsou předány aplikace spuštěná.

`-c|--configuration {Debug|Release}`

Definuje konfiguraci sestavení. Výchozí hodnota je `Debug`.

`-f|--framework <FRAMEWORK>`

Vytvoří a spustí aplikace pomocí zadané [framework](../../standard/frameworks.md). Rozhraní musí být zadán v souboru projektu.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`-p|--project <PATH/PROJECT.csproj>`

Určuje cestu a název souboru projektu. (Viz poznámka.) Pokud není zadaný, výchozí se k aktuálnímu adresáři.

> [!NOTE]
> Použijte cestu a název souboru projektu s `-p|--project` možnost. Regrese v rozhraní příkazového řádku brání poskytuje cestu ke složce s .NET Core 1.x SDK. Další informace o tomto problému najdete v tématu [dotnet. Spusťte -p, nelze spustit projekt (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Příklady

Spusťte projekt v aktuálním adresáři:

`dotnet run`

Spusťte zadaného projektu:

`dotnet run --project /projects/proj1/proj1.csproj`

Spusťte projekt v aktuálním adresáři ( `--help` argument v tomto příkladu je předán do aplikace, protože `--` použit argument):

`dotnet run --configuration Release -- --help`
