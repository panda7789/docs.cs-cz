---
title: příkaz DotNet - .NET Core rozhraní příkazového řádku
description: Další informace o příkazu dotnet (obecný ovladač pro rozhraní .NET Core rozhraní příkazového řádku nástroje) a jeho použití.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 788dc746705f9328683019ab3ad9836204a1ea63
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805656"
---
# <a name="dotnet-command"></a>příkaz DotNet.

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet` -Obecné ovladače pro spouštění příkazy příkazového řádku.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a>Popis

`dotnet` je obecný ovladač pro nástrojů rozhraní příkazového řádku (CLI). Vyvolání sama o sobě poskytuje stručný využití pokyny.

Každý konkrétní funkce je implementovaná jako příkaz. Pokud chcete používat funkci, je příkaz zadaný po `dotnet`, jako například [ `dotnet build` ](dotnet-build.md). Všechny argumenty následující příkaz jsou vlastní argumenty.

Pouze `dotnet` slouží jako příkaz svoje vlastní je spuštění [framework závislé aplikace](../deploying/index.md). Zadejte aplikaci DLL po `dotnet` příkaz pro spuštění aplikace (například `dotnet myapp.dll`).

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

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

`--list-runtimes`

Zobrazuje nainstalované moduly runtime .NET Core.

`--list-sdks`

Zobrazuje nainstalované sady Core SDK pro rozhraní .NET.

`--roll-forward-on-no-candidate-fx`

 Zobrazí souhrn vpřed v žádné sdílené framework candidate.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.

`--version`

Vytiskne verzi rozhraní .NET Core SDK používá.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

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

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.

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

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Není podporována v každé příkazu; Zobrazit stránka konkrétní příkaz k určení, pokud tato možnost je k dispozici.

`--version`

Vytiskne verzi rozhraní .NET Core SDK používá.

---

## <a name="dotnet-commands"></a>příkazy DotNet.

### <a name="general"></a>Obecné

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

| Příkaz                                       | Funkce                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Sestavení aplikace .NET Core.                                     |
| [sestavení serverem DotNet.](dotnet-build-server.md) | Komunikuje se servery, které jsou spouštěné sestavení.                          |
| [dotnet clean](dotnet-clean.md)               | Čistá sestavení výstupy.                                                |
| [dotnet help](dotnet-help.md)                 | Zobrazí podrobnější online dokumentaci pro příkaz.           |
| [dotnet migrate](dotnet-migrate.md)           | Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Poskytuje přístup k MSBuild příkazového řádku.                        |
| [dotnet new](dotnet-new.md)                   | Inicializuje jazyka C# nebo projekt F # pro dané šablony.                |
| [dotnet pack](dotnet-pack.md)                 | Vytvoří balíček NuGet kódu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný. |
| [dotnet restore](dotnet-restore.md)           | Obnoví závislosti pro dané aplikaci.                  |
| [dotnet run](dotnet-run.md)                   | Spustí aplikaci ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)                   | Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.       |
| [dotnet restore](dotnet-store.md)               | Uchovává sestavení v úložišti balíček modulu runtime.                     |
| [dotnet test](dotnet-test.md)                 | Spustí testy použitím nástroje test runner.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Sestavení aplikace .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Čistá sestavení výstupy.                                              |
| [dotnet help](dotnet-help.md)       | Zobrazí podrobnější online dokumentaci pro příkaz.           |
| [dotnet migrate](dotnet-migrate.md) | Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.  |
| [dotnet msbuild](dotnet-msbuild.md) | Poskytuje přístup k MSBuild příkazového řádku.                        |
| [dotnet new](dotnet-new.md)         | Inicializuje jazyka C# nebo projekt F # pro dané šablony.                |
| [dotnet pack](dotnet-pack.md)       | Vytvoří balíček NuGet kódu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný. |
| [dotnet restore](dotnet-restore.md) | Obnoví závislosti pro dané aplikaci.                  |
| [dotnet run](dotnet-run.md)         | Spustí aplikaci ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)         | Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.       |
| [dotnet restore](dotnet-store.md)     | Uchovává sestavení v úložišti balíček modulu runtime.                     |
| [dotnet test](dotnet-test.md)       | Spustí testy použitím nástroje test runner.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Sestavení aplikace .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Čistá sestavení výstupy.                                              |
| [dotnet migrate](dotnet-migrate.md) | Migruje platný Preview 2 projektu na .NET Core SDK 1.0 projekt.  |
| [dotnet msbuild](dotnet-msbuild.md) | Poskytuje přístup k MSBuild příkazového řádku.                        |
| [dotnet new](dotnet-new.md)         | Inicializuje jazyka C# nebo projekt F # pro dané šablony.                |
| [dotnet pack](dotnet-pack.md)       | Vytvoří balíček NuGet kódu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje aplikace rozhraní .NET framework závislé nebo úplný a samostatný. |
| [dotnet restore](dotnet-restore.md) | Obnoví závislosti pro dané aplikaci.                  |
| [dotnet run](dotnet-run.md)         | Spustí aplikaci ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)         | Možnosti pro přidání, odebrání a seznam projekty v řešení souboru.       |
| [dotnet test](dotnet-test.md)       | Spustí testy použitím nástroje test runner.                                     |

---

### <a name="project-references"></a>Odkazy na projekt

Příkaz | Funkce
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Přidá odkaz na projekt.
[dotnet list reference](dotnet-list-reference.md) | Obsahuje seznam odkazů projektu.
[dotnet remove reference](dotnet-remove-reference.md) | Odebere odkaz na projekt.

### <a name="nuget-packages"></a>Balíčky NuGet

Příkaz | Funkce
--- | ---
[dotnet add package](dotnet-add-package.md) | Přidá balíčku NuGet.
[dotnet remove package](dotnet-remove-package.md) | Odebere balíček NuGet.

### <a name="nuget-commands"></a>Příkazy pro balíčky NuGet

Příkaz | Funkce
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Odstraní nebo unlists balíčku ze serveru.
[dotnet nuget locals](dotnet-nuget-locals.md) | Vymaže nebo vypíše místní prostředky NuGet například mezipaměti požadavek http, dočasnou vyrovnávací paměť nebo složku globální balíčky celého systému.
[dotnet nuget push](dotnet-nuget-push.md) | Nabízených oznámení balíček na server a vydává je.

### <a name="global-tools-commands"></a>Globální příkazy nástroje

[.NET core globální nástroje](global-tools.md) jsou dostupné od verze rozhraní .NET Core SDK 2.1.300:

Příkaz | Funkce
--- | ---
[Instalace nástroje pro DotNet.](dotnet-tool-install.md) | Nainstaluje nástroj globální na váš počítač.
[seznam nástrojů DotNet.](dotnet-tool-list.md) | Obsahuje seznam všech globálních nástrojů, které jsou nainstalovány v výchozí adresář na počítači nebo v zadané cestě.
[Odinstalace nástroje pro DotNet.](dotnet-tool-uninstall.md) | Odinstaluje nástroj globální z vašeho počítače.
[aktualizace nástrojů DotNet.](dotnet-tool-update.md) | Aktualizuje nástroj globální na váš počítač.

### <a name="additional-tools"></a>Další nástroje

Od verze rozhraní .NET Core SDK 2.1.300, několik nástrojů, které byly k dispozici pouze na jednotlivých projektů za použití `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK. Mezi tyto nástroje patří:

