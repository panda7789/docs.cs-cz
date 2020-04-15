---
title: dotnet, příkaz
description: Další informace o příkazu dotnet (obecný ovladač pro rozhraní příkazu .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: 9446808d7f23d762c7a3c8a58252664fc5dade5b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389600"
---
# <a name="dotnet-command"></a>dotnet, příkaz

**Tento článek se týká:** ✔️ .NET Core 2.1 SDK a novější verze

## <a name="name"></a>Name (Název)

`dotnet`- Obecný ovladač pro rozhraní CLI jádra .NET.

## <a name="synopsis"></a>Synopse

Získání informací o dostupných příkazech a prostředí:

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

`--roll-forward`je k dispozici od rozhraní .NET Core 3.x. Slouží `--roll-forward-on-no-candidate-fx` pro rozhraní .NET Core 2.x.

## <a name="description"></a>Popis

Příkaz `dotnet` má dvě funkce:

- Poskytuje příkazy pro práci s projekty .NET Core.

  Například [`dotnet build`](dotnet-build.md) vytvoří projekt. Každý příkaz definuje své vlastní možnosti a argumenty. Všechny příkazy `--help` podporují možnost tisku stručné dokumentace o použití příkazu.

- Spouští aplikace .NET Core.

  Určíte cestu k `.dll` souboru aplikace pro spuštění aplikace.  Spuštění aplikace znamená najít a spustit vstupní bod, což je v `Main` případě konzolových aplikací metoda. Například `dotnet myapp.dll` spustí `myapp` aplikaci. Informace o možnostech nasazení najdete v tématu [Nasazení aplikace .NET Core.](../deploying/index.md)

## <a name="options"></a>Možnosti

Různé možnosti `dotnet` jsou k dispozici samostatně, pro spuštění příkazu a pro spuštění aplikace.

### <a name="options-for-dotnet-by-itself"></a>Možnosti pro dotnet sám o sobě

Následující možnosti `dotnet` jsou samy o sobě. Například, `dotnet --info`. Tisknou informace o životním prostředí.

- **`--info`**

  Vytiskne podrobné informace o instalaci jádra .NET a prostředí počítače, jako je například aktuální operační systém, a potvrdí sha verze .NET Core.

- **`--version`**

  Vytiskne verzi sady .NET Core SDK, která se používá.

- **`--list-runtimes`**

  Vytiskne seznam nainstalovaných runčasů jádra .NET. Verze sady X86 sady SDK obsahuje pouze za běhu x86 a verze sady SDK x64 uvádí pouze za běhu x64.

- **`--list-sdks`**

  Vytiskne seznam nainstalovaných sad SDK jádra .NET.

- **`-h|--help`**

  Vytiskne seznam dostupných příkazů.

### <a name="sdk-options-for-running-a-command"></a>Možnosti sady SDK pro spuštění příkazu

Následující možnosti `dotnet` jsou pro s příkazem. Například, `dotnet build --help`.

- **`-d|--diagnostics`**

  Umožňuje diagnostický výstup.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty `q[uiet]` `m[inimal]`jsou `n[ormal]` `d[etailed]`, `diag[nostic]`, , a . Není podporováno v každém příkazu. Chcete-li zjistit, zda je tato možnost k dispozici, podívejte se na konkrétní příkazovou stránku.

- **`-h|--help`**

  Vytiskne dokumentaci pro daný `dotnet build --help`příkaz, například .

- **`command options`**

  Každý příkaz definuje možnosti specifické pro tento příkaz. Seznam dostupných možností naleznete na konkrétní stránce příkazů.

### <a name="runtime-options"></a>Možnosti běhu

Následující možnosti jsou `dotnet` k dispozici při spuštění aplikace. Například, `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Cesta obsahující sondování zásady a sestavení pro sondu.

- **`--additional-deps <PATH>`**

  Cesta k dalšímu souboru *.deps.json.* Soubor *deps.json* obsahuje seznam závislostí, závislostí kompilace a informací o verzi, které se používají k řešení konfliktů sestavení. Další informace najdete [v tématu Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.

- **`--fx-version <VERSION>`**

  Verze runtime .NET Core, která se má použít ke spuštění aplikace.

- **`--runtimeconfig`**

  Cesta k souboru *runtimeconfig.json.* Soubor *runtimeconfig.json* je konfigurační soubor, který obsahuje nastavení běhu. Další informace naleznete v [tématu Nastavení konfigurace rozhraní .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`****K dispozici v sdk .NET Core 2.x.**

  Definuje chování, když není k dispozici požadovaná sdílená architektura. `N`může být:

  - `0`- Zakázat i menší verze roll vpřed.
  - `1`- Roll vpřed na dílčí verzi, ale ne na hlavní verzi. Toto je výchozí chování.
  - `2`- Roll vpřed na menší a hlavní verze.

   Další informace naleznete v [tématu Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`****K dispozici počínaje sadou .NET Core SDK 3.0.**

  Určuje, jak se v aplikaci použije posun vpřed. Může `SETTING` být jedna z následujících hodnot. Pokud není `Minor` zadán, je výchozí.

  - `LatestPatch`- Přetočte se dopředu na nejvyšší verzi opravy. Tím se zakáže dílčí verze posunout vpřed.
  - `Minor`- Převrátit na nejnižší vyšší dílčí verze, pokud je požadována dílčí verze chybí. Pokud je k dispozici požadovaná dílčí verze, použije se zásada LatestPatch.
  - `Major`- Roll vpřed na nejnižší vyšší hlavní verze, a nejnižší dílčí verze, pokud požadované hlavní verze chybí. Pokud je k dispozici požadovaná hlavní verze, použije se zásada Vedlejší.
  - `LatestMinor`- Převrátit na nejvyšší dílčí verzi, a to i v případě, že je požadována dílčí verze je k dispozici. Určeno pro scénáře hostování komponent.
  - `LatestMajor`- Převrátit na nejvyšší hlavní a nejvyšší dílčí verze, i když požadované hlavní je přítomen. Určeno pro scénáře hostování komponent.
  - `Disable`- Neotáčejte se dopředu. Spojte se pouze se zadanou verzí. Tato zásada se nedoporučuje pro obecné použití, protože zakáže možnost převést na nejnovější opravy. Tato hodnota je doporučena pouze pro testování.

S výjimkou `Disable`aplikace budou všechna nastavení používat nejvyšší dostupnou verzi opravy.

Chování posunout vpřed lze také nakonfigurovat ve vlastnosti souboru projektu, vlastnosti konfiguračního souboru za běhu a proměnné prostředí. Další informace naleznete v [tématu Hlavní verze runtime posun vpřed](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>Příkazy dotnet

### <a name="general"></a>Obecné

| Příkaz                                       | Funkce                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Vytvoří aplikaci .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Spolupracuje se servery spuštěnými sestavením.                          |
| [dotnet clean](dotnet-clean.md)               | Čisté výstupy sestavení.                                                |
| [dotnet help](dotnet-help.md)                 | Zobrazuje podrobnější dokumentaci online pro příkaz.           |
| [dotnet migrate](dotnet-migrate.md)           | Přenese platný projekt Preview 2 do projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Poskytuje přístup k příkazovému řádku MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicializuje projekt C# nebo F# pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Vytvoří balíček NuGet vašeho kódu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje aplikaci závislou na rozhraní .NET nebo samostatnou aplikaci. |
| [dotnet restore](dotnet-restore.md)           | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)                   | Spustí aplikaci ze zdroje.                                   |
| [dotnet sln](dotnet-sln.md)                   | Možnosti pro přidání, odebrání a seznam projektů v souboru řešení.       |
| [dotnet store](dotnet-store.md)               | Ukládá sestavení v runtime balíček úložiště.                     |
| [dotnet test](dotnet-test.md)                 | Spustí testy pomocí testovacího běhu.                                     |

### <a name="project-references"></a>Odkazy na projekty

Příkaz | Funkce
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Přidá odkaz na projekt.
[dotnet list reference](dotnet-list-reference.md) | Zobrazí seznam odkazů na projekt.
[dotnet remove reference](dotnet-remove-reference.md) | Odebere odkaz na projekt.

### <a name="nuget-packages"></a>Balíčky NuGet

Příkaz | Funkce
--- | ---
[dotnet add package](dotnet-add-package.md) | Přidá balíček NuGet.
[dotnet remove package](dotnet-remove-package.md) | Odebere balíček NuGet.

### <a name="nuget-commands"></a>Příkazy NuGet

Příkaz | Funkce
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Odstraní nebo odřadí seznam balíčku ze serveru.
[dotnet nuget push](dotnet-nuget-push.md) | Odešle balíček na server a publikuje jej.
[dotnet nuget locals](dotnet-nuget-locals.md) | Vymaže nebo zobrazí seznam místních prostředků NuGet, jako je například mezipaměť http-request, dočasná mezipaměť nebo globální balíček pro celý počítač.
[dotnet nuget add source](dotnet-nuget-add-source.md) | Přidá zdroj NuGet.
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | Zakáže zdroj NuGet.
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | Povolí zdroj NuGet.
[dotnet nuget list source](dotnet-nuget-list-source.md) | Zobrazí seznam všech nakonfigurovaných zdrojů NuGet.
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | Odebere zdroj NuGet.
[dotnet nuget update source](dotnet-nuget-update-source.md) | Aktualizuje zdroj NuGet.

### <a name="global-tool-path-and-local-tools-commands"></a>Příkazy globálních nástrojů, cest nástrojů a místních nástrojů

Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku. Můžete psát nástroje sami nebo instalovat nástroje napsané třetími stranami. Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje. Další informace naleznete v tématu [Přehled nástrojů .NET Core](global-tools.md). Globální nástroje a nástroje cesta jsou k dispozici počínaje .NET Core SDK 2.1. Místní nástroje jsou k dispozici počínaje .NET Core SDK 3.0.

Příkaz | Funkce
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Nainstaluje do počítače nástroj.
[dotnet tool list](dotnet-tool-list.md) | Zobrazí seznam všech globálních, nástrojových cest nebo místních nástrojů, které jsou v počítači aktuálně nainstalovány.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstaluje nástroj ze zařízení.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje nástroj, který je nainstalován v počítači.

### <a name="additional-tools"></a>Další nástroje

Počínaje .NET Core SDK 2.1.300, počet nástrojů, které byly k `DotnetCliToolReference` dispozici pouze na základě projektu pomocí jsou nyní k dispozici jako součást .NET Core SDK. Tyto nástroje jsou uvedeny v následující tabulce:

| Nástroj                                              | Funkce                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Vytváří a spravuje vývojové certifikáty.                |
| [Ef](/ef/core/miscellaneous/cli/dotnet)           | Nástroje příkazového řádku Core entity Framework.                    |
| sql-cache                                         | Nástroje příkazového řádku mezipaměti serveru SQL Server.                         |
| [uživatelské tajemství](/aspnet/core/security/app-secrets) | Spravuje tajné kódy uživatelů vývoje.                            |
| [Sledovat](/aspnet/core/tutorials/dotnet-watch)      | Spustí sledovací proces souboru, který spustí příkaz při změně souborů. |

Další informace o jednotlivých `dotnet <tool-name> --help`nástrojích získáte zadáním příkazu .

## <a name="examples"></a>Příklady

Vytvořte novou aplikaci konzoly .NET Core:

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

  Určuje umístění runčasů jádra .NET, pokud nejsou nainstalovány ve výchozím umístění. Výchozí umístění v `C:\Program Files\dotnet`systému Windows je . Výchozí umístění na Linuxu a `/usr/share/dotnet`macOS je . Tato proměnná prostředí se používá pouze při spouštění aplikací prostřednictvím generovaných spustitelných souborů (apphosts). `DOTNET_ROOT(x86)`se používá místo toho při spuštění 32bitového spustitelného souboru v 64bitovém osu.

- `DOTNET_PACKAGES`

  Složka globálních balíčků. Pokud není nastavena, `~/.nuget/packages` je výchozí `%userprofile%\.nuget\packages` na Unix nebo na Windows.

- `DOTNET_SERVICING`

  Určuje umístění indexu obsluhy, který má sdílený hostitel použít při načítání za běhu.

- `DOTNET_NOLOGO`

  Určuje, zda se při prvním spuštění zobrazí uvítání a telemetrické zprávy .NET Core. Nastaví `true` ztlumení těchto zpráv `true` `1`(hodnoty `yes` , nebo `false` přijaté) nebo `false` `0`na `no` povolit (hodnoty , nebo přijaté). Pokud není nastavena, `false` výchozí je a zprávy se zobrazí při prvním spuštění. Všimněte si, že tento příznak `DOTNET_CLI_TELEMETRY_OPTOUT` nemá žádný vliv na telemetrii (viz pro odhlášení odesílání telemetrie).

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Určuje, zda jsou data o použití nástrojů .NET Core shromažďována a odesílána společnosti Microsoft. Nastavte `true` na odhlášení z funkce telemetrie (hodnoty `true`, `1`nebo `yes` přijaté). V opačném `false` případě nastavte na opt-li `false` `0`do `no` funkce telemetrie (hodnoty , nebo přijat). Pokud není nastavena, `false` výchozí je a funkce telemetrie je aktivní.

- `DOTNET_MULTILEVEL_LOOKUP`

  Určuje, zda jsou z globálního umístění vyřešeny zaběhu .NET Core, sdílené ho frameworku nebo sdk. Pokud není nastavena, je výchozí `true`hodnota 1 (logické). Nastavte 0 (logické) `false`není vyřešit z globálního umístění a mají izolované instalace .NET Core. Další informace o víceúrovňovém vyhledávání naleznete v [tématu Vyhledávání SharedFX na více úrovních](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**K dispozici počínaje sadou .NET Core 3.x SDK.**

  Určuje chování posunout vpřed. Další informace naleznete `--roll-forward` v této možnosti dříve v tomto článku.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**K dispozici v sdk .NET Core 2.x.**

  Zakáže dílčí verze posunout `0`vpřed, pokud je nastavena na . Další informace naleznete v [tématu Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Nastaví jazyk rozhraní rozhraní rozhraní SEkatelu `en-us`pomocí hodnoty národního prostředí, například . Podporované hodnoty jsou stejné jako pro Visual Studio. Další informace naleznete v části o změně jazyka instalačního programu v [dokumentaci k instalaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Platí pravidla správce prostředků .NET, takže nemusíte vybírat přesnou shodu,&mdash; `CultureInfo` můžete také vybrat potomky ve stromu. Pokud ji například nastavíte na `fr-CA`, vykázané nastavení matné a konstatování překlady vyhledá a použije. `fr` Pokud jej nastavíte na jazyk, který není podporován, rozhraní se konkretním rozhraním SE vrátí zpět do angličtiny.

- `DOTNET_DISABLE_GUI_ERRORS`

  Pro gui-umožnil generované spustitelné soubory - zakáže dialogové okno, které obvykle ukazuje pro určité třídy chyb. Pouze zapisuje `stderr` a ukončí v těchto případech.
  
- `DOTNET_ADDITIONAL_DEPS`

  Ekvivalentní možnost ipříkazové konzace `--additional-deps`.

- `DOTNET_RUNTIME_ID`

  Přepíše zjištěný rid.

- `DOTNET_SHARED_STORE`

  Umístění "sdílenéúložiště", které rozlišení sestavení spadá zpět do v některých případech.

- `DOTNET_STARTUP_HOOKS`

  Seznam sestavení pro načtení a spuštění spouštěcích háků z.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Řídí diagnostiku trasování z hostitelských `dotnet.exe`součástí, například , `hostfxr`a `hostpolicy`.

## <a name="see-also"></a>Viz také

- [Konfigurační soubory runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Nastavení konfigurace jádra .NET](../run-time-config/index.md)
