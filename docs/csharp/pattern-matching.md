---
title: Porovnávání vzorů C# – Průvodce
description: Další informace o výrazech porovnávání vzorů vC#
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: db509a0ebf1e205e9996ba8102757fe8c0b9ea3a
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501631"
---
# <a name="pattern-matching"></a>Porovnávání vzorů

Vzor testuje, že hodnota má určitý *tvar*a může *extrahovat* informace z hodnoty, když má odpovídající tvar. Porovnávání vzorů poskytuje stručnější syntaxi pro algoritmy, které už dnes používáte. Již jste vytvořili algoritmy porovnávání vzorů pomocí existující syntaxe. Zapisujete `if` nebo `switch` příkazy, které testují hodnoty. Když se tyto příkazy shodují, extrahujete a použijete informace z této hodnoty. Nové prvky syntaxe jsou rozšíření pro příkazy, které jste už obeznámeni s: `is` a `switch`. Tato nová rozšíření kombinují testování hodnoty a extrahuje tyto informace.

V tomto článku se podíváme na novou syntaxi a ukážeme vám, jak to umožňuje čitelný a výstižný kód. Porovnávání vzorů umožňuje idiomy, kde jsou data a kód odděleny, na rozdíl od objektů orientovaných na objekty, kde data a metody, které jsou s nimi manipulovány, jsou úzce spojeny.