| Nástroj                                              | Funkce                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev certifikátů                                         | Vytváří a spravuje certifikáty vývoj.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Nástroje příkazového řádku Entity Framework Core.                    |
| ukládání do mezipaměti SQL                                         | Nástroje příkazového řádku systému SQL Server mezipaměti.                         |
| [uživatel-tajné klíče](/aspnet/core/security/app-secrets) | Spravuje uživatele vývoj tajných klíčů.                            |
| [Sledování](/aspnet/core/tutorials/dotnet-watch)      | Spustí soubor sledovacího procesu, který spouští příkaz změna souborů. |

Další informace o nástroji pro každé provedení `dotnet <tool-name> --help`.

## <a name="examples"></a>Příklady

Vytvoří novou konzolovou aplikaci .NET Core:

`dotnet new console`

Obnovte závislosti pro danou aplikaci:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Sestavte projekt a jeho závislosti v daném adresáři:

`dotnet build`

Spustit framework závislé aplikace s názvem `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Proměnné prostředí

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Primární balíček mezipaměti. Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.

`DOTNET_SERVICING`

Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft. Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata). Jinak hodnota nastavena na `false` který se přidá do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijata). Pokud není nastavená, výchozí hodnota je `false` a funkci telemetrie je aktivní.

`DOTNET_MULTILEVEL_LOOKUP`

Určuje, zda .NET Core runtime, sdílený framework nebo sady SDK jsou vyřešit z globální umístění. Pokud není nastavena, je standardně `true`. Nastavte na `false` není vyřešit z globální umístění a mají izolované instalace .NET Core (hodnoty `0` nebo `false` přijímají). Další informace o víceúrovňovou vyhledávání najdete v tématu [více úroveň SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Zakáže malé verze dopředné posunutí. Další informace najdete v tématu [Posunutí vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Primární balíček mezipaměti. Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.

`DOTNET_SERVICING`

Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft. Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata). Jinak hodnota nastavena na `false` který se přidá do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijata). Pokud není nastavená, výchozí hodnota je `false` a funkci telemetrie je aktivní.

`DOTNET_MULTILEVEL_LOOKUP`

Určuje, zda .NET Core runtime, sdílený framework nebo sady SDK jsou vyřešit z globální umístění. Pokud není nastavena, je standardně `true`. Nastavte na `false` není vyřešit z globální umístění a mají izolované instalace .NET Core (hodnoty `0` nebo `false` přijímají). Další informace o víceúrovňovou vyhledávání najdete v tématu [více úroveň SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET pro základní 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Primární balíček mezipaměti. Pokud není nastavena, je standardně `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` v systému Windows.

`DOTNET_SERVICING`

Určuje umístění údržby indexu má použít pro sdílené hostitele při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, jestli se data o využití nástroje .NET Core shromažďuje a odesílá společnosti Microsoft. Nastavte na `true` vyjádřit výslovný nesouhlas funkci telemetrie (hodnoty `true`, `1`, nebo `yes` přijata). Jinak hodnota nastavena na `false` který se přidá do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijata). Pokud není nastavená, výchozí hodnota je `false` a funkci telemetrie je aktivní.

---
