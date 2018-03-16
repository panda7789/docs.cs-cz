---
title: "Prohlídka F #"
description: "Zkontrolujte některé z klíčových funkcích služby programovací jazyk v této ukázky s ukázky kódu F #."
keywords: "Visual f #, f #, funkční programování, .NET, prohlídka"
author: cartermp
ms.author: phcart
ms.date: 02/28/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 49775139-082e-442f-b5a2-dd402399b5d2
ms.openlocfilehash: 7327573a25aa62af28570b4a8662235f3e41a972
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="tour-of-f"></a>Prohlídka F # #

Číst a zapisovat F # – kód je nejlepší způsob, jak získat informace o F #.  Tento článek poskytuje některé fragmenty kódu, které můžete spustit na počítači a bude fungovat jako prohlídka prostřednictvím některé klíčové funkce jazyka F #.  Další informace o nastavení vývojového prostředí, podívejte se na [Začínáme](tutorials/getting-started/index.md).

Existují dvě primární koncepty v jazyce F #: typy a funkce.  Tato ukázka se zdůraznil funkce jazyka, které spadají do těchto dvěma konceptů.

## <a name="functions-and-modules"></a>Funkce a modulů

Na nejzákladnější požadované žádné program v F # jsou ***funkce*** uspořádány do ***moduly***.  [Funkce](language-reference/functions/index.md) práci na vstupy pro vytvoření výstupy a jsou uspořádány v části [moduly](language-reference/modules.md), které jsou primární způsob skupiny věcí v jazyce F #.  Jsou definované pomocí [ `let` vazby](language-reference/functions/let-bindings.md), které funkce pojmenujte a definovat její argumenty.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` vazby jsou také jak vázat hodnotu s názvem, podobně jako na proměnnou v dalších jazycích.  `let` vazby jsou ***neměnné*** ve výchozím nastavení, což znamená, že jakmile hodnota nebo funkce je vázána na název, nelze ji změnit na místě.  Jde na rozdíl od proměnných v jiných jazycích, které jsou ***měnitelný***, což znamená, jejich hodnoty lze změnit v libovolném bodě v čase.  Pokud budete potřebovat měnitelný vazbu, můžete použít `let mutable ...` syntaxe.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Čísla logických výrazů a řetězců

Jako jazyk rozhraní .NET, F # podporuje stejné základní [primitivní typy](language-reference/primitive-types.md) které existovat v rozhraní .NET.

Zde je, jak budou různé číselnými typy jsou reprezentována v jazyce F #:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Tady je co logické hodnoty a provádění základních podmíněnou logiku vypadá takto:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

A tady je co basic [řetězec](language-reference/strings.md) manipulaci vypadá takto:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Řazené kolekce členů

[Řazené kolekce členů](language-reference/tuples.md) jsou big pozornosti v jazyce F #.  Jsou to seskupení nepojmenované, ale seřazené hodnoty, které mohou být považovány za hodnoty sami.  Představte si je jako hodnoty, které jsou agregovat z jiných hodnot.  Mají mnoho používá, jako je například pohodlně z funkce vrátí více hodnot, nebo seskupení hodnoty pro některé ad-hoc pohodlí.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

Od verze F # 4.1, můžete také vytvořit `struct` řazené kolekce členů.  To také plně spolupracovat s C# 7/Visual Basic 15 řazené kolekce členů, které jsou taky `struct` řazených kolekcí členů:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Je důležité si uvědomit, že protože `struct` řazených kolekcí členů jsou typy hodnot, je nelze implicitně převést tak, aby odkazovaly řazené kolekce členů, nebo naopak.  Je nutné explicitně převést mezi referenčním a struktura řazené kolekce členů.

## <a name="pipelines-and-composition"></a>Zřetězením příkazů a sestavení

Přesměrováním operátory (`|>`, `<|`, `||>`, `<||`, `|||>`, `<|||`) a složení operátory (`>>` a `<<`) jsou používány při zpracování dat v jazyce F #.  Tyto operátory jsou funkce, které umožňují flexibilně navázat "kanály" funkcí.  V následujícím příkladu se provede jak může využít výhod těchto operátorů k vytvoření jednoduché funkční kanálu.

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L300)]

Ukázka výše provedené použití mnoha funkcí jazyka F #, včetně seznamu zpracování funkce, prvotřídní funkce a [částečné aplikace](language-reference/functions/index.md#partial-application-of-arguments).  I když se může stát poněkud pokročilé hluboké znalosti tyto koncepty, je nutné vymazat jak snadno funkce slouží ke zpracování dat, při vytváření kanálů.

## <a name="lists-arrays-and-sequences"></a>Pořadí, seznamy a pole

Pořadí, seznamy a pole jsou tři typy primární kolekcí v základní knihovny F #.

