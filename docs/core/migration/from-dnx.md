---
title: Migrace z DNX na .NET Core rozhraní příkazového řádku
description: Migrujte pomocí nástrojů pro .NET Core rozhraní příkazového řádku nástroje DNX.
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.openlocfilehash: dd3c31b88b619799e6b2e2596127d64d84918ca0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217448"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migrace z DNX na .NET Core rozhraní příkazového řádku (project.json)

## <a name="overview"></a>Přehled
RC1 systému .NET Core a ASP.NET Core 1.0 zavedl DNX nástrojů. RC2 verzi .NET Core a ASP.NET Core 1.0 se přesune ze DNX rozhraní příkazového řádku .NET Core.

Jako mírné aktualizačního programu můžeme recap, co byl DNX o. DNX byla modulu runtime a nástrojů, použít k sestavení .NET Core a, přesněji řečeno, aplikace ASP.NET Core 1.0. Se skládal z 3 hlavní části:

1. DNVM - instalační skript pro získání DNX
2. DNX (Dotnet provádění Runtime) – modul runtime, který provede kódu
3. DNŮ (Dotnet vývojáře nástroj) - nástrojů pro správu závislosti, vytváření a publikování aplikací

Se zavedením rozhraní příkazového řádku jsou všechny výše uvedené teď součástí jedné sady nástrojů. Ale protože DNX byla k dispozici v RC1 časový rámec, můžete mít projekty, které byly vytvořeny pomocí jeho, kterou chcete přesunout do nových nástrojů rozhraní příkazového řádku. 

Tato příručka k migraci se bude zabývat essentials o tom, jak migrovat projekty z DNX a na .NET Core rozhraní příkazového řádku. Pokud právě začínáte projektu na .NET Core od začátku, můžete přeskočit volně tohoto dokumentu. 

## <a name="main-changes-in-the-tooling"></a>Hlavní změny v nástroji
V nástroji, který by měl být uvedených nejprve jsou některé obecné změny. 

### <a name="no-more-dnvm"></a>Žádné další DNVM
DNVM zkratka pro *správce verzí DotNet* byl skriptu prostředí bash/PowerShell použít k instalaci DNX na váš počítač. Ho pomohl uživatelům získat DNX, které potřebují ze kanál, který zadal (nebo výchozí hodnoty), a také označit určité DNX "aktivní", který by umístí jej $PATH pro dané relace. To by umožnilo pomocí různých nástrojů.

DNVM byla přerušena, protože byla provedena redundantní změny brzo nástroje .NET Core rozhraní příkazového řádku se sadou funkcí.

Nástroje příkazového řádku pocházet zabalené dvěma hlavními způsoby:

1. Nativní instalačních programů pro danou platformu
2. Instalace skriptu jiných situacích (třeba servery položek konfigurace)

Zadána tato funkce DNVM install nejsou potřeba. Ale co o výběr funkcím runtime? 

Odkaz modul runtime v vaší `project.json` přidáním určité verze balíčku do vaší závislosti. Díky této změně aplikace budou moci používat nový modul runtime bits. Získání těchto bits do počítače, je stejné jako u rozhraní příkazového řádku: instalaci modulu runtime využít jeden z nativní instalační programy podporuje nebo jeho instalační skript. 

### <a name="different-commands"></a>Jiné příkazy
Pokud jste používali DNX, můžete použít některé příkazy z jednoho z jeho tři části (DNX, dnů nebo DNVM). Pomocí rozhraní příkazového řádku, některé z těchto příkazů změnit, některé nejsou dostupné a některé jsou stejné, ale mají mírně odlišné sémantiku. 

Následující tabulka uvádí mapování mezi příkazy DNX/dnů a jejich protějšky rozhraní příkazového řádku.


