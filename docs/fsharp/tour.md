---
title: ProhlídkaF#
description: Prozkoumat některé klíčové funkce F# programovací jazyk v této ukázky s ukázkami kódu.
ms.date: 11/06/2018
ms.openlocfilehash: 32bf892e97b29fcaf426791ef9ada15c9c35b5ae
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143737"
---
# <a name="tour-of-f"></a>ProhlídkaF# #

Nejlepší způsob, jak získat informace o F# je pro čtení a zápis F# kódu. Tento článek bude fungovat jako seznámíte některé klíčové funkce F# jazyka a umožňují některé fragmenty kódu, které můžete spustit na svém počítači. Další informace o nastavení vývojového prostředí, projděte si [Začínáme](tutorials/getting-started/index.md).

Existují dva hlavní koncepty v F#: funkcí a typů.  Tato ukázka se zvýraznit funkce jazyka, které spadají do těchto dvou konceptů.

## <a name="executing-the-code-online"></a>Spouští kód online

Pokud nemáte F# na vašem počítači nainstalovaný, můžete spustit všechny ukázky online s [Fable REPL](http://fable.io/repl/). Fable je dialekt F# , který se spustí přímo v prohlížeči. Chcete-li zobrazit ukázky, které následují v REPL, podívejte se na **ukázky > Další > Prohlídka F#**  v panelu nabídky na levé straně Fable REPL.

## <a name="functions-and-modules"></a>Funkce a moduly

