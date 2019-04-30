---
title: Sekvence
description: Další informace o použití F# seřazené posloupnosti, když máte velké, shromažďování dat ale Neočekáváme, že nemusí používat všechny elementy.
ms.date: 02/19/2019
ms.openlocfilehash: a7791be5e8bd07d81fe9e890fc5896b181f0cb39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770471"
---
# <a name="sequences"></a>Sekvence

> [!NOTE]
> Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

A *pořadí* je logické řady elementů jednoho typu. Sekvence jsou zvlášť užitečné, když máte velké, seřazené kolekce dat, ale neočekávají nutně používat všechny prvky. Jednotlivé pořadí, které prvky se zpracovávají pouze jako požadované, takže sekvenci může poskytovat lepší výkon než seznamu v situacích, v nichž jsou všechny prvky použít. Sekvence jsou reprezentovány `seq<'T>` typu, což je alias pro `System.Collections.Generic.IEnumerable`. Proto libovolný typ rozhraní .NET Framework, který implementuje `System.IEnumerable` může sloužit jako sekvenci. [Seq – modul](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) poskytuje podporu pro manipulaci s zahrnující pořadí.

## <a name="sequence-expressions"></a>Sekvence výrazů

A *pořadí výrazu* je výraz, který se vyhodnotí na sekvenci. Sekvence výrazů může trvat různých formách. Nejjednodušší podobě určuje rozsah. Například `seq { 1 .. 5 }` vytvoří posloupnost, která obsahuje pět prvků, včetně koncových bodů 1 a 5. Můžete také určit přírůstek (nebo snížení) mezi dvě double období. Například následující kód vytvoří posloupnost násobky 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Sekvence výrazů jsou tvořené F# výrazy, které vytvářejí hodnoty pořadí. Můžete použít `yield` – klíčové slovo k vytvoření hodnot, které se stanou součástí sekvence.

Tady je příklad.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Můžete použít `->` namísto `yield`, v takovém případě můžete vynechat `do` – klíčové slovo, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Následující kód vygeneruje seznam dvojic souřadnic spolu s index do pole, která představuje mřížky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if` Výraz používá v pořadí je filtr. Například sekvence pouze prvočísel, za předpokladu, že máte funkci `isprime` typu `int -> bool`, následujícím způsobem vytvoření sekvence.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Při použití `yield` nebo `->` v iteraci, každé iterace má generovat jeden element pořadí. V případě každé iteraci vytvoří řadu prvků, použijte `yield!`. V takovém případě jsou zřetězeny elementy generované při každé iteraci pro vytvoření závěrečné sekvenci.

Můžete zkombinovat více výrazů společně ve výrazu pořadí. Elementy generované každý výraz jsou společně zřetězených. Příklad najdete v části "Příklady" tohoto tématu.

## <a name="examples"></a>Příklady

První příklad používá výraz sekvence, která obsahuje iterace, filtr a yield generovat pole. Tento kód zobrazí posloupnost prvočísel mezi 1 a 100 do konzoly.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Následující kód používá `yield` vytvořit tabulku násobení, která se skládá z ticemi tří prvků, každá se skládá z dvou faktorů a produktu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Následující příklad ukazuje použití `yield!` kombinování jednotlivých sekvence na jedné závěrečné sekvenci. V tomto případě jsou zřetězeny pořadí pro každý podstrom v binárního stromu v rekurzivní funkce pro produkci závěrečné sekvenci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>Pomocí pořadí

Pořadí podporují řadu stejných funkcí jako [uvádí](lists.md). Pořadí také podporují operace, jako je seskupení a počítání pomocí funkcí generování klíče. Pořadí pro extrahování dílčích sekvencí, které podporují také více různých funkcí.

Mnoho datových typů, jako je například seznam, pole, nastaví a mapy jsou implicitně pořadí, protože je vyčíslitelné kolekce. Funkce, která přebírá pořadí, argument pracuje s žádným z běžné F# datových typů, kromě libovolný typ dat rozhraní .NET Framework, která implementuje `System.Collections.Generic.IEnumerable<'T>`. Porovnejte to funkci, která převezme seznam jako argument, který jde převzít jenom seznamy. Typ `seq<'T>` je – zkratka typu pro `IEnumerable<'T>`. To znamená, že libovolný typ, který implementuje obecné `System.Collections.Generic.IEnumerable<'T>`, která obsahuje pole, seznamy, nastaví a mapy v F#a také většina typy rozhraní .NET Framework kolekce, je kompatibilní s `seq` typ a je možné kdykoli se očekává sekvence .

## <a name="module-functions"></a>Modul funkce

[Seq – modul](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) v [Microsoft.fsharp.Collections – obor názvů](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) obsahuje funkce pro práci s pořadí. Tyto funkce pracují s seznamy, pole, mapy a sady, protože všechny tyto typy jsou vyčíslitelné a proto lze považovat za pořadí.

## <a name="creating-sequences"></a>Vytváření pořadí

Můžete vytvořit pořadí pomocí výrazů pořadí, jak je popsáno výše, nebo pomocí některých funkcí.

Můžete vytvořit prázdnou sekvencí pomocí [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), nebo vytvoříte pořadí pouze jednoho zadaného prvku s použitím [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Můžete použít [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) vytvoření sekvence, pro kterou se prvky vytvářejí pomocí funkce, která zadáte. Pořadí je rovněž poskytnout velikost. Tato funkce je stejně jako [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), s tím rozdílem, že prvky se nevytvoří, dokud iterovat sekvence. Následující kód ilustruje použití funkce `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