| Příkaz DNX                       | Příkaz rozhraní příkazového řádku       | Popis                                                                                                       |
|--------------------------------   |----------------   |-----------------------------------------------------------------------------------------------------------------  |
| dnx spustit                           | Spustit DotNet.        | Spuštění kódu ze zdroje.                                                                                             |
| sestavení dnů                         | sestavení DotNet.      | Sestavení binární IL kódu.                                                                                  |
| pack dnů                          | pack DotNet.       | Balíček NuGet balíček kódu.                                                                          |
| dnx \[příkaz] (například "dnx web")   | NENÍ K DISPOZICI\*             | DNX světě spusťte příkaz, jak jsou definovány v project.json.                                                       |
| instalace dnů                       | NENÍ K DISPOZICI\*             | Na světě DNX nainstalujte balíček jako závislost.                                                              |
| obnovení dnů                       | obnovení DotNet.    | Obnovte závislosti zadaný v souboru project.json. ([viz Poznámka](#dotnet-restore-note))                                                               |
| publikování dnů                       | publikování DotNet.    | Publikování aplikace pro nasazení v jednom ze tří formuláře (přenosné přenosné s nativní a samostatná).    |
| wrap dnů                          | NENÍ K DISPOZICI\*             | DNX světě zabalit project.json v csproj.                                                                      |
| příkazy dnů                      | NENÍ K DISPOZICI\*             | DNX světě spravujte příkazů globálně nainstalované.                                                             |

(\*) – tyto funkce nejsou podporovány v rozhraní příkazového řádku záměrné. 

## <a name="dnx-features-that-are-not-supported"></a>DNX funkce, které nejsou podporovány
Jako v tabulce výš ukazuje jsou funkcí na světě DNX, který jsme se rozhodli podpora v rozhraní příkazového řádku, alespoň na čas, který. V této části se projít nejdůležitější ty a popisují důvody, které nejsou podporovány je a také alternativní řešení Chcete-li.

### <a name="global-commands"></a>Globální příkazy
DNŮ byly dodány s názvem "globální příkazy" konceptu. Tyto byly v podstatě konzolové aplikace zabalené jako balíčky NuGet se skript prostředí, který by měl vyvolat DNX, který jste zadali ke spuštění aplikace. 

Rozhraní příkazového řádku nepodporuje tento koncept. Ale podporuje koncept přidání příkazů na projektu, které lze vyvolat pomocí známé `dotnet <command>` syntaxe.

### <a name="installing-dependencies"></a>Instalování závislostí
Od verze v1, nástroje příkazového řádku .NET Core nemají `install` příkaz pro instalaci závislosti. Chcete-li nainstalovat balíček z NuGet, museli byste ji přidat jako závislost pro vaše `project.json` souboru a poté spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)). 

### <a name="running-your-code"></a>Spuštěním kódu
Pro spouštění vašeho kódu dvěma způsoby. Jedním ze zdroje, je s `dotnet run`. Na rozdíl od `dnx run`, to nebude provádět žádné kompilace v paměti. Ve skutečnosti se vyvolat `dotnet build` vytvářet kód a spusťte integrovaný binárního souboru. 

Další možností je pomocí `dotnet` sám sebe pro spouštění vašeho kódu. K tomu je potřeba poskytnutí cesty na vaše sestavení: `dotnet path/to/an/assembly.dll`. 

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migrace DNX projektu na .NET Core rozhraní příkazového řádku
Kromě používání nové příkazy při práci s kódu, existují tři hlavní věci left v migraci z DNX:

1. Migrace `global.json` soubor, pokud jste mohli používat rozhraní příkazového řádku.
2. Migrace souboru projektu (`project.json`) své vlastní nástrojů rozhraní příkazového řádku.
3. Migrace z rozhraní API žádné DNX svým BCL. 

### <a name="changing-the-globaljson-file"></a>Změna souboru global.json
`global.json` Souboru chová jako soubor řešení pro RC1 a RC2 (nebo novější) projekty. Aby rozhraní příkazového řádku nástroje (stejně jako Visual Studio) k rozlišení mezi RC1 a novějších verzích, používají `"sdk": { "version" }` vlastnost odlišení který projekt je RC1 nebo novější. Pokud `global.json` nemá tento uzel vůbec, předpokládá se nejnovější. 

