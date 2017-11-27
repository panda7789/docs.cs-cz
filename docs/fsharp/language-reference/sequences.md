---
title: Sekvence (F#)
description: "Další informace o použití F # pořadí, když máte velký, seřazené shromažďování dat, ale není nutně očekávat používat všechny elementy."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 23dc7d75-cd26-4df2-9be3-9d1aba5c4443
ms.openlocfilehash: b0562a6efbd2398cd8730bb835a1833955fee1c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="sequences"></a>Sekvence

> [!NOTE]
Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

A *pořadí* je logické řadu elementy všechny jednoho typu. Pořadí jsou zvláště užitečné, když máte velký, seřazené shromažďování dat, ale není chtít použít všechny elementy. Jednotlivé pořadí, které elementy se vypočítávají pouze jako povinné, sekvenci můžou poskytovat lepší výkon než seznam v situacích, ve kterých není všechny prvky používají. Pořadí jsou reprezentované pomocí `seq<'T>` typu, který je alias pro `System.Collections.Generic.IEnumerable`. Proto žádný typ rozhraní .NET Framework, který implementuje `System.IEnumerable` lze použít jako sekvenci. [Seq – modul](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) poskytuje podporu pro manipulaci s zahrnující pořadí.

## <a name="sequence-expressions"></a>Sekvenční výrazy
A *pořadí výraz* je výraz, který se vyhodnocuje sekvenci. Sekvenční výrazy může trvat několik formulářů. Nejjednodušší forma určuje rozsah. Například `seq { 1 .. 5 }` vytvoří sekvenci, která obsahuje pět prvky, včetně koncových bodů, 1 až 5. Můžete také určit přírůstek (nebo snížení) mezi dvě tečky double. Například následující kód vytvoří pořadí násobky čísla 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

Sekvenční výrazy se vytvářejí F # výrazů, které vytvářejí hodnoty pořadí. Mohou používat `yield` – klíčové slovo k vytvoření hodnoty, které se stanou součástí sekvenci.

Tady je příklad.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

Můžete použít `->` operátor místo `yield`, v takovém případě můžete vynechat `do` – klíčové slovo, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

Následující kód vytvoří seznam dvojice souřadnic společně s index do pole, které představuje mřížky.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if` Výraz použitý v sekvenci, kdy je filtr. Například pro vygenerování pořadí pouze prvočísel za předpokladu, že máte funkci `isprime` typu `int -> bool`, vytvořit sekvenci následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

Při použití `yield` nebo `->` v iterace, očekává se každé iteraci ke generování jeden element pořadí. Pokud každé iteraci vytváří pořadí elementů, použijte `yield!`. V takovém případě jsou zřetězeny elementy generuje při každém opakování k vytvoření konečné pořadí.

Můžete kombinovat více výrazů ve výrazu pořadí společně. Elementy generované každý výraz jsou zřetězeny společně. Příklad najdete v části "Příklady" v tomto tématu.

## <a name="examples"></a>Příklady
V prvním příkladu používá pořadí výraz, který obsahuje iterace, filtr a yield ke generování pole. Tento kód Vytiskne posloupnost prvočísel od 1 do 100 ke konzole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

Následující kód používá `yield` vytvořit násobení tabulku, která se skládá z řazených kolekcí členů elementů tři, každý se skládá z dva faktory a produktu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

Následující příklad ukazuje použití `yield!` se zkombinovat do jednoho konečné pořadí jednotlivých pořadí. V takovém případě jsou zřetězeny pořadí pro každý podstrom v binárního stromu v rekurzivní funkce, která se vytvoří konečnou pořadí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a>Pomocí pořadí
Pořadí podporují řadu stejné funkce jako [uvádí](lists.md). Pořadí také podporují operací, jako je seskupování a poté pomocí funkce generování klíče. Pořadí také podporují více různých funkcí pro extrahování dílčích sekvencí.

Mnoho typů dat, jako je například seznamy, pole, nastaví a mapy jsou implicitně pořadí, protože je vyčíslitelná kolekce. Funkci, která přebírá sekvenci jako argument pracuje s žádným z běžných F # datových typů, dále na libovolný datový typ rozhraní .NET Framework, který implementuje `System.Collections.Generic.IEnumerable<'T>`. To protějšek funkce, která přebírá seznam jako argument, který se zobrazí. Typ `seq<'T>` je zkratka typu pro `IEnumerable<'T>`. To znamená, že žádný typ, který implementuje obecné `System.Collections.Generic.IEnumerable<'T>`, což zahrnuje pole, seznamy, nastaví a map v F # a také většina rozhraní .NET Framework typy kolekcí, je kompatibilní s `seq` zadejte a dá se použít bez ohledu na sekvenci se očekává.


## <a name="module-functions"></a>Funkce modulu
[Seq – modul](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) v [Microsoft.FSharp.Collections – obor názvů](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) obsahuje funkce pro práci s pořadí. Tyto funkce pracovat s seznamy, pole, mapy a nastaví taky, protože všechny tyto typy jsou vyčíslitelná a proto mohou být považovány za pořadí.


## <a name="creating-sequences"></a>Vytváření pořadí
Můžete vytvořit pořadí pomocí sekvenční výrazy, jak je popsáno výše, nebo pomocí některých funkcí.

Můžete vytvořit prázdnou sekvencí pomocí [SEQ.Empty –](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), nebo můžete vytvořit sekvenci jenom jeden zadaný element pomocí [SEQ.singleton –](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

Můžete použít [SEQ.init –](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) vytvoření pořadí, pro kterou se vytváří elementy pomocí funkce, které zadáte. Je také zadat velikost pořadí. Tato funkce je podobně jako [list.init –](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)kromě toho, že prvky se nevytvoří, dokud iterace sekvenci. Následující kód ilustruje použití funkce `Seq.init`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

Výstup

```
0 10 20 30 40
```

Pomocí [SEQ.ofarray –](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) a [SEQ.oflist – & č. 60;. T & č. 62; Funkce](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), můžete vytvořit pořadí z poli a seznamy. Ale můžete také převést poli a seznamy pořadí pomocí operátor přetypování. Obě tyto metody jsou uvedené v následující kód.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

Pomocí [SEQ.CAST –](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), vytvoříte pořadí z slabě typovaná kolekce, jako je například názvům definovaným v `System.Collections`. Takové slabě typovaná kolekce mají typ elementu `System.Object` a jsou uvedené pomocí neobecnou `System.Collections.Generic.IEnumerable&#96;1` typu. Následující kód ukazuje použití `Seq.cast` převést `System.Collections.ArrayList` do sekvenci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

Můžete definovat nekonečné pořadí pomocí [SEQ.initinfinite –](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) funkce. Pořadí poskytují funkce, která generuje každý prvek z indexu elementu. Nekonečné pořadí je možné z důvodu opožděné vyhodnocení; elementy jsou vytvářeny podle potřeby voláním funkce, která zadáte. Následující příklad kódu vytvoří nekonečné posloupností plovoucí desetinnou čárkou, v tomto případě střídání řadu recipročních kvadratických následných celých čísel.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[SEQ.unfold –](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generuje sekvenci z výpočetní funkce, která přebírá stavu a převede jej k vytvoření každý následující prvek v pořadí. Stav je právě hodnotu, která se používá k výpočtu každý prvek a můžete změnit, protože každý prvek je počítaný. Druhý argument `Seq.unfold` je počáteční hodnota, která se používá ke spuštění pořadí. `Seq.unfold`používá typ možnosti pro stav, který umožňuje ukončit sekvenci vrácením `None` hodnotu. Následující kód ukazuje dva příklady pořadí, `seq1` a `fib`, které jsou generovány nástrojem `unfold` operaci. První, `seq1`, je stejně jednoduché pořadí s číslic obsahující až 100. Druhá s názvem `fib`, používá `unfold` k výpočtu Fibonacciho pořadí. Protože každý prvek v pořadí Fibonacciho je součet hodnot předchozích dvou čísel Fibonacciho, je hodnota stavu řazené kolekce členů, která se skládá z předchozích dvou čísel v pořadí. Počáteční hodnota je `(1,1)`, první dvě čísla v pořadí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

Výstup vypadá takto:

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

Následující kód je příklad, který používá mnoho funkcí modulu pořadí zde popsané generovat a výpočet hodnot nekonečné pořadí. Kód může trvat několik minut.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a>Vyhledávání a vyhledávání elementů
Pořadí podporu funkcí, které jsou k dispozici seznamy: [SEQ.EXISTS –](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [SEQ.exists2 –](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [SEQ.find –](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [SEQ.findindex –](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [ SEQ.Pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [SEQ.tryfind –](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), a [SEQ.tryfindindex –](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a). Verze tyto funkce, které jsou k dispozici pro pořadí vyhodnocení pořadí pouze do elementu, který má být vyhledán pro. Příklady najdete v tématu [uvádí](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).


## <a name="obtaining-subsequences"></a>Získání dílčích sekvencí
[SEQ.Filter –](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) a [SEQ.Choose –](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) jsou jako odpovídající funkce, které jsou k dispozici pro seznamy, s tím rozdílem, že filtrování a výběr nedojde, dokud se vyhodnocují elementy pořadí.

[SEQ.truncate –](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) vytvoří posloupnost z jiného pořadí, ale omezuje pořadí pro zadaný počet elementů. [SEQ.Take –](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) vytvoří nové pořadí, který obsahuje pouze zadaný počet elementů od začátku pořadí. Pokud jsou méně prvky v pořadí, než zadáte využít, `Seq.take` vyvolá `System.InvalidOperationException`. Rozdíl mezi `Seq.take` a `Seq.truncate` je, že `Seq.truncate` nevytváří chybu, pokud je počet elementů méně než číslo zadané.

Následující kód ukazuje chování a rozdíly mezi `Seq.truncate` a `Seq.take`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

Výstup, než dojde k chybě, je následující.

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

Pomocí [SEQ.TakeWhile –](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), můžete zadat funkce predikátu (logická funkce) a vytvořit pořadí z jiného pořadí skládá z těchto elementů původní pořadí, pro kterou je predikát `true`, ale zastavení před první prvek, pro který predikát vrátí `false`. [SEQ.Skip –](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) vrátí sekvenci, která přeskočí zadaný počet prvních prvků jiné pořadí a vrátí zbývající elementy. [SEQ.SkipWhile –](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) Vrátí pořadí, který přeskočí první elementy jiné sekvence tak dlouho, dokud predikát vrátí `true`a vrátí zbývající elementy, počínaje první prvek, pro který predikát vrátí `false`.

Následující příklad kódu ukazuje chování a rozdíly mezi `Seq.takeWhile`, `Seq.skip`, a `Seq.skipWhile`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

Výstup je následující.

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>Pořadí transformace
[SEQ.Pairwise –](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) vytvoří nové pořadí, ve kterém následných elementy vstupu sekvence seskupeny do řazené kolekce členů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[SEQ.windowed –](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) jako `Seq.pairwise`kromě toho, že místo vytváření pořadí řazené kolekce členů, vyvolá pořadí polí obsahujících kopie přiléhající elementů ( *okno*) z pořadí. Zadejte počet sousedících prvky, které chcete v každém poli.

Následující příklad kódu ukazuje použití `Seq.windowed`. V takovém případě je počet elementů v okně 3. Tento příklad používá `printSeq`, která je definována v předcházejícím příkladu.

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

## <a name="operations-with-multiple-sequences"></a>Operace s více pořadí
[SEQ.zip –](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) a [SEQ.zip3 –](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) vezme dva nebo tři pořadí a vytvoří pořadí řazené kolekce členů. Tyto funkce jsou jako odpovídající funkce dostupné pro [uvádí](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d). Není k dispozici žádná odpovídající funkce k oddělení jedním sekvenčním do dvou nebo více pořadí. Pokud tuto funkci potřebujete pro pořadí, převeďte sekvenci na seznamu a použít [list.Unzip –](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).


## <a name="sorting-comparing-and-grouping"></a>Řazení, porovnání a seskupení
Podporované pro seznamy řazení funkce pracovat také s pořadí. To zahrnuje [SEQ.Sort –](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) a [SEQ.sortby –](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f). Tyto funkce iteraci v rámci celého pořadí.

Porovnání dvou pořadí pomocí [SEQ.comparewith –](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) funkce. Funkce pak porovná následných elementy a zastaví, když zjistí první nerovné pár. Žádné další prvky nepřispívají k porovnání.

Následující kód ukazuje použití `Seq.compareWith`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

V předchozí kód pouze první prvek je počítaný a zkontrolován a výsledkem je, -1.

[SEQ.countby –](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) trvá funkci, která generuje hodnotu s názvem *klíč* pro jednotlivé elementy. Klíč se generuje pro každý prvek voláním této funkce pro každý element. `Seq.countBy`Vrátí pořadí, který obsahuje hodnoty klíče a počet prvků, které vygenerovány každou hodnotu klíče.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

Výstup je následující.

```
(1, 34) (2, 33) (0, 33)
```

Předchozí výstup ukazuje, že byly 34 elementy původní pořadí, které vytvořil klíč 1, 33 hodnoty, které vytvořil klíč 2 a 33 hodnoty, které vytvořil klíč 0.

Elementy pořadí můžete seskupovat podle volání [SEQ.GroupBy –](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd). `Seq.groupBy`provede sekvenci a funkci, která vygeneruje klíč z elementu. Funkce je provést pro každý element pořadí. `Seq.groupBy`Vrátí pořadí řazené kolekce členů, kde první prvek každá řazená kolekce členů je klíč a druhý je pořadí prvků, které vytvářejí klíči.

Následující příklad kódu ukazuje použití `Seq.groupBy` při vytváření oddílů pořadí čísel od 1 do 100 do tří skupin, které mají odlišné hodnoty klíče, 0, 1, 2.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

Výstup je následující.

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

Můžete vytvořit sekvenci, která eliminuje elementy s duplicitním voláním [SEQ.DISTINCT –](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401). Nebo můžete použít [SEQ.distinctby –](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), což trvá generování klíče funkce k volání na jednotlivé prvky. Výsledné pořadí obsahuje prvky původní pořadí, které mají jedinečné klíče; novější prvky, které vytváří duplicitní klíč pro starší element budou odstraněny.

Následující příklad kódu ukazuje použití `Seq.distinct`. `Seq.distinct`ukazují generování pořadí, které představují binární čísla, a pak zobrazující, že jsou pouze různých elementů 0 a 1.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

Následující kód ukazuje `Seq.distinctBy` počínaje sekvenci, která obsahuje kladné a záporné čísel a použitím funkce absolutní hodnotu jako funkce generování klíče. Výsledné pořadí chybí kladná čísla, které odpovídají záporná čísla v pořadí, protože záporná čísla se zobrazují v dřívější části pořadí a proto jsou vybrané místo kladná čísla, které mají stejné absolutní hodnota, nebo klíč.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a>Jen pro čtení a uložené v mezipaměti pořadí
[SEQ.ReadOnly –](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) vytvoří kopii sekvenci jen pro čtení. `Seq.readonly`je užitečné, když máte kolekci pro čtení a zápis, jako je například pole, a nechcete upravit původní kolekci. Tato funkce umožňuje zachovat data zapouzdření. V následujícím příkladu kódu se vytvoří typ, který obsahuje pole. Zpřístupní vlastnosti pole, ale místo vrací pole, vrátí sekvenci, která je vytvořená z pole pomocí `Seq.readonly`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[SEQ.Cache –](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) vytvoří uložené verze pořadí. Použít `Seq.cache` předejdete přehodnocení pořadí nebo pokud máte více vláken, které používají sekvenci, ale ujistěte se, že je každý prvek reagovali na ni pouze jednou. Když máte sekvenci, která se používá více vláken, může mít jedno vlákno, které vytvoří výčet a vypočítá hodnoty pro původní pořadí a zbývající vláken můžete použít v mezipaměti pořadí.


## <a name="performing-computations-on-sequences"></a>Provádění výpočtů v pořadí
Jednoduché aritmetické operace jsou například ty, seznamů, jako například [SEQ.average –](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [SEQ.SUM –](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [SEQ.averageby –](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [SEQ.sumby –](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)a tak dále.

[SEQ.fold –](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [SEQ.reduce –](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), a [SEQ.Scan –](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) jsou jako odpovídající funkce, které jsou k dispozici pro seznamy. Pořadí podporovat podmnožině úplné variace tyto funkce, která uvádí podpory. Další informace a příklady naleznete v tématu [uvádí](lists.md).

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F #](index.md)

[Typy F #](fsharp-types.md)
