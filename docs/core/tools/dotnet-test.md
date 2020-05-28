---
title: dotnet – příkaz testu
description: Příkaz dotnet test se používá ke spouštění testů jednotek v daném projektu.
ms.date: 04/29/2020
ms.openlocfilehash: b427954fe0026e6ac96d3bbce2b70b5c44e884e0
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005372"
---
# <a name="dotnet-test"></a>dotnet test

**Tento článek se týká:** ✔️ .net Core 2,1 SDK a novějších verzí

## <a name="name"></a>Name

`dotnet test`– Testovací ovladač .NET, který se používá ke spouštění testů jednotek.

## <a name="synopsis"></a>Stručný obsah

```dotnetcli
dotnet test [<PROJECT> | <SOLUTION> | <DIRECTORY> | <DLL>]
    [-a|--test-adapter-path <PATH_TO_ADAPTER>] [--blame]
    [-c|--configuration <CONFIGURATION>]
    [--collect <DATA_COLLECTOR_FRIENDLY_NAME>]
    [-d|--diag <PATH_TO_DIAGNOSTICS_FILE>] [-f|--framework <FRAMEWORK>]
    [--filter <EXPRESSION>] [--interactive]
    [-l|--logger <LOGGER_URI/FRIENDLY_NAME>] [--no-build]
    [--nologo] [--no-restore] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--results-directory <PATH>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--settings <SETTINGS_FILE>] [-t|--list-tests]
    [-v|--verbosity <LEVEL>] [[--] <RunSettings arguments>]

dotnet test -h|--help
```

## <a name="description"></a>Description

`dotnet test`Příkaz slouží ke spuštění testů jednotek v daném řešení. Příkaz sestaví `dotnet test` řešení a spustí testovací hostitelskou aplikaci pro každý projekt testů v řešení. Testovací hostitel provede v daném projektu testy pomocí testovacího rozhraní, například: MSTest, NUnit nebo xUnit, a ohlásí úspěch nebo neúspěch každého testu. Pokud jsou všechny testy úspěšné, Test Runner vrátí 0 jako ukončovací kód; jinak, pokud nějaký test selže, vrátí 1.

Pro projekty zaměřené na více platforem jsou testy spouštěny pro každou cílovou architekturu. Testovací hostitel a testovací rozhraní jednotky jsou zabaleny jako balíčky NuGet a jsou obnoveny jako běžné závislosti pro projekt.

Projekty testů určují testovací spouštěč pomocí obyčejného `<PackageReference>` prvku, jak je vidět v následujícím ukázkovém souboru projektu:

[!code-xml[XUnit Basic Template](../../../samples/snippets/csharp/xunit-test/xunit-test.csproj)]

Kde `Microsoft.NET.Test.Sdk` je testovací hostitel, `xunit` je testovací rozhraní. A `xunit.runner.visualstudio` je testovací adaptér, který umožňuje, aby architektura xUnit spolupracovala s testovacím hostitelem.

### <a name="implicit-restore"></a>Implicitní obnovení

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

## <a name="arguments"></a>Argumenty

- **`PROJECT | SOLUTION | DIRECTORY | DLL`**

  - Cesta k testovacímu projektu.
  - Cesta k řešení
  - Cesta k adresáři, který obsahuje projekt nebo řešení.
  - Cesta k souboru projektu testů *. dll* .

  Pokud není zadán, vyhledá projekt nebo řešení v aktuálním adresáři.

## <a name="options"></a>Možnosti

- **`-a|--test-adapter-path <PATH_TO_ADAPTER>`**

  Cesta k adresáři, ve kterém se mají hledat další testovací adaptéry Jsou zkontrolovány pouze soubory *DLL* s příponou `.TestAdapter.dll` . Pokud není zadán, bude prohledán adresář souboru Test *. dll* .

- **`--blame`**

  Spustí testy v režimu viny. Tato možnost je užitečná při izolaci problematických testů, které způsobují selhání hostitele testu. Při zjištění chyby vytvoří soubor sekvence v `TestResults/<Guid>/<Guid>_Sequence.xml` , který zachytí pořadí testů, které byly spuštěny před selháním.

- **`-c|--configuration <CONFIGURATION>`**

  Definuje konfiguraci sestavení. Výchozí hodnota je `Debug` , ale konfigurace vašeho projektu může přepsat toto výchozí nastavení sady SDK.

