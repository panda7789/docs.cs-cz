---
title: Prohlídka jazyka F#
description: 'Prohlédněte si některé z klíčových funkcí programovacího jazyka F # v této prohlídce s ukázkami kódu.'
ms.date: 08/14/2020
ms.openlocfilehash: b115317e1f47ef7e18333cae4145b99e11645579
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558592"
---
# <a name="tour-of-f"></a>Prohlídka F\#

Nejlepším způsobem, jak se seznámit s F #, je čtení a zápis kódu F #. Tento článek bude sloužit jako prohlídka prostřednictvím některých klíčových funkcí jazyka F # a poskytuje některé fragmenty kódu, které můžete na svém počítači spustit. Další informace o nastavení vývojového prostředí najdete [Začínáme](get-started/index.md).

V jazyce F # jsou k dispozici dvě primární koncepce: funkce a typy.  Tato prohlídka bude zdůraznit funkce jazyka, které spadají do těchto dvou konceptů.

## <a name="executing-the-code-online"></a>Online spuštění kódu

Pokud nemáte v počítači nainstalovanou F #, můžete v prohlížeči spustit všechny ukázky pomocí příkazu [Try f # v](https://tryfsharp.fsbolero.io/)rámci webového sestavení. Fable je dialekt jazyka F #, který se spouští přímo v prohlížeči. Chcete-li zobrazit ukázky, které následují ve REPL, podívejte se na **ukázky > > prohlídku F #** v levém panelu nabídek REPL Fable.

## <a name="functions-and-modules"></a>Funkce a moduly

Nejdůležitější části libovolného programu jazyka F # jsou ***funkce*** uspořádané do ***modulů***.  [Funkce](./language-reference/functions/index.md) provádějí práci na vstupy pro vytváření výstupů a jsou uspořádány pod [moduly](./language-reference/modules.md), což jsou hlavní způsob seskupení objektů v jazyce F #.  Jsou definovány pomocí [ `let` vazby](./language-reference/functions/let-bindings.md), která dává funkci název a definuje její argumenty.

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

`let` vazby také způsob vázání hodnoty k názvu, podobně jako proměnná v jiných jazycích.  `let` vazby jsou ve výchozím nastavení ***neměnné*** , což znamená, že jakmile je hodnota nebo funkce vázána na název, nelze ji změnit na místě.  To je v kontrastu s proměnnými v jiných jazycích, které jsou ***proměnlivé***, což znamená, že jejich hodnoty je možné kdykoli změnit v libovolném časovém okamžiku.  Pokud potřebujete proměnlivou vazbu, můžete použít `let mutable ...` syntaxi.

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Čísla, logické hodnoty a řetězce

Jazyk F # v rámci jazyka .NET podporuje stejné základní [primitivní typy](language-reference/basic-types.md) , které existují v rozhraní .NET.

Tady je způsob reprezentace různých číselných typů v F #:

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

Tady je, jaké logické hodnoty a provádění základní podmíněné logiky vypadají takto:

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

A jak vypadá základní manipulace s [řetězci](./language-reference/strings.md) , vypadá takto:

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>N-tice

[Řazené kolekce členů](./language-reference/tuples.md) jsou velkými transakcemi v F #.  Jsou seskupením nepojmenovaných, ale seřazené hodnoty, které lze považovat za samotné hodnoty.  Ty si můžete představit jako hodnoty agregované z jiných hodnot.  Mají mnoho použití, jako je například pohodlné vrácení více hodnot z funkce nebo seskupování hodnot pro některé praktické pohodlí.

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

Můžete také vytvořit `struct` řazené kolekce členů.  Tyto akce také spolupracují s C# 7/Visual Basic 15 řazenými kolekcemi členů, které jsou také `struct` řazené kolekce členů:

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

Je důležité si uvědomit, že protože `struct` řazené kolekce členů jsou typy hodnot, nelze je implicitně převést na referenční řazené kolekce členů ani naopak.  Je nutné explicitně převést mezi odkazem a strukturou řazené kolekce členů.