Pro ilustraci těchto nových idiomy je možné pracovat se strukturami, které představují geometrické obrazce pomocí příkazů pro porovnávání vzorů. Pravděpodobně jste obeznámeni s vytvářením hierarchií tříd a vytvářením [virtuálních metod a přepsaných metod](methods.md#inherited) pro přizpůsobení chování objektu na základě typu modulu runtime objektu.

Tyto techniky nejsou možné pro data, která nejsou strukturovaná v hierarchii tříd. Když jsou data a metody oddělené, potřebujete další nástroje. Nové *vzory porovnávání* konstrukcí umožňují pomocí syntaxe čištění kontrolovat data a manipulovat tok řízení na základě jakékoli podmínky těchto dat. Již jste napsali příkazy `if` a `switch`, které testují hodnotu proměnné. Píšete `is` příkazy, které testují typ proměnné. *Porovnávání vzorů* přidává do těchto příkazů nové funkce.

V tomto článku vytvoříte metodu, která vypočítá oblast různých geometrických tvarů. Ale provedete to bez nutnosti vytvářet objektově orientované techniky a sestavovat hierarchii tříd pro různé tvary.
Místo toho použijete *porovnávání se vzorem* .
Při procházení této ukázky je třeba na rozdíl od tohoto kódu tento kód rozčleněný jako na hierarchii objektů. Pokud se data, která musíte dotazovat a manipulovat, není hierarchií tříd, porovnávání vzorů umožňuje elegantní návrhy.

Místo toho, aby se spouštěla definice abstraktního obrazce a přidala se různé konkrétní třídy tvarů, začněte místo toho, aby se pro každý geometrický tvar spouštěly jenom jednoduché datové definice:

[!code-csharp[ShapeDefinitions](../../samples/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z těchto struktur napíšeme metodu, která vypočítá oblast nějakého tvaru.

## <a name="the-is-type-pattern-expression"></a>Výraz vzoru typu `is`

Před C# 7,0 byste museli testovat každý typ v řadě `if` a `is` příkazy:

[!code-csharp[ClassicIsExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Výše uvedený kód je klasický výraz *vzoru typu*: testujete proměnnou pro určení jejího typu a provedení jiné akce založené na tomto typu.

Tento kód se bude jednodušší pomocí rozšíření pro výraz `is` pro přiřazení proměnné, pokud je test úspěšný:

[!code-csharp[IsPatternExpression](../../samples/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

V této aktualizované verzi výraz `is` testuje proměnnou a přiřadí ji k nové proměnné správného typu. Všimněte si také, že tato verze zahrnuje typ `Rectangle`, což je `struct`. Nový výraz `is` pracuje s typy hodnot a typy odkazů.

Pravidla jazyka pro výrazy porovnávání vzorů vám pomůžou vyhnout se nepříliš nepoužitým výsledkům výrazu shody. V předchozím příkladu jsou proměnné `s`, `c`a `r` pouze v oboru a jednoznačně přiřazeny, pokud mají příslušné výrazy porovnávání vzorů `true` výsledky. Pokud se pokusíte použít buď proměnnou v jiném umístění, kód vygeneruje chyby kompilátoru.

Pojďme si tato pravidla podrobněji prošetřit, počínaje oborem. Proměnná `c` je v oboru pouze ve větvi `else` prvního příkazu `if`. Proměnná `s` je v rozsahu `ComputeAreaModernIs`metody. To je proto, že každá větev příkazu `if` vytvoří samostatný obor pro proměnné. Nicméně samotný příkaz `if` ne. To znamená, že proměnné deklarované v příkazu `if` jsou ve stejném oboru jako příkaz `if` (metoda v tomto případě). Toto chování není specifické pro porovnávání se vzorem, ale je definované chování pro proměnné obory a `if` a `else` příkazy.

Proměnné `c` a `s` jsou přiřazeny, pokud jsou příslušné `if` příkazy pravdivé z důvodu omezení s omezením přiřazeným při hodnotě true.

> [!TIP]
> V ukázkách v tomto tématu se používá doporučený konstrukce, kde porovnávání vzorů `is` výraz jednoznačně přiřadí proměnnou shody ve `true` větvi příkazu `if`.
> Můžete vrátit zpět logiku tím, že říkáte `if (!(shape is Square s))` a proměnná `s` by byla jednoznačně přiřazena pouze ve větvi `false`. I když je tento C#postup platný, nedoporučujeme, protože je lepší postupovat podle logiky.

Tato pravidla znamenají, že nebudete mít pravděpodobně náhodný přístup k výsledku výrazu porovnávání vzorů, když tento model nebyl splněn.

## <a name="using-pattern-matching-switch-statements"></a>Použití příkazů `switch` porovnávání vzorů

V době, kdy bude trvat, možná budete muset podporovat jiné typy tvarů. Pokud se počet podmínek, které testujete, roste, zjistíte, že použití výrazů pro porovnávání vzorů `is` může být náročné. Kromě vyžadování `if`ch příkazů u každého typu, který chcete kontrolovat, jsou výrazy `is` omezeny na testování, pokud vstup odpovídá jedinému typu. V tomto případě zjistíte, že se výrazy `switch` porovnávání vzorů stávají lepší volbou. 

Tradiční příkaz `switch` byl výraz Pattern: podporuje se konstantní vzorek.
Můžete porovnat proměnnou s libovolnou konstantou použitou v příkazu `case`:

[!code-csharp[ClassicSwitch](../../samples/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Jediný vzor podporovaný příkazem `switch` byl konstantním vzorem. Bylo větší omezení na číselné typy a typ `string`.
Tato omezení byla odebrána a nyní můžete napsat příkaz `switch` pomocí vzoru typu:

[!code-csharp[Switch Type Pattern](../../samples/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Vzor odpovídající příkazu `switch` používá známou syntaxi pro vývojáře, kteří používali tradiční příkaz jazyka C-Style `switch`. Každý `case` je vyhodnocen a je proveden kód pod podmínkou, která odpovídá vstupní proměnné. Provádění kódu nemůže "klesnout do" z jednoho výrazu Case do dalšího. Syntaxe příkazu `case` vyžaduje, aby každý `case` končit `break`, `return`nebo `goto`.

> [!NOTE]
> Příkazy `goto` pro skok na jiný popisek jsou platné pouze pro konstantní vzorek (příkaz klasického přepínače).

Existují důležitá nová pravidla, kterými se řídí příkaz `switch`. Byla odebrána omezení pro typ proměnné ve výrazu `switch`.
V tomto příkladu může být použit libovolný typ, například `object`. Výrazy Case již nejsou omezeny na konstantní hodnoty. Odebrání tohoto omezení znamená, že změna pořadí `switch` oddíly může změnit chování programu.

V případě omezení na konstantní hodnoty nesmí více než jeden `case` popisek odpovídat hodnotě výrazu `switch`. Kombinaci s pravidlem, které každá `switch` oddíl nesmí projít do další části, a za tím, že `switch` oddíly lze změnit v libovolném pořadí, aniž by to mělo vliv na chování.
Nyní s obecnější `switch` výrazy je pořadí každé části věcí. Výrazy `switch` jsou vyhodnocovány v textovém pořadí. Provádění přenese do prvního `switch` popisku, který odpovídá výrazu `switch`.  
`default` případ bude proveden pouze v případě, že se neshodují žádné popisky case. `default` případ se vyhodnocuje jako poslední bez ohledu na jeho textovou objednávku. Pokud není k dispozici žádný `default` případ a žádný z ostatních příkazů `case` se neshoduje, provádění pokračuje na příkazu, který následuje po příkazu `switch`. Není spuštěn žádný kód popisku `case`.

## <a name="when-clauses-in-case-expressions"></a>klauzule `when` ve výrazech `case`

Pro prvky, které mají 0 oblast s použitím klauzule `when` na `case` popisku, můžete vytvořit zvláštní případy. Čtverec s délkou druhé délky 0 nebo kroužek s poloměrem 0 má oblast 0. Tuto podmínku určíte pomocí klauzule `when` na `case` popisku:  

[!code-csharp[ComputeDegenerateShapes](../../samples/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Tato změna ukazuje několik důležitých bodů o nové syntaxi. Nejprve lze použít více `case`ch popisků na jeden oddíl `switch`. Blok příkazu se spustí, když některý z těchto popisků je `true`. Pokud je v tomto případě výraz `switch` buď kruhem, nebo čtvercem s 0 oblastí, vrátí metoda konstantu 0.

Tento příklad zavádí dvě různé proměnné na dvou `case` jmenovky pro první blok `switch`. Všimněte si, že příkazy v tomto bloku `switch` nepoužívají buď proměnné `c` (pro kruh), nebo `s` (u čtverce).
Ani jedna z těchto proměnných není jednoznačně přiřazena v tomto `switch`m bloku.
Pokud se některý z těchto případů shodují, je přiřazena jasně jedna z proměnných.
Není však možné sdělit, *které* bylo přiřazeno v době kompilace, protože případná shoda by mohla být v době běhu. Z tohoto důvodu, když použijete více `case`ch popisků pro stejný blok, nebudete v příkazu `case` zavádět novou proměnnou, nebo použijete pouze proměnnou v klauzuli `when`.

Přidávají se tyto obrazce s 0 oblastí, takže přidáváme několik dalších typů tvarů: obdélník a trojúhelník:

[!code-csharp[AddRectangleAndTriangle](../../samples/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Tato sada změn přidává `case` popisky pro negenerovaný případ a popisky a bloky pro každý nový tvar. 

Nakonec můžete přidat `null` případ, abyste zajistili, že argument nebude `null`:

[!code-csharp[NullCase](../../samples/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Speciální chování pro vzor `null` je zajímavé, protože konstanta `null` ve vzorku nemá typ, ale lze ji převést na libovolný odkazový typ nebo na typ s možnou hodnotou null. Místo převedení `null` na libovolný typ jazyk definuje, že `null` hodnota nebude odpovídat žádnému vzoru typu bez ohledu na typ doby kompilace proměnné. Toto chování vytvoří nový vzor typu založený `switch`, který je konzistentní s příkazem `is`: `is` příkazy Always vrací `false`, pokud je hodnota zaškrtnuta `null`. Je také jednodušší: po zkontrolování typu nebudete potřebovat další kontrolu null. Můžete vidět, že neexistují žádné kontroly null v žádném z bloků Case výše uvedených vzorků: nejsou nezbytné, protože odpovídající vzorek typu garantuje hodnotu, která není null.

## <a name="var-declarations-in-case-expressions"></a>deklarace `var` ve výrazech `case`

Zavedení `var` jako jednoho z výrazů shody zavádí nová pravidla pro porovnávání vzorů.

Prvním pravidlem je, že deklarace `var` následuje po normálním odvození typu: typ je odvozen jako statický typ výrazu přepínače. V tomto pravidle typ vždy odpovídá.

Druhým pravidlem je, že deklarace `var` nemá kontrolu hodnoty null, kterou obsahují jiné výrazy vzoru typu. To znamená, že proměnná může mít hodnotu null a v takovém případě je potřeba vrátit hodnotu null.

Tato dvě pravidla znamenají, že v mnoha případech deklarace `var` ve výrazu `case` odpovídá stejným podmínkám jako výraz `default`.
Vzhledem k tomu, že všechny jiné než výchozí případy jsou upřednostňovány `default`m, nebude případ `default` nikdy spuštěn.

> [!NOTE]
> Kompilátor negeneruje upozornění v případech, kdy byl `default` případ napsaný, ale nikdy se nespustí. To je konzistentní s chováním aktuálního příkazu `switch`, kde jsou uvedeny všechny možné případy.

Třetí pravidlo zavádí, kde může být užitečný případ `var`. Představte si, že provádíte porovnávání vzorů, kde vstup je řetězec a hledáte známé hodnoty příkazu. Můžete napsat něco jako:

[!code-csharp[VarCaseExpression](../../samples/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

`var` Case odpovídá `null`, prázdnému řetězci nebo jakémukoli řetězci, který obsahuje pouze prázdné znaky. Všimněte si, že předchozí kód používá operátor `?.`, aby se zajistilo, že nechtěně nevyvolá <xref:System.NullReferenceException>. `default` případ zpracovává všechny další řetězcové hodnoty, které nejsou pochopeny tímto analyzátorem příkazů.

Toto je jeden z příkladů, kde můžete chtít zvážit výraz případu `var`, který se liší od výrazu `default`.

## <a name="conclusions"></a>Závěry

*Konstrukce porovnávání vzorů* vám umožňují snadno spravovat tok řízení mezi různými proměnnými a typy, které nesouvisí s hierarchií dědičnosti. Můžete také řídit logiku pro použití libovolné podmínky, kterou testujete u proměnné. Umožňuje vzory a idiomy, které budete potřebovat častěji při sestavování více distribuovaných aplikací, kde data a metody, které pracují s těmito daty, jsou oddělené. Všimněte si, že struktury tvarů použité v této ukázce neobsahují žádné metody, pouze vlastnosti jen pro čtení.
Porovnávání vzorů funguje s jakýmkoli datovým typem. Zapisujete výrazy, které prozkoumají objekt, a na základě těchto podmínek proveďte rozhodnutí toku řízení.

Porovnejte kód z této ukázky s návrhem, který by následoval z vytváření hierarchie tříd pro abstraktní `Shape` a specifické odvozené tvary z každého s vlastní implementací virtuální metody pro výpočet oblasti. Často zjistíte, že výrazy porovnávání vzorů můžou být velmi užitečným nástrojem při práci s daty a chcete oddělit informace týkající se úložiště dat, která se týkají chování.

## <a name="see-also"></a>Viz také

- [Kurz: použití funkcí pro porovnávání vzorů k rozšiřování datových typů](tutorials/pattern-matching.md)
