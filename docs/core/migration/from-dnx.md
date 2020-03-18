---
title: Migrace z dnx na rozhraní CLI jádra .NET
description: Migrujte z použití nástrojů DNX na nástroje .NET Core CLI.
ms.date: 06/20/2016
ms.openlocfilehash: 31317f110ae1e8586b78becd757d0a8ff07f1459
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503830"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migrace z DNX na rozhraní CLI jádra .NET (project.json)

## <a name="overview"></a>Přehled
Verze RC1 .NET Core a ASP.NET Core 1.0 představila nástroje DNX. Verze RC2 .NET Core a ASP.NET Core 1.0 se přesunula z DNX do rozhraní .NET Core CLI.

Jako mírný opakovací, pojďme shrnout, co DNX bylo asi. DNX byl runtime a sada nástrojů používaných k vytváření .NET Core a konkrétněji ASP.NET aplikací Core 1.0. Skládá se ze 3 hlavních kusů:

1. DNVM - instalační skript pro získání DNX
2. DNX (Dotnet Execution Runtime) - runtime, který spouští váš kód
3. DNU (Dotnet Developer Utility) - nástroje pro správu závislostí, vytváření a publikování vašich aplikací

Se zavedením cli, všechny výše uvedené jsou nyní součástí jedné sady nástrojů. Vzhledem k tomu, že dnx byl k dispozici v časovém rámci RC1, můžete mít projekty, které byly vytvořeny pomocí něj, které byste chtěli přejít na nové nástroje rozhraní příkazového příkazu.

Tento průvodce migrací bude zahrnovat základní informace o tom, jak migrovat projekty mimo DNX a na rozhraní .NET Core CLI. Pokud právě začínáte projekt na .NET Core od začátku, můžete tento dokument volně přeskočit.

## <a name="main-changes-in-the-tooling"></a>Hlavní změny v nástrojích
V nástrojích jsou uvedeny některé obecné změny, které by měly být popsány jako první.

### <a name="no-more-dnvm"></a>Už žádné DNVM
DNVM, zkratka pro *DotNet Version Manager* byl bash / PowerShell skript používaný k instalaci DNX na vašem počítači. To pomohlo uživatelům získat DNX, které potřebují z krmiva, které zadali (nebo výchozí ty), stejně jako označit určité DNX "aktivní", který by dal na $PATH pro danou relaci. To by vám umožnilo používat různé nástroje.

DNVM byla ukončena, protože jeho sada funkcí byla redundantní změny přicházející v rozhraní .NET Core CLI.

ClI je dodáván a zabalen dvěma hlavními způsoby:

1. Nativní instalační programy pro danou platformu
2. Instalace skriptu pro jiné situace (například ci servery)

Vzhledem k tomu nejsou funkce instalace DNVM potřebné. Ale co funkce výběru za běhu?

Odkazujete na runtime `project.json` ve vašem přidáním balíčku určité verze do vašich závislostí. S touto změnou bude aplikace moci používat nové bity runtime. Získání těchto bitů do počítače je stejné jako u cli: nainstalujete runtime prostřednictvím jednoho z nativních instalačních programů, které podporuje, nebo prostřednictvím instalačního skriptu.

### <a name="different-commands"></a>Různé příkazy
Pokud jste používali DNX, použili jste některé příkazy z jedné z jeho tří částí (DNX, DNU nebo DNVM). S ROZHRANÍ MAT Některá z těchto příkazů se změní, některé nejsou k dispozici a některé jsou stejné, ale mají mírně odlišnou sémantiku.

V následující tabulce je zobrazeno mapování mezi příkazy DNX/DNU a jejich protějšky v příkazech cli.

