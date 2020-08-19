---
title: Sekvence
description: 'Naučte se používat sekvence F #, pokud máte rozsáhlou uspořádanou kolekci dat, ale nechcete nutně očekávat použití všech prvků.'
ms.date: 08/13/2020
ms.openlocfilehash: c84e0aebcc79a595c0ae3b9075648fb629bdd65c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559034"
---
# <a name="sequences"></a>Sekvence

*Sekvence* je logická řada prvků všech jednoho typu. Sekvence jsou zvláště užitečné v případě, že máte rozsáhlou uspořádanou kolekci dat, ale nemusí nutně očekávat použití všech prvků. Jednotlivé prvky sekvence jsou vypočítány pouze jako povinné, takže sekvence může poskytovat lepší výkon než seznam v situacích, kdy nejsou použity všechny prvky. Sekvence jsou reprezentovány `seq<'T>` typem, který je aliasem pro <xref:System.Collections.Generic.IEnumerable%601> . Proto může být jakýkoli typ rozhraní .NET, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní, použit jako sekvence. [Modul SEQ](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) poskytuje podporu pro manipulace zahrnující sekvence.

## <a name="sequence-expressions"></a>Výrazy sekvence

*Výraz sekvence* je výraz, který je vyhodnocen jako sekvence. Výrazy sekvence mohou mít několik forem. Nejjednodušší formulář určuje rozsah. Například `seq { 1 .. 5 }` vytvoří sekvenci, která obsahuje pět prvků, včetně koncových bodů 1 a 5. Můžete také určit přírůstek (nebo snížení) mezi dvěma dvojitými tečkami. Například následující kód vytvoří sekvenci násobek 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Výrazy sekvence jsou tvořeny výrazy jazyka F #, které vytvářejí hodnoty sekvence. Hodnoty můžete také generovat programově:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Předchozí příklad používá `->` operátor, který umožňuje určit výraz, jehož hodnota se stane součástí sekvence. Můžete použít pouze `->` v případě, že každá část kódu, která následuje, vrací hodnotu.