## <a name="pipelines-and-composition"></a>Kanály a kompozice

Operátory kanálu, jako `|>` je například, jsou používány rozsáhle při zpracování dat v F #. Tyto operátory jsou funkce, díky kterým můžete flexibilním způsobem vytvořit kanály funkcí. V následujícím příkladu se dozvíte, jak můžete využít tyto operátory k sestavení jednoduchého funkčního kanálu:

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

Předchozí ukázka využívala mnoho funkcí F #, včetně funkcí pro zpracování seznamu, funkcí první třídy a [částečné aplikace](./language-reference/functions/index.md#partial-application-of-arguments). I když může být důkladné porozumění každé z těchto konceptů poněkud pokročilé, mělo by být jasné, jak snadno se funkce dají použít ke zpracování dat při sestavování kanálů.

## <a name="lists-arrays-and-sequences"></a>Seznamy, pole a posloupnosti

Seznamy, pole a sekvence jsou tři typy primární kolekce v knihovně F # Core.

[Seznamy](./language-reference/lists.md) jsou seřazené, neměnné kolekce prvků stejného typu.  Jedná se o jednorázově propojené seznamy, což znamená, že jsou určeny pro výčet, ale nedostatečná volba pro náhodný přístup a zřetězení, pokud jsou velké.  Na rozdíl od seznamů v jiných oblíbených jazycích, které obvykle nepoužívají samostatně propojený seznam k reprezentaci seznamů.

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

[Pole](./language-reference/arrays.md) jsou pevná velikost, *proměnlivé* kolekce prvků stejného typu.  Podporují rychlý náhodný přístup k prvkům a jsou rychlejší než seznamy F #, protože jsou pouze souvislými bloky paměti.

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

[Sekvence](./language-reference/sequences.md) jsou logické řady prvků, všechny stejného typu.  Jedná se o obecnější typ než seznamy a pole, které je možné zobrazit v libovolné logické sérii prvků.  Jsou také úsporné, protože mohou být ***opožděny***, což znamená, že prvky lze vypočítat pouze v případě potřeby.

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Rekurzivní funkce

