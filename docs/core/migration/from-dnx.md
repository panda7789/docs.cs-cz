---
title: Migrace z DNX až po .NET Core CLI
description: Migrace z DNX nástroje, nástroje rozhraní příkazového řádku .NET Core pomocí.
ms.date: 06/20/2016
ms.custom: seodec18
ms.openlocfilehash: da2b3bdb6bf6cb5cdf772d54996471d54fe0a92b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674862"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migrace z DNX až po .NET Core CLI (project.json)

## <a name="overview"></a>Přehled
Vydání .NET Core a ASP.NET Core 1.0 RC1 zavedené DNX nástroje. V RC2 verzi .NET Core a ASP.NET Core 1.0 přesunuta z DNX na rozhraní příkazového řádku .NET Core.

Jako lehká aktualizačního programu Pojďme rekapitulace, DNX byl o. DNX byl modul runtime a sadu nástrojů sloužící k sestavení .NET Core a přesněji řečeno, aplikace ASP.NET Core 1.0. To se skládal z 3 hlavních částí:

1. DNVM - instalační skript pro získání DNX
2. DNX (Dotnet prováděcí modul Runtime) – modul runtime, který se spustí váš kód
3. DNŮ (Dotnet vývojářské nástroje) – nástroje pro správu závislostí, sestavování a publikování aplikací

Se zavedením rozhraní příkazového řádku všechny výše uvedené jsou teď součástí jedné sady nástrojů. Ale protože DNX byla k dispozici v RC1 časový rámec, můžete mít projekty, které byly sestaveny, kterou chcete přesunout nových nástrojů rozhraní příkazového řádku. 

Tato příručka k migraci bude zabývat Základy o tom, jak migrovat projekty z DNX a do příkazového řádku .NET Core. Pokud právě začínáte projekt v rozhraní .NET Core od začátku, můžete přeskočit volně tohoto dokumentu. 

## <a name="main-changes-in-the-tooling"></a>Hlavní změny nástroje
Existují některé obecné změny nástroje, musí nejprve uvedeno. 

### <a name="no-more-dnvm"></a>Žádné další DNVM
DNVM zkratka pro *správce verzí DotNet* byl použitý k instalaci DNX na svém počítači skript bashe nebo Powershellu. Na tom uživatelé získat DNX, které potřebujete z informačního kanálu, který určily (nebo výchozí hodnoty), i označit určité DNX "aktivní", který by umístí jej $PATH pro danou relaci. To by umožnilo pomocí různých nástrojů.

DNVM bylo přerušeno, protože byla provedena redundantní změn v nástrojích příkazového řádku .NET Core se sadou funkcí.

Nástroje rozhraní příkazového řádku jsou uspořádaná do dva hlavní způsoby:

1. Nativních instalačních programů pro danou platformu
2. Nainstalujete skript pro jiných situacích (třeba servery CI)

To směru, instalace funkce DNVM nejsou potřeba. Ale co o výběr funkce modulu runtime? 

Odkazovat runtime ve vaší `project.json` tak, že přidáte balíček určitou verzi závislosti. Díky této změně vaší aplikace budete moci použít nové bity modulu runtime. Získání těchto bits do počítače je stejný jako u rozhraní příkazového řádku: Instalace modulu runtime prostřednictvím jednoho z nativních instalačních programů podporuje nebo prostřednictvím jeho instalační skript. 

### <a name="different-commands"></a>Různé příkazy
Pokud jste používali DNX, můžete použít některé příkazy z jednoho z jeho tří částí (DNX, dnů nebo DNVM). Pomocí rozhraní příkazového řádku, některé z těchto příkazů změnit, některé nejsou k dispozici a některé jsou stejné, ale mají mírně odlišnou sémantiku. 

Následující tabulka uvádí mapování mezi příkazy DNX/dnů a jejich protějšky v rozhraní příkazového řádku.