Alternativně můžete zadat `do` klíčové slovo s nepovinným `yield` následujícím způsobem:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Následující kód vygeneruje seznam dvojic souřadnic spolu s indexem do pole, které představuje mřížku. Všimněte si, že první `for` výraz vyžaduje, `do` aby byl zadán.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if`Výraz použitý v sekvenci je filtr. Chcete-li například vygenerovat sekvenci pouze číselných apostrofů za předpokladu, že máte funkci `isprime` typu `int -> bool` , sestavte sekvenci následujícím způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Jak bylo uvedeno dříve, `do` je zde požadováno, protože není k dispozici žádná `else` větev, která přechází do `if` . Pokud se pokusíte použít `->` , zobrazí se chyba oznamující, že ne všechny větve vrací hodnotu.

## <a name="the-yield-keyword"></a>Klíčové slovo `yield!`

V některých případech můžete chtít zahrnout sekvenci prvků do jiné sekvence. Chcete-li zahrnout sekvenci v rámci jiné sekvence, je nutné použít `yield!` klíčové slovo:

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

Dalším způsobem, jak si myslíme `yield!` , je, že sloučí vnitřní sekvenci a potom v nadřazené sekvenci vloží.

Při `yield!` použití ve výrazu musí všechny ostatní jednotlivé hodnoty používat `yield` klíčové slovo:

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

Předchozí příklad vytvoří hodnotu `x` kromě všech hodnot z `1` na `x` pro každý `x` .

## <a name="examples"></a>Příklady

První příklad používá výraz sekvence, který obsahuje iteraci, filtr a výtěžnost pro vygenerování pole. Tento kód vytiskne sekvenci prvočísla mezi 1 a 100 do konzoly.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Následující příklad vytvoří tabulku násobení, která se skládá z řazených kolekcí členů tří prvků, z nichž každý obsahuje dva faktory a produkt:

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Následující příklad ukazuje použití `yield!` pro kombinování jednotlivých sekvencí do jediné konečné sekvence. V tomto případě jsou sekvence pro každý podstrom v binárním stromu zřetězeny rekurzivní funkcí a vytvoří finální sekvenci.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Používání sekvencí

Sekvence podporují mnoho stejných funkcí jako [seznamy](lists.md). Sekvence také podporují operace, jako je seskupování a počítání, pomocí funkcí pro generování klíčů. Sekvence také podporují více různorodých funkcí pro extrakci dílčích sekvencí.

Mnoho datových typů, například seznamy, pole, sady a mapy, jsou implicitně sekvencované, protože se jedná o vyčíslitelné kolekce. Funkce, která přebírá sekvenci jako argument funguje s libovolnými běžnými datovými typy jazyka F # kromě libovolného datového typu .NET, který implementuje `System.Collections.Generic.IEnumerable<'T>` . Naproti tomu funkci, která přebírá seznam jako argument, který může přijímat jenom seznamy. Typ `seq<'T>` je zkratka typu pro `IEnumerable<'T>` . To znamená, že každý typ, který implementuje obecné `System.Collections.Generic.IEnumerable<'T>` , včetně polí, seznamů, sad a map v F # a také většiny typů kolekcí .NET, je kompatibilní s `seq` typem a lze jej použít všude, kde je očekávána sekvence.

## <a name="module-functions"></a>Funkce modulu

[Modul SEQ](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) v [oboru názvů FSharp. Collections](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections.html) obsahuje funkce pro práci s sekvencemi. Tyto funkce fungují společně se seznamy, poli, mapami a sadami, protože všechny tyto typy jsou vyčíslitelné, a proto je lze považovat za sekvence.

## <a name="creating-sequences"></a>Vytváření sekvencí

Můžete vytvářet sekvence pomocí výrazů pořadí, jak je popsáno výše, nebo pomocí určitých funkcí.

Prázdnou sekvenci lze vytvořit pomocí [Seq. Empty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#empty)nebo můžete vytvořit sekvenci pouze jednoho zadaného elementu pomocí [Seq. singleton](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#singleton).

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

Pomocí [Seq.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#init) lze vytvořit sekvenci, pro kterou jsou vytvořeny prvky pomocí funkce, kterou zadáte. Můžete také zadat velikost sekvence. Tato funkce je stejná jako [List.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#init), s tím rozdílem, že elementy nejsou vytvořeny, dokud neprovedete iteraci v sekvenci. Následující kód ilustruje použití funkce `Seq.init`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

Výstup je

```console
0 10 20 30 40
```

Pomocí funkcí [Seq. ofArray –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofArray) a [seq. oflist –&#60; ne&#62;te](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofList), můžete vytvořit sekvence z polí a seznamů. Pole a seznamy však můžete také převést na sekvence pomocí operátoru přetypování. Obě metody jsou uvedeny v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

Pomocí [Seq. cast](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cast)můžete vytvořit sekvenci ze slabě typované kolekce, jako jsou například definované v `System.Collections` . Tyto slabě typové kolekce mají typ prvku `System.Object` a jsou vyčísleny pomocí neobecného `System.Collections.Generic.IEnumerable&#96;1` typu. Následující kód ilustruje použití `Seq.cast` pro převod na `System.Collections.ArrayList` sekvenci.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