Zpracování kolekcí nebo sekvencí prvků se obvykle provádí pomocí [rekurze](./language-reference/functions/index.md#recursive-functions) v F #.  I když jazyk F # podporuje smyčky a imperativní programování, rekurze je preferovaná, protože je snazší zaručit správnost.

> [!NOTE]
> V následujícím příkladu je použito porovnávání vzorů prostřednictvím `match` výrazu.  Tato základní konstrukce se zabývá dále v tomto článku.

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

Jazyk F # má také úplnou podporu pro optimalizaci volání funkce tail, což je způsob optimalizace rekurzivních volání, která jsou stejně rychlá jako konstrukce smyčky.

## <a name="record-and-discriminated-union-types"></a>Typy záznamů a rozlišených sjednocení

Typy záznamů a sjednocení jsou dva základní datové typy, které se používají v kódu F # a jsou obecně nejlepším způsobem reprezentace dat v programu F #.  I když se to podobá třídám v jiných jazycích, jedna z jejich primárních rozdílů je, že mají strukturální sémantiku rovnosti.  To znamená, že jsou "nativně" srovnatelné a rovnost je přímá – stačí pouze kontrolovat, zda je jeden jiný.

[Záznamy](./language-reference/records.md) jsou agregátem pojmenovaných hodnot s volitelnými členy (jako jsou metody).  Pokud jste obeznámeni s jazykem C# nebo Java, pak by se měly líbit podobně jako POCOs nebo Pojo – pouze se strukturální rovností a menší procedury.

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

Záznamy můžete také vyjádřit jako struktury. To se provádí s `[<Struct>]` atributem:

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

[Rozlišené sjednocení (du)](./language-reference/discriminated-unions.md) jsou hodnoty, které by mohly představovat počet pojmenovaných forem nebo případů.  Data uložená v typu můžou být jedna z několika různých hodnot.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

Du můžete použít také jako *jednotná sjednocení*, která vám pomůžou s modelováním domén přes primitivní typy.  Často se používá k reprezentaci řetězců a dalších primitivních typů, které představují konkrétní význam.  Použití jenom primitivní reprezentace dat ale může mít za následek omylem přiřazení nesprávné hodnoty!  V takovém případě může být v tomto scénáři vyjasnění každého typu informací v případě samostatného sjednocení s jedním případem.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

Jak ukazuje výše uvedený příklad, k získání základní hodnoty v jednoduchém sjednocovacím sjednocení, je nutné explicitně zrušit balení.

Kromě toho du také podporuje rekurzivní definice, což vám umožní snadno reprezentovat stromy a podstaty rekurzivní data.  Tady je příklad, jak můžete reprezentovat binární vyhledávací strom s `exists` `insert` funkcemi a.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

Vzhledem k tomu, že du umožňuje znázornit rekurzivní strukturu stromu v datovém typu, která je provozována v této rekurzivní struktuře, je jednoduchá a zaručuje správnost.  Podporuje se také v porovnávání vzorů, jak je znázorněno níže.

Kromě toho můžete reprezentovat du jako s `struct` `[<Struct>]` atributem:

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

Existují však dvě klíčové věci, které je potřeba vzít v úvahu:

1. Hodnotu DU pro struct nelze rekurzivně definovat.
2. Struktura DU musí mít jedinečné názvy pro každý z jejích případů.

Nepodaří-li se postupovat podle výše uvedeného výsledku, dojde k chybě kompilace.

## <a name="pattern-matching"></a>Porovnávání vzorů

[Porovnávání vzorů](./language-reference/pattern-matching.md) je funkce jazyka F #, která umožňuje správnou funkci pro práci na typech F #.  Ve výše uvedených ukázkách jste si pravděpodobně všimli trochu `match x with ...` syntaxe.  Tento konstruktor umožňuje kompilátoru, který může pochopit "tvar" datových typů, aby bylo možné přihlédnout ke všem možným případům při použití datového typu prostřednictvím toho, co se říká vyčerpávající porovnávání vzorů.  To je neuvěřitelně výkonné pro správnost a dá se cleverly použít k "zaznamenání", co by normálně představovalo při kompilaci za běhu.

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

Něco, co jste si možná všimli, je použití `_` vzoru.  Tento vzor je známý jako [zástupný znak](./language-reference/pattern-matching.md#wildcard-pattern), což je způsob, jak se vyjádřit, co něco je.  I když je to pohodlnější, můžete náhodně obejít porovnávání vyčerpávajících vzorů a už nebudete využívat výhody při kompilaci, pokud se nebudete opatrní používat `_` .  Je nejvhodnější použít, pokud nezáleží na určitých částech desloženého typu při porovnávání vzorů, nebo na konci klauzule, pokud jste ve výrazu porovnávání se vzorem využívali všechny smysluplné případy.

V následujícím příkladu `_` je použit případ při neúspěchu operace analýzy.

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L744-L762)]

[Aktivní vzory](./language-reference/active-patterns.md) představují další efektivní konstrukci pro použití s porovnáváním vzorů.  Umožňují rozdělit vstupní data do vlastních formulářů a jejich rozložení na webu volání porovnávání vzorů.  Mohou být také parametrizované, takže umožňují definovat oddíl jako funkci.  Rozšiřování předchozího příkladu na podporu aktivních vzorů vypadá nějak takto:

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>Volitelné typy

Jedním z speciálních případů rozlišených typů Union je typ možnosti, který je tak užitečný, aby byl součástí základní knihovny F #.

