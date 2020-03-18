---
title: Telemetrie sady .NET Core SDK
description: Seznamte se s telemetrickými funkcemi sady .NET Core SDK, které shromažďují informace o využití pro analýzu, která data jsou shromažďována a jak je zakázat.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 9d5d7ff09ade89712f2fbbe35224851bb1c28b4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156683"
---
# <a name="net-core-sdk-telemetry"></a>Telemetrie sady .NET Core SDK

Sada [.NET Core SDK](index.md) obsahuje funkci telemetrie, která shromažďuje data o využití a informace o výjimkách při selhání rozhraní .NET Core CLI. Rozhraní PŘÍKAZOVÉHO NASTAVENÍ .NET Core cli je dodáváno se sadou .NET Core SDK a je sadou sloves, která umožňují vytvářet, testovat a publikovat aplikace .NET Core. Je důležité, aby tým .NET pochopil, jak se nástroje používají, aby je bylo možné zlepšit. Informace o selhání pomáhá týmu vyřešit problémy a opravit chyby.

Shromážděné údaje jsou anonymní a jsou zveřejňovány souhrnně pod [licencí Creative Commons Attribution License](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Rozsah

`dotnet`má dvě funkce: spouštět aplikace a spouštět příkazy příkazového příkazu. Telemetrie *se neshromažďuje* při spuštění `dotnet` aplikace v následujícím formátu:

- `dotnet [path-to-app].dll`

Telemetrie *se shromažďuje* při použití některého z [příkazů rozhraní PŘÍKAZOVÉHO PŘÍKAZU .NET Core](index.md), například:

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Jak se odhlásit

Funkce telemetrie sady .NET Core SDK je ve výchozím nastavení povolena. Chcete-li odhlásit funkci telemetrie, `1` nastavte `true`proměnnou `DOTNET_CLI_TELEMETRY_OPTOUT` prostředí na nebo .

Instalační program sady .NET Core SDK odesílá také jednu položku telemetrie, když dojde k úspěšné instalaci. Chcete-li se `DOTNET_CLI_TELEMETRY_OPTOUT` odhlásit, nastavte před instalací sady .NET Core SDK proměnnou prostředí.

## <a name="disclosure"></a>Zveřejnění

Sada .NET Core SDK zobrazí text podobný následujícímu při prvním spuštění jednoho z příkazů `dotnet build`rozhraní [PŘÍKAZU .NET Core (například](index.md) ). Text se může mírně lišit v závislosti na verzi sady SDK, kterou používáte. Toto "první spuštění" prostředí je, jak microsoft vás upozorní na shromažďování dat.

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a>Datové body

Funkce telemetrie neshromažďuje osobní údaje, jako jsou uživatelská jména nebo e-mailové adresy. Neprohledá váš kód a neextrahuje data na úrovni projektu, jako je název, úložiště nebo autor. Data se bezpečně odesílají na servery Microsoftu pomocí technologie [Azure Monitor,](https://azure.microsoft.com/services/monitor/) která je držena pod omezeným přístupem a publikuje se pod přísnými bezpečnostními kontrolami ze zabezpečených systémů [Azure Storage.](https://azure.microsoft.com/services/storage/)

Ochrana vašeho soukromí je pro nás důležitá. Pokud máte podezření, že telemetrie shromažďuje citlivá data nebo jsou nebezpečně nebo nevhodně zpracována, zasuzujte problém do úložiště [dotnet/cli](https://github.com/dotnet/cli/issues) nebo odešlete e-mail k [dotnet@microsoft.com](mailto:dotnet@microsoft.com) prošetření.

Funkce telemetrie shromažďuje následující data:

| Verze sady SDK | Data |
|--------------|------|
| Všechny          | Časové razítko vyvolání. |
| Všechny          | Příkaz vyvolán (například "sestavení"), zahashované počínaje 2.1. |
| Všechny          | Tři oktetové IP adresy používané k určení zeměpisné polohy. |
| Všechny          | Operační systém a verze. |
| Všechny          | Runtime ID (RID) sada SDK je spuštěna. |
| Všechny          | Verze sady .NET Core SDK. |
| Všechny          | Profil telemetrie: volitelná hodnota používaná pouze s explicitním přihlášením uživatele a interně používaná u společnosti Microsoft. |
| >=2,0        | Příkaz argumenty a možnosti: několik argumentů a možností jsou shromažďovány (ne libovolné řetězce). Viz [shromážděné možnosti](#collected-options). Hashed po 2.1.300. |
| >=2,0         | Zda je sada SDK spuštěna v kontejneru. |
| >=2,0         | Cílové rámce (z `TargetFramework` události), hash začíná v 2.1. |
| >=2,0         | Hashed Media Access Control (MAC) adresa: kryptograficky (SHA256) anonymní a jedinečné ID pro počítač. |
| >=2,0         | Zahashed aktuální pracovní adresář. |
| >=2,0         | Nainstalujte zprávu o úspěchu s názvem souboru exe zahasovaného instalačního programu. |
| >=2.1.300     | Verze jádra. |
| >=2.1.300     | Libc vydání / verze. |
| >=3.0.100     | Zda byl výstup přesměrován (true nebo false). |
| >=3.0.100     | Při selhání cli/SDK typ výjimky a jeho trasování zásobníku (pouze CLI/SDK kód je součástí trasování zásobníku odeslána). Další informace naleznete [v tématu .NET Core CLI/SDK výjimka výjimky telemetrie shromážděny](#net-core-clisdk-crash-exception-telemetry-collected). |

### <a name="collected-options"></a>Shromážděné možnosti

Některé příkazy odesílají další data. Podmnožina příkazů odešle první argument:

| Příkaz               | Odeslaná data prvního argumentu                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | Nápověda příkazu je dotazován.  |
| `dotnet new <arg>`    | Název šablony (hash).             |
| `dotnet add <arg>`    | Slovo `package` nebo `reference`.      |
| `dotnet remove <arg>` | Slovo `package` nebo `reference`.      |
| `dotnet list <arg>`   | Slovo `package` nebo `reference`.      |
| `dotnet sln <arg>`    | Slovo `add`, `list`, `remove`nebo .    |
| `dotnet nuget <arg>`  | Slovo `delete`, `locals`, `push`nebo . |

Podmnožina příkazů odešle vybrané volby, pokud jsou použity, spolu s jejich hodnotami:

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

S `--verbosity` výjimkou `--sdk-package-version`a , všechny ostatní hodnoty jsou zahashovat počínaje .NET Core 2.1.100 SDK.

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>Shromážděná telemetrie výjimky selhání rozhraní CLI jádra jádra nebo sady SDK

Pokud dojde k chybě rozhraní .NET Core CLI/SDK, shromažďuje název výjimky a trasování zásobníku kódu CLI/SDK. Tyto informace jsou shromažďovány k posouzení problémů a zlepšení kvality sady .NET Core SDK a CLI. Tento článek obsahuje informace o shromažďinách. Poskytuje také tipy, jak uživatelé, kteří vytváří vlastní verzi sady .NET Core SDK, mohou zabránit neúmyslnému zveřejnění osobních nebo citlivých informací.

### <a name="types-of-collected-data"></a>Typy shromážděných údajů

Rozhraní .NET Core CLI shromažďuje informace pouze pro výjimky cli/SDK, nikoli výjimky ve vaší aplikaci. Shromážděná data obsahuje název výjimky a trasování zásobníku. Toto trasování zásobníku je kódu CLI/SDK.

Následující příklad ukazuje druh dat, která jsou shromažďována:

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

### <a name="avoid-inadvertent-disclosure-of-information"></a>Vyhněte se neúmyslnému zveřejnění informací

Přispěvatelé .NET Core a kdokoli jiný, kdo používá verzi sady .NET Core SDK, kterou sami vytvořili, by měli zvážit cestu k jejich zdrojovému kódu sady SDK. Pokud dojde k chybě při použití sady .NET Core SDK, která je vlastní ladění sestavení nebo nakonfigurován s vlastní soubory symbolů sestavení, cesta zdrojového souboru Sady SDK z počítače sestavení se shromažďují jako součást trasování zásobníku a není zakódován.

Z tohoto důvodu vlastní sestavení sady .NET Core SDK by neměla být umístěna v adresářích, jejichž názvy cest zveřejňují osobní nebo citlivé informace.

## <a name="see-also"></a>Viz také

- [Telemetrie rozhraní CLI .NET - data Q2 2 2 2 2](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [Referenční zdroj telemetrie (úložiště dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
