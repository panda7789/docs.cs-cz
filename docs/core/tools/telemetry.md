---
title: Telemetrie .NET Core SDK
description: Objevte funkce telemetrie .NET Core SDK, které shromažďují informace o využití pro analýzu, shromažďovaná data a jejich zakázání.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 01376cabc4f59f64c59a78dcff061fb6ec11e3c3
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359230"
---
# <a name="net-core-sdk-telemetry"></a>Telemetrie .NET Core SDK

[.NET Core SDK](index.md) obsahuje funkci telemetrie, která shromažďuje data o využití a informace o výjimkách při selhání .NET Core CLI. .NET Core CLI se dodává s .NET Core SDK a je to sada operací, které umožňují sestavovat, testovat a publikovat aplikace .NET Core. Je důležité, aby tým .NET pochopil, jak se nástroje používají, aby bylo možné je zlepšit. Informace o selháních pomáhají týmu vyřešit problémy a opravovat chyby.

Shromážděná data jsou anonymní a publikovaná v rámci [licence Creative](https://creativecommons.org/licenses/by/4.0/)navýšení.

## <a name="scope"></a>Obor

`dotnet` má dvě funkce: spouštění aplikací a provádění příkazů CLI. Telemetrii *není shromažďována* při použití `dotnet` ke spuštění aplikace v následujícím formátu:

- `dotnet [path-to-app].dll`

Telemetrie *se shromáždí* při použití některého z [.NET Core CLI příkazů](index.md), jako je například:

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak odhlásit

Funkce telemetrie .NET Core SDK je ve výchozím nastavení povolená. Chcete-li se odhlásit z funkce telemetrie, nastavte `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí na `1` nebo `true` .

V případě, že dojde k úspěšné instalaci, posílá instalační program .NET Core SDK také jednu položku telemetrie. Pokud se chcete odhlásit, nastavte `DOTNET_CLI_TELEMETRY_OPTOUT` proměnnou prostředí před instalací .NET Core SDK.

## <a name="disclosure"></a>Námitk

.NET Core SDK zobrazí text podobný následujícímu při prvním spuštění jednoho z [.NET Core CLI příkazů](index.md) (například `dotnet build` ). Text se může v závislosti na verzi sady SDK, kterou používáte, mírně lišit. Toto je postup "prvního spuštění", který vás Microsoft upozorní na shromažďování dat.

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

Chcete-li zakázat tuto zprávu a uvítací zprávu .NET Core, nastavte `DOTNET_NOLOGO` proměnnou prostředí na `true` . Všimněte si, že tato proměnná nemá žádný vliv na odhlášení telemetrie.

## <a name="data-points"></a>Datové body

Funkce telemetrie neshromažďuje osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy. Nekontroluje váš kód a neextrahuje data na úrovni projektu, jako je název, úložiště nebo autor. Data se odesílají zabezpečeně na servery Microsoftu pomocí [Azure monitor](https://azure.microsoft.com/services/monitor/) technologie, která se drží pod omezeným přístupem, a publikují se v rámci striktních bezpečnostních mechanismů pro [Azure Storage](https://azure.microsoft.com/services/storage/) systémy.

Ochrana vašich osobních údajů je pro nás důležitá. Pokud máte podezření, že telemetrie shromažďuje citlivá data nebo jsou data nezabezpečená nebo nevhodně zpracovaná, zapište problém do úložiště [dotnet/SDK](https://github.com/dotnet/sdk/issues) nebo odešlete e-mail [dotnet@microsoft.com](mailto:dotnet@microsoft.com) pro šetření.

Funkce telemetrie shromažďuje následující data:

| Verze sady SDK | Data |
|--------------|------|
| Vše          | Časové razítko vyvolání |
| Vše          | Byl vyvolán příkaz (například "Build"), který začíná hodnotou hash 2,1. |
| Vše          | Tři oktety, které se používají k určení geografického umístění. |
| Vše          | Operační systém a verze. |
| Vše          | ID modulu runtime (RID), na kterém je sada SDK spuštěná. |
| Vše          | Verze .NET Core SDK |
| Vše          | Profil telemetrie: volitelná hodnota se používá jenom s výslovným výslovným souhlasem uživatele a používá se interně v Microsoftu. |
| >= 2,0        | Argumenty a možnosti příkazu: několik argumentů a možností je shromažďováno (nejedná se o libovolný řetězec). Viz [shromážděné možnosti](#collected-options). Hodnota hash po 2.1.300 |
| >= 2,0         | Určuje, jestli je sada SDK spuštěná v kontejneru. |
| >= 2,0         | Cílová rozhraní (z `TargetFramework` události) vyhodnotí hodnotu hash začínající v 2,1. |
| >= 2,0         | Adresa MAC Access Control médií (MAC): kryptograficky (SHA256) anonymní a jedinečné ID pro počítač. |
| >= 2,0         | Aktuální pracovní adresář má hodnotu hash. |
| >= 2,0         | Sestava úspěšné instalace s názvem souboru EXE instalačního programu s algoritmem hash |
| >= 2.1.300     | Verze jádra. |
| >= 2.1.300     | Verze nebo verze LIBC. |
| >= 3.0.100     | Určuje, zda byl výstup přesměrován (true nebo false). |
| >= 3.0.100     | V případě selhání CLI/SDK je typ výjimky a jeho trasování zásobníku (do odeslaného trasování zásobníku je zahrnut pouze kód CLI/SDK). Další informace najdete v tématu [shromážděná telemetrie výjimek při selhání .NET Core CLI/SDK](#net-core-clisdk-crash-exception-telemetry-collected). |

### <a name="collected-options"></a>Shromážděné možnosti

Některé příkazy odesílají další data. Podmnožina příkazů odesílá první argument:

| Příkaz               | Data prvního argumentu byla odeslána.                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | Dotaz na příkaz se dotazuje na.  |
| `dotnet new <arg>`    | Název šablony (s algoritmem hash)             |
| `dotnet add <arg>`    | Slovo `package` nebo `reference` .      |
| `dotnet remove <arg>` | Slovo `package` nebo `reference` .      |
| `dotnet list <arg>`   | Slovo `package` nebo `reference` .      |
| `dotnet sln <arg>`    | Slovo `add` , `list` , nebo `remove` .    |
| `dotnet nuget <arg>`  | Slovo `delete` , `locals` , nebo `push` . |

Podmnožina příkazů odesílá vybrané možnosti, pokud jsou použity, spolu s jejich hodnotami:

| Možnost                  | Příkazy                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | Všechny příkazy                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`                  |
| `--framework`           | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest` |
| `--runtime`             | `dotnet build`,  `dotnet publish`                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

S výjimkou `--verbosity` a `--sdk-package-version` jsou všechny ostatní hodnoty hash od .NET Core 2.1.100 SDK.

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>Shromážděná telemetrie výjimek při selhání .NET Core CLI/SDK

Pokud .NET Core CLI/SDK selže, shromažďuje název výjimky a trasování zásobníku kódu CLI/SDK. Tyto informace jsou shromažďovány k vyhodnocení problémů a zlepšení kvality .NET Core SDK a CLI. Tento článek poskytuje informace o datech, která shromažďujeme. Poskytuje také tipy k tomu, jak si uživatelé, kteří vytvářejí svou vlastní verzi .NET Core SDK, můžou zabránit nechtěnému zveřejnění osobních nebo citlivých informací.

### <a name="types-of-collected-data"></a>Typy shromážděných dat

.NET Core CLI shromažďuje informace pouze o výjimkách CLI/SDK, nikoli výjimkách v aplikaci. Shromážděná data obsahují název výjimky a trasování zásobníku. Toto trasování zásobníku je kódu CLI/SDK.

Následující příklad znázorňuje druh shromažďovaných dat:

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a>Vyhněte se nechtěnému zveřejňování informací

Přispěvatelé .NET Core a všichni ostatní spouštějí verzi .NET Core SDK, kterou samy vytvořili, by měli zvážit cestu ke svému zdrojovému kódu sady SDK. Pokud dojde k chybě při použití .NET Core SDK, které je vlastní sestavení ladění nebo nakonfigurováno pomocí vlastních souborů symbolů sestavení, bude cesta ke zdrojovému souboru sady SDK z sestavovacího počítače shromažďována jako součást trasování zásobníku a není použita hodnota hash.

Z tohoto důvodu by se vlastní sestavení .NET Core SDK neměla nacházet v adresářích, jejichž názvy cest zveřejňují osobní nebo citlivé informace.

## <a name="see-also"></a>Viz také

- [.NET Core CLI dat telemetrie](https://dotnet.microsoft.com/platform/telemetry)
- [Zdroj odkazů telemetrie (úložiště dotnet/SDK)](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
