---
title: Porovnávání vzorů – průvodce C#
description: 'Informace o vzorodpovídající výrazy v C #'
ms.date: 04/10/2019
ms.technology: csharp-fundamentals
ms.assetid: 1e575c32-2e2b-4425-9dca-7d118f3ed15b
ms.openlocfilehash: bb6baf3771024d02b2027f81fd35b8be4872cf6e
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249230"
---
# <a name="pattern-matching"></a>Porovnávání vzorů

Vzorky testují, zda má hodnota určitý *tvar*, a mohou *extrahovat* informace z hodnoty, pokud má odpovídající tvar. Porovnávání vzorů poskytuje stručnější syntaxi pro algoritmy, které již používáte dnes. Již můžete vytvořit algoritmy porovnávání vzorů pomocí existující syntaxe. `if` Napíšete `switch` nebo příkazy, které testují hodnoty. Potom, když tyto příkazy shodují, extrahovat a používat informace z této hodnoty. Nové prvky syntaxe jsou rozšířením příkazů, `is` které `switch`již znáte: a . Tato nová rozšíření kombinovat testování hodnoty a extrahování těchto informací.

V tomto článku se podíváme na novou syntaxi, která vám ukáže, jak umožňuje čitelný, výstižný kód. Porovnávání vzorů umožňuje idiomy, kde jsou odděleny data a kód, na rozdíl od objektově orientovaných návrhů, kde jsou data a metody, které s nimi manipulují, pevně spojeny.