[Uvádí](language-reference/lists.md) jsou seřazené, neměnné kolekce elementů stejného typu.  Jsou jednotlivě propojené seznamy, což znamená, že jsou určené pro výčet, ale nízký volbou pro náhodný přístup a zřetězení, pokud jsou velké.  Tato tvořeny seznamy v oblíbených jazyků, které obvykle nepoužívejte seznam samostatně propojené představují seznamy.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Pole](language-reference/arrays.md) jsou pevné velikosti, *měnitelný* kolekce elementů stejného typu.  Podporují vysoká rychlost náhodného přístup elementů a je rychlejší než F # uvádí protože se právě souvislý bloky paměti.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Pořadí](language-reference/sequences.md) logické řadu elementů všechny stejného typu.  Toto jsou další obecné typ než seznamy a polí, schopny "zobrazení" do libovolné logické řady elementů.  Budou také zvýraznění protože můžou být ***opožděné***, což znamená, že elementy můžete vypočítat jenom v případě potřeby.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Rekurzivní funkce

Zpracování kolekce nebo pořadí elementů obvykle provádí pomocí [rekurze](language-reference/functions/index.md#recursive-functions) v jazyce F #.  I když F # obsahuje podporu pro smyčky a imperativní programování, rekurze je preferovaná, protože je jednodušší zajistit správnost.

>[!NOTE]
Následující příklad využívá vzor odpovídající pomocí `match` výraz.  Tato základní koncept je popsaná později v tomto článku.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F # má také plnou podporu pro optimalizaci volání Tail, což je způsob, jak optimalizovat rekurzivní volání, aby byly stejně tak rychlé konstrukcí smyčky.

## <a name="record-and-discriminated-union-types"></a>Záznam a rozlišovaná sjednocení typů

Záznam a Union typy jsou dva základní datové typy používané v F # – kód a jsou obecně nejlepší způsob, jak představují data v programu F #.  Díky tomu je podobná třídy v jiných jazycích, jednu primární rozdíly mezi nimi sice, ke kterým mají sémantiku strukturální rovnosti.  To znamená, že jsou "nativní" porovnatelný a rovnosti je jednoduchá – jenom zkontrolujte, jestli je rovno dalších jeden.

[Zaznamenává](language-reference/records.md) jsou agregace pojmenovaných hodnot, se volitelné členy (například metody).  Pokud jste obeznámeni s jazyka C# nebo Java, pak tyto by měli považovat podobné POCOs nebo Pojo - právě s strukturální rovnosti a méně procedury.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

Od verze F # 4.1, může také představovat záznamy jako `struct`s.  To lze provést pomocí `[<Struct>]` atribut:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[Rozlišované sjednocení (DUs)](language-reference/discriminated-unions.md) jsou hodnoty, které by mohly být číslo s názvem formulářů nebo případů.  Data uložená v typu může být jedna z několika různých hodnot.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Můžete taky DUs jako *jeden případ Rozlišované sjednocení*, abyste s doménou modelování přes primitivní typy.  Další primitivní typy, řetězce a často se používají k vyjádření něco a proto mají zvláštní význam.  Však pomocí jenom primitivní znázornění dat může mít za následek omylem přiřazení nesprávnou hodnotu!  Každý typ informací jako odlišné jedním – případ typu union představující můžete vynutit správnost v tomto scénáři.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Jak ukazuje ukázka výše, chcete-li získat základní hodnotu v jedním případ Rozlišované sjednocení, musí se explicitně rozbalení.

Kromě toho DUs také podporují rekurzivní definice umožňuje snadno představují stromy a ze své podstaty rekurzivní data.  Můžete zde je ukázka, jak může představovat binárního stromu vyhledávání s `exists` a `insert` funkce.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Protože DUs umožňují představují rekurzivní struktura stromu s datovým typem, pracující na tuto strukturu rekurzivní je jednoduchý a zaručuje správnost.  Je také podporována v porovnávání vzorů, jak je uvedeno níže.

Kromě toho může představovat DUs jako `struct`s s `[<Struct>]` atribut:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Existují však dvě klíčové věci, třeba vzít v úvahu při této:

1. Struktura DU nemůže být definovaný rekurzivně.
2. Struktura DU musí mít jedinečné názvy pro každý z jeho případech.

Chyba kompilace způsobí selhání použít postup popsaný výše.

## <a name="pattern-matching"></a>Porovnávání vzorů

[Vzor párování](language-reference/pattern-matching.md) je funkce jazyka F #, která umožňuje správnost pro provoz na typů F #.  Ve výše uvedené ukázky, pravděpodobně zaznamenali s bit `match x with ...` syntaxe.  Tato konstrukce umožňuje kompilátoru, který můžete porozumět "tvar" datové typy, chcete-li vynutit, abyste účet pro všechny případy možné při použití datový typ prostřednictvím, která se označuje jako vyčerpávající porovnávání vzorů.  To je velmi efektivní správnost a cleverly slouží k "navýšení" co bude obvykle runtime problém do kompilaci.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L739)]

Můžete také zkrácený `function` konstrukce pro porovnávání vzorů, které lze využít při psaní funkce, které využívají [částečné aplikace](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L741-L759)]

