---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240867"
---
# <a name="dotnet-command"></a>dotnet – příkaz

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Název

`dotnet` – obecný ovladač pro .NET Core CLI.

## <a name="synopsis"></a>Stručný obsah

Chcete-li získat informace o dostupných příkazech a prostředí:

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

Spuštění příkazu (vyžaduje instalaci sady SDK):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

Spuštění aplikace:

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward` je k dispozici od verze .NET Core 3. x. Použijte `--roll-forward-on-no-candidate-fx` pro .NET Core 2. x.

## <a name="description"></a>Popis

Příkaz `dotnet` má dvě funkce:

- Poskytuje příkazy pro práci s projekty .NET Core.

  Například [`dotnet build`](dotnet-build.md) sestavit projekt. Každý příkaz definuje vlastní parametry a argumenty. Všechny příkazy podporují možnost `--help` pro tisk stručné dokumentace k použití příkazu.

- Spouští aplikace .NET Core.

  Zadejte cestu k souboru aplikace `.dll` pro spuštění aplikace. Například `dotnet myapp.dll` spouští aplikaci `myapp`. Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .

## <a name="options"></a>Možnosti

K dispozici jsou různé možnosti `dotnet` samostatně, pro spuštění příkazu a pro spuštění aplikace.

### <a name="options-for-dotnet-by-itself"></a>Možnosti pro dotnet samotné

Následující možnosti jsou `dotnet` samotné. například `dotnet --info`. Tisknou informace o daném prostředí.

- **`--info`**

  Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.

- **`--version`**

  Vytiskne verzi .NET Core SDK, která se používá.

- **`--list-runtimes`**

  Vytiskne seznam nainstalovaných modulů runtime .NET Core.

- **`--list-sdks`**

  Vytiskne seznam nainstalovaných sad SDK .NET Core.

- **`-h|--help`**

  Vytiskne seznam dostupných příkazů.

### <a name="sdk-options-for-running-a-command"></a>Možnosti sady SDK pro spuštění příkazu

Následující možnosti jsou pro `dotnet` s příkazem. například `dotnet build --help`.

- **`-d|--diagnostics`**

  Povolí výstup diagnostiky.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`a `diag[nostic]`. Nepodporováno v každém příkazu. Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.

- **`-h|--help`**

  Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help`.

- **`command options`**

  Každý příkaz definuje možnosti specifické pro tento příkaz. Seznam dostupných možností najdete v tématu konkrétní příkazová stránka.

### <a name="runtime-options"></a>Možnosti modulu runtime

Když `dotnet` spouští aplikaci, jsou k dispozici následující možnosti. například `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Cesta obsahující zásady a sestavení pro zjišťování k testování

- **`--additional-deps <PATH>`**

  Cesta k dodatečnému souboru *. DEPS. JSON* . Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.

- **`--fx-version <VERSION>`**

  Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace

