---
title: "příkaz Obnovit DotNet - .NET Core rozhraní příkazového řádku"
description: "Zjistěte, jak obnovit závislosti a specifické pro projekt nástroje pomocí příkazu restore dotnet."
keywords: "příkaz DotNet obnovit, rozhraní příkazového řádku, rozhraní příkazového řádku, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 11/30/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 50e8d5c335386c41e36a490263a4f4ebd2bd39ba
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="dotnet-restore"></a>obnovení DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet restore` -Obnoví závislosti a nástroje projektu.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a>Popis

`dotnet restore` Příkaz používá NuGet Obnovit závislosti, jakož i projektu konkrétní nástroje, které jsou určené v souboru projektu. Ve výchozím nastavení jsou v paralelní provést obnovení závislosti a nástroje.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Chcete-li obnovit závislosti, musí NuGet informační kanály, kde se nachází balíčky. Informační kanály se obvykle poskytují prostřednictvím *NuGet.config* konfigurační soubor. Výchozí konfigurační soubor je zadat při instalaci nástrojů příkazového řádku. Zadejte další informační kanály tak, že vytvoříte vlastní *NuGet.config* soubor v adresáři projektu. Můžete také určit další kanály pro volání na příkazovém řádku.

Závislosti, zadáte umístění obnoveného balíčky během obnovení operace pomocí `--packages` argument. Pokud není zadáno, výchozí mezipaměti balíček NuGet se používá, který se nachází v `.nuget/packages` adresář v domovském adresáři uživatele ve všech operačních systémů (například */home/user1* v systému Linux nebo *C:\Users\user1*  v systému Windows).

Pro konkrétní projekt nástrojů, `dotnet restore` nejprve obnoví balíček, ve kterém se nástroj nachází v balení a potom pokračuje k obnovení nástroje závislosti uvedeného v souboru projektu.

Chování `dotnet restore` příkaz je ovlivňován některá nastavení v *Nuget.Config* soubor, pokud je k dispozici. Například nastavení `globalPackagesFolder` v *NuGet.Config* umístí obnovené balíčků NuGet v zadané složce. Jde o alternativu k určení `--packages` možnost `dotnet restore` příkaz. Další informace najdete v tématu [NuGet.Config odkaz](/nuget/schema/nuget-config-file).

## <a name="implicit-dotnet-restore"></a>Implicitní `dotnet restore`

Od verze rozhraní .NET 2.0 jádra, `dotnet restore` spuštění implicitně v případě potřeby při vydání následující příkazy:

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

Ve většině případů potřebujete už explicitně použít `dotnet restore` příkaz. 

V některých případech je nepohodlná pro `dotnet restore` ke spuštění implicitně. Například některé automatizované systémy, jako je například systémy sestavení muset volat `dotnet restore` explicitně k řízení, když dojde k obnovení, abyste se mohli řídit využití sítě. Aby se zabránilo `dotnet restore` ve spuštění implicitně, můžete použít `--no-restore` přepínače s žádným z těchto příkazů zakázat implicitní obnovení.

## <a name="arguments"></a>Arguments

`ROOT`

Cesty k souboru projektu k obnovení.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`--configfile <FILE>`

Konfigurační soubor NuGet (*NuGet.config*) používat pro operaci obnovení.

`--disable-parallel`

Zakáže obnovení více projektů současně.

`--force`

Vynutí všechny závislosti pro přeloženy i v případě, že poslední obnovení bylo úspěšné. Jde o ekvivalent odstraňování *project.assets.json* souboru.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--ignore-failed-sources`

Pouze upozornění na selhání zdroje, pokud jsou balíčky splňuje požadavek na verzi.

`--no-cache`

Určuje, pro balíčky a žádostí HTTP do mezipaměti.

`--no-dependencies`

Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.

`--packages <PACKAGES_DIRECTORY>`

Určuje adresář pro obnovené balíčky.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje modul runtime pro obnovení balíčků. Slouží k obnovení balíčků pro moduly runtime není explicitně uvedené v `<RuntimeIdentifiers>` značky v *.csproj* souboru. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md). Zadejte více identifikátorů RID tak, že zadáte tuto možnost vícekrát.

`-s|--source <SOURCE>`

Určuje zdroj balíčku NuGet k použití během operace obnovení. Všechny zdroje, zadaný v přepíše *NuGet.config* soubory. Zadáním více než jednou. tuto možnost lze zadat více zdrojů.

`--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`--configfile <FILE>`

Konfigurační soubor NuGet (*NuGet.config*) používat pro operaci obnovení.

`--disable-parallel`

Zakáže obnovení více projektů současně.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz.

`--ignore-failed-sources`

Pouze upozornění na selhání zdroje, pokud jsou balíčky splňuje požadavek na verzi.

`--no-cache`

Určuje, pro balíčky a žádostí HTTP do mezipaměti.

`--no-dependencies`

Při obnovování projektu s odkazy na projekt na projekt (P2P), obnoví kořenového projektu a není odkazuje.

`--packages <PACKAGES_DIRECTORY>`

Určuje adresář pro obnovené balíčky.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Určuje modul runtime pro obnovení balíčků. Slouží k obnovení balíčků pro moduly runtime není explicitně uvedené v `<RuntimeIdentifiers>` značky v *.csproj* souboru. Seznam Runtime identifikátorů (RID), najdete v článku [identifikátorů RID katalogu](../rid-catalog.md). Zadejte více identifikátorů RID tak, že zadáte tuto možnost vícekrát.

`-s|--source <SOURCE>`

Určuje zdroj balíčku NuGet k použití během operace obnovení. Všechny zdroje, zadaný v přepíše *NuGet.config* soubory. Zadáním více než jednou. tuto možnost lze zadat více zdrojů.

`--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`.

## <a name="examples"></a>Příklady

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři:

`dotnet restore`

Závislosti a nástroje pro obnovení `app1` v zadané cestě nalezen projektu:

`dotnet restore ~/projects/app1/app1.csproj`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesta k souboru, který je k dispozici jako zdroj:

`dotnet restore -s c:\packages\mypackages`

Obnovte závislosti a nástroje pro projekt v aktuálním adresáři pomocí cesty k souborům dvě zadané jako zdroje:

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

Obnovte závislosti a nástroje pro projekt v aktuální adresář a zobrazuje pouze minimální výstup:

`dotnet restore --verbosity minimal`
