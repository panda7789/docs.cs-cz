---
title: "příkaz Obnovit DotNet - .NET Core rozhraní příkazového řádku"
description: "Zjistěte, jak obnovit závislosti a specifické pro projekt nástroje pomocí příkazu restore dotnet."
keywords: "příkaz DotNet obnovit, rozhraní příkazového řádku, rozhraní příkazového řádku, .NET Core"
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 82a78dcb0cc85e2ba087b6df5ee029cbfb687358
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-restore"></a>obnovení DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet restore`-Obnoví závislosti a nástroje projektu.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

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

## <a name="arguments"></a>Arguments

`ROOT`

Cesty k souboru projektu k obnovení.

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

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

Určuje zdroj balíčku NuGet k použití během operace obnovení. Všechny zdroje, zadaný v přepíše *NuGet.config* souborům. Zadáním více než jednou. tuto možnost lze zadat více zdrojů.

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

Určuje zdroj balíčku NuGet k použití během operace obnovení. Všechny zdroje, zadaný v přepíše *NuGet.config* souborům. Zadáním více než jednou. tuto možnost lze zadat více zdrojů.

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
