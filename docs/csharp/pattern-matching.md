---
title: Shoda vzoru – průvodce v C#
description: Další informace o výrazy v jazyce C# pro porovnávání
keywords: Rozhraní .NET, rozhraní .NET core, C#
ms.date: 01/24/2017
ms.author: wiwagn
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: a0f80fc2c019cefa81506d9dcdeabc57a1e98c2b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="pattern-matching"></a>Porovnávání vzorů #

Vzory otestovat, zda hodnota má určitou *tvaru*a můžete *extrahovat* informace z hodnotu, pokud má odpovídající tvaru. Shoda vzoru poskytuje přesnější syntaxe pro algoritmy, které už používáte ještě dnes. Vytvoříte již algoritmy pomocí stávající syntaxe porovnávání vzorů. Psaní `if` nebo `switch` příkazy, které testovací hodnoty. Pokud tyto příkazy shodují, pak rozbalte a použít informace z tuto hodnotu. Nové prvky syntaxe jsou rozšíření se příkazy, které jste již obeznámeni s: `is` a `switch`. Tyto nové přípony kombinovat testování hodnotu a extrakci těchto informací.

V tomto tématu se podíváme na nové syntaxe ukazují, jak umožňuje čtení, přesné kódu. Shoda vzoru umožňuje idioms kde dat a kód jsou oddělené, na rozdíl od objektově orientované návrhů kde data a metody, které s nimi manipulovat jsou úzce spojeny.

