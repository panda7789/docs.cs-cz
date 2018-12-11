---
title: příkaz DotNet
description: Další informace o příkazu dotnet (obecný ovladač pro nástroje .NET Core CLI) a jeho použití.
ms.date: 06/04/2018
ms.openlocfilehash: 081f295cc71c3cd46de465efb12f131e7b2d36d9
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53170838"
---
# <a name="dotnet-command"></a>příkaz DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Název

`dotnet` – Nástroj pro správu zdrojového kódu .NET a binární soubory.

## <a name="synopsis"></a>Souhrn

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
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a>Popis

`dotnet` je nástroj pro správu zdrojového kódu .NET a binární soubory. Uvádí příkazy, které provádějí konkrétní úlohy, jako například [ `dotnet build` ](dotnet-build.md) a [ `dotnet run` ](dotnet-run.md). Každý příkaz definuje vlastní argumenty. Typ `--help` po každém z nich pro přístup k stručný dokumentace nápovědy.

`dotnet` je možné ke spouštění aplikací, tak, že zadáte aplikaci knihovny DLL, jako například `dotnet myapp.dll`. Zobrazit [nasazení aplikace .NET Core](../deploying/index.md) pro další informace o možnosti nasazení.

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Cesta k dalším *deps.json* souboru.

`--additionalprobingpath <PATH>`

Cestu, která obsahuje testování zásad a sestavení testu.

`-d|--diagnostics`

Umožňuje diagnostický výstup.

`--fx-version <VERSION>`

Verze modulu runtime .NET Core se použije ke spuštění aplikace.

`-h|--help`

Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`. `dotnet --help` Vypíše seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.

`--list-runtimes`

Zobrazuje nainstalované moduly runtime .NET Core.

`--list-sdks`

Zobrazí nainstalovaný .NET Core SDK.

`--roll-forward-on-no-candidate-fx`

 Zakáže podverze Posunutí vpřed, pokud nastavit `0`. Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.

`--version`

Vytiskne na verzi .NET Core SDK používá.

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Cesta k dalším *deps.json* souboru.

`--additionalprobingpath <PATH>`

Cestu, která obsahuje testování zásad a sestavení testu.

`-d|--diagnostics`

Umožňuje diagnostický výstup.

`--fx-version <VERSION>`

Verze modulu runtime .NET Core se použije ke spuštění aplikace.

`-h|--help`

Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`. `dotnet --help` Vypíše seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.

`--roll-forward-on-no-candidate-fx`

 Zakáže podverze Posunutí vpřed, pokud nastavit `0`. Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.

`--version`

Vytiskne na verzi .NET Core SDK používá.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Cestu, která obsahuje testování zásad a sestavení testu.

`-d|--diagnostics`

Umožňuje diagnostický výstup.

`--fx-version <VERSION>`

Verze modulu runtime .NET Core se použije ke spuštění aplikace.

`-h|--help`

Dokumentace pro zadaný příkaz, například vytiskne `dotnet build --help`. `dotnet --help` Vypíše seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o instalaci .NET Core a prostředí počítače, jako je například aktuální operační systém a verze .NET Core SHA potvrzení.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, a `diag[nostic]`. Nepodporované ve každý příkaz; Zobrazit stránka konkrétní příkaz k určení, zda tato možnost je k dispozici.

`--version`

Vytiskne na verzi .NET Core SDK používá.

---

## <a name="dotnet-commands"></a>příkazy DotNet

### <a name="general"></a>Obecné

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

| Příkaz                                       | Funkce                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Sestavení aplikace .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Komunikuje se servery pro spuštění sestavení.                          |
| [dotnet clean](dotnet-clean.md)               | Čištění výstupy sestavení.                                                |
| [dotnet help](dotnet-help.md)                 | Zobrazí podrobnější online dokumentaci pro příkaz.           |
| [dotnet migrate](dotnet-migrate.md)           | Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Poskytuje přístup k příkazovému řádku nástroje MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicializuje C# nebo F# projektu pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Vytvoří balíček NuGet kódu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje závisí na architektuře nebo samostatné aplikaci .NET. |
| [dotnet restore](dotnet-restore.md)           | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)                   | Spuštění aplikace ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)                   | Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.       |
| [dotnet restore](dotnet-store.md)               | Sestavení se ukládá do úložiště balíčků modulu runtime.                     |
| [dotnet test](dotnet-test.md)                 | Spustí testy pomocí nástroje test runner.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Sestavení aplikace .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Čištění výstupy sestavení.                                              |
| [dotnet help](dotnet-help.md)       | Zobrazí podrobnější online dokumentaci pro příkaz.           |
| [dotnet migrate](dotnet-migrate.md) | Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Poskytuje přístup k příkazovému řádku nástroje MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicializuje C# nebo F# projektu pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)       | Vytvoří balíček NuGet kódu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje závisí na architektuře nebo samostatné aplikaci .NET. |
| [dotnet restore](dotnet-restore.md) | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)         | Spuštění aplikace ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)         | Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.       |
| [dotnet restore](dotnet-store.md)     | Sestavení se ukládá do úložiště balíčků modulu runtime.                     |
| [dotnet test](dotnet-test.md)       | Spustí testy pomocí nástroje test runner.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Sestavení aplikace .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Čištění výstupy sestavení.                                              |
| [dotnet migrate](dotnet-migrate.md) | Migruje platný projekt ve verzi Preview 2 na projekt .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Poskytuje přístup k příkazovému řádku nástroje MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicializuje C# nebo F# projektu pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)       | Vytvoří balíček NuGet kódu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje závisí na architektuře nebo samostatné aplikaci .NET. |
| [dotnet restore](dotnet-restore.md) | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)         | Spuštění aplikace ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)         | Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.       |
| [dotnet test](dotnet-test.md)       | Spustí testy pomocí nástroje test runner.                                     |