- **`--collect <DATA_COLLECTOR_FRIENDLY_NAME>`**

  Povolí shromažďování dat pro testovací běh. Další informace najdete v tématu [monitorování a analýza testovacího běhu](https://aka.ms/vstest-collect).
  
  Chcete-li shromáždit pokrytí kódu na jakékoli platformě, která je podporována rozhraním .NET Core, nainstalujte [Coverlet](https://github.com/coverlet-coverage/coverlet/blob/master/README.md) a použijte `--collect:"XPlat Code Coverage"` možnost.

  Ve Windows můžete pokrytí kódu shromažďovat pomocí `--collect "Code Coverage"` Možnosti. Tato možnost vygeneruje soubor *. pokrytí* , který lze otevřít v aplikaci Visual Studio 2019 Enterprise. Další informace najdete v tématu [Použití pokrytí kódu](/visualstudio/test/using-code-coverage-to-determine-how-much-code-is-being-tested) a [přizpůsobení analýzy pokrytí kódu](/visualstudio/test/customizing-code-coverage-analysis).

- **`-d|--diag <PATH_TO_DIAGNOSTICS_FILE>`**

  Povolí diagnostický režim pro testovací platformu a zapisuje diagnostické zprávy do zadaného souboru a do souborů vedle sebe. Proces, který zaznamenává zprávy, určuje, které soubory jsou vytvořeny, například `*.host_<date>.txt` pro protokol testu hostitele a `*.datacollector_<date>.txt` protokol sběru dat.

- **`-f|--framework <FRAMEWORK>`**

  Vynutí použití `dotnet` nebo .NET Framework testovacího hostitele pro binární soubory testu. Tato možnost určuje pouze typ hostitele, který se má použít. Skutečná verze rozhraní, která se má použít, se určuje pomocí *runtimeconfig. JSON* testovacího projektu. Pokud není zadaný, použije se k určení typu hostitele [atribut pro sestavení targetFramework](/dotnet/api/system.runtime.versioning.targetframeworkattribute) . Když je tento atribut ze souboru *. dll*odstraněn, je použit hostitel .NET Framework.

- **`--filter <EXPRESSION>`**

  Odfiltruje testy v aktuálním projektu pomocí daného výrazu. Další informace najdete v části [Podrobnosti o možnosti filtru](#filter-option-details) . Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).

- **`-h|--help`**

  Vypíše krátkou nápovědu k příkazu.

- **`--interactive`**

  Umožňuje zastavení příkazu zastavit a počkat na vstup nebo akci uživatele. Například k dokončení ověřování. K dispozici od verze .NET Core 3,0 SDK.

- **`-l|--logger <LOGGER_URI/FRIENDLY_NAME>`**

  Určuje protokolovací nástroj pro výsledky testů. Na rozdíl od MSBuild test dotnet nepřijímá zkratky: místo `-l "console;v=d"` použití `-l "console;verbosity=detailed"` .

- **`--no-build`**

  Před spuštěním nevytvoří testovací projekt. Také implicitně nastaví `--no-restore` příznak-.

- **`--nologo`**

  Spusťte testy bez zobrazení banneru Microsoft TestPlatform. K dispozici od verze .NET Core 3,0 SDK.

- **`--no-restore`**

  Při spuštění příkazu neprovede implicitní obnovení.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Adresář, ve kterém se mají najít binární soubory, které se mají spustit. Pokud není zadaný, použije se výchozí cesta `./bin/<configuration>/<framework>/` .  Pro projekty s více cílovými rozhraními (prostřednictvím `TargetFrameworks` Vlastnosti) musíte definovat i `--framework` při zadání této možnosti. `dotnet test`vždy spouští testy z výstupního adresáře. Můžete použít <xref:System.AppDomain.BaseDirectory%2A?displayProperty=nameWithType> pro využívání testovacích prostředků ve výstupním adresáři.

- **`-r|--results-directory <PATH>`**

  Adresář, do kterého budou umístěny výsledky testů. Pokud zadaný adresář neexistuje, vytvoří se. Výchozí hodnota je `TestResults` v adresáři, který obsahuje soubor projektu.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Cílový modul runtime, pro který se má testovat.

- **`-s|--settings <SETTINGS_FILE>`**

  `.runsettings`Soubor, který se má použít pro spuštění testů. Všimněte si, že `TargetPlatform` element (x86 | x64) nemá žádný vliv na `dotnet test` . Chcete-li spustit testy, které cílí na x86, nainstalujte verzi x86 rozhraní .NET Core. Bitová verze příkazu *dotnet. exe* , který je na cestě, bude použit pro spouštění testů. Další informace najdete v následujících materiálech:

  - [Nakonfigurujte testy jednotek pomocí `.runsettings` souboru.](/visualstudio/test/configure-unit-tests-by-using-a-dot-runsettings-file)
  - [Konfigurace testovacího běhu](https://github.com/Microsoft/vstest-docs/blob/master/docs/configure.md)

- **`-t|--list-tests`**

  Vypíše všechny zjištěné testy v aktuálním projektu.

- **`-v|--verbosity <LEVEL>`**

  Nastaví úroveň podrobností příkazu. Povolené hodnoty jsou `q[uiet]` , `m[inimal]` ,, a `n[ormal]` `d[etailed]` `diag[nostic]` . Výchozí formát je `minimal`. Další informace naleznete v tématu <xref:Microsoft.Build.Framework.LoggerVerbosity>.

- **`RunSettings`** náhodné

 Inline `RunSettings` se předávají jako poslední argumenty příkazového řádku za znakem "--" (Všimněte si místa za-). `RunSettings`Jako páry jsou zadány vložené `[name]=[value]` . K oddělení více párů se používá mezera `[name]=[value]` .

  Příklad: `dotnet test -- MSTest.DeploymentEnabled=false MSTest.MapInconclusiveToFailed=True`

  Další informace najdete v tématu [předávání argumentů runsettings pomocí příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md).

## <a name="examples"></a>Příklady

- Spustit testy v projektu v aktuálním adresáři:

  ```dotnetcli
  dotnet test
  ```

- Spustit testy v `test1` projektu:

  ```dotnetcli
  dotnet test ~/projects/test1/test1.csproj
  ```

- Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor výsledků testů ve formátu TRX:

  ```dotnetcli
  dotnet test --logger trx
  ```

- Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor pokrytí kódu (po instalaci [Coverlet](https://github.com/tonerdo/coverlet/blob/master/README.md)):

  ```dotnetcli
  dotnet test --collect:"XPlat Code Coverage"
  ```

- Spusťte testy v projektu v aktuálním adresáři a vygenerujte soubor pokrytí kódu (pouze Windows):

  ```dotnetcli
  dotnet test --collect "Code Coverage"
  ```

- Spusťte testy v projektu v aktuálním adresáři a log s detailní podrobností do konzoly:

  ```dotnetcli
  dotnet test --logger "console;verbosity=detailed"
  ```
  
  - Spusťte testy v projektu v aktuálním adresáři a Nahlášením testů, které probíhaly při selhání hostitele testu:

  ```dotnetcli
  dotnet test --blame
  ```

## <a name="filter-option-details"></a>Podrobnosti možnosti filtru

`--filter <EXPRESSION>`

`<Expression>`má formát `<property><operator><value>[|&<Expression>]` .

`<property>`je atributem `Test Case` . Níže jsou uvedené vlastnosti podporované oblíbenými rozhraními pro testování částí:

| Testovací rozhraní | Podporované vlastnosti                                                                                      |
| -------------- | --------------------------------------------------------------------------------------------------------- |
| MSTest         | <ul><li>FullyQualifiedName</li><li>Name</li><li>NázevTřídy</li><li>Priorita</li><li>TestCategory</li></ul> |
| xUnit          | <ul><li>FullyQualifiedName</li><li>DisplayName</li><li>Traits</li></ul>                                   |
| NUnit          | <ul><li>FullyQualifiedName</li><li>Name</li><li>TestCategory</li><li>Priorita</li></ul>                                   |

`<operator>`Popisuje vztah mezi vlastností a hodnotou:

| Operátor | Funkce        |
| :------: | --------------- |
| `=`      | Přesná shoda     |
| `!=`     | Nepřesná shoda |
| `~`      | Contains        |
| `!~`     | Neobsahuje    |

`<value>`je řetězec. U všech hledání se nerozlišují malá a velká písmena.

Výraz bez objektu `<operator>` je automaticky považován za `contains` `FullyQualifiedName` vlastnost on (například `dotnet test --filter xyz` je stejný jako `dotnet test --filter FullyQualifiedName~xyz` ).

Výrazy se dají spojit s podmíněnými operátory:

| Operátor            | Funkce |
| ------------------- | -------- |
| <code>&#124;</code> | NEBO       |
| `&`                 | AND      |

Výrazy můžete uzavřít do závorek při použití podmíněných operátorů (například `(Name~TestMethod1) | (Name~TestMethod2)` ).

Další informace a příklady použití selektivního filtrování testů jednotek naleznete v tématu [spuštění selektivních testů jednotek](../testing/selective-unit-tests.md).

## <a name="see-also"></a>Viz také

- [Architektury a cíle](../../standard/frameworks.md)
- [Katalog identifikátorů runtime .NET Core (RID)](../rid-catalog.md)
- [Předávání argumentů runsettings prostřednictvím příkazového řádku](https://github.com/Microsoft/vstest-docs/blob/master/docs/RunSettingsArguments.md)
