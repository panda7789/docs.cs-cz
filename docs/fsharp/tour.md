---
title: Prohlídka jazyka F#
description: Prohlédněte si některé klíčové funkce F# programovacího jazyka v této prohlídce s ukázkami kódu.
ms.date: 11/06/2018
ms.openlocfilehash: cfea2827dcec65f9e3606e8528179029e1f2db84
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423809"
---
# <a name="tour-of-f"></a>Prohlídka F\#

Nejlepším způsobem, jak se dozvědět F# , je čtení a psaní F# kódu. Tento článek bude fungovat jako prohlídka prostřednictvím některých klíčových funkcí F# jazyka a poskytuje některé fragmenty kódu, které můžete na svém počítači spustit. Další informace o nastavení vývojového prostředí najdete [Začínáme](get-started/index.md).

Existují dvě primární koncepce F#: funkce a typy.  Tato prohlídka bude zdůraznit funkce jazyka, které spadají do těchto dvou konceptů.

## <a name="executing-the-code-online"></a>Online spuštění kódu

Pokud jste na svém F# počítači nenainstalovali, můžete v prohlížeči spustit všechny ukázky pomocí [ F# příkazu WebAssembly](https://tryfsharp.fsbolero.io/). Fable je dialekt F# , který se spouští přímo v prohlížeči. Pokud si chcete prohlédnout ukázky, které následují ve REPL, podívejte se na **ukázky > > F# prohlídku** v levém panelu nabídek REPLu Fable.

## <a name="functions-and-modules"></a>Funkce a moduly

Nejdůležitější části každého F# programu jsou ***funkce*** uspořádané do ***modulů***.  [Funkce](./language-reference/functions/index.md) provádí práci na vstupech a vytváří výstupy a jsou uspořádány pod [moduly](./language-reference/modules.md), které jsou hlavním způsobem, v F#němž se seskupují objekty.  Jsou definovány pomocí [`let` vazby](./language-reference/functions/let-bindings.md), která dává funkci název a definuje její argumenty.

