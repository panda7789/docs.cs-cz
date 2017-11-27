---
title: "příkaz DotNet - .NET Core rozhraní příkazového řádku"
description: "Další informace o příkazu dotnet (obecný ovladač pro rozhraní .NET Core rozhraní příkazového řádku nástroje) a jeho použití."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: bba8d77cda7538bf008dc0f510f9279d3c695c3d
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2017
---
# <a name="dotnet-command"></a>příkaz DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet`-Obecné ovladače pro spouštění příkazy příkazového řádku.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a>Popis

`dotnet`je obecný ovladač pro nástrojů rozhraní příkazového řádku (CLI). Vyvolání sama o sobě poskytuje stručný využití pokyny.

Každý konkrétní funkce je implementovaná jako příkaz. Chcete-li používat funkci, je příkaz zadaný po `dotnet`, jako například [ `dotnet build` ](dotnet-build.md). Všechny argumenty následující příkaz jsou vlastní argumenty.

Pouze `dotnet` slouží jako příkaz svoje vlastní je spuštění [framework závislé aplikace](../deploying/index.md). Zadejte aplikaci DLL po `dotnet` příkaz pro spuštění aplikace (například `dotnet myapp.dll`).

## <a name="options"></a>Možnosti

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

`--additionaldeps <PATH>`

Cesta k další *deps.json* souboru.

`--additionalprobingpath <PATH>`

Cesta obsahující testování zásad a sestavení testovat.

`-d|--diagnostics`

Umožňuje výstup diagnostiky.

`--fx-version <VERSION>`

Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz. Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.

`--roll-forward-on-no-candidate-fx`

 Zobrazí souhrn vpřed v žádné sdílené framework candidate.

`-v|--verbose`

Umožňuje podrobný výstup.

`--version`

Vytiskne verzi rozhraní .NET Core SDK používá.

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Cesta obsahující testování zásad a sestavení testovat.

`-d|--diagnostics`

Umožňuje výstup diagnostiky.

`--fx-version <VERSION>`

Verze nainstalovaného .NET Core runtime se použije ke spuštění aplikace.

`-h|--help`

Vytiskne krátké nápovědy pro příkaz. Pokud pomocí `dotnet`, vytiskne také seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o nástroji příkazového řádku a prostředí, například v aktuálním operačním systému, potvrzení SHA pro verze a další informace.

`-v|--verbose`

Umožňuje podrobný výstup.

`--version`

Vytiskne verzi rozhraní .NET Core SDK používá.

---

## <a name="dotnet-commands"></a>příkazy DotNet.

### <a name="general"></a>Obecné

# <a name="net-core-2xtabnetcore2x"></a>[.NET pro základní 2.x](#tab/netcore2x)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [sestavení DotNet.](dotnet-build.md)     | Sestavení aplikace .NET Core.                                     |
| [Vyčištění DotNet.](dotnet-clean.md)     | Čistá sestavení výstupy.                                              |
| [Nápověda DotNet.](dotnet-help.md)       | Zobrazí podrobnější online dokumentaci pro příkaz.           |
| [migrace DotNet.](dotnet-migrate.md) | Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.  |
| [msbuild DotNet.](dotnet-msbuild.md) | Poskytuje přístup k MSBuild příkazového řádku.                        |
| [nové DotNet.](dotnet-new.md)         | Inicializuje jazyka C# nebo projekt F # pro dané šablony.                |
| [pack DotNet.](dotnet-pack.md)       | Vytvoří balíček NuGet kódu.                               |
| [publikování DotNet.](dotnet-publish.md) | Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný. |
| [obnovení DotNet.](dotnet-restore.md) | Obnoví závislosti pro dané aplikaci.                  |
| [Spustit DotNet.](dotnet-run.md)         | Spustí aplikaci ze zdroje.                                   |
| [SLN – DotNet.](dotnet-sln.md)         | Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.       |
| [úložiště DotNet.](dotnet-store.md)     | Uchovává sestavení v úložišti balíček modulu runtime.                     |
| [test DotNet.](dotnet-test.md)       | Spustí testy použitím nástroje test runner.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [sestavení DotNet.](dotnet-build.md)     | Sestavení aplikace .NET Core.                                     |
| [Vyčištění DotNet.](dotnet-clean.md)     | Čistá sestavení výstupy.                                              |
| [migrace DotNet.](dotnet-migrate.md) | Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.  |
| [msbuild DotNet.](dotnet-msbuild.md) | Poskytuje přístup k MSBuild příkazového řádku.                        |
| [nové DotNet.](dotnet-new.md)         | Inicializuje jazyka C# nebo projekt F # pro dané šablony.                |
| [pack DotNet.](dotnet-pack.md)       | Vytvoří balíček NuGet kódu.                               |
| [publikování DotNet.](dotnet-publish.md) | Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný. |
| [obnovení DotNet.](dotnet-restore.md) | Obnoví závislosti pro dané aplikaci.                  |
| [Spustit DotNet.](dotnet-run.md)         | Spustí aplikaci ze zdroje.                                   |
| [SLN – DotNet.](dotnet-sln.md)         | Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.       |
| [test DotNet.](dotnet-test.md)       | Spustí testy použitím nástroje test runner.                                     |

---

### <a name="project-references"></a>Odkazy na projekt

Příkaz | Funkce
--- | ---
[Přidat odkaz DotNet.](dotnet-add-reference.md) | Přidáte odkaz na projekt.
[referenční seznam DotNet.](dotnet-list-reference.md) | Zobrazí seznam odkazů projektu.
[Odebrat odkaz DotNet.](dotnet-remove-reference.md) | Odeberte odkaz na projekt.

### <a name="nuget-packages"></a>Balíčky NuGet

Příkaz | Funkce
--- | ---
[Přidejte balíček DotNet.](dotnet-add-package.md) | Přidejte balíček NuGet.
[Odebrat balíček DotNet.](dotnet-remove-package.md) | Odebrání balíčku NuGet.

### <a name="nuget-commands"></a>Příkazy pro balíčky NuGet

Příkaz | Funkce
--- | ---
[odstranění nuget DotNet.](dotnet-nuget-delete.md) | Odstraní nebo unlists balíčku ze serveru.
[místní hodnoty nuget DotNet.](dotnet-nuget-locals.md) | Vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.
[nabízená nuget DotNet.](dotnet-nuget-push.md) | Nabízených oznámení balíček na server a vydává je.

## <a name="examples"></a>Příklady

Inicializace ukázkové aplikace konzoly .NET Core, která můžete zkompilovat a spustit:

`dotnet new console`

Obnovte závislosti pro danou aplikaci:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Sestavte projekt a jeho závislosti v daném adresáři:

`dotnet build`

Spustit framework závislé aplikace s názvem `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Proměnné prostředí

`DOTNET_PACKAGES`

Primární balíček mezipaměti. Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.

`DOTNET_SERVICING`

Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft. Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata) nastavena, jinak hodnota `false` k vyslovení souhlasu s funkcí telemetrie (hodnoty `false`, `0`, nebo `no` přijata). Pokud není nastavená, výchozí hodnoty je `false`, a je aktivní funkce telemetrie.
