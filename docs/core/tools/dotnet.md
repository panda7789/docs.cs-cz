---
title: dotnet – příkaz
description: Přečtěte si o příkazu dotnet (obecný ovladač pro .NET Core CLI) a jeho použití.
ms.date: 02/13/2020
ms.openlocfilehash: 88e92b3ff5e8f68b980015a817434dd2d67df93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378844"
---
# <a name="dotnet-command"></a>dotnet – příkaz

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Name

`dotnet`– Obecný ovladač pro .NET Core CLI.

## <a name="synopsis"></a>Stručný obsah

Chcete-li získat informace o dostupných příkazech a prostředí:

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

Spuštění příkazu (vyžaduje instalaci sady SDK):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

Spuštění aplikace:

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward`je k dispozici od verze .NET Core 3. x. Používá se `--roll-forward-on-no-candidate-fx` pro .NET Core 2. x.

## <a name="description"></a>Popis

`dotnet`Příkaz má dvě funkce:

- Poskytuje příkazy pro práci s projekty .NET Core.

  Například [`dotnet build`](dotnet-build.md) sestavení projektu. Každý příkaz definuje vlastní parametry a argumenty. Všechny příkazy podporují `--help` možnost tisku stručné dokumentace k použití příkazu.

- Spouští aplikace .NET Core.

  Zadejte cestu k `.dll` souboru aplikace pro spuštění aplikace.  Pro spuštění aplikace znamená, že se má vyhledat a spustit vstupní bod, který je v případě konzolových aplikací `Main` metoda. Například `dotnet myapp.dll` spustí `myapp` aplikaci. Další informace o možnostech nasazení najdete v tématu [nasazení aplikace .NET Core](../deploying/index.md) .

## <a name="options"></a>Možnosti

K dispozici jsou různé možnosti pro `dotnet` spuštění příkazu a pro spuštění aplikace.

### <a name="options-for-dotnet-by-itself"></a>Možnosti pro dotnet samotné

Následující možnosti jsou samotné pro `dotnet` sebe sama. Například, `dotnet --info`. Tisknou informace o daném prostředí.

- **`--info`**

  Vytiskne podrobné informace o instalaci .NET Core a počítačovém prostředí, jako je aktuální operační systém, a potvrzení SHA verze .NET Core.

- **`--version`**

  Vytiskne verzi .NET Core SDK, která se používá.

- **`--list-runtimes`**

  Vytiskne seznam nainstalovaných modulů runtime .NET Core. Verze x86 sady SDK obsahuje jenom modul runtime x86 a verze x64 sady SDK obsahuje jenom technologie runtime x64.

- **`--list-sdks`**

  Vytiskne seznam nainstalovaných sad SDK .NET Core.

- **`-h|--help`**

  Vytiskne seznam dostupných příkazů.

### <a name="sdk-options-for-running-a-command"></a>Možnosti sady SDK pro spuštění příkazu

Následující možnosti jsou pro `dotnet` s příkazem. Například, `dotnet build --help`.

- **`-d|--diagnostics`**

  Povolí výstup diagnostiky.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` . Nepodporováno v každém příkazu. Pokud chcete zjistit, zda je tato možnost k dispozici, zobrazte konkrétní příkazová stránka.

- **`-h|--help`**

  Vytiskne dokumentaci pro daný příkaz, například `dotnet build --help` .

- **`command options`**

  Každý příkaz definuje možnosti specifické pro tento příkaz. Seznam dostupných možností najdete v tématu konkrétní příkazová stránka.

### <a name="runtime-options"></a>Možnosti modulu runtime

Při spuštění aplikace jsou k dispozici následující možnosti `dotnet` . Například, `dotnet myapp.dll --roll-forward Major`.

- **`--additionalprobingpath <PATH>`**

  Cesta obsahující zásady a sestavení pro zjišťování k testování

- **`--additional-deps <PATH>`**

  Cesta k dodatečnému souboru *. DEPS. JSON* . Soubor *DEPS. JSON* obsahuje seznam závislostí, závislosti kompilace a informace o verzi používané k řešení konfliktů sestavení. Další informace najdete v tématu [běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) na GitHubu.

- **`--depsfile <PATH_TO_DEPSFILE>`**

  Cesta k souboru *DEPS. JSON* . Soubor *DEPS. JSON* je konfigurační soubor, který obsahuje informace o závislostech nezbytných ke spuštění aplikace. Tento soubor je vygenerovaný .NET Core SDK.