[!code-fsharp[BasicFunctions](~/samples/snippets/fsharp/tour.fs#L101-L133)]

vazby `let` jsou také způsobem vázání hodnoty k názvu, podobně jako proměnná v jiných jazycích.  vazby `let` jsou ve výchozím nastavení ***neměnné*** , což znamená, že jakmile je hodnota nebo funkce vázána na název, nelze ji změnit místně.  To je v kontrastu s proměnnými v jiných jazycích, které jsou ***proměnlivé***, což znamená, že jejich hodnoty je možné kdykoli změnit v libovolném časovém okamžiku.  Pokud potřebujete proměnlivou vazbu, můžete použít `let mutable ...` syntaxi.

[!code-fsharp[Immutability](~/samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Čísla, logické hodnoty a řetězce

Jako jazyk .NET F# podporuje stejné základní [primitivní typy](language-reference/basic-types.md) , které existují v rozhraní .NET.

Tady je způsob reprezentace různých číselných typů v F#:

[!code-fsharp[Numbers](~/samples/snippets/fsharp/tour.fs#L49-L68)]

Tady je, jaké logické hodnoty a provádění základní podmíněné logiky vypadají takto:

[!code-fsharp[Bools](~/samples/snippets/fsharp/tour.fs#L142-L152)]

A jak vypadá základní manipulace s [řetězci](./language-reference/strings.md) , vypadá takto:

[!code-fsharp[Strings](~/samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>N-tice

[Řazené kolekce členů](./language-reference/tuples.md) jsou velkými transakcemi F#.  Jsou seskupením nepojmenovaných, ale seřazené hodnoty, které lze považovat za samotné hodnoty.  Ty si můžete představit jako hodnoty agregované z jiných hodnot.  Mají mnoho použití, jako je například pohodlné vrácení více hodnot z funkce nebo seskupování hodnot pro některé praktické pohodlí.

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L186-L203)]

Od F# 4,1 můžete také vytvořit `struct` řazené kolekce členů.  Tyto akce také spolupracují s C# 7/Visual Basic 15 řazenými kolekcemi členů, které jsou také `struct` řazené kolekce členů:

[!code-fsharp[Tuples](~/samples/snippets/fsharp/tour.fs#L205-L218)]

Je důležité si uvědomit, že protože `struct` řazené kolekce členů jsou typy hodnot, nelze je implicitně převést na referenční řazené kolekce členů ani naopak.  Je nutné explicitně převést mezi odkazem a strukturou řazené kolekce členů.

## <a name="pipelines-and-composition"></a>Kanály a kompozice

Operátory kanálu, jako je například `|>`, jsou používány rozsáhle při F#zpracování dat v. Tyto operátory jsou funkce, díky kterým můžete flexibilním způsobem vytvořit kanály funkcí. V následujícím příkladu se dozvíte, jak můžete využít tyto operátory k sestavení jednoduchého funkčního kanálu:

[!code-fsharp[Pipelines](~/samples/snippets/fsharp/tour.fs#L227-L282)]

Předchozí ukázka využívala mnoho funkcí nástroje, F#včetně funkcí pro zpracování seznamu, funkcí první třídy a [částečné aplikace](./language-reference/functions/index.md#partial-application-of-arguments). I když může být důkladné porozumění každé z těchto konceptů poněkud pokročilé, mělo by být jasné, jak snadno se funkce dají použít ke zpracování dat při sestavování kanálů.

## <a name="lists-arrays-and-sequences"></a>Seznamy, pole a posloupnosti

Seznamy, pole a sekvence jsou tři typy primární kolekce v F# základní knihovně.

[Seznamy](./language-reference/lists.md) jsou seřazené, neměnné kolekce prvků stejného typu.  Jedná se o jednorázově propojené seznamy, což znamená, že jsou určeny pro výčet, ale nedostatečná volba pro náhodný přístup a zřetězení, pokud jsou velké.  Na rozdíl od seznamů v jiných oblíbených jazycích, které obvykle nepoužívají samostatně propojený seznam k reprezentaci seznamů.

[!code-fsharp[Lists](~/samples/snippets/fsharp/tour.fs#L309-L359)]

[Pole](./language-reference/arrays.md) jsou pevná velikost, *proměnlivé* kolekce prvků stejného typu.  Podporují rychlý náhodný přístup k prvkům a jsou rychlejší než F# seznamy, protože jsou pouze souvislými bloky paměti.

[!code-fsharp[Arrays](~/samples/snippets/fsharp/tour.fs#L368-L407)]

[Sekvence](./language-reference/sequences.md) jsou logické řady prvků, všechny stejného typu.  Jedná se o obecnější typ než seznamy a pole, které je možné zobrazit v libovolné logické sérii prvků.  Jsou také úsporné, protože mohou být ***opožděny***, což znamená, že prvky lze vypočítat pouze v případě potřeby.

[!code-fsharp[Sequences](~/samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Rekurzivní funkce

Zpracování kolekcí nebo sekvencí prvků se obvykle provádí pomocí [rekurze](./language-reference/functions/index.md#recursive-functions) v F#.  I F# když podporuje smyčky a imperativní programování, rekurze je preferovaná, protože je snazší zaručit správnost.

> [!NOTE]
> V následujícím příkladu je použito porovnávání vzorů prostřednictvím výrazu `match`.  Tato základní konstrukce se zabývá dále v tomto článku.

[!code-fsharp[RecursiveFunctions](~/samples/snippets/fsharp/tour.fs#L461-L500)]

F#má také úplnou podporu pro optimalizaci volání funkce tail, což je způsob optimalizace rekurzivních volání, která jsou stejně rychlá jako konstrukce smyčky.

## <a name="record-and-discriminated-union-types"></a>Typy záznamů a rozlišených sjednocení

Typy záznamů a sjednocení jsou dva základní datové typy, F# které se používají v kódu, a jsou obecně nejlepším způsobem reprezentace dat F# v programu.  I když se to podobá třídám v jiných jazycích, jedna z jejich primárních rozdílů je, že mají strukturální sémantiku rovnosti.  To znamená, že jsou "nativně" srovnatelné a rovnost je přímá – stačí pouze kontrolovat, zda je jeden jiný.

[Záznamy](./language-reference/records.md) jsou agregátem pojmenovaných hodnot s volitelnými členy (jako jsou metody).  Pokud jste obeznámeni s C# nástrojem nebo Java, pak by se měly líbit podobně jako POCOs nebo Pojo – stejně jako strukturální rovnost a menší procedury.

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L507-L559)]

Od F# 4,1 můžete také reprezentovat záznamy jako `struct`s.  To se provádí s atributem `[<Struct>]`:

[!code-fsharp[Records](~/samples/snippets/fsharp/tour.fs#L561-L568)]

[Rozlišené sjednocení (du)](./language-reference/discriminated-unions.md) jsou hodnoty, které by mohly představovat počet pojmenovaných forem nebo případů.  Data uložená v typu můžou být jedna z několika různých hodnot.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L575-L631)]

Du můžete použít také jako *jednotná sjednocení*, která vám pomůžou s modelováním domén přes primitivní typy.  Často se používá k reprezentaci řetězců a dalších primitivních typů, které představují konkrétní význam.  Použití jenom primitivní reprezentace dat ale může mít za následek omylem přiřazení nesprávné hodnoty!  V takovém případě může být v tomto scénáři vyjasnění každého typu informací v případě samostatného sjednocení s jedním případem.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L633-L654)]

Jak ukazuje výše uvedený příklad, k získání základní hodnoty v jednoduchém sjednocovacím sjednocení, je nutné explicitně zrušit balení.

Kromě toho du také podporuje rekurzivní definice, což vám umožní snadno reprezentovat stromy a podstaty rekurzivní data.  Tady je příklad, jak můžete reprezentovat binární strom vyhledávání s funkcemi `exists` a `insert`.

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L656-L683)]

Vzhledem k tomu, že du umožňuje znázornit rekurzivní strukturu stromu v datovém typu, která je provozována v této rekurzivní struktuře, je jednoduchá a zaručuje správnost.  Podporuje se také v porovnávání vzorů, jak je znázorněno níže.

Kromě toho můžete reprezentovat du jako `struct`s s atributem `[<Struct>]`:

[!code-fsharp[Unions](~/samples/snippets/fsharp/tour.fs#L685-L696)]

Existují však dvě klíčové věci, které je potřeba vzít v úvahu:

1. Hodnotu DU pro struct nelze rekurzivně definovat.
2. Struktura DU musí mít jedinečné názvy pro každý z jejích případů.

Nepodaří-li se postupovat podle výše uvedeného výsledku, dojde k chybě kompilace.

## <a name="pattern-matching"></a>Porovnávání vzorů

[Porovnávání vzorů](./language-reference/pattern-matching.md) je F# funkce jazyka, která umožňuje správnou funkci pro provoz F# na typech.  Ve výše uvedených ukázkách jste si pravděpodobně všimli, že se syntaxí `match x with ...`.  Tento konstruktor umožňuje kompilátoru, který může pochopit "tvar" datových typů, aby bylo možné přihlédnout ke všem možným případům při použití datového typu prostřednictvím toho, co se říká vyčerpávající porovnávání vzorů.  To je neuvěřitelně výkonné pro správnost a dá se cleverly použít k "zaznamenání", co by normálně představovalo při kompilaci za běhu.

[!code-fsharp[PatternMatching](~/samples/snippets/fsharp/tour.fs#L705-L742)]

Něco, co jste si všimli, je použití `_`ho vzoru.  Tento vzor je známý jako [zástupný znak](./language-reference/pattern-matching.md#wildcard-pattern), což je způsob, jak se vyjádřit, co něco je.  I když je to pohodlnější, můžete náhodně obejít porovnávání vyčerpávajících vzorů a už nebudete využívat výhody při kompilaci, pokud nebudete s používáním `_`opatrní.  Je nejvhodnější použít, pokud nezáleží na určitých částech desloženého typu při porovnávání vzorů, nebo na konci klauzule, pokud jste ve výrazu porovnávání se vzorem využívali všechny smysluplné případy.

[Aktivní vzory](./language-reference/active-patterns.md) představují další efektivní konstrukci pro použití s porovnáváním vzorů.  Umožňují rozdělit vstupní data do vlastních formulářů a jejich rozložení na webu volání porovnávání vzorů.  Mohou být také parametrizované, takže umožňují definovat oddíl jako funkci.  Rozšiřování předchozího příkladu na podporu aktivních vzorů vypadá nějak takto:

[!code-fsharp[ActivePatterns](~/samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>Volitelné typy

Jedním z speciálních případů rozlišených typů Union je typ možnosti, který je tak užitečný, aby byl součástí F# základní knihovny.

[Typ možnosti](./language-reference/options.md) je typ, který představuje jeden ze dvou případů: hodnotu nebo nic vůbec.  Používá se v jakémkoli scénáři, kdy hodnota může nebo nemusí být výsledkem konkrétní operace.  Tím se pak vynutí, abyste si v obou případech přihlédli na místo toho, aby se to týkalo v době kompilace.  Ty se často používají v rozhraních API, kde `null` slouží k reprezentaci "Nothing", což eliminuje nutnost zabývat se `NullReferenceException`mi v mnoha případech.

[!code-fsharp[Options](~/samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Měrné jednotky

Jedna jedinečná funkce F#systému typů je schopnost poskytnout kontext pro číselné literály prostřednictvím měrných jednotek.

Měrné [jednotky](./language-reference/units-of-measure.md) umožňují přidružit číselný typ k jednotce, například měřiče, a mít funkce provádět práci na jednotkách, nikoli číselné literály.  To umožňuje kompilátoru ověřit, že typy číselných literálů předaného smyslem v rámci určitého kontextu, čímž eliminuje běhové chyby spojené s tímto druhem práce.

[!code-fsharp[UnitsOfMeasure](~/samples/snippets/fsharp/tour.fs#L817-L842)]

F# Základní knihovna definuje mnoho typů jednotek si a převod jednotek.  Pokud se chcete dozvědět víc, podívejte se na [obor názvů Microsoft.FSharp.data.UnitSystems.si](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Třídy a rozhraní

F#má také úplnou podporu pro třídy .NET, [rozhraní](./language-reference/interfaces.md), [abstraktní třídy](./language-reference/abstract-classes.md), [Dědičnost](./language-reference/inheritance.md)a tak dále.

[Třídy](./language-reference/classes.md) jsou typy, které představují objekty rozhraní .NET, které mohou mít vlastnosti, metody a události jako své [členy](./language-reference/members/index.md).

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L845-L880)]

Definování obecných tříd je také velmi jasné.

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L883-L908)]

Chcete-li implementovat rozhraní, můžete použít buď syntaxi `interface ... with`, nebo [výraz objektu](./language-reference/object-expressions.md).

[!code-fsharp[Classes](~/samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Které typy použít

Přítomnost tříd, záznamů, rozlišených sjednocení a řazených kolekcí členů vede na důležitou otázku: které byste měli použít?  Stejně jako většina všeho v životě závisí odpověď na vaše okolnosti.

Řazené kolekce členů jsou skvělé pro vracení více hodnot z funkce a použití ad-hoc agregace hodnot jako samotné hodnoty.

Záznamy jsou "krok nahoru" od řazených kolekcí členů, které mají pojmenované popisky a podporují volitelné členy.  Jsou skvělé pro proceduryou reprezentaci dat během přenosu prostřednictvím programu.  Protože mají strukturální rovnost, lze je snadno použít s porovnáním.

Rozlišené sjednocení má mnoho použití, ale výhody základního programu je možné je využít ve spojení s porovnáváním vzorů, aby se zohlednily všechny možné "tvary", které mohou mít data.  

Třídy jsou skvělé pro velký počet důvodů, například když potřebujete vyjádřit informace a také tyto informace spojit s funkcemi.  Jako pravidlo pro palec, pokud máte funkce, které jsou koncepčně svázané s některými daty, použití tříd a Princip objektově orientovaného programování je velká výhoda.  Třídy jsou také preferovaným datovým typem při spolupráci s C# a Visual Basic, protože tyto jazyky používají třídy pro skoro vše.

## <a name="next-steps"></a>Další kroky

Teď, když jste viděli některé z primárních funkcí jazyka, byste měli být připraveni napsat své první F# programy!  Podívejte se [Začínáme](get-started/index.md) a Naučte se, jak nastavit vývojové prostředí a napsat nějaký kód.

Další kroky pro další informace vám můžou být libovolné, co byste chtěli, ale doporučujeme [Seznámení s F# funkčním programováním v](./introduction-to-functional-programming/index.md) nástroji, abyste se mohli seznámit s koncepty základních funkcí programování.  Ty budou zásadní při vytváření robustních programů v F#nástroji.

Podívejte se také na [ F# referenční informace k jazyku](./language-reference/index.md) , kde se zobrazí komplexní kolekce koncepčního obsahu. F#