| Příkaz DNX                       | Rozhraní příkazového řádku       | Popis                                                                                                       |
|--------------------------------   |----------------   |-----------------------------------------------------------------------------------------------------------------  |
| Spustit dnx                           | Spusťte příkaz DotNet        | Spuštění kódu ze zdroje.                                                                                             |
| třeba sestavení                         | DotNet sestavení      | Sestavení binární soubor IL kódu.                                                                                  |
| třeba balíček                          | balíčku DotNet       | Zabalíte balíček NuGet kódu.                                                                          |
| dnx \[příkazu] (například "dnx web")   | NENÍ K DISPOZICI\*             | Ve světě DNX spusťte příkaz definované souboru project.json.                                                       |
| třeba instalace                       | NENÍ K DISPOZICI\*             | Ve světě DNX nainstalujte balíček jako závislost.                                                              |
| dnů obnovení                       | DotNet restore    | Obnovte závislosti podle vašeho souboru project.json. ([viz Poznámka](#dotnet-restore-note))                                                               |
| publikování dnů                       | publikování DotNet    | Publikování aplikace pro nasazení v jednom ze tří formulářů (přenosná, přenosná s nativní a samostatné).    |
| wrap dnů                          | NENÍ K DISPOZICI\*             | Ve světě DNX zabalte project.json v souboru csproj.                                                                      |
| příkazy dnů                      | NENÍ K DISPOZICI\*             | Ve světě DNX Správa globálně nainstalovanou příkazů.                                                             |

(\*) – tyto funkce nejsou podporovány v rozhraní příkazového řádku návrhu. 

## <a name="dnx-features-that-are-not-supported"></a>DNX funkce, které nejsou podporovány
Jako tabulka nahoře ukazuje jsou funkce z DNX světa, které jsme se rozhodli podpora v rozhraní příkazového řádku, alespoň prozatím. Tato část se projít ty nejdůležitější a popisují odůvodnění nejsou podporovány je stejně jako alternativní řešení, pokud je potřebujete.

### <a name="global-commands"></a>Globální příkazy
TŘEBA dodán jako součást pojem nazývá "globální příkazy". Tohle byly v podstatě konzolové aplikace podobu balíčky NuGet se skript prostředí, který by měl vyvolat DNX jste zadali a spusťte aplikaci. 

Rozhraní příkazového řádku nepodporuje tento koncept. , Ale podporují koncept přidání příkazů jednotlivých projektů, které je možné vyvolat pomocí známé `dotnet <command>` syntaxe.

### <a name="installing-dependencies"></a>Instalování závislostí
Od verze v1, nástroje rozhraní příkazového řádku .NET Core nemají `install` příkaz pro instalování závislostí. Abyste mohli nainstalovat balíček z Nugetu, je třeba ho přidat jako závislost na vaše `project.json` souboru a pak spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)). 

### <a name="running-your-code"></a>Spuštění kódu
Existují dva hlavní způsoby, jak spustit kód. Jednou ze zdroje, je s `dotnet run`. Na rozdíl od `dnx run`, to nebude provádět žádné kompilace v paměti. Ve skutečnosti se vyvolá `dotnet build` sestavení kódu a potom spusťte sestavené binární soubor. 

Dalším způsobem používá `dotnet` své vlastní spuštění kódu. Je to tím, že poskytuje cestu k sestavení: `dotnet path/to/an/assembly.dll`. 

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migrace projektu DNX na .NET Core CLI
Kromě použití nových příkazů, při práci s kódem, existují tři hlavní věci v migrace z DNX:

1. Migrace `global.json` soubor, pokud jste si ji mohli použít rozhraní příkazového řádku.
2. Migrace souboru projektu (`project.json`) samotné nástrojů rozhraní příkazového řádku.
3. Migrace z libovolné rozhraní API DNX na své ekvivalenty BCL. 

### <a name="changing-the-globaljson-file"></a>Změna soubor global.json
`global.json` Soubor lze chápat jako soubor řešení pro RC1 a RC2 (nebo novější) projekty. Aby rozhraní příkazového řádku nástroje (stejně jako Visual Studio) k rozlišení RC1 a novějších verzích, používají `"sdk": { "version" }` vlastnost rozlišovat kterého projektu se RC1 nebo novější. Pokud `global.json` nemá tento uzel, se předpokládá, že se na nejnovější verzi. 

