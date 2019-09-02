---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI nástroje) a jeho využití.
ms.date: 06/04/2018
ms.openlocfilehash: 61542a3fff8bba6e2c3e55a4db5a746620d79ca1
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202506"
---
# <a name="dotnet-command"></a>dotnet – příkaz

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet`– Nástroj pro správu zdrojového kódu a binárních souborů .NET.

## <a name="synopsis"></a>Stručný obsah

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>Popis

`dotnet`je nástroj pro správu zdrojového kódu a binárních souborů .NET. Zpřístupňuje příkazy, které provádějí konkrétní úkoly, [`dotnet build`](dotnet-build.md) jako například a. [`dotnet run`](dotnet-run.md) Každý příkaz definuje své vlastní argumenty. Typ `--help` za každým příkazem pro přístup k krátké dokumentaci k nápovědě.

`dotnet`lze použít ke spouštění aplikací zadáním knihovny DLL aplikace, například `dotnet myapp.dll`. Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .

## <a name="options"></a>Možnosti

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`--additional-deps <PATH>`

Cesta k dodatečnému souboru *. DEPS. JSON* .

`--additionalprobingpath <PATH>`

Cesta obsahující zásady a sestavení pro zjišťování k testování

`--depsfile`

Cesta k souboru *DEPS. JSON* .

Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení. Další informace o tomto souboru najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.

`-d|--diagnostics`

Povolí výstup diagnostiky.

`--fx-version <VERSION>`

Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace

`-h|--help`

Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`. `dotnet --help`vytiskne seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.

`--list-runtimes`

Zobrazí nainstalované moduly runtime .NET Core.

`--list-sdks`

Zobrazí nainstalované sady SDK .NET Core.

`--roll-forward-on-no-candidate-fx <N>`

Definuje chování v případě, že požadovaná sdílená architektura není k dispozici. `N` může být:
* `0`– Zakažte u sebe i menší verzi.
* `1`– Navýšení se dopředá na podverzi, ale ne na hlavní verzi. Toto je výchozí chování.
* `2`– Posunutí posunu k dílčím a hlavním verzím

 Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.

`--runtimeconfig`

Cesta k souboru *runtimeconfig. JSON* .

Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]` Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.

`--version`

Vytiskne verzi .NET Core SDK, která se používá.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`--additional-deps <PATH>`

Cesta k dodatečnému souboru *. DEPS. JSON* .

`--additionalprobingpath <PATH>`

Cesta obsahující zásady a sestavení pro zjišťování k testování

`--depsfile`

Cesta k souboru *DEPS. JSON* .

Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení. Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-d|--diagnostics`

Povolí výstup diagnostiky.

`--fx-version <VERSION>`

Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace

`-h|--help`

Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`. `dotnet --help`vytiskne seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.

`--roll-forward-on-no-candidate-fx`

 Zakáže posunutí dílčí verze, pokud je nastaveno `0`na. Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.

`--runtimeconfig`

Cesta k souboru *runtimeconfig. JSON* .

Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime. Další podrobnosti najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]` Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.

`--version`

Vytiskne verzi .NET Core SDK, která se používá.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Cesta obsahující zásady a sestavení pro zjišťování k testování

`--depsfile`

Cesta k souboru *DEPS. JSON* .

Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení. Další podrobnosti o tomto souboru najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-d|--diagnostics`

Povolí výstup diagnostiky.

`--fx-version <VERSION>`

Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace

`-h|--help`

Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`. `dotnet --help`vytiskne seznam dostupných příkazů.

`--info`

Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.

`--runtimeconfig`

Cesta k souboru *runtimeconfig. JSON* .

Soubor *runtimeconfig. JSON* je konfigurační soubor obsahující konfigurační nastavení modulu runtime. Další podrobnosti najdete v tématu [běhové konfigurační soubory na GitHubu](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-v|--verbosity <LEVEL>`

Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]` `d[etailed]`, a .`diag[nostic]` Nepodporováno v každém příkazu; Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.

`--version`

Vytiskne verzi .NET Core SDK, která se používá.

---

## <a name="dotnet-commands"></a>Příkazy dotnet

### <a name="general"></a>Obecné

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

| Příkaz                                       | Funkce                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Vytvoří aplikaci .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Komunikuje se servery spuštěnými sestavením.                          |
| [dotnet clean](dotnet-clean.md)               | Vyčistit výstupy sestavení.                                                |
| [dotnet help](dotnet-help.md)                 | Zobrazí podrobnější dokumentaci pro příkaz online.           |
| [dotnet migrate](dotnet-migrate.md)           | Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Poskytuje přístup k příkazovému řádku MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicializuje projekt C# nebo F# pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Vytvoří balíček NuGet vašeho kódu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci. |
| [dotnet restore](dotnet-restore.md)           | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)                   | Spustí aplikaci ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)                   | Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.       |
| [dotnet restore](dotnet-store.md)               | Ukládá sestavení do úložiště balíčků modulu runtime.                     |
| [dotnet test](dotnet-test.md)                 | Spustí testy pomocí nástroje Test Runner.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Vytvoří aplikaci .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Vyčistit výstupy sestavení.                                              |
| [dotnet help](dotnet-help.md)       | Zobrazí podrobnější dokumentaci pro příkaz online.           |
| [dotnet migrate](dotnet-migrate.md) | Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Poskytuje přístup k příkazovému řádku MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicializuje projekt C# nebo F# pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)       | Vytvoří balíček NuGet vašeho kódu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci. |
| [dotnet restore](dotnet-restore.md) | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)         | Spustí aplikaci ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)         | Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.       |
| [dotnet restore](dotnet-store.md)     | Ukládá sestavení do úložiště balíčků modulu runtime.                     |
| [dotnet test](dotnet-test.md)       | Spustí testy pomocí nástroje Test Runner.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| Příkaz                             | Funkce                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Vytvoří aplikaci .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Vyčistit výstupy sestavení.                                              |
| [dotnet migrate](dotnet-migrate.md) | Migruje platný projekt verze Preview 2 na projekt .NET Core SDK 1,0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Poskytuje přístup k příkazovému řádku MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicializuje projekt C# nebo F# pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)       | Vytvoří balíček NuGet vašeho kódu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci. |
| [dotnet restore](dotnet-restore.md) | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)         | Spustí aplikaci ze zdroje.                                   |
| [dotnet run](dotnet-sln.md)         | Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.       |
| [dotnet test](dotnet-test.md)       | Spustí testy pomocí nástroje Test Runner.                                     |