Většina základních částí žádné F# programu jsou ***funkce*** uspořádají ***moduly***.  [Funkce](language-reference/functions/index.md) provádějí práci na vstupy pro vytvoření výstupy a jsou uspořádané pod [moduly](language-reference/modules.md), který jste hlavní způsob, jak vše seskupit v F#.  Jsou definovány pomocí [ `let` vazby](language-reference/functions/let-bindings.md), které funkce pojmenujte a definovat jeho argumenty.

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` vazby jsou také, jak vázat hodnotu s názvem, podobně jako na proměnnou v jiných jazycích.  `let` vazby jsou ***neměnné*** ve výchozím nastavení, což znamená, že jakmile hodnotě nebo funkci je vázán na název, nejde změnit na místě.  Tím se liší od proměnné v jiných jazycích, které jsou ***proměnlivé***, což znamená jejich hodnoty lze změnit v libovolném bodě v čase.  Pokud budete potřebovat proměnlivé vazby, můžete použít `let mutable ...` syntaxe.

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>Řetězce, čísla a logické hodnoty

Jako jazyk .NET F# podporuje stejné základní [primitivní typy](language-reference/primitive-types.md) , která existují v rozhraní .NET.

Zde je, jak různé číselné typy jsou reprezentovány v F#:

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

Zde je jaké logické hodnoty a provádění základních podmíněné logiky bude vypadat takto:

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

A tady je co basic [řetězec](language-reference/strings.md) manipulaci s bude vypadat takto:

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>Řazené kolekce členů

[Řazené kolekce členů](language-reference/tuples.md) je to důležitá záležitost v F#.  Jsou to seskupení nepojmenované, ale seřazený hodnot, které lze považovat za samotné hodnoty.  Představte si je jako hodnoty, které se shromažďují od jiné hodnoty.  Mají mnoho účelů, jako je například jednoduše vrátí více hodnot z funkce nebo seskupení hodnot ke zvýšení pohodlí některé ad-hoc.

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

Od verze F# 4.1, můžete také vytvořit `struct` řazené kolekce členů.  Tyto také plně spolupracovat s C# 7/jazyka Visual Basic 15 řazených kolekcí členů, které jsou také `struct` řazených kolekcí členů:

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

Je důležité si uvědomit, že protože `struct` řazených kolekcí členů jsou typy hodnot, jsou nelze implicitně převést na odkaz řazených kolekcí členů, nebo naopak.  Je nutné explicitně převést mezi referenční a struktura řazené kolekce členů.

## <a name="pipelines-and-composition"></a>Kanály a skládání

Operátory kanálu jako `|>` jsou často používány při zpracování dat v F#. Tyto operátory jsou funkce, které umožňují vytvořit "kanály" funkcí, pružným způsobem. Následující příklad vás provede jak můžete využít tyto operátory k vytváření jednoduchých funkční kanál:

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

Provedené předchozí ukázce použití mnoha funkcí F#, včetně funkcí pro zpracování seznamu, funkce první třídy, a [částečné použití argumentů](language-reference/functions/index.md#partial-application-of-arguments). I když hlubší porozumění tyto koncepty můžete stát poněkud rozšířené, by mělo být jasné funkce jak snadno lze použít ke zpracování dat při sestavování kanálů.

## <a name="lists-arrays-and-sequences"></a>Seznamů, polí a pořadí

Seznamů, polí a pořadí jsou tři primární kolekci typů v F# základní knihovny.

[Obsahuje seznam](language-reference/lists.md) jsou seřazené, neměnné kolekce elementů stejného typu.  Jsou jednotlivě propojený seznam, což znamená, že jsou určeny pro výčet, ale špatně zvolená pro náhodný přístup a zřetězení, pokud jsou velké.  Tento rozdíl od seznamy v dalších oblíbených jazyků, které obvykle nevyužívají jednotlivě propojený seznam představující seznamy.

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[Pole](language-reference/arrays.md) jsou pevné velikosti, *proměnlivé* kolekce elementů stejného typu.  Podporují rychlý náhodný přístup prvků a jsou rychlejší než F# uvádí, protože se právě souvislých bloků paměti.

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[Pořadí](language-reference/sequences.md) jsou logické řady elementů, všechny stejného typu.  Jedná se o obecnější typ než seznamy a pole, který "zobrazení" do žádné logické řady elementů.  Jsou také příležitost vyniknout protože můžou být ***opožděné***, což znamená, že prvky nelze vypočítat, jenom když jsou potřeba.

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>Rekurzivní funkce

Zpracování kolekce nebo pořadí prvků se obvykle provádí pomocí [rekurze](language-reference/functions/index.md#recursive-functions) v F#.  I když F# obsahuje podporu pro smyčky a imperativní programování rekurze je preferovaná, protože je jednodušší zajistit správnost.

> [!NOTE]
> Následující příklad používá porovnávání vzorů přes `match` výrazu.  Tento základní konstruktor se věnujeme dále v tomto článku.

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F#také obsahuje plnou podporu pro volání optimalizaci funkce Tail, což je způsob, jak optimalizovat rekurzivní volání jsou stejně rychlé jako konstrukci smyčky.

## <a name="record-and-discriminated-union-types"></a>Záznam a typy rozlišených sjednocení

Záznam a sjednocovacích typů jsou dvě základní datové typy používané v F# kódu a obecně jsou nejlepší způsob, jak reprezentaci dat v F# programu.  I když se díky tomu je podobný třídy v jiných jazycích, jedním z primárních rozdíly mezi nimi je, ke kterým mají sémantiku strukturální rovnost.  To znamená, že jsou "nativní" srovnatelné a rovnost je jednoduchá – jenom zkontrolujte, jestli jedna je rovná druhé.

[Záznamy](language-reference/records.md) jsou agregátem pojmenovaných hodnot s volitelnými členy (jako jsou metody).  Pokud jste obeznámeni s použitím jazyka C# nebo Java, pak tyto měli pocit, že podobný POCOs nebo objektů Pojo – pouze s strukturální rovnost a méně procedury.

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

Od verze F# 4.1, můžete také představovat záznamy jako `struct`s.  Používá se k tomu `[<Struct>]` atribut:

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[Rozlišovaná sjednocení (du)](language-reference/discriminated-unions.md) jsou hodnoty, které by mohly představovat celou řadu pojmenovaných forem nebo případů.  Data uložená v typu může být jedna z několika různých hodnot.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Můžete také použít du jako *jedním případem Rozlišované sjednocení*, abychom vám pomohli s domény oproti primitivním typům modelování.  Často, řetězce a jiné primitivní typy se používají k vyjádření něco a jsou tedy uvedeny konkrétní význam.  Nicméně používání pouze primitivní znázornění dat může přinést omylem přiřadíte nesprávnou hodnotu!  Představuje jednotlivé typy informací jako odlišné sjednocení jedním případem můžete vynutit správnosti v tomto scénáři.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

Jak ukazuje předchozí ukázka, chcete-li získat základní hodnotu v jedním případem rozlišovaného sjednocení, musíte ho explicitně rozbalení.

Kromě toho du podporují i rekurzivní definice, umožňuje snadno představují stromy a ze své podstaty dat rekurzivní.  Tady je například jak může představovat binárního vyhledávacího stromu s `exists` a `insert` funkce.

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Protože du umožňují představují rekurzivní strukturu stromu s datovým typem, operací nad touto strukturou rekurzivní je jednoduché a zaručuje správnosti.  To je podporováno také v porovnávání vzorů, jak je znázorněno níže.

Kromě toho může představovat du jako `struct`s `[<Struct>]` atribut:

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

Existují však dvou důležitých věcí, které vzít v úvahu při tím:

1. Rozlišované sjednocení typu Struktura nemůže být definované rekurzivně.
2. Rozlišované sjednocení typu Struktura musí mít jedinečné názvy pro každý ze svých případů.

Pokud nedodržíte výše způsobí chybu kompilace.

## <a name="pattern-matching"></a>Porovnávání vzorů

[Vzor odpovídající](language-reference/pattern-matching.md) je F# funkci jazyka, která umožňuje správnosti provozu na F# typy.  Ve výše uvedené ukázky, budete si pravděpodobně všimli hodně `match x with ...` syntaxe.  Tento konstruktor umožňuje kompilátoru, který by rozuměla "tvar" datové typy, chcete-li požadovat, abyste pro účet pro všechny případy, je to možné, používáte-li datový typ prostřednictvím, která se označuje jako vyčerpávající porovnávání vzorů.  To je velmi efektivní správnost a cleverly umožňuje "přenést" co bude obvykle runtime problém v době kompilace.

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

Můžete také použít zkrácený `function` konstrukce pro porovnávání vzorů, což je užitečné při psaní využívání funkce, která zjednodušují [částečné použití argumentů](language-reference/functions/index.md#partial-application-of-arguments):

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L744-L762)]

Možná jste si je použití `_` vzor.  To se označuje jako [zástupných](language-reference/pattern-matching.md#wildcard-pattern), což je způsob, jak o tom, že "I nezáleží na tom něco je".  I když je to praktické, můžete nechtěně vynechat vyčerpávající porovnávání vzorů už výhod kompilace enforcements, pokud si nejste opatrní při použití `_`.  To je nejlepší použít při nezáleží určité rozložená typu při vzor odpovídající nebo konečné klauzule mají výčtu každopádně smysluplné ve vzorku s odpovídajícím výrazem.

[Aktivní vzory](language-reference/active-patterns.md) představují další efektivní konstrukci pro použití s porovnáváním vzorů.  Umožňují rozdělit vstupní data do vlastních forem, přičemž rozkládají v místě volání webu shoda vzoru.  Mohou také být parametrizovány, což umožní definovat oddílu jako funkce.  Rozšíření pro podporu aktivní vzory předchozího příkladu vypadá přibližně takto:

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>Doplňkové typy

Jeden zvláštní případ rozlišovaného sjednocení s typy je typ možnosti, což je užitečné, že je součástí F# základní knihovny.

[Typ možnosti](language-reference/options.md) je typ, který představuje jednu ze dvou případů: hodnotu, nebo nic vůbec.  Používá se ve všech scénářích, kde hodnota může nebo nemusí dojít z konkrétní operace.  To potom vynutí pro oba případy, takže obavy za kompilace než modul runtime žádný problém.  Ty se často používají v rozhraních API kde `null` se používá k reprezentování "hodnotu nothing" místo toho tedy tím eliminuje nutnost starat o `NullReferenceException` v mnoha případech platí.

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>Měrné jednotky

Jeden jedinečné funkce F#na systém typů je schopnost poskytovat kontext pro číselné literály prostřednictvím měrné jednotky.

[Měrné jednotky](language-reference/units-of-measure.md) umožňují přiřaďte číselný typ jednotek, jako je například měřičů, a mít funkce provádějí práci na jednotky spíše než číselné literály.  To umožňuje kompilátoru ověřte, že typy číselné literály předaný dávat smysl v určitém kontextu, čímž se zmenšuje chyby za běhu přidružené k tento druh pracovní.

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

F# Základní knihovna definuje mnoho SI typy jednotek a převody jednotek.  Další informace, podívejte se [Microsoft.fsharp.data.unitsystems.si – Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d).

## <a name="classes-and-interfaces"></a>Třídy a rozhraní

F#také obsahuje plnou podporu pro třídy .NET [rozhraní](language-reference/interfaces.md), [abstraktní třídy](language-reference/abstract-classes.md), [dědičnosti](language-reference/inheritance.md), a tak dále.

[Třídy](language-reference/classes.md) jsou typy, které představují objekty .NET, který může mít vlastnosti, metody a události jako jeho [členy](language-reference/members/index.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

Definování obecné třídy je také velmi jednoduché.

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

Chcete-li implementovat rozhraní, můžete použít buď `interface ... with` syntaxe nebo [objektový výraz](language-reference/object-expressions.md).

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>Typy, které chcete použít

Třídy, záznamy, Rozlišované sjednocení a řazených kolekcí členů vede k důležitá Otázka: které byste měli používat?  Podobně jako většina všechno v životě odpověď závisí na konfiguraci.

Řazené kolekce členů jsou velmi vhodné pro vrácení více hodnot z funkce a pomocí ad-hoc agregace hodnot jako vlastní hodnota.

Záznamy jsou "krok až" z řazené kolekce členů s názvem popisky a podpora pro volitelné členy.  Jsou skvělé pro diskuse nad reprezentace dat během přenosu prostřednictvím programu.  Protože mají strukturální rovnost, jsou snadno použitelné s porovnání.

Rozlišovaná sjednocení mají spoustu využití, ale výhody pro jádro je moct dál využívat ve spojení s porovnáváním vzorů pro všechny možné "tvary", které může mít data.  

Třídy jsou velmi vhodné pro velký počet úmyslů, například když potřebujete znázornění informací a také spojit tyto informace k funkcím.  Říci když máte funkci, která je koncepčně vázané na data, používání tříd a principy Object-Oriented programování je velkou výhodou.  Třídy jsou také upřednostňované datový typ při vzájemné spolupráci s C# a Visual Basic, protože tyto jazyky použití tříd pro téměř vše, co.

## <a name="next-steps"></a>Další kroky

Teď, když jste viděli některé z primární funkce jazyka, měli byste napsat první F# programy!  Podívejte se na [Začínáme](tutorials/getting-started/index.md) informace o nastavení vývojového prostředí a napsání kódu.

Další kroky pro získání informací může být cokoli, co chcete, ale doporučujeme [Úvod do funkčního programování v F# ](introduction-to-functional-programming/index.md) k blíž se seznámit s základní koncepty Funkcionálního programování.  Budou to důležité pro vytváření robustních aplikací F#.

Také, podívejte se [ F# referenční informace k jazyku](language-reference/index.md) zobrazíte ucelená kolekce koncepční obsah na F#.