[Typ možnosti](./language-reference/options.md) je typ, který představuje jeden ze dvou případů: hodnotu nebo nic vůbec.  Používá se v jakémkoli scénáři, kdy hodnota může nebo nemusí být výsledkem konkrétní operace.  Tím se pak vynutí, abyste si v obou případech přihlédli na místo toho, aby se to týkalo v době kompilace.  Ty se často používají v rozhraních API `null` , kde se místo toho reprezentují "nic", což eliminuje nutnost zabývat se `NullReferenceException` v mnoha případech.

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Měrné jednotky

Jedna jedinečná funkce systému typů F # je schopnost poskytnout kontext pro číselné literály prostřednictvím měrných jednotek.

Měrné [jednotky](./language-reference/units-of-measure.md) umožňují přidružit číselný typ k jednotce, například měřiče, a mít funkce provádět práci na jednotkách, nikoli číselné literály.  To umožňuje kompilátoru ověřit, že typy číselných literálů předaného smyslem v rámci určitého kontextu, čímž eliminuje běhové chyby spojené s tímto druhem práce.

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

Základní knihovna jazyka F # definuje mnoho typů jednotek typu a převod jednotek.  Pokud se chcete dozvědět víc, podívejte se na [obor názvů FSharp. data. UnitSystems. si. UnitSymbols](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-data-unitsystems-si-unitsymbols.html).

## <a name="classes-and-interfaces"></a>Třídy a rozhraní

Jazyk F # má také plnou podporu tříd .NET, [rozhraní](./language-reference/interfaces.md), [abstraktních tříd](./language-reference/abstract-classes.md), [dědičnosti](./language-reference/inheritance.md)a tak dále.

[Třídy](./language-reference/classes.md) jsou typy, které představují objekty rozhraní .NET, které mohou mít vlastnosti, metody a události jako své [členy](./language-reference/members/index.md).

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

Definování obecných tříd je také velmi jasné.

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

Chcete-li implementovat rozhraní, můžete použít buď `interface ... with` syntaxi, nebo [výraz objektu](./language-reference/object-expressions.md).

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Které typy použít

Přítomnost tříd, záznamů, rozlišených sjednocení a řazených kolekcí členů vede na důležitou otázku: které byste měli použít?  Stejně jako většina všeho v životě závisí odpověď na vaše okolnosti.

Řazené kolekce členů jsou skvělé pro vracení více hodnot z funkce a použití ad-hoc agregace hodnot jako samotné hodnoty.

Záznamy jsou "krok nahoru" od řazených kolekcí členů, které mají pojmenované popisky a podporují volitelné členy.  Jsou skvělé pro proceduryou reprezentaci dat během přenosu prostřednictvím programu.  Protože mají strukturální rovnost, lze je snadno použít s porovnáním.

Rozlišené sjednocení má mnoho použití, ale výhody základního programu je možné je využít ve spojení s porovnáváním vzorů, aby se zohlednily všechny možné "tvary", které mohou mít data.  

Třídy jsou skvělé pro velký počet důvodů, například když potřebujete vyjádřit informace a také tyto informace spojit s funkcemi.  Jako pravidlo pro palec, pokud máte funkce, které jsou koncepčně svázané s některými daty, použití tříd a Princip objektově orientovaného programování je velká výhoda.  Třídy jsou také preferovaným datovým typem při spolupráci s C# a Visual Basic, protože tyto jazyky používají třídy pro skoro vše.

## <a name="next-steps"></a>Další kroky

Teď, když jste viděli některé z primárních funkcí jazyka, byste měli být připraveni napsat své první programy F #!  Podívejte se [Začínáme](get-started/index.md) a Naučte se, jak nastavit vývojové prostředí a napsat nějaký kód.

Další kroky pro další informace, které vám pomůžou, je, jak se vám líbí, ale [v jazyce F # doporučujeme seznámení s funkčním programováním](./introduction-to-functional-programming/index.md) a získat tak přehled o základních konceptech programování.  Ty budou nezbytné při vytváření robustních programů v jazyce F #.

Podívejte se také na [referenční informace jazyka F #](./language-reference/index.md) , abyste viděli komplexní kolekci koncepčního obsahu v F #.