Aby bylo možné aktualizovat `global.json` souboru, buď odeberte vlastnost nebo ji nastavte na konkrétní verzi nástroje, které chcete použít v tomto případě **1.0.0-preview2-003121**:

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migrace souboru projektu
Rozhraní příkazového řádku a DNX používají stejné základní projekt systém na základě `project.json` souboru. Syntaxe a sémantika souboru projektu jsou podstatě stejné, s malé rozdíly podle scénáře. Existují také některé změny schématu, které se zobrazí [soubor schématu](http://json.schemastore.org/project).

Pokud vytváříte konzolovou aplikaci, musíte do souboru projektu přidejte následující fragment kódu:

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Tím se nastaví `dotnet build` pro vydávání vstupní bod pro vaši aplikaci fakticky spustitelného kódu. Pokud vytváříte knihovny tříd, jednoduše vynechejte části výše. Samozřejmě, po přidání výše uvedeném fragmentu k vaší `project.json` souboru, je nutné přidat statické vstupní bod. S přechodem vypnout DNX poskytované DI již nejsou k dispozici, a proto to musí být základní vstupní bod .NET: `static void Main()`.

Pokud máte části "příkazy" vaší `project.json`, můžete jej odebrat. Některé příkazy, které používají k existovat jako dnů příkazy, jako je například rozhraní Entity Framework příkazového řádku, jsou právě přesně do být – projekt rozšíření rozhraní příkazového řádku. Pokud jste vytvořili vlastní příkazy, které používáte ve vašich projektů, budete muset nahraďte rozšíření rozhraní příkazového řádku. V takovém případě `commands` uzlu v `project.json` musí být nahrazen `tools` uzlu a vyžaduje určení závislostí nástroje. 

Poté, co jsou tyto věci dokončí, musíte rozhodnout, jaký typ přenositelnost chcete pro aplikaci. S .NET Core jsme investovaly do poskytování spektrum přenositelnost možnosti, které lze vybírat. Například můžete chtít mít plně *přenosné* aplikace nebo můžete nastavit, aby se *nezávislý* aplikace. Možnost přenosné aplikace se víc podobá pracovní aplikace rozhraní .NET Framework: je nutné sdílená součást provést v cílovém počítači (.NET Core). Samostatný aplikace nevyžaduje .NET Core nainstalována na cílový, ale budete muset vytvořit jednu aplikaci pro každý operační systém, které chcete podporovat. Tyto typy přenositelnost a další jsou popsané v [typ přenositelnost aplikace](../deploying/index.md) dokumentu. 

Po volání na jaký typ přenositelnost chcete budete muset změnit vaše cílové framework(s). Pokud jste zapisovali aplikací pro .NET Core, pravděpodobně používáte `dnxcore50` jako cílové rozhraní. Pomocí rozhraní příkazového řádku a změny, nové [.NET Standard](../../standard/net-standard.md) uvést do režimu, rozhraní musí být jeden z následujících:

1. `netcoreapp1.0` -Pokud píšete aplikace na .NET Core (včetně aplikací ASP.NET Core)
2. `netstandard1.6` -Pokud píšete knihovny tříd pro .NET Core

Pokud používáte jiné `dnx` cílem, jako je třeba `dnx451` budete muset změnit také ty. `dnx451` by mělo být změněno na `net451`. Podrobnosti najdete [.NET Standard](../../standard/net-standard.md) Další informace. 

Vaše `project.json` je většinou připraven. Budete muset projít seznamu závislosti a závislosti aktualizovat na novější verze, zvlášť pokud používáte ASP.NET Core závislosti. Pokud jste používali samostatné balíčky pro rozhraní API BCL, můžete použít balíček modulu runtime, jak je popsáno v [typ přenositelnost aplikace](../deploying/index.md) dokumentu. 

Jakmile budete připraveni, můžete se pokusit o obnovení s `dotnet restore` ([viz Poznámka](#dotnet-restore-note)). V závislosti na verzi vašeho závislostí mohou nastat chyby, pokud NuGet nejde vyřešit závislosti pro jednu z výše uvedených cílové architektury. Toto je problém "bodu v čase"; v průběhu času bude více balíčků zahrnují podporu pro tyto architektury. Teď, pokud spustíte do této, můžete použít `imports` v rámci `framework` uzlu určení na NuGet, že ji můžete obnovit balíčky cílení na rozhraní v rámci příkazu "importuje". Obnovení chyby, které máte v takovém případě by měl poskytovat dostatek informací s oznámením, která rozhraní, která chcete importovat. Pokud jste mírně ztracené nebo pro toto nové, obecně zadání `dnxcore50` a `portable-net45+win8` v `imports` příkaz udělat podvodné. Fragmentu kódu JSON níže ukazuje, jak vypadá takto:

```json
    "frameworks": {
        "netcoreapp1.0": { 
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

Spuštění `dotnet build` všechny chyby případné sestavení se zobrazí, když by neměl být příliš mnoho. Po kódu je sestavení a funguje správně, můžete ho s nástroj runner otestovat. Spuštění `dotnet <path-to-your-assembly>` a prohlédněte si ho spustit.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]