Pro ilustraci těchto nových idiomů, pojďme pracovat s strukturami, které představují geometrické tvary pomocí příkazy odpovídající vzorky. Pravděpodobně jste obeznámeni s vytvářením hierarchií tříd a vytvářením [virtuálních metod a přepsaných metod](methods.md#inherited) pro přizpůsobení chování objektů na základě typu runtime objektu.

Tyto techniky nejsou možné pro data, která není strukturována v hierarchii tříd. Pokud jsou data a metody oddělené, potřebujete další nástroje. Nové konstrukce *porovnávání vzorů* umožňují čistší syntaxi zkoumat data a manipulovat s tokem řízení na základě jakékoli podmínky těchto dat. Již `if` napíšete `switch` příkazy a že test hodnoty proměnné. Napíšete `is` příkazy, které testují typ proměnné. *Porovnávání vzorů* přidá nové možnosti těchto příkazů.

V tomto článku vytvoříte metodu, která vypočítá oblast různých geometrických tvarů. Ale uděláte to bez použití objektově orientovaných technik a vytvoření hierarchie tříd pro různé tvary.
Místo toho použijete *porovnávání vzorů.*
Při procházení této ukázky porovnejte tento kód s tím, jak by byl strukturován jako hierarchie objektů. Pokud data, která je nutné dotazovat a manipulovat s nimi, nejsou hierarchií tříd, porovnávání vzorů umožňuje elegantní návrhy.

Místo toho, abypočínaje abstraktní definicí tvaru a přidáním různých specifických tříd tvarů, začněme místo toho s jednoduchými definicemi dat pouze pro každý z geometrických tvarů:

[!code-csharp[ShapeDefinitions](../../samples/snippets/csharp/PatternMatching/Shapes.cs#01_ShapeDefinitions "Shape definitions")]

Z těchto struktur napíšeme metodu, která vypočítá oblast nějakého tvaru.

## <a name="the-is-type-pattern-expression"></a>Výraz `is` vzor textu

Před C# 7.0, budete muset otestovat každý `if` typ `is` v sérii a příkazy:

[!code-csharp[ClassicIsExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#02_ClassicIsExpression "Classic type pattern using is")]

Tento kód výše je klasický výraz *typu vzoru*: Testujete proměnnou k určení jeho typu a s jinou akci na základě tohoto typu.

Tento kód se stává jednodušší `is` pomocí rozšíření výrazu přiřadit proměnnou, pokud test úspěšné:

[!code-csharp[IsPatternExpression](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#03_IsPatternExpression "is pattern expression")]

V této aktualizované `is` verzi výraz testuje proměnnou a přiřazuje ji k nové proměnné správného typu. Všimněte si také, `Rectangle` že tato verze `struct`obsahuje typ, který je . Nový `is` výraz pracuje s typy hodnot i s typy odkazů.

Jazyková pravidla pro výrazy porovnávání vzorů vám pomohou vyhnout se zneužití výsledků výrazu shody. Ve výše uvedeném příkladu `c`jsou `r` proměnné `s`, a jsou pouze v oboru `true` a jednoznačně přiřazeny, pokud mají výsledky příslušné výrazy shody vzoru. Pokud se pokusíte použít jednu z proměnných v jiném umístění, váš kód generuje chyby kompilátoru.

Podívejme se na obě tato pravidla podrobně, počínaje rozsahem. Proměnná `c` je v oboru `else` pouze v `if` pobočce prvního příkazu. Proměnná `s` je v oboru `ComputeAreaModernIs`v metodě . Je to proto, že `if` každá větev příkazu vytvoří samostatný obor pro proměnné. Nicméně, `if` prohlášení samo o sobě není. To znamená, že `if` proměnné deklarované v `if` příkazu jsou ve stejném oboru jako příkaz (metoda v tomto případě.) Toto chování není specifické pro porovnávání vzorů, ale je `if` `else` definované chování pro proměnné obory a příkazy.

Proměnné a `c` `s` jsou přiřazeny, `if` pokud jsou příslušné příkazy true z důvodu definitivně přiřazena při true mechanismu.

> [!TIP]
> Ukázky v tomto tématu použít doporučenou konstrukci, kde vzor odpovídající `is` výraz rozhodně přiřadí match proměnnou v `true` pobočce příkazu. `if`
> Můžete obrátit logiku `if (!(shape is Square s))` tím, `s` že říká a proměnná by určitě přiřazena pouze v oboru. `false` I když je platný C#, není doporučeno, protože je více matoucí sledovat logiku.

Tato pravidla znamenají, že je nepravděpodobné, že byste omylem přistupovali k výsledku výrazu shody vzoru, pokud tento vzor nebyl splněn.

## <a name="using-pattern-matching-switch-statements"></a>Použití příkazů `switch` porovnávání vzorů

Jak plyne čas, možná budete muset podporovat jiné typy tvarů. S tím, jak se zvyšuje počet podmínek, které `is` testujete, zjistíte, že použití výrazů odpovídajících vzorů mů e být těžkopádné. Kromě vyžadování `if` příkazů pro každý typ, který `is` chcete zkontrolovat, jsou výrazy omezeny na testování, pokud vstup odpovídá jednomu typu. V takovém případě zjistíte, `switch` že výrazy porovnávání vzorů se stanou lepší volbou.

Tradiční `switch` příkaz byl vzor výraz: podporuje konstantní vzor.
Můžete porovnat proměnnou s libovolnou `case` konstantou použitou v příkazu:

[!code-csharp[ClassicSwitch](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#04_ClassicSwitch "Classic switch statement")]

Jediným vzorem podporovaným příkazem `switch` byl konstantní vzor. Byl dále omezen na číselné typy a `string` typ.
Tato omezení byla odebrána a nyní `switch` můžete napsat příkaz pomocí vzoru typu:

[!code-csharp[Switch Type Pattern](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#05_SwitchTypePattern "Compute with `switch` expression")]

Příkaz porovnávání `switch` vzorů používá známou syntaxi vývojářům, kteří použili tradiční příkaz stylu `switch` C. Každý `case` je vyhodnocen a kód pod podmínkou, která odpovídá vstupní proměnné je proveden. Spuštění kódu nemůže "propadnout" z jednoho výrazu případu na další; syntaxe `case` příkazu vyžaduje, `case` aby `break`každý `return`konec `goto`s , , nebo .

> [!NOTE]
> Příkazy `goto` přejít na jiný popisek jsou platné pouze pro konstantní vzor (klasický příkaz switch).

Existují důležitá nová pravidla, `switch` kterými se řídí prohlášení. Omezení typu proměnné ve výrazu `switch` byla odebrána.
Lze použít libovolný `object` typ, například v tomto příkladu. Výrazy případu již nejsou omezeny na konstantní hodnoty. Odebrání tohoto omezení znamená, že změna pořadí `switch` oddílů může změnit chování programu.

Pokud jsou omezeny na konstantní `case` hodnoty, může hodnotu `switch` výrazu odpovídat více než jeden popisek. Zkombinujte to s `switch` pravidlem, že každý oddíl nesmí propadnout `switch` do další části a z toho vyplývá, že oddíly mohou být uspořádány v libovolném pořadí bez ovlivnění chování.
Nyní, s více `switch` zobecněnými výrazy, záleží na pořadí každé sekce. Výrazy `switch` jsou vyhodnocovány v textovém pořadí. Spuštění se přenáší `switch` na první `switch` popisek, který odpovídá výrazu.  
Případ `default` bude proveden pouze v případě, že se neshodují žádné jiné popisky případu. Případ `default` je hodnocen jako poslední, bez ohledu na jeho textové pořadí. Pokud neexistuje žádný `default` případ a žádný `case` z ostatních příkazů odpovídat, `switch` provádění pokračuje na příkaz následující prohlášení. Žádný kód `case` popisků není spuštěn.

## <a name="when-clauses-in-case-expressions"></a>`when`klauzule `case` ve výrazech

Pomocí klauzule na popisku `when` `case` můžete vytvořit speciální případy pro ty obrazce, které mají oblast 0. Čtverec s délkou strany 0 nebo kružnice s poloměrem 0 má oblast 0. Tuto podmínku `when` určíte pomocí `case` klauzule na popisku:  

[!code-csharp[ComputeDegenerateShapes](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#07_ComputeDegenerateShapes "Compute shapes with 0 area")]

Tato změna ukazuje několik důležitých bodů o nové syntaxi. Nejprve `case` lze na jeden `switch` oddíl použít více popisků. Blok příkazu je proveden, pokud `true`je některý z těchto popisků . V tomto případě `switch` pokud je výraz kruh nebo čtverec s oblastí 0, metoda vrátí konstantu 0.

Tento příklad zavádí dvě různé proměnné `case` ve dvou `switch` popiscích pro první blok. Všimněte si, `switch` že příkazy `c` v tomto bloku nepoužívají proměnné `s` (pro kruh) nebo (pro čtverec).
Ani jedna z těchto proměnných `switch` je v tomto bloku určitě přiřazena.
Pokud se některý z těchto případů shoduje, je zřejmé, že byla přiřazena jedna z proměnných.
Je však nemožné zjistit, *který* byl přiřazen v době kompilace, protože oba případy mohou odpovídat za běhu. Z tohoto důvodu většinou při `case` použití více popisků pro stejný blok, nezavedete novou proměnnou v příkazu, `case` nebo budete používat pouze proměnnou v klauzuli. `when`

Po přidání těchto obrazců s oblastí 0 přidáme několik dalších typů tvarů: obdélník a trojúhelník:

[!code-csharp[AddRectangleAndTriangle](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#09_AddRectangleAndTriangle "Add rectangle and triangle")]

 Tato sada změn `case` přidá popisky pro degenerovaný případ a popisky a bloky pro každý z nových obrazců.

Nakonec můžete přidat `null` případ, abyste zajistili, `null`že argument není:

[!code-csharp[NullCase](../../samples/snippets/csharp/PatternMatching/GeometricUtilities.cs#10_NullCase "Add null case")]

Zvláštní chování pro `null` vzorek je zajímavé, protože konstanta `null` ve vzorku nemá typ, ale může být převedena na libovolný typ odkazu nebo typ hodnoty s hodnotou s možnou hodnotou, kterou lze hodnotit. Spíše než `null` převést na libovolný typ, `null` jazyk definuje, že hodnota nebude odpovídat žádný typ vzor, bez ohledu na typ kompilace proměnné. Toto chování `switch` je nový vzorek `is` typu `is` na základě `false` konzistentní s příkazem: příkazy vždy vrátit, když je `null`zaškrtnutá hodnota . Je to také jednodušší: jakmile zkontrolujete typ, nepotřebujete další kontrolu null. Můžete vidět, že z toho, že neexistují žádné nulové kontroly v některém z bloků případu výše uvedených vzorků: nejsou nutné, protože odpovídající vzor typu zaručuje hodnotu bez nuly.

## <a name="var-declarations-in-case-expressions"></a>`var`deklarace `case` ve výrazech

Zavedení `var` jako jeden z výrazů shody zavádí nová pravidla do shody vzoru.

První pravidlo je, `var` že deklarace se řídí pravidly odvození normálního typu: Typ je odvozen za statický typ výrazu switch. Z tohoto pravidla se typ vždy shoduje.

Druhým pravidlem `var` je, že deklarace nemá kontrolu null, které zahrnují jiné výrazy typu vzor. To znamená, že proměnná může být null a kontrola null je nezbytné v tomto případě.

Tato dvě pravidla znamenají, že `var` v mnoha `case` případech deklarace ve `default` výrazu odpovídá stejným podmínkám jako výraz.
Vzhledem k tomu, že `default` jakýkoli případ, který není výchozí, je upřednostňován před případem, `default` případ se nikdy neprovede.

> [!NOTE]
> Kompilátor nevyzařuje upozornění v `default` těch případech, kdy byl případ zapsán, ale nikdy se nespustí. To je v `switch` souladu s aktuální chování příkazu, kde byly uvedeny všechny možné případy.

Třetí pravidlo zavádí použití, `var` kde může být případ užitečný. Představte si, že provádíte porovnávání vzorů, kde je vstup em řetězec a hledáte známé hodnoty příkazů. Můžete napsat něco jako:

[!code-csharp[VarCaseExpression](../../samples/snippets/csharp/PatternMatching/Program.cs#VarCaseExpression "use a var case expression to filter white space")]

Případ `var` odpovídá `null`, prázdný řetězec nebo libovolný řetězec, který obsahuje pouze prázdné místo. Všimněte si, že `?.` předchozí kód používá operátor k zajištění, <xref:System.NullReferenceException>že není omylem hodit . Případ `default` zpracovává všechny ostatní řetězcové hodnoty, které nejsou chápány v tomto analyzátoru příkazů.

Toto je jeden příklad, kde `var` můžete chtít zvážit `default` případ výraz, který je odlišný od výrazu.

## <a name="conclusions"></a>Závěry

*Konstrukce porovnávání vzorů* umožňují snadno spravovat tok řízení mezi různými proměnnými a typy, které nejsou spojeny hierarchií dědičnosti. Můžete také řídit logiku použít všechny podmínky, které testujete na proměnné. Umožňuje vzory a idiomy, které budete potřebovat častěji při vytváření více distribuovaných aplikací, kde jsou data a metody, které pracují s daty, oddělené. Všimněte si, že struktury tvarů použité v této ukázce neobsahují žádné metody, pouze vlastnosti jen pro čtení.
Porovnávání vzorů funguje s libovolným datovým typem. Napíšete výrazy, které prozkoumat objekt a provádět rozhodnutí o toku řízení na základě těchto podmínek.

Porovnejte kód z této ukázky s návrhem, `Shape` který by vyplýval z vytvoření hierarchie tříd pro abstraktní a specifické odvozené tvary, z nichž každý s vlastní implementací virtuální metody pro výpočet oblasti. Často zjistíte, že výrazy porovnávání vzorů mohou být velmi užitečným nástrojem při práci s daty a chcete oddělit obavy o úložiště dat od obav o chování.

## <a name="see-also"></a>Viz také

- [Kurz: Použití funkcí porovnávání vzorů k rozšíření datových typů](tutorials/pattern-matching.md)
