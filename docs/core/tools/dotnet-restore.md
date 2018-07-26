---
title: příkaz DotNet restore - rozhraní příkazového řádku .NET Core
description: Zjistěte, jak obnovit závislostí a specifické pro projekt nástroje pomocí příkazu dotnet restore.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 0eaab1aa1bc52bd5b3c51a6ed2dd7a59c35a4aa5
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960585"
---
# <a name="dotnet-restore"></a>DotNet restore

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet restore` -Obnoví závislostí a nástrojů projektu.

## <a name="synopsis"></a>Souhrn

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache]
    [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```
---

## <a name="description"></a>Popis

`dotnet restore` Příkaz používá NuGet pro obnovení závislostí, stejně jako nástroje specifické pro projekt, které jsou uvedeny v souboru projektu. Ve výchozím nastavení obnovení závislostí a tools spouští paralelně.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

K obnovení závislosti, potřebuje NuGet informační kanály, kde se nacházejí balíčky. Informační kanály jsou obvykle k dispozici prostřednictvím *NuGet.config* konfigurační soubor. Výchozí konfigurační soubor je k dispozici při instalaci nástroje rozhraní příkazového řádku. Zadejte další informační kanály tím, že vytvoříte vlastní *NuGet.config* soubor v adresáři projektu. Zadejte také další kanály na vyvolání z příkazového řádku.

Pro závislosti, zadáte umístění obnoveného balíčky při použití operace obnovení `--packages` argument. Pokud není zadán, výchozí mezipaměti balíčku NuGet se používá, která byla nalezena v `.nuget/packages` adresáře do domovského adresáře uživatele ve všech operačních systémech. Například */home/user1* v Linuxu nebo *C:\Users\user1* na Windows.

Pro nástroje specifické pro projekt `dotnet restore` nejprve obnoví balíček, ve které je zabalena nástroj a pak pokračuje k obnovení závislostí nástroje uvedené v souboru projektu.

Chování `dotnet restore` příkaz je ovlivněna některá nastavení v *Nuget.Config* soubor, pokud jsou k dispozici. Například nastavení `globalPackagesFolder` v *NuGet.Config* umístí obnovené balíčky NuGet v zadané složce. Jedná se o alternativu k určení `--packages` možnost `dotnet restore` příkazu. Další informace najdete v tématu [odkaz na soubor NuGet.Config](/nuget/schema/nuget-config-file).

## <a name="implicit-dotnet-restore"></a>Implicitní `dotnet restore`

Od verze rozhraní .NET Core 2.0, `dotnet restore` spuštění implicitně v případě potřeby při vydání následující příkazy:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Ve většině případů už nepotřebujete explicitně `dotnet restore` příkazu.

V některých případech může být nepraktické spustit `dotnet restore` implicitně. Například některé automatizované systémy, jako jsou systémy sestavení potřebné k volání `dotnet restore` explicitně k řízení, pokud dojde k obnovení tak, aby se můžete řídit využití sítě. Aby se zabránilo `dotnet restore` ve spuštění implicitně, můžete použít `--no-restore` příznak s žádným z těchto příkazů můžete zakázat implicitní obnovení.

## <a name="arguments"></a>Arguments

`ROOT`

Volitelná cesta k souboru projektu, chcete-li obnovit.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Konfigurační soubor NuGet (*NuGet.config*) pro operaci obnovení.

`--disable-parallel`

Zakáže obnovování několika projektů najednou.

`--force`

Způsobí, že všechny závislosti vyřešit i v případě, že poslední obnovení bylo úspěšné. Zadání tohoto příznaku je stejný jako odstranění *project.assets.json* souboru.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--ignore-failed-sources`

Pouze upozornění na neúspěšné zdroje, pokud existují balíčky, které splňují požadavek na verzi.

`--no-cache`

Určuje, balíčky a požadavky HTTP do mezipaměti.

`--no-dependencies`

Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.

`--packages <PACKAGES_DIRECTORY>`

Určuje adresář pro obnovený balíčky.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje modul runtime pro obnovení balíčků. Tento parametr slouží k obnovení balíčků pro moduly runtime, které nejsou výslovně uvedené v `<RuntimeIdentifiers>` značku *.csproj* souboru. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md). Poskytuje více identifikátorů RID, protože zadání této možnosti více než jednou.

`-s|--source <SOURCE>`

Určuje zdroj balíčku NuGet pro použití během operace obnovení. Toto nastavení potlačí všechny zdroje podle *NuGet.config* soubory. Více zdrojů můžete zadat tak, že zadáte tuto možnost vícekrát.

`--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--configfile <FILE>`

Konfigurační soubor NuGet (*NuGet.config*) pro operaci obnovení.

`--disable-parallel`

Zakáže obnovování několika projektů najednou.

`-h|--help`

Vytiskne krátký nápovědy pro příkaz.

`--ignore-failed-sources`

Pouze upozornění na neúspěšné zdroje, pokud existují balíčky, které splňují požadavek na verzi.

`--no-cache`

Určuje, balíčky a požadavky HTTP do mezipaměti.

`--no-dependencies`

Při obnovování projekt s odkazy typu projekt projekt (P2P), obnoví kořenového projektu a nikoli odkazy.

`--packages <PACKAGES_DIRECTORY>`

Určuje adresář pro obnovený balíčky.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje modul runtime pro obnovení balíčků. Tento parametr slouží k obnovení balíčků pro moduly runtime, které nejsou výslovně uvedené v `<RuntimeIdentifiers>` značku *.csproj* souboru. Seznam identifikátorů modulů Runtime (RID), najdete v článku [katalog identifikátorů RID](../rid-catalog.md). Poskytuje více identifikátorů RID, protože zadání této možnosti více než jednou.

`-s|--source <SOURCE>`

Určuje zdroj balíčku NuGet pro použití během operace obnovení. Tím se přepíše všechny zdroje podle *NuGet.config* soubory. Více zdrojů můžete zadat tak, že zadáte tuto možnost vícekrát.

`--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

## <a name="examples"></a>Příklady

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři:

`dotnet restore`

Obnovte závislosti a nástroje pro `app1` projekt najít v zadané cestě:

`dotnet restore ~/projects/app1/app1.csproj`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí jako zdroj zadaná cesta k souboru:

`dotnet restore -s c:\packages\mypackages`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souborům dvou zdrojů ve formě:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Obnovte závislosti a nástroje pro projekt do aktuálního adresáře a zobrazuje pouze minimální výstupu:

`dotnet restore --verbosity minimal`