---

### <a name="project-references"></a>Odkazy na projekty

Příkaz | Funkce
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Přidá odkaz na projekt.
[dotnet list reference](dotnet-list-reference.md) | Vypíše odkazy na projekt.
[dotnet remove reference](dotnet-remove-reference.md) | Odebere odkaz na projekt.

### <a name="nuget-packages"></a>Balíčky NuGet

Příkaz | Funkce
--- | ---
[dotnet add package](dotnet-add-package.md) | Přidá balíček NuGet.
[dotnet remove package](dotnet-remove-package.md) | Odebere balíček NuGet.

### <a name="nuget-commands"></a>Příkazy NuGet

Příkaz | Funkce
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Odstraní nebo zruší výpis balíčku ze serveru.
[dotnet nuget locals](dotnet-nuget-locals.md) | Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.
[dotnet nuget push](dotnet-nuget-push.md) | Odešle balíček na server a publikuje ho.

### <a name="global-tools-commands"></a>Příkazy globálních nástrojů

K dispozici jsou [globální nástroje .NET Core](global-tools.md) od .NET Core SDK 2.1.300:

Příkaz | Funkce
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Nainstaluje na váš počítač globální nástroj.
[dotnet tool list](dotnet-tool-list.md) | Zobrazí seznam všech globálních nástrojů, které jsou aktuálně nainstalované ve výchozím adresáři na vašem počítači nebo v zadané cestě.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstaluje z počítače globální nástroj.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje na svém počítači globální nástroj.

### <a name="additional-tools"></a>Další nástroje

Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé `DotnetCliToolReference` projekty pomocí, jako součást .NET Core SDK. Tyto nástroje jsou uvedené v následující tabulce:

| Nástroj                                              | Funkce                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| vývoj – certifikáty                                         | Vytvoří a spravuje vývojové certifikáty.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core nástroje příkazového řádku.                    |
| sql-cache                                         | Nástroje příkazového řádku pro SQL Server cache                         |
| [uživatel – tajné klíče](/aspnet/core/security/app-secrets) | Spravuje tajné klíče uživatele.                            |
| [sledovací](/aspnet/core/tutorials/dotnet-watch)      | Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní. |

Další informace o jednotlivých nástrojích získáte tak `dotnet <tool-name> --help`, že zadáte.

## <a name="examples"></a>Příklady

Vytvoří novou konzolovou aplikaci .NET Core:

`dotnet new console`

Obnovit závislosti pro danou aplikaci:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Sestavení projektu a jeho závislostí v daném adresáři:

`dotnet build`

Spusťte knihovnu DLL aplikace, například `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Proměnné prostředí

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2,1](#tab/netcore21)

`DOTNET_PACKAGES`

Složka globálních balíčků. Pokud není nastavená, použije se `~/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.

`DOTNET_SERVICING`

Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu. Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout). V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty). Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.

`DOTNET_MULTILEVEL_LOOKUP`

Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění. Pokud není nastaven, použije se výchozí `true`hodnota. Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false` Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Zakáže posunutí dílčí verze, pokud je nastaveno `0`na. Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2,0](#tab/netcore20)

`DOTNET_PACKAGES`

Mezipaměť primárního balíčku. Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.

`DOTNET_SERVICING`

Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu. Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout). V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty). Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.

`DOTNET_MULTILEVEL_LOOKUP`

Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění. Pokud není nastaven, použije se výchozí `true`hodnota. Nastavte na hodnotu neřešitelné z globálního umístění a používejte izolované instalace rozhraní .NET Core ( `0` hodnoty `false` nebo jsou přijatelné). `false` Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Mezipaměť primárního balíčku. Pokud není nastavená, použije se `$HOME/.nuget/packages` ve výchozím nastavení `%userprofile%\.nuget\packages` v systému UNIX nebo Windows.

`DOTNET_SERVICING`

Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu. Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijmout). V opačném případě `false` nastavte, aby se přihlásil k funkcím `0`telemetrie ( `no` hodnoty `false`, nebo přijaty). Pokud není nastavená, je výchozí `false` nastavení a funkce telemetrie je aktivní.

---

## <a name="see-also"></a>Viz také:

- [Běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