Abyste mohli aktualizovat `global.json` souboru, buď odeberte vlastnost nebo ji nastavte na konkrétní verzi nástroje, které chcete použít v tomto případě **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migrace souboru projektu
Rozhraní příkazového řádku a DNX pomocí stejného systému základního projektu na základě `project.json` souboru. Syntaxe a sémantiky soubor projektu jsou podstatě totéž, s založené na scénářích malé rozdíly. Existují také některé změny schématu, která se zobrazí [soubor schématu](http://json.schemastore.org/project).

Pokud vytváříte konzolovou aplikaci, budete muset přidat následující fragment kódu do souboru projektu:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Toto dá pokyn `dotnet build` vygenerovat vstupní bod pro vaši aplikaci fakticky spustitelného kódu. Pokud vytváříte knihovnu tříd, jednoduše vynechejte výše uvedené části. Samozřejmě, po přidání výše uvedeném fragmentu do vaší `project.json` souboru, je třeba přidat statická vstupní bod. S přechodem na vypnuto DNX poskytované DI už nejsou k dispozici, a proto to musí být základní vstupní bod .NET: `static void Main()`.

Pokud máte části "příkazy" vaší `project.json`, můžete ho odebrat. Některé příkazy, které používají existovat jako třeba příkazy, jako je například příkazy rozhraní příkazového řádku Entity Framework, jsou při přenosu bude – projekt rozšíření rozhraní příkazového řádku. Pokud jste vytvořili vlastní příkazy, které používáte ve svých projektech, musíte nahradit je jejich rozšíření rozhraní příkazového řádku. V takovém případě `commands` uzel v `project.json` musí být nahrazen `tools` uzlu a je potřeba seznam závislosti, nástroje. 

Po dokončení těchto věcí, musíte se rozhodnout, jaký typ přenositelnost chcete pro aplikaci. S .NET Core jsme investovali do poskytuje celé spektrum od přenositelnost možnosti, které můžete vybrat z. Například můžete chtít mít plně *přenosné* aplikace nebo můžete chtít mít *samostatná* aplikace. Možnost přenosné aplikace se víc pracovních aplikací rozhraní .NET Framework: potřebuje Sdílená komponenta ke spuštění na cílovém počítači (.NET Core). Samostatné aplikace nevyžaduje rozhraní .NET Core na cílovém počítači nainstalována, ale budete muset vytvořit jednu aplikaci pro každý operační systém, které chcete podporovat. Tyto typy přenositelnost a další jsou popsány v [typ přenositelnosti aplikace](../deploying/index.md) dokumentu. 

Po provedení volání na jaký typ má přenositelnost, budete muset změnit cílovou architekturu. Pokud jste zapisovali aplikací pro .NET Core, pravděpodobně používáte `dnxcore50` jako cílové rozhraní. Pomocí rozhraní příkazového řádku a změny, které nový [.NET Standard](../../standard/net-standard.md) převést do režimu, rozhraní musí být jedním z následujících akcí:

1. `netcoreapp1.0` – Při psaní aplikací v rozhraní .NET Core (včetně aplikací ASP.NET Core)
2. `netstandard1.6` -Pokud píšete knihoven tříd pro .NET Core

Pokud používáte jiné `dnx` cílí, jako je třeba `dnx451` budete muset změnit ty také. `dnx451` měli byste místo `net451`. Najdete [.NET Standard](../../standard/net-standard.md) tématu pro další informace. 

Vaše `project.json` většinou připravený. Budete muset projít seznamu závislosti a závislosti aktualizovat na novější verze, zejména v případě, že používáte závislostí ASP.NET Core. Pokud jste používali samostatné balíčky pro BCL API, můžete použít balíček modulu runtime, jak je vysvětleno v [typ přenositelnosti aplikace](../deploying/index.md) dokumentu. 

Jakmile budete připraveni, můžete se pokusit o obnovení s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)). V závislosti na verzi závislosti mohou nastat chyby, pokud NuGet nejde vyřešit závislosti pro jednu z výše uvedených cílová rozhraní. Toto je problém "bodu v čase"; v průběhu času bude více balíčků zahrnují podporu pro tyto architektury. Teď, pokud narazíte na to, můžete použít `imports` příkaz v rámci `framework` uzel určení na NuGet, můžete obnovit balíčky cílí na rozhraní framework v rámci příkazu "importuje". Obnovení chyby, které získáte v tomto případě by měla poskytnout dostatek informací, které vám říct, které rozhraní, které potřebujete k importu. Pokud se mírně ztracené nebo na tuto novou, obecně platí, určení `dnxcore50` a `portable-net45+win8` v `imports` příkaz by měl provádět zdvih. Následující fragment kódu JSON ukazuje, jak to vypadá jako:

```json
    "frameworks": {
        "netcoreapp1.0": { 
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Spuštění `dotnet build` se zobrazí případné chyby konečné sestavení, i když by neměl být příliš mnoho z nich. Poté, co váš kód je sestavení a správně funguje, si to můžete otestovat pomocí Spouštěče. Spustit `dotnet <path-to-your-assembly>` a vidět ji spustit.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]