Výstup je

```
0 10 20 30 40
```

S použitím [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) a [Seq.ofList&#60;'T&#62; funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), můžete vytvořit pořadí v poli a seznamy. Ale můžete také převést poli a seznamy pořadí pomocí operátoru přetypování. Obě tyto metody jsou uvedeny v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

S použitím [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), vytvoříte pořadí z slabě typované kolekce, jako je například jsou definované v `System.Collections`. Takové slabě typované kolekce mít typ prvku `System.Object` a jsou uvedené s použitím neobecné `System.Collections.Generic.IEnumerable&#96;1` typu. Následující kód ukazuje použití `Seq.cast` převést `System.Collections.ArrayList` na sekvenci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Nekonečná sekvence můžete definovat pomocí [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) funkce. Pro sekvenci poskytují funkce, která generuje každý prvek od indexu elementu. Nekonečná sekvence jsou možné kvůli opožděné vyhodnocení; prvky jsou vytvořeny podle potřeby pomocí volání funkce, která zadáte. Následující příklad kódu vytvoří nekonečná sekvence s plovoucí desetinnou čárkou čísla bod v tomto případě střídavé řadu recipročních druhých mocnin celých po sobě jdoucích čísel.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[SEQ.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generuje posloupnost z výpočetní funkce, který přebírá stavu a převede ho k vytvoření každé následné element v pořadí. Stav je právě hodnotu, která se používá k výpočtu každý prvek a můžete změnit, protože každý element je vypočítán. Druhý argument `Seq.unfold` je počáteční hodnota, která se používá ke spuštění sekvence. `Seq.unfold` používá typ možnosti pro stav, který umožňuje ukončit pořadí tak, že vrací `None` hodnotu. Následující kód ukazuje dva příklady sekvencí, `seq1` a `fib`, které jsou generovány nástrojem `unfold` operace. První s názvem `seq1`, je stejně jednoduché pořadí s čísly až 20. Druhá s názvem `fib`, používá `unfold` vypočítat Fibonacciho pořadí. Protože každý prvek v pořadí Fibonacciho součtu předchozích dvou čísel Fibonacciho, je hodnota stavu řazené kolekce členů, která se skládá z předchozích dvou čísel v pořadí. Počáteční hodnota je `(1,1)`, první dvě čísla v pořadí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

Výstup je následující:

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Následující kód představuje příklad, který používá mnoho funkcí modulu pořadí je zde popsáno pro generování a výpočet hodnot nekonečná sekvence. Kód může trvat několik minut.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>Hledání a hledání elementů

Pořadí podporu funkcí, které jsou k dispozici se seznamy: [SEQ.EXISTS](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind ](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), a [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Verze těchto funkcí, které jsou k dispozici pro pořadí vyhodnocení pořadí pouze do elementu, který má být vyhledán pro. Příklady najdete v tématu [uvádí](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).

## <a name="obtaining-subsequences"></a>Získání dílčích sekvencí, které

[SEQ.Filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) a [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) jsou jako odpovídající funkce, které jsou k dispozici pro seznamy, s tím rozdílem, že filtrování a zvolíte nedojde, dokud se vyhodnocují v pořadí prvků.

[SEQ.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) vytvoří sekvenci z jiné pořadí, ale omezuje pořadí zadaný počet prvků. [SEQ.Take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) vytvoří nové pořadí, který obsahuje pouze zadaný počet prvků od začátku sekvenci. Pokud jsou menší počet prvků v sekvenci, než určovat přijmout, `Seq.take` vyvolá `System.InvalidOperationException`. Rozdíl mezi `Seq.take` a `Seq.truncate` je, že `Seq.truncate` nevytváří chybu, pokud počet prvků, které je méně než číslo zadané.

Následující kód ukazuje chování a rozdíly mezi `Seq.truncate` a `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

Výstup, než dojde k chybě, je následujícím způsobem.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

S použitím [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), můžete určit predikát – funkce (logická funkce) a vytvořte sekvenci z jiné pořadí skládá z těchto prvků původní pořadí, pro kterou predikát je `true`, ale stop před první prvek, pro kterou predikát vrátí `false`. [SEQ.Skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) vrátí sekvenci, který přeskočí zadaný počet prvních prvků jiné pořadí a vrací zbývající prvky. [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) vrátí sekvenci, který přeskočí prvních prvků jiné pořadí jako predikát vrátí `true`a vrátí zbývající prvky počínaje prvním prvkem, pro kterou predikát vrátí `false`.

Následující příklad kódu ukazuje chování a rozdíly mezi `Seq.takeWhile`, `Seq.skip`, a `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

Výstup je následující.

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Pořadí transformace

[SEQ.Pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) vytvoří nové pořadí, ve kterém jsou seskupené po sobě jdoucí prvky vstupní sekvence do řazených kolekcí členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[SEQ.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) je stejná jako `Seq.pairwise`, s tím rozdílem, že místo vytváření posloupnost řazených kolekcí členů, vyvolá pořadí polí, které obsahují kopie sousedícími elementy ( *okno*) z pořadí. Zadejte počet sousedící prvky, které chcete v každé pole.

Následující příklad kódu ukazuje použití `Seq.windowed`. Počet prvků v okně, které v tomto případě je 3. V příkladu `printSeq`, který je definován v předcházejícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

Výstup je následující.

Počáteční sekvence:

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>Operace s několika sekvencemi

[SEQ.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) a [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) trvat dvě nebo tři sekvence a vytvářet posloupnost řazené kolekce členů. Tyto funkce jsou jako odpovídající funkce, které jsou k dispozici pro [uvádí](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Neexistuje žádné odpovídající funkce k oddělení do dvou nebo několika sekvencemi jednoho pořadí. Pokud potřebujete tuto funkci pro sekvenci, převod sekvence na seznamu a pomocí [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

## <a name="sorting-comparing-and-grouping"></a>Řazení, porovnávání a seskupování

Řazení funkce podporované pro seznamy pracovat i s pořadí. Jedná se o [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) a [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Tyto funkce iteraci v rámci celého pořadí.

Porovnání dvou sekvencí pomocí [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) funkce. Funkce pak porovná po sobě jdoucí prvky a zastaví, pokud se setká s první pár nerovnost. Žádné další prvky nepřispívají k porovnání.

Následující kód ukazuje použití `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

V předchozím kódu je jenom první prvek vypočítané a prozkoumat a výsledkem je hodnota -1.

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) používá funkce, která generuje hodnotu s názvem *klíč* pro každý prvek. Vygeneruje klíč pro každý prvek volající tuto funkci na každý prvek. `Seq.countBy` Vrátí sekvenci, která obsahuje hodnoty klíče a počet prvků, které generují každou hodnotu klíče.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

Výstup je následující.

```
(1, 34) (2, 33) (0, 33)
```

Předchozí výstup ukazuje, že byly 34 prvky původní sekvenci, který vytvořil klíč 1, 33 hodnoty, které klíč 2 a 33 hodnoty, které klíč 0.

Můžete seskupit elementy pořadí voláním [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy` přijímá sekvenci a funkci, která vygeneruje klíč z elementu. Funkce je spuštěna na každý prvek pořadí. `Seq.groupBy` Vrátí sekvenci řazených kolekcí členů, kde první prvek jednotlivé řazené kolekce členů je klíč a druhý je posloupnost prvků, které vytvářejí tento klíč.

Následující příklad kódu ukazuje použití `Seq.groupBy` rozdělit do tří skupin, které mají odlišné hodnoty klíče, 0, 1 a 2 sekvenci čísel od 1 do 100.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

Výstup je následující.

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Můžete vytvořit sekvenci, která odstraní duplicitní prvky pomocí volání [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Nebo můžete použít [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), který by funkce generování klíče k volání na každý prvek. Výsledné pořadí obsahuje prvky původní sekvence, které mají jedinečné klíče; novější prvky, které vytvoří duplicitní klíč na předchozí prvek se zahodí.

Následující příklad kódu ukazuje použití `Seq.distinct`. `Seq.distinct` je znázorněn generováním sekvence, které reprezentaci binárních čísel, a potom znázorňující, že pouze různých elementů jsou 0 a 1.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

Následující kód ukazuje `Seq.distinctBy` počínaje sekvenci, která obsahuje kladná a záporná čísla a použitím funkce absolutní hodnotu jako funkci generování klíče. Výsledné pořadí chybí kladná čísla, které odpovídají záporná čísla v pořadí, protože záporná čísla zobrazí výše v pořadí a proto jsou vybrány místo kladná čísla, která mají stejné absolutní hodnota, nebo klíč.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>Jen pro čtení a uložená v mezipaměti pořadí

[SEQ.ReadOnly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) vytvoří kopii sekvence jen pro čtení. `Seq.readonly` je užitečné, když máte kolekci pro čtení i zápis, jako je například pole, a nechcete upravit původní kolekci. Tuto funkci můžete použít pro zachování dat zapouzdření. V následujícím příkladu kódu se vytvoří typ obsahující pole. Zpřístupní vlastnosti pole, ale místo vrácení pole, vrátí sekvenci, která je vytvořena z pole pomocí `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[SEQ.Cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) vytvoří uloženou verzi sekvenci. Použít `Seq.cache` aby se zabránilo přehodnocení pořadí nebo pokud máte více vláken, které používají sekvenci, ale musíte přesvědčit, že každý element je reagovali na ni jenom jednou. Když máte sekvenci, která se používá více vláken, může mít jedno vlákno, které vytvoří výčet a vypočítá hodnoty pro původní pořadí a zbývající vlákna můžete použít v mezipaměti pořadí.

## <a name="performing-computations-on-sequences"></a>Provádění výpočtů v pořadí

Jednoduché aritmetické operace jsou podobné těm seznamů, jako je například [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), a tak dále.

[SEQ.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), a [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) jsou jako odpovídající funkce, které jsou k dispozici pro seznamy. Pořadí podporují podmnožinu úplné variace tyto funkce se seznamem podpory. Další informace a příklady najdete v tématu [uvádí](lists.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Typy F#](fsharp-types.md)
