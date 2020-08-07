---
title: Sekvence
description: 'Naučte se používat sekvence F #, pokud máte rozsáhlou uspořádanou kolekci dat, ale nechcete nutně očekávat použití všech prvků.'
ms.date: 11/04/2019
ms.openlocfilehash: fa5073f33b9dae52371c249bfb257a2446b4d26a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855319"
---
# <a name="sequences"></a>Sekvence

*Sekvence* je logická řada prvků všech jednoho typu. Sekvence jsou zvláště užitečné v případě, že máte rozsáhlou uspořádanou kolekci dat, ale nemusí nutně očekávat použití všech prvků. Jednotlivé prvky sekvence jsou vypočítány pouze jako povinné, takže sekvence může poskytovat lepší výkon než seznam v situacích, kdy nejsou použity všechny prvky. Sekvence jsou reprezentovány `seq<'T>` typem, který je aliasem pro <xref:System.Collections.Generic.IEnumerable%601> . Proto může být jakýkoli typ rozhraní .NET, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní, použit jako sekvence. [Modul SEQ](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) poskytuje podporu pro manipulace zahrnující sekvence.

> [!NOTE]
> Reference k rozhraní docs.microsoft.com API pro F # není dokončená. Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .

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

Výsledkem určení pouze `x` v předchozím příkladu bude sekvence, která negeneruje žádné hodnoty.

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

[Modul SEQ](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) v [oboru názvů Microsoft. FSharp. Collections](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) obsahuje funkce pro práci s sekvencemi. Tyto funkce fungují společně se seznamy, poli, mapami a sadami, protože všechny tyto typy jsou vyčíslitelné, a proto je lze považovat za sekvence.

## <a name="creating-sequences"></a>Vytváření sekvencí

Můžete vytvářet sekvence pomocí výrazů pořadí, jak je popsáno výše, nebo pomocí určitých funkcí.