- **`--runtimeconfig`**

  Cesta k souboru *runtimeconfig. JSON* . Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení běhu. Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`** **k dispozici v sadě .NET Core 2. x SDK.**

  Definuje chování v případě, že požadovaná sdílená architektura není k dispozici. `N` může být:

  - `0` – zakažte u sebe i menší verzi.
  - `1` – předejte se k dílčí verzi, ale ne k hlavní verzi. Toto je výchozí chování.
  - `2` – předejte se do menších a hlavních verzí.

   Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.

- **`--roll-forward <SETTING>`** **k dispozici od .NET Core SDK 3,0.**

  Určuje, jak se v aplikaci aplikuje posunutí. `SETTING` může být jedna z následujících hodnot. Pokud není zadaný, `Minor` je výchozí hodnota.

  - `LatestPatch` – vraťte se k nejvyšší verzi opravy. Tím se zakáže dílčí verze s posunem.
  - v případě, že chybí požadovaná podverze, `Minor` – převeďte na nejnižší nižší verzi. Pokud je k dispozici požadovaná dílčí verze, použije se zásada LatestPatch.
  - Pokud chybí požadovaná hlavní verze, `Major` – převeďte na nejnižší vyšší hlavní verzi a nejnižší podverzi. Pokud je k dispozici požadovaná hlavní verze, použije se vedlejší zásada.
  - `LatestMinor` – převeďte do nejvyšší dílčí verze, i když je k dispozici požadovaná dílčí verze. Určeno pro scénáře hostování součástí.
  - `LatestMajor` – převeďte do nejvyšší hlavní a nejvyšší dílčí verze, a to i v případě, že je k dispozici požadovaná hlavní verze. Určeno pro scénáře hostování součástí.
  - `Disable` – nezavádět do popředí. Vytvoří se jenom vazba na určenou verzi. Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám. Tato hodnota se doporučuje jenom pro testování.

S výjimkou `Disable`budou všechna nastavení využívat nejvyšší dostupnou verzi opravy.

Chování při posunutí nahoru lze také nakonfigurovat v vlastnost souboru projektu, vlastnosti konfiguračního souboru modulu runtime a proměnné prostředí. Další informace najdete v tématu o [zavedení modulu runtime hlavní verze – posunutí](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>Příkazy dotnet

### <a name="general"></a>Obecné

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

### <a name="global-tool-path-and-local-tools-commands"></a>Příkazy globálních nástrojů, nástrojů a cest a místních nástrojů

Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku. Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou. Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje. Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md). Nástroje pro globální a cestu nástrojů jsou k dispozici od .NET Core SDK 2,1. K dispozici jsou místní nástroje od .NET Core SDK 3,0.

Příkaz | Funkce
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Nainstaluje nástroj na váš počítač.
[dotnet tool list](dotnet-tool-list.md) | Zobrazí seznam všech nástrojů, které jsou aktuálně nainstalované na vašem počítači, na základě globálních nástrojů, nástrojů a cest.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstaluje nástroj z počítače.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje nástroj, který je nainstalovaný na vašem počítači.

### <a name="additional-tools"></a>Další nástroje

Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí `DotnetCliToolReference` jsou nyní k dispozici jako součást .NET Core SDK. Tyto nástroje jsou uvedené v následující tabulce:

| Nástroj                                              | Funkce                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| vývoj – certifikáty                                         | Vytvoří a spravuje vývojové certifikáty.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core nástroje příkazového řádku.                    |
| sql-cache                                         | Nástroje příkazového řádku pro SQL Server cache                         |
| [uživatel – tajné klíče](/aspnet/core/security/app-secrets) | Spravuje tajné klíče uživatele.                            |
| [sledovací](/aspnet/core/tutorials/dotnet-watch)      | Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní. |

Další informace o jednotlivých nástrojích získáte, když zadáte `dotnet <tool-name> --help`.

## <a name="examples"></a>Příklady

Vytvořte novou konzolovou aplikaci .NET Core:

```dotnetcli
dotnet new console
```

Sestavení projektu a jeho závislostí v daném adresáři:

```dotnetcli
dotnet build
```

Spuštění aplikace:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Proměnné prostředí

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Určuje umístění modulů runtime .NET Core, pokud nejsou nainstalovány ve výchozím umístění. Výchozí umístění ve Windows je `C:\Program Files\dotnet`. Výchozí umístění v systému Linux a macOS je `/usr/share/dotnet`. Tato proměnná prostředí se používá jenom při spouštění aplikací prostřednictvím generovaných spustitelných souborů (apphosts). místo toho se používá `DOTNET_ROOT(x86)`, když se na 64 operačním systému spouští 32 spustitelný soubor.

- `DOTNET_PACKAGES`

  Složka globálních balíčků. Pokud není nastavené, použije se výchozí nastavení `~/.nuget/packages` v systému UNIX nebo `%userprofile%\.nuget\packages` ve Windows.

- `DOTNET_SERVICING`

  Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu. Nastavte na `true` pro výslovný souhlas funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté). Jinak nastavte `false` tak, aby se přihlásil k funkcím telemetrie (hodnoty `false`, `0`nebo přijaté `no`). Pokud není nastavená, výchozí hodnota je `false` a funkce telemetrie je aktivní.

- `DOTNET_MULTILEVEL_LOOKUP`

  Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění. Pokud není nastavené, použije se výchozí hodnota 1 (logická `true`). Nastavte na 0 (logický `false`), aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core. Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD` **k dispozici počínaje verzí .NET Core 3. x SDK.**

  Určuje chování při posunu nahoru. Další informace najdete v části `--roll-forward` možnosti výše v tomto článku.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **k dispozici v sadě .NET Core 2. x SDK.**

  Zakáže posunutí dílčí verze, pokud je nastaveno na `0`. Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.

- `DOTNET_CLI_UI_LANGUAGE`

  Nastaví jazyk uživatelského rozhraní CLI pomocí hodnoty národního prostředí, například `en-us`. Podporované hodnoty jsou stejné jako u sady Visual Studio. Další informace najdete v části o změně jazyka instalačního programu v [dokumentaci k instalaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Použijí se pravidla správce prostředků .NET, takže nemusíte vybírat přesnou shodu&mdash;můžete také vybrat následníky ve stromu `CultureInfo`. Například pokud nastavíte `fr-CA`, rozhraní příkazového řádku nalezne a použije překlady `fr`. Pokud ho nastavíte na jazyk, který není podporován, rozhraní příkazového řádku se vrátí do angličtiny.

- `DOTNET_DISABLE_GUI_ERRORS`

  U generovaných spustitelných souborů s povoleným grafickým uživatelským rozhraním – zakáže dialogová okna, která obvykle zobrazuje určité třídy chyb. Zapisuje pouze do `stderr` a v těchto případech skončí.
  
- `DOTNET_ADDITIONAL_DEPS`

  Ekvivalent možnosti CLI `--additional-deps`.

- `DOTNET_RUNTIME_ID`

  Přepíše zjištěný identifikátor RID.

- `DOTNET_SHARED_STORE`

  Umístění sdíleného úložiště, na které se rozlišení sestavení vrátí v některých případech.

- `DOTNET_STARTUP_HOOKS`

  Seznam sestavení pro načtení a spuštění spouštěcích háky z.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Řídí trasování diagnostiky z komponent hostování, například `dotnet.exe`, `hostfxr`a `hostpolicy`.

## <a name="see-also"></a>Viz také

- [Běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Nastavení konfigurace runtime .NET Core](../run-time-config/index.md)