---

### <a name="project-references"></a>Odkazy na projekt

Příkaz | Funkce
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Přidá odkaz na projekt.
[dotnet list reference](dotnet-list-reference.md) | Obsahuje odkazy na projekt.
[dotnet remove reference](dotnet-remove-reference.md) | Odebere odkaz na projekt.

### <a name="nuget-packages"></a>Balíčky NuGet

Příkaz | Funkce
--- | ---
[dotnet add package](dotnet-add-package.md) | Přidá balíček NuGet.
[dotnet remove package](dotnet-remove-package.md) | Odebere balíček NuGet.

### <a name="nuget-commands"></a>Příkazy pro balíčky NuGet

Příkaz | Funkce
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Odstraní nebo unlists balíčku ze serveru.
[dotnet nuget locals](dotnet-nuget-locals.md) | Vymaže nebo vypíše místní prostředky NuGet, třeba mezipaměť požadavku http, dočasná mezipaměť nebo celý počítač globální složku balíčků.
[dotnet nuget push](dotnet-nuget-push.md) | Odešle balíček na server a publikuje ji.

### <a name="global-tools-commands"></a>Globální příkazy nástroje

[Globální nástroje .NET core](global-tools.md) jsou k dispozici od verze rozhraní .NET Core SDK 2.1.300:

Příkaz | Funkce
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Globální nástroj nainstaluje na svém počítači.
[dotnet tool list](dotnet-tool-list.md) | Vypíše všechny globální nástroje aktuálně nainstalované ve výchozím adresáři na svém počítači nebo v zadané cestě.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstaluje nástroj globální z vašeho počítače.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje nástroj globální na svém počítači.

### <a name="additional-tools"></a>Další nástroje

Počínaje řadou nástrojů, které byly k dispozici pouze v jednotlivých projektů pomocí sady .NET Core SDK 2.1.300, `DotnetCliToolReference` jsou teď k dispozici jako součást sady .NET Core SDK. Tyto nástroje jsou uvedeny v následující tabulce:

| Nástroj                                              | Funkce                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Vytváří a spravuje certifikáty vývoje.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Nástroje příkazového řádku Entity Framework Core.                    |
| SQL-cache                                         | Nástroje příkazového řádku systému SQL Server mezipaměti.                         |
| [tajné klíče uživatelů](/aspnet/core/security/app-secrets) | Slouží ke správě tajných kódů uživatelů vývoje.                            |
| [Sledování](/aspnet/core/tutorials/dotnet-watch)      | Spustí se soubor sledování, které se spustí příkaz, když se změní soubory. |

Další informace o jednotlivých nástrojích, zadejte `dotnet <tool-name> --help`.

## <a name="examples"></a>Příklady

Vytvoří novou konzolovou aplikaci .NET Core:

`dotnet new console`

Obnovte závislosti pro dané aplikace:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Sestavení projektu a jeho závislosti v daném adresáři:

`dotnet build`

Spustit aplikaci knihovny DLL, jako například `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Proměnné prostředí

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Primární balíček mezipaměti. Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.

`DOTNET_SERVICING`

Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu. Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí). V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí). Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.

`DOTNET_MULTILEVEL_LOOKUP`

Určuje, zda modul runtime .NET Core, sdílené architektuře nebo sady SDK jsou vyřešené z globálního místa. Pokud není nastavená, použije se výchozí `true`. Nastavte na `false` se vyřešit z globálního místa a mají izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijímány). Další informace o víceúrovňových vyhledávání najdete v tématu [víceúrovňovými SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Zakáže podverze Posunutí vpřed, pokud nastavit `0`. Další informace najdete v tématu [posunout vpřed](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Primární balíček mezipaměti. Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.

`DOTNET_SERVICING`

Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu. Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí). V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí). Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.

`DOTNET_MULTILEVEL_LOOKUP`

Určuje, zda modul runtime .NET Core, sdílené architektuře nebo sady SDK jsou vyřešené z globálního místa. Pokud není nastavená, použije se výchozí `true`. Nastavte na `false` se vyřešit z globálního místa a mají izolované instalace .NET Core (hodnoty `0` nebo `false` jsou přijímány). Další informace o víceúrovňových vyhledávání najdete v tématu [víceúrovňovými SharedFX vyhledávání](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Primární balíček mezipaměti. Pokud není nastavená, použije se výchozí `$HOME/.nuget/packages` v systému Unix nebo `%HOME%\NuGet\Packages` na Windows.

`DOTNET_SERVICING`

Určuje umístění index údržby pro použití sdílené hostitele při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, zda data o využití nástroje .NET Core je shromažďovat a odesílat do Microsoftu. Nastavte na `true` odhlásit funkce telemetrie (hodnoty `true`, `1`, nebo `yes` přijetí). V opačném případě nastavte na `false` do funkce telemetrie (hodnoty `false`, `0`, nebo `no` přijetí). Pokud není nastavený, výchozí hodnota je `false` a funkce telemetrie je aktivní.

---