Prázdnou sekvenci lze vytvořit pomocí [Seq. Empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)nebo můžete vytvořit sekvenci pouze jednoho zadaného elementu pomocí [Seq. singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

Pomocí [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) lze vytvořit sekvenci, pro kterou jsou vytvořeny prvky pomocí funkce, kterou zadáte. Můžete také zadat velikost sekvence. Tato funkce je stejná jako [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), s tím rozdílem, že elementy nejsou vytvořeny, dokud neprovedete iteraci v sekvenci. Následující kód ilustruje použití funkce `Seq.init`.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

Výstup je

```console
0 10 20 30 40
```

Pomocí funkcí [Seq. ofArray –](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) a [seq. oflist –&#60; ne&#62;te](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), můžete vytvořit sekvence z polí a seznamů. Pole a seznamy však můžete také převést na sekvence pomocí operátoru přetypování. Obě metody jsou uvedeny v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

Pomocí [Seq. cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)můžete vytvořit sekvenci ze slabě typované kolekce, jako jsou například definované v `System.Collections` . Tyto slabě typové kolekce mají typ prvku `System.Object` a jsou vyčísleny pomocí neobecného `System.Collections.Generic.IEnumerable&#96;1` typu. Následující kód ilustruje použití `Seq.cast` pro převod na `System.Collections.ArrayList` sekvenci.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

Můžete definovat nekonečné sekvence pomocí funkce [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) . Pro takové sekvence zadáte funkci, která generuje každý prvek z indexu elementu. Nekonečné sekvence jsou možné z důvodu opožděného vyhodnocení; prvky jsou vytvořeny podle potřeby voláním funkce, kterou zadáte. Následující příklad kódu vytvoří nekonečnou sekvenci čísel s plovoucí desetinnou čárkou, v tomto případě alternující řady reciprocals čtverců po sobě jdoucích celých čísel.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq. unskládání](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generuje sekvenci z funkce výpočtu, která přebírá stav a transformuje ho za účelem vytvoření každého následného prvku v sekvenci. Stav je pouze hodnota, která se používá k výpočtu každého prvku a může se změnit při výpočtu každého prvku. Druhý argument na `Seq.unfold` je počáteční hodnota, která se používá ke spuštění sekvence. `Seq.unfold`používá typ možnosti pro stav, který umožňuje ukončit sekvenci vrácením `None` hodnoty. Následující kód ukazuje dva příklady sekvencí `seq1` a `fib` , které jsou generovány `unfold` operací. První, `seq1` , je pouze jednoduchá sekvence s čísly až 20. Druhý `fib` používá `unfold` k výpočtu sekvence Fibonacci. Vzhledem k tomu, že každý prvek v sekvenci Fibonacci je součtem předchozích dvou čísel Fibonacci, hodnota stavu je řazená kolekce členů, která se skládá z předchozích dvou čísel v sekvenci. Počáteční hodnota je `(1,1)` první dvě čísla v sekvenci.

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

Sekvence podporují funkce, které jsou k dispozici v seznamech: [Seq. Exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq. exists2 –](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq. Find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq. findIndex –](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq. vyskl](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq. tryFind –](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)a [Seq. tryFindIndex –](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Verze těchto funkcí, které jsou k dispozici pro sekvence, vyhodnocují sekvenci pouze do hledaného prvku. Příklady najdete v tématu [seznam](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Získání dílčích sekvencí

Příkazy [Seq. Filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) a [Seq. Choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) se podobají odpovídajícím funkcím, které jsou k dispozici pro seznamy, s výjimkou toho, že filtrování a výběr se neprojeví, dokud se prvky sekvence nevyhodnotí.

[Seq. oříznutí](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) vytvoří sekvenci z jiné sekvence, ale omezí sekvenci na zadaný počet prvků. [Seq. pořídit](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) vytvoří novou sekvenci, která bude obsahovat pouze zadaný počet prvků od začátku sekvence. Pokud je v sekvenci méně prvků, než je určeno pro provedení, `Seq.take` vyvolá výjimku `System.InvalidOperationException` . Rozdíl mezi `Seq.take` a `Seq.truncate` je, že `Seq.truncate` nevytvoří chybu, pokud je počet prvků menší než zadané číslo.

Následující kód ukazuje chování a rozdíly mezi `Seq.truncate` a `Seq.take` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

Výstup, před výskytem chyby, je následující.

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

Pomocí [Seq. TakeWhile –](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)lze zadat funkci predikátu (logická funkce) a vytvořit sekvenci z jiné sekvence, která je tvořena těmito prvky původní sekvence, pro kterou je predikát `true` , ale zastavit před prvním prvkem, pro který se predikát vrátí `false` . [Seq. Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) vrátí sekvenci, která přeskočí zadaný počet prvních prvků v jiné sekvenci a vrátí zbývající prvky. [Seq. SkipWhile –](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) vrací sekvenci, která přeskočí první prvky jiné sekvence, pokud se vrátí predikát `true` a vrátí zbývající prvky počínaje prvním prvkem, pro který se predikát vrátí `false` .

Následující příklad kódu ilustruje chování a rozdíly mezi, a `Seq.takeWhile` `Seq.skip` `Seq.skipWhile` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

Výstup je následující.

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Transformace sekvencí

[Seq.](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) Pairwise vytvoří nové pořadí, ve kterém jsou po sobě následující prvky vstupní sekvence seskupeny do řazených kolekcí členů.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq. Window](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) se podobá `Seq.pairwise` , s tím rozdílem, že namísto vytváření posloupnosti řazených kolekcí členů vytvoří sekvenci polí, které obsahují kopie sousedících prvků ( *okno*) z sekvence. Zadejte počet sousedících prvků, které mají být v každém poli.

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

[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) a [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) přebírají dvě nebo tři sekvence a vytvoří sekvenci řazených kolekcí členů. Tyto funkce jsou podobné odpovídajícím funkcím, které jsou k dispozici pro [seznamy](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Neexistuje žádná odpovídající funkce pro oddělení jedné sekvence do dvou nebo více sekvencí. Pokud tuto funkci pro sekvenci potřebujete, převeďte ji na seznam a použijte [seznam. dekomprimovat](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

## <a name="sorting-comparing-and-grouping"></a>Řazení, porovnávání a seskupování

Funkce řazení podporované pro seznamy také fungují s sekvencemi. To zahrnuje [Seq. Sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) a [Seq. sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Tyto funkce iterují celou sekvenci.

Porovnáte dvě sekvence pomocí funkce [Seq. compareWith –](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) . Funkce porovná úspěšné prvky a zastaví, když nalezne první neshodnou dvojici. Žádné další prvky nepřispívají k porovnání.

Následující kód ukazuje použití `Seq.compareWith` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

V předchozím kódu je vypočítán a zkontrolován pouze první prvek a výsledkem je-1.

[Seq. CountBy –](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) přebírá funkci, která generuje hodnotu nazvanou *klíč* pro každý prvek. Klíč je vygenerován pro každý prvek voláním této funkce na každý prvek. `Seq.countBy`pak vrátí sekvenci, která obsahuje hodnoty klíče, a počet prvků, které vygenerovaly jednotlivé hodnoty klíče.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

Výstup je následující.

```console
(1, 34) (2, 33) (0, 33)
```

Předchozí výstup ukazuje, že byly 34 prvky původní sekvence, které vytvořily hodnoty klíče 1, 33 hodnoty, které vytvořily klíč 2, a 33 hodnoty, které vytvořily klíč 0.

Prvky sekvence lze seskupit voláním [Seq. GroupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy`provede sekvenci a funkci, která generuje klíč z prvku. Funkce je spuštěna u každého prvku sekvence. `Seq.groupBy`vrací sekvenci řazených kolekcí členů, kde první prvek každé řazené kolekce členů je klíč a druhá je sekvence prvků, které tvoří tento klíč.

Následující příklad kódu ukazuje použití `Seq.groupBy` pro rozdělení posloupnosti čísel od 1 do 100 do tří skupin, které mají jedinečné klíčové hodnoty 0, 1 a 2.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

Výstup je následující.

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Můžete vytvořit sekvenci, která eliminuje duplicitní prvky voláním [Seq. DISTINCT](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Případně můžete použít [Seq. distinctBy –](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), který převezme funkci generování klíčů, která má být volána u každého prvku. Výsledná sekvence obsahuje prvky původní sekvence, které mají jedinečné klíče; později prvky, které vytvoří duplicitní klíč k dřívějšímu prvku, jsou zahozeny.

Následující příklad kódu ukazuje použití `Seq.distinct` . `Seq.distinct`je znázorněno vygenerováním sekvencí, které představují binární čísla, a následným zobrazením, že jediné samostatné prvky jsou 0 a 1.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

Následující kód ukazuje `Seq.distinctBy` , že začíná sekvencí, která obsahuje záporné a kladné číslo a pomocí funkce absolutní hodnoty jako funkce pro generování klíčů. V výsledné sekvenci chybí všechna kladná čísla, která odpovídají záporným číslům v sekvenci, protože záporná čísla se zobrazí dříve v sekvenci, a proto jsou vybrána namísto kladných čísel, která mají stejnou absolutní hodnotu nebo klíč.

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Jen pro čtení a posloupnosti v mezipaměti

[Seq. ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) vytvoří kopii sekvence jen pro čtení. `Seq.readonly`je užitečné v případě, že máte kolekci pro čtení i zápis, jako je například pole, a nechcete změnit původní kolekci. Tato funkce se dá použít k zachování zapouzdření dat. V následujícím příkladu kódu je vytvořen typ, který obsahuje pole. Vlastnost zpřístupňuje pole, ale místo vrácení pole vrátí sekvenci, která je vytvořena z pole pomocí `Seq.readonly` .

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq. cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) vytvoří uloženou verzi sekvence. Použijte `Seq.cache` k zamezení opětovného vyhodnocení sekvence, nebo pokud máte více vláken, která používají sekvenci, musíte se ujistit, že každý prvek bude pracovat pouze v jednom okamžiku. Máte-li sekvenci, která je používána více vlákny, můžete mít jedno vlákno, které vytvoří výčet a vypočítá hodnoty pro původní sekvenci a zbývající vlákna mohou použít sekvenci uloženou v mezipaměti.

## <a name="performing-computations-on-sequences"></a>Provádění výpočtů na sekvencích

Jednoduché aritmetické operace jsou podobné jako u seznamů, například [Seq. Average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq. Sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq. averageBy –](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq. sumBy –](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)a tak dále.

[Seq. reskládání](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq. zmenšení](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)a [Seq. Scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) jsou podobné odpovídající funkce, které jsou k dispozici pro seznamy. Sekvence podporují podmnožinu úplných variací těchto funkcí, které seznam podporují. Další informace a příklady najdete v tématu [seznam](lists.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Typy F#](fsharp-types.md)