- **`--runtimeconfig`**

  Cesta k souboru *runtimeconfig. JSON* . Soubor *runtimeconfig. JSON* je konfigurační soubor, který obsahuje nastavení běhu. Další informace najdete v tématu [nastavení konfigurace runtime .NET Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward <SETTING>`****K dispozici od .NET Core SDK 3,0.**

  Určuje, jak se v aplikaci aplikuje posunutí. `SETTING`Může to být jedna z následujících hodnot. Pokud není zadán, `Minor` je výchozí hodnota.

  - `LatestPatch`– Vraťte se k nejvyšší verzi opravy. Tím se zakáže dílčí verze s posunem.
  - `Minor`-Posunutí nahoru na nejnižší nižší verzi, pokud chybí požadovaná dílčí verze. Pokud je k dispozici požadovaná dílčí verze, použije se zásada LatestPatch.
  - `Major`-Pokud chybí požadovaná hlavní verze, převeďte nahoru na nejnižší vyšší hlavní verzi a nejnižší podverzi. Pokud je k dispozici požadovaná hlavní verze, použije se vedlejší zásada.
  - `LatestMinor`– Převeďte dál na nejvyšší dílčí verzi, i když je k dispozici požadovaná dílčí verze. Určeno pro scénáře hostování součástí.
  - `LatestMajor`– Převeďte předem na nejvyšší hlavní a nejvyšší podverzi, i když je k dispozici požadovaná hlavní verze. Určeno pro scénáře hostování součástí.
  - `Disable`– Nezavádět předem. Vytvoří se jenom vazba na určenou verzi. Tyto zásady se nedoporučují pro obecné použití, protože zakazují možnost navrátit se k nejnovějším opravám. Tato hodnota se doporučuje jenom pro testování.

  Kromě `Disable` toho všechna nastavení použijí nejvyšší dostupnou verzi opravy.

  Chování při posunutí nahoru lze také nakonfigurovat v vlastnost souboru projektu, vlastnosti konfiguračního souboru modulu runtime a proměnné prostředí. Další informace najdete v tématu o [zavedení modulu runtime hlavní verze – posunutí](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

- **`--roll-forward-on-no-candidate-fx <N>`****K dispozici v sadě .NET Core 2. x SDK.**

  Definuje chování v případě, že požadovaná sdílená architektura není k dispozici. `N`může být:

  - `0`– Zakažte u sebe i menší verzi.
  - `1`– Navýšení se dopředá na podverzi, ale ne na hlavní verzi. Toto je výchozí chování.
  - `2`– Posunutí posunu k dílčím a hlavním verzím

  Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.

  Počínaje rozhraním .NET Core 3,0 je tato možnost nahrazena aplikací `--roll-forward` a tato možnost by se měla použít místo toho.

- **`--fx-version <VERSION>`**

  Verze modulu runtime .NET Core, která se má použít ke spuštění aplikace

  Tato možnost přepíše verzi prvního odkazu na rozhraní v `.runtimeconfig.json` souboru aplikace. To znamená, že funguje podle očekávání pouze v případě, že existuje pouze jeden odkaz na rozhraní. Pokud má aplikace více než jeden odkaz na rozhraní, může použití této možnosti způsobit chyby.

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
| [dotnet new](dotnet-new.md)                   | Inicializuje projekt C# nebo F # pro danou šablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Vytvoří balíček NuGet vašeho kódu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje aplikaci závislou na rozhraní .NET Framework nebo samostatnou aplikaci. |
| [dotnet restore](dotnet-restore.md)           | Obnoví závislosti pro danou aplikaci.                  |
| [dotnet run](dotnet-run.md)                   | Spustí aplikaci ze zdroje.                                   |
| [dotnet sln](dotnet-sln.md)                   | Možnosti pro přidání, odebrání a výpis projektů v souboru řešení.       |
| [dotnet store](dotnet-store.md)               | Ukládá sestavení do úložiště balíčků modulu runtime.                     |
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
[dotnet nuget push](dotnet-nuget-push.md) | Odešle balíček na server a publikuje ho.
[dotnet nuget locals](dotnet-nuget-locals.md) | Vymaže nebo vypíše místní prostředky NuGet, jako je mezipaměť požadavků HTTP, dočasná mezipaměť nebo složka globálních balíčků v celém počítači.
[dotnet nuget add source](dotnet-nuget-add-source.md) | Přidá zdroj NuGet.
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | Zakáže zdroj NuGet.
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | Povoluje zdroj NuGet.
[dotnet nuget list source](dotnet-nuget-list-source.md) | Zobrazí seznam všech nakonfigurovaných zdrojů NuGet.
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | Odebere zdroj NuGet.
[dotnet nuget update source](dotnet-nuget-update-source.md) | Aktualizuje zdroj NuGet.

### <a name="global-tool-path-and-local-tools-commands"></a>Příkazy globálních nástrojů, nástrojů a cest a místních nástrojů

Nástroje jsou konzolové aplikace, které jsou nainstalovány z balíčků NuGet a jsou vyvolány z příkazového řádku. Můžete psát nástroje sami nebo instalovat nástroje napsané třetí stranou. Nástroje jsou také známé jako globální nástroje, nástroje pro cestu nástrojů a místní nástroje. Další informace najdete v tématu [Přehled nástrojů .NET Core](global-tools.md). Nástroje pro globální a cestu nástrojů jsou k dispozici od .NET Core SDK 2,1. K dispozici jsou místní nástroje od .NET Core SDK 3,0.

Příkaz | Funkce
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Nainstaluje nástroj na váš počítač.
[dotnet tool list](dotnet-tool-list.md) | Zobrazí seznam všech nástrojů, které jsou aktuálně nainstalované na vašem počítači, na základě globálních nástrojů, nástrojů a cest.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstaluje nástroj z počítače.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje nástroj, který je nainstalovaný na vašem počítači.

### <a name="additional-tools"></a>Další nástroje

Počínaje .NET Core SDK 2.1.300 je teď k dispozici několik nástrojů, které byly k dispozici pouze pro jednotlivé projekty pomocí, `DotnetCliToolReference` jako součást .NET Core SDK. Tyto nástroje jsou uvedené v následující tabulce:

| Nástroj                                              | Funkce                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| vývoj – certifikáty                                         | Vytvoří a spravuje vývojové certifikáty.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core nástroje příkazového řádku.                    |
| SQL – mezipaměť                                         | Nástroje příkazového řádku pro SQL Server cache                         |
| [uživatel – tajné klíče](/aspnet/core/security/app-secrets) | Spravuje tajné klíče uživatele.                            |
| [sledovací](/aspnet/core/tutorials/dotnet-watch)      | Spustí sledovací proces souborů, který spustí příkaz, když se soubory změní. |

Další informace o jednotlivých nástrojích získáte tak, že zadáte `dotnet <tool-name> --help` .

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

  Určuje umístění modulů runtime .NET Core, pokud nejsou nainstalovány ve výchozím umístění. Výchozí umístění ve Windows je `C:\Program Files\dotnet` . Výchozí umístění v systémech Linux a macOS je `/usr/share/dotnet` . Tato proměnná prostředí se používá jenom při spouštění aplikací prostřednictvím generovaných spustitelných souborů (apphosts). `DOTNET_ROOT(x86)`se používá místo toho, když je spuštěný 32 spustitelný soubor na 64 operačním systému.

- `DOTNET_PACKAGES`

  Složka globálních balíčků. Pokud není nastavená, použije se `~/.nuget/packages` ve výchozím nastavení v systému UNIX nebo `%userprofile%\.nuget\packages` Windows.

- `DOTNET_SERVICING`

  Určuje umístění indexu údržby používaného sdíleným hostitelem při načítání modulu runtime.

- `DOTNET_NOLOGO`

  Určuje, jestli se při prvním spuštění zobrazují zprávy Welcome a telemetrie .NET Core. Nastavte na `true` ztlumení těchto zpráv (hodnoty `true` , `1` nebo `yes` přijmout), nebo nastavte na hodnotu `false` Povolit (hodnoty `false` , `0` nebo `no` přijmout). Pokud není nastavená, použije se výchozí nastavení `false` a zprávy se zobrazí při prvním spuštění. Tento příznak nemá žádný vliv na telemetrii (viz `DOTNET_CLI_TELEMETRY_OPTOUT` pro odsouhlasení z odesílající telemetrie).

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Určuje, jestli se data o využití nástrojů .NET Core shromažďují a odesílají do Microsoftu. Nastavte na `true` výslovný souhlas funkce telemetrie (hodnoty `true` , `1` nebo `yes` přijmout). V opačném případě nastavte, aby se `false` přihlásil k funkcím telemetrie (hodnoty `false` , `0` nebo `no` přijaty). Pokud není nastavená, je výchozí nastavení `false` a funkce telemetrie je aktivní.

- `DOTNET_MULTILEVEL_LOOKUP`

  Určuje, zda je rozhraní .NET Core Runtime, sdílené rozhraní nebo sada SDK vyřešeno z globálního umístění. Pokud není nastavené, použije se výchozí hodnota 1 (logická `true` ). Nastavte na 0 (logický `false` ), aby se nepřeložily z globálního umístění a měly izolované instalace .NET Core. Další informace o vyhledávání na více úrovních najdete v tématu [SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**K dispozici počínaje rozhraním .NET Core 3. x.**

  Určuje chování při posunu nahoru. Další informace najdete v části `--roll-forward` výše v tomto článku.

- `DOTNET_ROLL_FORWARD_TO_PRERELEASE`**K dispozici počínaje rozhraním .NET Core 3. x.**

  Pokud je nastaveno na `1` (povoleno), povolí návrat k předběžnému vydání verze z vydané verze. Ve výchozím nastavení ( `0` -zakázáno) platí, že pokud je vyžadovaná vydaná verze modulu runtime .NET Core, znamená to, že je k dispozici jenom nainstalovaná verze Release.

  Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)nahoru.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**K dispozici v .NET Core 2. x.**

  Zakáže posunutí dílčí verze, pokud je nastaveno na `0` . Další informace najdete v tématu o tom, jak [Posunout](../whats-new/dotnet-core-2-1.md#roll-forward)nahoru.

  Toto nastavení nahrazuje rozhraní .NET Core 3,0 podle `DOTNET_ROLL_FORWARD` . Místo toho by se mělo použít nové nastavení.

- `DOTNET_CLI_UI_LANGUAGE`

  Nastaví jazyk uživatelského rozhraní CLI pomocí hodnoty národního prostředí, například `en-us` . Podporované hodnoty jsou stejné jako u sady Visual Studio. Další informace najdete v části o změně jazyka instalačního programu v [dokumentaci k instalaci sady Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Použijí se pravidla správce prostředků .NET, takže nemusíte vybírat přesnou shodu, &mdash; můžete také vybrat následníky ve `CultureInfo` stromové struktuře. Například pokud nastavíte na `fr-CA` , rozhraní příkazového řádku nalezne a použije `fr` překlady. Pokud ho nastavíte na jazyk, který není podporován, rozhraní příkazového řádku se vrátí do angličtiny.

- `DOTNET_DISABLE_GUI_ERRORS`

  V případě generovaných spustitelných souborů s povoleným grafickým uživatelským rozhraním – zakáže dialogová okna, která obvykle zobrazuje určité třídy chyb. `stderr`V těchto případech zapisuje a ukončuje se.
  
- `DOTNET_ADDITIONAL_DEPS`

  Ekvivalent možnosti CLI `--additional-deps` .

- `DOTNET_RUNTIME_ID`

  Přepíše zjištěný identifikátor RID.

- `DOTNET_SHARED_STORE`

  Umístění sdíleného úložiště, na které se rozlišení sestavení vrátí v některých případech.

- `DOTNET_STARTUP_HOOKS`

  Seznam sestavení pro načtení a spuštění spouštěcích háky z.

- `DOTNET_BUNDLE_EXTRACT_BASE_DIR`**K dispozici počínaje rozhraním .NET Core 3. x.**

  Určuje adresář, do kterého se extrahuje aplikace s jedním souborem, než se spustí.

  Další informace najdete v tématu [spustitelné soubory s jedním souborem](../whats-new/dotnet-core-3-0.md#single-file-executables).

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Řídí trasování diagnostiky z komponent hostování, například `dotnet.exe` , `hostfxr` a `hostpolicy` .

  * `COREHOST_TRACE=[0/1]`-Defaulted `0` -Tracing Disabled. Pokud je nastaveno na `1` , trasování diagnostiky je povoleno.
  * `COREHOST_TRACEFILE=<file path>`-má vliv, pokud je povoleno trasování prostřednictvím `COREHOST_TRACE=1` . Při nastavení se trasovací informace zapisují do zadaného souboru, jinak se do něj zapisují trasovací informace `stderr` . **K dispozici počínaje rozhraním .NET Core 3. x.**
  * `COREHOST_TRACE_VERBOSITY=[1/2/3/4]`– Výchozí hodnota je `4` . Toto nastavení se používá pouze v případě, že je povoleno trasování prostřednictvím `COREHOST_TRACE=1` . **K dispozici počínaje rozhraním .NET Core 3. x.**
    * `4`– zapisují se všechny informace o trasování.
    * `3`– zapisují se jenom informativní, varovné a chybové zprávy.
    * `2`– zapíší se jenom upozornění a chybové zprávy.
    * `1`-jsou zapsány pouze chybové zprávy.

  Typický způsob, jak získat podrobné informace o trasování o spuštění aplikace, je nastavit `COREHOST_TRACE=1` a `COREHOST_TRACEFILE=host_trace.txt` následně spustit aplikaci. V aktuálním adresáři se vytvoří nový soubor `host_trace.txt` s podrobnými informacemi.

## <a name="see-also"></a>Viz také

- [Běhové konfigurační soubory](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Nastavení konfigurace runtime .NET Core](../run-time-config/index.md)