| DNX, příkaz                    | Příkaz příkazového příkazu, příkaz    | Popis                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| dnx běh                        | `dotnet run`     | Spusťte kód ze zdroje.                                                                                           |
| dnu sestavení                      | `dotnet build`   | Vytvořte il binární kód.                                                                                |
| dnu balíček                       | `dotnet pack`    | Balíček do NuGet balíček vašeho kódu.                                                                        |
| dnx \[příkaz] (například "dnx web") | N/a\*          | Ve světě DNX spusťte příkaz definovaný v souboru project.json.                                                     |
| dnu instalace                    | N/a\*          | Ve světě DNX nainstalujte balíček jako závislost.                                                            |
| dnu obnovení                    | `dotnet restore` | Obnovení závislostí zadaných v souboru project.json. ([viz poznámka](#dotnet-restore-note))                                                            |
| dnu publikovat                    | `dotnet publish` | Publikujte aplikaci pro nasazení v jednom ze tří formulářů (přenosné, přenosné s nativní a samostatné). |
| zábal dnu                       | N/a\*          | Ve světě DNX zabalte project.json do csproj.                                                                    |
| dnu příkazy                   | N/a\*          | Ve světě DNX spravujte globálně nainstalované příkazy.                                                           |

(\*) - tyto funkce nejsou v rozhraní zanesení podle návrhu podporovány.

## <a name="dnx-features-that-are-not-supported"></a>Funkce DNX, které nejsou podporovány
Jak ukazuje výše uvedená tabulka, existují funkce ze světa DNX, které jsme se rozhodli nepodporovat v CLI, alespoň prozatím. Tato část projde ty nejdůležitější a nastínit důvody, které nepodporují, stejně jako řešení, pokud je potřebujete.

### <a name="global-commands"></a>Globální příkazy
DNU přišel s konceptem nazvaným "globální příkazy". Jednalo se v podstatě o konzolové aplikace zabalené jako balíčky NuGet se skriptem prostředí, který by vyvolal dnx, který jste zadali ke spuštění aplikace.

ClI nepodporuje tento koncept. Podporuje však koncept přidání příkazů pro projekt, které lze vyvolat pomocí `dotnet <command>` známé syntaxe.

### <a name="installing-dependencies"></a>Instalace závislostí
Od v1 rozhraní PŘÍKAZOVÉHO PŘÍKAZU jádra `install` .NET nemá příkaz pro instalaci závislostí. Chcete-li nainstalovat balíček z NuGet, budete muset přidat jako `project.json` závislost do `dotnet restore` souboru a pak spustit[(viz poznámka](#dotnet-restore-note)).

### <a name="running-your-code"></a>Spuštění kódu
Kód lze spustit dvěma hlavními způsoby. Jeden je ze `dotnet run`zdroje, s . Na `dnx run`rozdíl od , to nebude dělat žádné kompilace v paměti. Bude skutečně `dotnet build` vyvolat k sestavení kódu a potom spustit vytvořený binární soubor.

Jiný způsob, `dotnet` jak je použití sám spustit kód. To se provádí poskytnutím cesty `dotnet path/to/an/assembly.dll`k sestavení: .

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migrace projektu DNX do rozhraní .NET Core CLI
Kromě použití nových příkazů při práci s kódem, existují tři hlavní věci vlevo v migraci z DNX:

1. `global.json` Pokud jej máte, můžete soubor použít, pokud jej budete moci používat.
2. Migrace samotného souboru`project.json`projektu ( ) na nástroje vykreslování lisování lisů.
3. Migrace z libovolného řešení API DNX na jejich protějšky BCL.

### <a name="changing-the-globaljson-file"></a>Změna souboru global.json
Soubor `global.json` se chová jako soubor řešení pro projekty RC1 a RC2 (nebo novější). V pořadí pro .NET Core CLI (stejně jako Visual Studio) rozlišovat mezi `"sdk": { "version" }` RC1 a novější verze, používají vlastnost, aby se rozlišování, který projekt je RC1 nebo novější. Pokud `global.json` nemá tento uzel vůbec, předpokládá se, že nejnovější.

Chcete-li `global.json` aktualizovat soubor, odeberte vlastnost nebo ji nastavte na přesnou verzi nástrojů, které chcete použít, v tomto případě **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migrace souboru projektu

CLI a DNX oba používají stejný základní `project.json` projektový systém založený na souboru. Syntaxe a sémantiku souboru projektu jsou téměř stejné, s malými rozdíly na základě scénářů. Existují také některé změny schématu, které můžete vidět v [souboru schématu](http://json.schemastore.org/project).

Pokud vytváříte konzolovou aplikaci, je třeba do souboru projektu přidat následující úryvek:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

To instruuje k vyzařování `dotnet build` vstupního bodu pro vaši aplikaci, efektivně, takže váš kód runnable. Pokud vytváříte knihovnu tříd, jednoduše vynechete výše uvedenou část. Samozřejmě, jakmile přidáte výše uvedený úryvek do `project.json` souboru, musíte přidat statický vstupní bod. S přechodem z DNX, DI služby, které poskytuje již nejsou k dispozici, `static void Main()`a proto to musí být základní .NET vstupní bod: .

Pokud máte v oddílu "příkazy" v aplikaci `project.json`, můžete ji odebrat. Některé příkazy, které dříve existovaly jako příkazy DNU, například příkazy rozhraní příkazu CLI rozhraní entity framework, jsou portovány jako rozšíření pro projekt na rozhraní příkazového příkazu. Pokud jste vytvořili vlastní příkazy, které používáte ve svých projektech, je třeba je nahradit rozšířením příkazového příkazu. V tomto případě `commands` uzel `project.json` v musí být nahrazen `tools` uzla a je třeba uvést seznam závislostí nástroje.

Po dokončení těchto věcí se musíte rozhodnout, jaký typ přenositelnosti si pro aplikaci přejete. S rozhraním .NET Core jsme investovali do poskytování spektra možností přenositelnosti, ze kterých si můžete vybrat. Můžete například chtít mít plně *přenosnou* aplikaci nebo můžete mít *samostatnou aplikaci.* Možnost přenosné aplikace je spíše jako aplikace rozhraní .NET Framework: potřebuje sdílenou komponentu k jeho spuštění v cílovém počítači (.NET Core). Samostatná aplikace nevyžaduje .NET Core, které mají být nainstalovány na cíl, ale je nutné vytvořit jednu aplikaci pro každý operační systém, který chcete podporovat. Tyto typy přenositelnosti a další jsou popsány v dokumentu [typu přenositelnosti aplikace.](../deploying/index.md)

Jakmile provedete volání o jaký typ přenositelnosti, musíte změnit cílené rozhraní. Pokud jste psali aplikace pro .NET Core, jste s největší pravděpodobností používali `dnxcore50` jako cílené rozhraní. S rozhraní maty a změny, které přinesl nový [standard .NET,](../../standard/net-standard.md) musí být rámec jedním z následujících:

1. `netcoreapp1.0`- pokud píšete aplikace na .NET Core (včetně ASP.NET core aplikací)
2. `netstandard1.6`- pokud píšete knihovny tříd pro .NET Core

Pokud používáte `dnx` jiné cíle, jako `dnx451` budete muset změnit ty stejně. `dnx451`by měla `net451`být změněna na .
Další informace naleznete v tématu [standardu .NET.](../../standard/net-standard.md)

Vaše `project.json` je nyní většinou připraven. Musíte projít seznam závislostí a aktualizovat závislosti na jejich novější verze, zejména pokud používáte ASP.NET základní závislosti. Pokud jste používali samostatné balíčky pro řešení API BCL, můžete použít balíček runtime, jak je vysvětleno v dokumentu [typu přenositelnosti aplikace.](../deploying/index.md)

Jakmile budete připraveni, můžete zkusit obnovení s `dotnet restore` ( viz[poznámka](#dotnet-restore-note)). V závislosti na verzi vašich závislostí může dojít k chybám, pokud NuGet nelze vyřešit závislosti pro jeden z výše uvedených cílových rozhraní. Jedná se o problém "point-in-time"; jak čas postupuje, bude stále více balíčků zahrnovat podporu těchto rámců. Pro tuto chvíli, pokud narazíte na `imports` to, `framework` můžete použít příkaz v rámci uzlu určit NuGet, že můžete obnovit balíčky cílení na rozhraní v rámci "imports" prohlášení.
Chyby obnovení, které získáte v tomto případě by měl poskytnout dostatek informací, které vám řeknou, které architektury je třeba importovat. Pokud jste mírně ztraceni nebo nové, obecně, `dnxcore50` `portable-net45+win8` zadání `imports` a v prohlášení by měl udělat trik. JSON úryvek níže ukazuje, jak to vypadá:

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Spuštění `dotnet build` se zobrazí případné chyby sestavení, i když by nemělo být příliš mnoho z nich. Poté, co váš kód je sestavení a běží správně, můžete vyzkoušet s běžec. Spusťte `dotnet <path-to-your-assembly>` a uvidíte, že běží.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