Něco může dojít k tomu je použití `_` vzor.  To se označuje jako [zástupný znak – vzor](language-reference/pattern-matching.md#wildcard-pattern), což je způsob, jak o tom, že "I nezajímá je něco je".  I když je to vhodné, můžete nechtěně vynechat vyčerpávající porovnávání vzorů a už využívat kompilaci enforcements, pokud nejste opatrní při použití `_`.  Je nevhodnější používat, pokud vám nezáleží určité typu rozložená, když vzor odpovídající nebo klauzuli konečné při mít výčet všech smysluplný případech ve tvaru odpovídající výrazu.

[Aktivní vzorky](language-reference/active-patterns.md) jsou jiné výkonné konstrukce pro použití s porovnávání vzorů.  Umožňují vám oddílu vstupních dat do vlastních formulářích, decomposing je v lokalitě vzor shody volání.  Jejich lze také nastavit parametry, což umožňuje definovat oddílu jako funkce.  Předchozí příklad pro podporu aktivní vzorky se zvětšující vypadá přibližně takto:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L761-L783)]

## <a name="optional-types"></a>Volitelné typy

Jeden zvláštní případ Rozlišované sjednocení typů je možnost typu, což je užitečné, že je součástí základní knihovny F #.

[Typ možnosti](language-reference/options.md) je typ, který představuje jednu ze dvou případů: hodnotu nebo nic na všechny.  Používá se v žádném scénáři, kde hodnota může nebo nemusí být důsledkem určité operace.  Potom vynutí se tak, abyste účet pro oba případy, což kompilaci problém spíše než runtime problém.  To se často používají rozhraní API kde `null` se používá k reprezentování "nic" místo toho eliminovat potřebu starat o `NullReferenceException` v mnoha případech.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L791-L811)]

## <a name="units-of-measure"></a>Měrné jednotky

Jeden jedinečný funkce F # pro typ systému je schopnost poskytovat kontext pro číselné literály prostřednictvím měrné jednotky.

[Měrné jednotky](language-reference/units-of-measure.md) vám umožní přidružit číselného typu jednotkou, například měřidla, a mít funkce práci na jednotkách a ne číselné literály.  To umožňuje kompilátor ověřte, že typy číselné literály předaná smysl v určitých kontextu, a odstraňuje tak chyby za běhu přidružené tento druh práce.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L818-L839)]

F # základní knihovny definuje mnoho typů jednotek ma a převody jednotek.  Další informace, podívejte se [Microsoft.fsharp.data.unitsystems.si – Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Třídy a rozhraní

F # má také plnou podporu pro rozhraní .NET třídy [rozhraní](language-reference/interfaces.md), [abstraktní třídy](language-reference/abstract-classes.md), [dědičnosti](language-reference/inheritance.md)a tak dále.

[Třídy](language-reference/classes.md) jsou typy, které představují objekty .NET, která může mít vlastnosti, metod a událostí jako jeho [členy](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L848-L877)]

Definování obecné třídy je také velmi jednoduché.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L884-L905)]

Chcete-li implementovat rozhraní, můžete použít buď `interface ... with` syntaxe nebo [objekt výraz](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L912-L931)]

## <a name="which-types-to-use"></a>Jaké typy pro použití

Třídy, záznamy, Rozlišované sjednocení a řazených kolekcí členů vede k důležité otázku: který mám použít?  Většina všechno ve životnost, jako je odpověď závisí na vaší okolností.

Jsou skvěle hodí k vrácení více hodnot z funkce a používání ad-hoc agregace hodnot jako vlastní hodnota řazené kolekce členů.

Záznamy jsou "krok nahoru" z řazené kolekce členů s názvem popisky a podporu pro volitelné členy.  Jsou ideální pro nízké procedury reprezentace dat během přenosu prostřednictvím vašeho programu.  Vzhledem k tomu, že budou mít strukturální rovnosti, jsou nejjednodušší porovnání.

Rozlišovaná sjednocení mít mnoho používá, ale základní výhodou je, abyste mohli používat je ve spojení s porovnávání vzorů pro účet pro všechny možné "tvary" mající data.  

Třídy jsou ideální pro velký počet důvodů, například když potřebujete představují informace a také tie tyto informace k funkcím.  Jako existuje pravidlo Pokud máte funkci, která je koncepčně vázaný k některým datům pomocí třídy a zásady Object-Oriented programování je velký výhody.  Třídy jsou také upřednostňované datový typ při interoperabilitě se službou C# a Visual Basic, jak tyto jazyky použít třídy téměř všem.

## <a name="next-steps"></a>Další kroky

Teď, když jste viděli některé z primární funkce jazyka, byste měli být připravení zápis vaše první programů F #!  Podívejte se na [Začínáme](tutorials/getting-started/index.md) se dozvíte, jak nastavit vývojové prostředí a napsat kód.

Další kroky k dalších informací může být vám líbí, ale doporučujeme [funguje jako hodnoty první třídy](introduction-to-functional-programming/functions-as-first-class-values.md) <!--[Introduction to Functional Programming in F#](introduction-to-functional-programming/index.md)--> získat celý základní koncepty programování funkční.  Budou to důležité pro sestavování robustní programů v jazyce F #.

Také, podívejte se [referenční dokumentace jazyka F #](language-reference/index.md) zobrazíte komplexní kolekce konceptuálního obsahu v F #.