Můžete definovat nekonečné sekvence pomocí funkce [Seq.initInfinite](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#initInfinite) . Pro takové sekvence zadáte funkci, která generuje každý prvek z indexu elementu. Nekonečné sekvence jsou možné z důvodu opožděného vyhodnocení; prvky jsou vytvořeny podle potřeby voláním funkce, kterou zadáte. Následující příklad kódu vytvoří nekonečnou sekvenci čísel s plovoucí desetinnou čárkou, v tomto případě alternující řady reciprocals čtverců po sobě jdoucích celých čísel.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq. unskládání](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#unfold) generuje sekvenci z funkce výpočtu, která přebírá stav a transformuje ho za účelem vytvoření každého následného prvku v sekvenci. Stav je pouze hodnota, která se používá k výpočtu každého prvku a může se změnit při výpočtu každého prvku. Druhý argument na `Seq.unfold` je počáteční hodnota, která se používá ke spuštění sekvence. `Seq.unfold` používá typ možnosti pro stav, který umožňuje ukončit sekvenci vrácením `None` hodnoty. Následující kód ukazuje dva příklady sekvencí `seq1` a `fib` , které jsou generovány `unfold` operací. První, `seq1` , je pouze jednoduchá sekvence s čísly až 20. Druhý `fib` používá `unfold` k výpočtu sekvence Fibonacci. Vzhledem k tomu, že každý prvek v sekvenci Fibonacci je součtem předchozích dvou čísel Fibonacci, hodnota stavu je řazená kolekce členů, která se skládá z předchozích dvou čísel v sekvenci. Počáteční hodnota je `(1,1)` první dvě čísla v sekvenci.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

Výstup je následující:

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Následující kód je příklad, který používá mnoho funkcí modulu Sequence popsaných tady pro generování a výpočet hodnot nekonečné sekvence. Spuštění kódu může trvat několik minut.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Hledání a hledání elementů

Sekvence podporují funkce, které jsou k dispozici v seznamech: [Seq. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq. exists2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#find), [Seq. findIndex –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#findIndex), [Seq. vyskl](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pick), [Seq. tryFind –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFind)a [Seq. tryFindIndex –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex). Verze těchto funkcí, které jsou k dispozici pro sekvence, vyhodnocují sekvenci pouze do hledaného prvku. Příklady najdete v tématu [seznam](lists.md).

## <a name="obtaining-subsequences"></a>Získání dílčích sekvencí

Příkazy [Seq. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#filter) a [Seq. Choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#choose) se podobají odpovídajícím funkcím, které jsou k dispozici pro seznamy, s výjimkou toho, že filtrování a výběr se neprojeví, dokud se prvky sekvence nevyhodnotí.

[Seq. oříznutí](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#truncate) vytvoří sekvenci z jiné sekvence, ale omezí sekvenci na zadaný počet prvků. [Seq. pořídit](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#take) vytvoří novou sekvenci, která bude obsahovat pouze zadaný počet prvků od začátku sekvence. Pokud je v sekvenci méně prvků, než je určeno pro provedení, `Seq.take` vyvolá výjimku `System.InvalidOperationException` . Rozdíl mezi `Seq.take` a `Seq.truncate` je, že `Seq.truncate` nevytvoří chybu, pokud je počet prvků menší než zadané číslo.

Následující kód ukazuje chování a rozdíly mezi `Seq.truncate` a `Seq.take` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

Výstup, před výskytem chyby, je následující.

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

Pomocí [Seq. TakeWhile –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#takeWhile)lze zadat funkci predikátu (logická funkce) a vytvořit sekvenci z jiné sekvence, která je tvořena těmito prvky původní sekvence, pro kterou je predikát `true` , ale zastavit před prvním prvkem, pro který se predikát vrátí `false` . [Seq. Skip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skip) vrátí sekvenci, která přeskočí zadaný počet prvních prvků v jiné sekvenci a vrátí zbývající prvky. [Seq. SkipWhile –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skipWhile) vrací sekvenci, která přeskočí první prvky jiné sekvence, pokud se vrátí predikát `true` a vrátí zbývající prvky počínaje prvním prvkem, pro který se predikát vrátí `false` .

Následující příklad kódu ilustruje chování a rozdíly mezi, a `Seq.takeWhile` `Seq.skip` `Seq.skipWhile` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

Výstup je následující.

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Transformace sekvencí

[Seq.](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pairwise) Pairwise vytvoří nové pořadí, ve kterém jsou po sobě následující prvky vstupní sekvence seskupeny do řazených kolekcí členů.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq. Window](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#windowed) se podobá `Seq.pairwise` , s tím rozdílem, že namísto vytváření posloupnosti řazených kolekcí členů vytvoří sekvenci polí, které obsahují kopie sousedících prvků ( *okno*) z sekvence. Zadejte počet sousedících prvků, které mají být v každém poli.

Následující příklad kódu ukazuje použití `Seq.windowed` . V tomto případě počet prvků v okně je 3. Příklad používá `printSeq` , který je definován v předchozím příkladu kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

Výstup je následující.

Počáteční sekvence:

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Operace s více sekvencemi

[Seq.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip) a [Seq.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip3) přebírají dvě nebo tři sekvence a vytvoří sekvenci řazených kolekcí členů. Tyto funkce jsou podobné odpovídajícím funkcím, které jsou k dispozici pro [seznamy](lists.md). Neexistuje žádná odpovídající funkce pro oddělení jedné sekvence do dvou nebo více sekvencí. Pokud tuto funkci pro sekvenci potřebujete, převeďte ji na seznam a použijte [seznam. dekomprimovat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip).

## <a name="sorting-comparing-and-grouping"></a>Řazení, porovnávání a seskupování

Funkce řazení podporované pro seznamy také fungují s sekvencemi. To zahrnuje [Seq. Sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sort) a [Seq. sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sortBy). Tyto funkce iterují celou sekvenci.

Porovnáte dvě sekvence pomocí funkce [Seq. compareWith –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#compareWith) . Funkce porovná úspěšné prvky a zastaví, když nalezne první neshodnou dvojici. Žádné další prvky nepřispívají k porovnání.

Následující kód ukazuje použití `Seq.compareWith` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

V předchozím kódu je vypočítán a zkontrolován pouze první prvek a výsledkem je-1.

[Seq. CountBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#countBy) přebírá funkci, která generuje hodnotu nazvanou *klíč* pro každý prvek. Klíč je vygenerován pro každý prvek voláním této funkce na každý prvek. `Seq.countBy` pak vrátí sekvenci, která obsahuje hodnoty klíče, a počet prvků, které vygenerovaly jednotlivé hodnoty klíče.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

Výstup je následující.

```console
(1, 34) (2, 33) (0, 33)
```

Předchozí výstup ukazuje, že byly 34 prvky původní sekvence, které vytvořily hodnoty klíče 1, 33 hodnoty, které vytvořily klíč 2, a 33 hodnoty, které vytvořily klíč 0.

Prvky sekvence lze seskupit voláním [Seq. GroupBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#groupBy). `Seq.groupBy` provede sekvenci a funkci, která generuje klíč z prvku. Funkce je spuštěna u každého prvku sekvence. `Seq.groupBy` vrací sekvenci řazených kolekcí členů, kde první prvek každé řazené kolekce členů je klíč a druhá je sekvence prvků, které tvoří tento klíč.

Následující příklad kódu ukazuje použití `Seq.groupBy` pro rozdělení posloupnosti čísel od 1 do 100 do tří skupin, které mají jedinečné klíčové hodnoty 0, 1 a 2.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

Výstup je následující.

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Můžete vytvořit sekvenci, která eliminuje duplicitní prvky voláním [Seq. DISTINCT](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinct). Případně můžete použít [Seq. distinctBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinctBy), který převezme funkci generování klíčů, která má být volána u každého prvku. Výsledná sekvence obsahuje prvky původní sekvence, které mají jedinečné klíče; později prvky, které vytvoří duplicitní klíč k dřívějšímu prvku, jsou zahozeny.

Následující příklad kódu ukazuje použití `Seq.distinct` . `Seq.distinct` je znázorněno vygenerováním sekvencí, které představují binární čísla, a následným zobrazením, že jediné samostatné prvky jsou 0 a 1.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

Následující kód ukazuje `Seq.distinctBy` , že začíná sekvencí, která obsahuje záporné a kladné číslo a pomocí funkce absolutní hodnoty jako funkce pro generování klíčů. V výsledné sekvenci chybí všechna kladná čísla, která odpovídají záporným číslům v sekvenci, protože záporná čísla se zobrazí dříve v sekvenci, a proto jsou vybrána namísto kladných čísel, která mají stejnou absolutní hodnotu nebo klíč.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Jen pro čtení a posloupnosti v mezipaměti

[Seq. ReadOnly](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#readonly) vytvoří kopii sekvence jen pro čtení. `Seq.readonly` je užitečné v případě, že máte kolekci pro čtení i zápis, jako je například pole, a nechcete změnit původní kolekci. Tato funkce se dá použít k zachování zapouzdření dat. V následujícím příkladu kódu je vytvořen typ, který obsahuje pole. Vlastnost zpřístupňuje pole, ale místo vrácení pole vrátí sekvenci, která je vytvořena z pole pomocí `Seq.readonly` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq. cache](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cache) vytvoří uloženou verzi sekvence. Použijte `Seq.cache` k zamezení opětovného vyhodnocení sekvence, nebo pokud máte více vláken, která používají sekvenci, musíte se ujistit, že každý prvek bude pracovat pouze v jednom okamžiku. Máte-li sekvenci, která je používána více vlákny, můžete mít jedno vlákno, které vytvoří výčet a vypočítá hodnoty pro původní sekvenci a zbývající vlákna mohou použít sekvenci uloženou v mezipaměti.

## <a name="performing-computations-on-sequences"></a>Provádění výpočtů na sekvencích

Jednoduché aritmetické operace jsou podobné jako u seznamů, například [Seq. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#average), [Seq. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sum), [Seq. averageBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#averageBy), [Seq. sumBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sumBy)a tak dále.

[Seq. reskládání](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#fold), [Seq. zmenšení](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#reduce)a [Seq. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#scan) jsou podobné odpovídající funkce, které jsou k dispozici pro seznamy. Sekvence podporují podmnožinu úplných variací těchto funkcí, které seznam podporují. Další informace a příklady najdete v tématu [seznam](lists.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Typy F#](fsharp-types.md)