Pro ilustraci tyto nové idioms, budeme pracovat s struktury, které představují geometrické obrazce pomocí příkazů porovnávání vzorů. Znáte pravděpodobně vytváření hierarchie tříd a vytváření [virtuální metody a přepsané metody](methods.md#inherited) k přizpůsobení chování objektů na základě runtime typu objektu.

Tyto techniky nejsou možné pro data, která neodpovídá struktuře hierarchie tříd. Pokud data a metody jsou oddělené, je potřeba další nástroje. Nové *porovnávání vzorů* konstrukce povolit čisticí syntaxe sloužící ke zkoumání dat a manipulaci s řízení toku na základě těchto dat žádné podmínky. Již zápisu `if` příkazy a `switch` , testovací hodnoty proměnné. Psaní `is` příkazy, které testovací typ proměnné. *Shoda vzoru* přidá nové funkce se tyto příkazy.

V tomto tématu vytvoříte metodu, která vypočítá oblasti jiné geometrické obrazce. Ale můžete to udělat bez nutnosti techniky objektově orientované a vytvoření hierarchie tříd pro různých tvarů.
Budete používat *porovnávání vzorů* místo. Další zdůraznit, že používáme nejsou dědičnosti, budete provedete jednotlivé obrazce `struct` místo třídu. Všimněte si, že jiný `struct` typy nelze zadat běžné uživatelem definovaný základní typ, takže dědičnosti není možné návrhu.
Při procházení této ukázce protějšek tento kód s tom, jak by strukturovaná jako objekt hierarchie. Když data je nutné zadat dotaz a manipulaci s není hierarchie tříd, porovnávání vzorů umožňuje velmi elegantní návrhů.

Namísto spuštění pomocí definice abstraktní tvar a přidávání tříd různých konkrétní tvaru, začneme místo jednoduché datové pouze definice pro každý geometrické obrazce:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z těchto struktur můžete napsat metodu, která vypočítá oblasti některé tvaru.

## <a name="the-is-type-pattern-expression"></a>`is` Zadejte vzor výrazu

Před C# 7.0, museli byste otestujte všechny typy v řadě `if` a `is` příkazy:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Jestli je výše uvedený kód classic výraz *typ vzor*: testujete proměnnou k určení typu a přepnutím různé akce v závislosti na typu.

Tento kód bude jednodušší pomocí rozšíření pro `is` výrazu přiřadit proměnné Pokud test úspěšné:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

V této aktualizované verzi `is` výraz jak testy proměnnou a přiřadí ji k nové proměnné správné typu. Navíc Všimněte si, že tato verze zahrnuje `Rectangle` typu, který je `struct`. Nové `is` výraz funguje s typy hodnot, jakož i odkazové typy.

Jazyk pravidla pro vzor odpovídající výrazy umožňuje vyhnout se zneužití výsledky výrazu shody. V příkladu výše, proměnné `s`, `c`, a `r` pouze v oboru a výborný přiřazený, když se odpovídající vzor shody výrazy `true` výsledky. Pokud se pokusíte použít buď proměnné na jiné místo, vygeneruje kód chyby kompilátoru.

Podívejme se na obě tato pravidla podrobně počínaje oboru. Proměnná `c` nachází v oboru pouze v `else` větev první `if` příkaz. Proměnná `s` nachází v oboru v metodě `ComputeArea`. Důvodem je, že každou větev `if` příkaz vytváří samostatný obor pro proměnné. Ale `if` příkaz sám nemá. To znamená proměnných deklarovaných v `if` příkaz jsou ve stejném oboru jako `if` – příkaz (metoda v tomto případě.) Toto chování není specifické pro porovnávání vzorů, ale je definovaný chování pro proměnné obory a `if` a `else` příkazy.

Proměnné `c` a `s` jsou přiřazeny, kdy příslušné `if` příkazy jsou splněny kvůli výborný přiřazené při true mechanismus.

> [!TIP]
> Ukázky v tomto tématu použijte doporučené konstrukce, kde je vzor shody `is` výraz výborný přiřadí proměnné shoda v `true` větev `if` příkaz.
> Bylo možné změnit logiku vyslovením `if (!(shape is Square s))` a proměnná `s` by výborný přiřadit pouze v `false` firemní pobočky. To je platný C#, se nedoporučuje, protože je pro postupujte podle logiky více matoucí.

Tato pravidla znamená, že jste nepravděpodobné, že omylem přístupu výsledek výrazu vzor shody v případě, že tento vzor nebyl splněn.

## <a name="using-pattern-matching-switch-statements"></a>Použití porovnávání vzorů `switch` příkazy

Odehrává ve, musíte pro podporu dalších typů tvaru. S růstem počet podmínky testujete zjistíte to pomocí `is` výrazy pro porovnávání se může stát náročná. Kromě nutnosti `if` příkazy pro každý typ, který chcete zkontrolovat, `is` výrazy jsou omezeny na testování, pokud odpovídá jeden typ vstupu. V takovém případě budete zjistíte, že `switch` vzor odpovídající výrazy stane lepší volbou. 

Tradiční `switch` příkaz byl výraz vzor: to, že nepodporuje konstantní vzor.
Může porovnat proměnnou, do které žádné konstanta použít v `case` příkaz:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Pouze vzoru podporovanému službou `switch` příkaz byl vzoru konstantní. Byl další omezeno na číselnou typy a `string` typu.
Tato omezení jsme odebrali, a teď můžete napsat `switch` příkaz s použitím vzoru typu:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Shoda vzoru `switch` příkaz používá známé syntaxe pro vývojáře, kteří použili tradiční stylu jazyka C `switch` příkaz. Každý `case` je vyhodnocena a spouští kód pod podmínku, která odpovídá vstupní proměnné. Provádění kódu nelze "předáno" z jeden výraz case na další; syntaxe `case` příkaz vyžaduje, aby se každý `case` končit `break`, `return`, nebo `goto`.

> [!NOTE]
> `goto` Příkazy Přejít na jiný štítek jsou platné pouze pro konstantní vzor příkaz classic přepínače.

Důležité nové pravidel určujících `switch` příkaz. Omezení pro typ proměnné v `switch` výraz se odebraly.
Jakýkoli typ, jako například `object` v tomto příkladu může použít. Výrazy case již nejsou omezeny na konstantní hodnoty. Odebrání tohoto omezení znamená, že změna `switch` části může změnit chování programu.

Pokud omezené na konstantní hodnoty, víc než jeden `case` popisek může odpovídat hodnotě `switch` výraz. Kombinovat s pravidlo, všechny `switch` části nesmí přejít k další části, a ho a potom, `switch` části může měnit v libovolném pořadí bez ovlivnění chování.
Nyní, s více zobecněn `switch` záleží na pořadí každého oddílu, výrazy. `switch` Výrazy jsou vyhodnocovány v textové pořadí. Provádění přenese na první `switch` štítek, který odpovídá `switch` výraz.  
Všimněte si, že `default` případu bude spuštěn pouze pokud odpovídají žádné případu popisky. `default` Případ vyhodnotí poslední, bez ohledu na jeho textovou pořadí. Pokud neexistuje žádné `default` případ a žádná druhá `case` příkazy shodují, provádění pokračuje na následující příkaz `switch` příkaz. Žádná z `case` spuštění kódu popisky.

## <a name="when-clauses-in-case-expressions"></a>`when` Klauzule v `case` výrazy

Můžete použít zvláštní případy pro tyto obrazce, které mají 0 oblasti pomocí `when` klauzule ve `case` popisek. Čtverce s délkou straně 0 nebo kruh se serverem radius 0 má 0 oblasti. Určíte, že podmínky použití `when` klauzule ve `case` štítku:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Tato změna ukazuje několik důležitých bodů o nové syntaxe. První, více `case` štítky můžete použít na jednu `switch` části. Blok příkazu je provést, pokud žádné z těchto popisky je `true`. V této instanci Pokud `switch` výraz je kruh nebo čtverce oblasti, 0, vrátí metoda konstanta 0.

V tomto příkladu představuje dvou různých proměnných ve dvou `case` štítky pro první `switch` bloku. Všimněte si, že příkazy v tomto `switch` bloku nepoužívejte buď proměnné `c` (pro kruhu) nebo `s` (pro druhou mocninu).
Ani jeden z těchto proměnných výborný přiřazené v tomto `switch` bloku.
Pokud některý z těchto případů shodují, jasně proměnných byl přiřazen.
Je však možné zjistit *který* byl přiřazen při kompilaci, protože obou případech může odpovídat za běhu. Z tohoto důvodu většina časy při použití více `case` štítky pro stejného bloku, nebude zavést nové proměnné v `case` příkaz, nebo se použije pouze proměnné v `when` klauzule.

S přidá tyto obrazce oblasti, 0, můžeme přidat několik další typy tvar: obdélníku a trojúhelník:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Tuto sadu změn přidá `case` popisky degenerovanou případu a popisky a bloky pro každou novou tvarů. 

Nakonec můžete přidat `null` případ zajistit argument není `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Zvláštní chování `null` vzor je zajímavé protože konstanta `null` ve vzoru nemá typ, ale může být převedena na všechny odkaz na typ nebo typ s možnou hodnotou Null. Místo převést `null` do libovolného typu, který definuje jazyk `null` hodnota nebude odpovídat žádnému typ vzoru, bez ohledu na typ kompilaci proměnné. Díky tomuto chování nové `switch` na základě typu vzor konzistentní s `is` příkaz: `is` příkazy vždy vrátí `false` po hodnotu, se kontroluje `null`. Je také jednodušší: Po zaškrtnutí typ nepotřebujete dodatečnou kontrolu hodnotu null. Uvidíte, že ze skutečnosti, že neexistují žádné null kontroly v žádném případu bloků ukázky výše: nejsou potřebné, protože odpovídající vzoru typ zaručuje nenulovou hodnotu.

## <a name="var-declarations-in-case-expressions"></a>`var` deklarace v `case` výrazy

Zavedení `var` jako jeden z výrazů shodu porovnávací zavádí nové pravidel.

První pravidlo je, že `var` deklarace odpovídá normální typ odvozená pravidla: typ je odvodit jako statický typ výrazu přepínače. Od tohoto pravidla vždy odpovídá typu.

Druhé pravidlo je, že `var` deklarace nemá hodnotu null. Zkontrolujte, zda jiné výrazy typu vzor zahrnout. To znamená, že proměnná může mít hodnotu null a v takovém případě je nutné kontrolu hodnotu null.

Tyto dvě pravidla znamenají, že v mnoha případech `var` deklarace v `case` výraz odpovídá stejných podmínek, `default` výraz.
Protože všechny jiné než výchozí případem je upřednostňovaný k `default` případě `default` případ se nikdy neprovede.

> [!NOTE]
> Kompilátor není posílat upozornění v případech, kde `default` případ byla zapsána, ale nikdy spustí. To je konzistentní s aktuálním `switch` chování příkaz, kde uvedeny všechny možné případy.

Třetí pravidlo zavádí používá kde `var` případě může být užitečná. Představte si, že vedete porovnávací, kde je vstupní řetězec a hledání známých příkaz hodnoty. Můžete napsat něco podobného jako:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Případ odpovídá `null`, prázdný řetězec nebo libovolný řetězec, který obsahuje jenom prázdné znaky. Všimněte si, že předchozí kód používá `?.` operátor zajistit, že nevyvolá omylem <xref:System.NullReferenceException>. `default` Případ zpracovává všechny řetězcové hodnoty, které nejsou rozumí analyzátor tento příkaz.

Toto je jeden příklad, kde můžete vzít v úvahu `var` výraz, který se liší od případu `default` výraz.

## <a name="conclusions"></a>Závěrů

*Vzor párování konstrukce* vám umožní snadno spravovat tok řízení mezi různé proměnné a typy, které nejsou spojené hierarchie dědičnosti. Můžete také ovládat logiku používat všechny podmínky, které můžete testovat na proměnnou. Umožňuje vzory a idioms, které budete potřebovat více často, jak vytvořit více distribuovaných aplikací, kde jsou oddělené data a metody, které pracují s tato data. Můžete si všimnout, že tvar struktury, použít v této ukázce neobsahují žádné metody, vlastnosti stačí jen pro čtení.
Porovnávání vzorů. funguje s žádným typem data. Zápis výrazů, které prověřují objekt a rozhodnutí řízení toku na základě těchto podmínek.

Porovnat kód od této ukázky s návrh, který byste použili ve vytváření hierarchie tříd pro abstraktní `Shape` a konkrétní odvozené obrazce každou s vlastní implementace virtuální metodu pro výpočet oblasti. Budete často zjistíte, že vzor odpovídající výrazy mohou být velmi užitečné nástroje při práci s daty a chcete si nemuseli dělat starosti úložiště dat nezávislá si nemuseli dělat starosti chování.

