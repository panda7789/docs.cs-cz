---
title: Seznamy (F#)
description: 'Další informace o seznamech F #, seřazený, neměnné řadu prvků stejného typu.'
ms.date: 05/16/2016
ms.openlocfilehash: 60e7edb56bdf498e3ba51aff028d8564eb68d0f1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798845"
---
# <a name="lists"></a>Seznamy

> [!NOTE]
Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

Seznam v jazyce F # je seřazený, neměnné řadu prvků stejného typu. K provádění základních operací v seznamech, použijte funkci v [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

## <a name="creating-and-initializing-lists"></a>Vytváření a inicializaci seznamy

Můžete definovat seznam podle explicitně uvedete seznam rozložení elementů, oddělené středníky a uzavřený v hranatých závorkách a jak je znázorněno v následující řádek kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Můžete také umístit zalomení mezi prvky, v takovém případě jsou volitelné středníky. Druhá syntaxe může způsobit čitelnější kód po delší dobu výrazy inicializace prvek nebo když chcete zahrnout komentář pro každý prvek.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Za normálních okolností všechny prvky seznamu musí být stejného typu. Výjimkou je, že seznam, ve kterém jsou prvky uvedeny na základní typ může mít prvky, které jsou odvozené typy. Proto je přijatelné, protože obě `Button` a `CheckBox` jsou odvozeny z `Control`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Můžete také definovat prvky seznamu pomocí rozsah indikovaný celých čísel oddělených operátor rozsahu (`..`), jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Pár uzavřenou do hranatých závorek není nic mezi nimi je zadaný prázdný seznam.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Můžete také použít výrazu pořadí k vytvoření seznamu. Zobrazit [výrazech pořadí](sequences.md#sequence-expressions) Další informace. Například následující kód vytvoří seznam druhých mocnin celých čísel od 1 do 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operátory pro práci se seznamy

Prvky do seznamu můžete připojit pomocí `::` – operátor (nevýhody). Pokud `list1` je `[2; 3; 4]`, následující kód vytvoří `list2` jako `[100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Můžete zřetězit seznamy, které mají nekompatibilní typy s použitím `@` operátoru, stejně jako v následujícím kódu. Pokud `list1` je `[2; 3; 4]` a `list2` je `[100; 2; 3; 4 ]`, tento kód vytvoří `list3` jako `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Funkce pro provádění operací na seznamy jsou k dispozici v [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Protože jsou neměnné seznamy v jazyce F #, všechny změny operace generovat nové seznamy místo úpravy existujících seznamů.

Seznamy v jazyce F # jsou implementovány jako jednotlivě propojený seznam, což znamená, že operace, které přistupují k začátku seznamu jsou O(1), a je O přístup k prvkům (*n*).

## <a name="properties"></a>Vlastnosti

Typ seznamu podporuje následující vlastnosti:

|Vlastnost|Typ|Popis|
|--------|----|-----------|
|[hlavní](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|První prvek.|
|[prázdný](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Statické vlastnosti, která vrací prázdný seznam příslušného typu.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true` Pokud seznam neobsahuje žádné prvky.|
|[Položka](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Element v zadaném indexu (počítáno od nuly).|
|[Délka](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Počet prvků.|
|[Funkce Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Seznam bez první prvek.|
Následuje několik příkladů použití těchto vlastností.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Použití seznamů

Programování se seznamy umožňuje provádět komplexní operace s menším objemem kódu. Tato část popisuje běžné operace na seznamy, které jsou důležité pro funkční programování.

### <a name="recursion-with-lists"></a>Rekurze se seznamy

Seznamy jsou jednoznačně hodí pro rekurzivní programovacích postupech. Vezměte v úvahu operace, která je třeba provést na každý prvek seznamu. Můžete udělat tento rekurzivně tak, že provoz na začátku seznamu a následným předáním konec seznamu, která je menší seznam, který se skládá z původního seznamu bez první prvek, zpátky na další úroveň rekurze.

Zápis rekurzivní funkci, použijte operátor nevýhody (`::`) v porovnávání vzorů, což vám umožní hlavní seznam nezávislá na konci.

Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro implementaci rekurzivní funkci, která provádí operace na seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Předchozí kód funguje dobře pro krátké seznamy, ale pro větší seznamy, ho může přetečení zásobníku. Následující kód se zvyšuje na tento kód pomocí argumentu akumulátor standardní způsob pro práci s rekurzivní funkce. Použijte argument akumulátor díky rekurzivní funkce tail, což šetří místo v zásobníku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

Funkce `RemoveAllMultiples` je rekurzivní funkci, která přijímá dva seznamy. První seznam obsahuje čísla, jejichž násobky se odeberou a druhým seznamem je seznamu, ze kterého mají být odebrány čísla. Kód v následujícím příkladu používá tato rekurzivní funkce pro odstranění všech jiných prvočísel ze seznamu, v důsledku byste museli opustit seznam prvočísel.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Výstup vypadá takto:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Modul funkce

[Modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) poskytuje funkce, které přístup k prvkům seznamu. Head element je nejrychlejší a nejjednodušší přístup. Použijte vlastnost [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) nebo funkci modul [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Konec seznamu přístupné prostřednictvím [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) vlastnost nebo [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) funkce. Nalezení prvku podle indexu, použijte [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) funkce. `List.nth` projde seznam. Proto se jedná O (*n*). Pokud váš kód používá `List.nth` často, můžete chtít zvážit použití pole namísto seznamu. Přístup k prvkům v poli je O(1).

### <a name="boolean-operations-on-lists"></a>Logická operace v seznamech

[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) funkce určuje, zda seznam obsahuje všechny prvky.

[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) funkce se vztahuje datový typ Boolean test na prvky seznam a vrátí `true` Pokud libovolný prvek splňuje testu. [List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) je podobné, ale funguje v po sobě jdoucích dvojice elementů v dva seznamy.

Následující kód demonstruje použití `List.exists`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

Výstup vypadá takto:

```
For list [0; 1; 2; 3], contains zero is true
```

Následující příklad ukazuje použití `List.exists2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

Výstup vypadá takto:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

Můžete použít [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) Pokud budete chtít otestovat, jestli všechny prvky seznamu splňují podmínku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

Výstup vypadá takto:

```
true
false
```

Obdobně [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) Určuje, jestli splňují všechny prvky na odpovídající pozici v dva seznamy logický výraz, který zahrnuje každý pár prvků.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

Výstup vypadá takto:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Operace řazení v seznamech

[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), a [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funkce řazení seznamy. Funkce třídění určuje, které tyto tři funkce používat. `List.sort` používá výchozí obecného porovnání. Pro porovnání hodnot používá obecného porovnání globálních operátorů podle funkce obecného porovnání. Funguje to pro efektivní nejrůznější typy prvků, jako je například jednoduché číselné typy, řazených kolekcí členů, záznamy, rozlišovaná sjednocení, seznamů, polí a libovolný typ, který implementuje `System.IComparable`. Pro typy, které implementují `System.IComparable`, používá obecného porovnání `System.IComparable.CompareTo()` funkce. Obecného porovnání také funguje s řetězci, ale používá pořadí řazení nezávislé na jazykové verzi. Obecného porovnání neměla používat pro nepodporované typy, jako jsou typy funkcí. Navíc je nejvhodnější pro malé strukturované typy; výkonu obecného porovnání výchozí pro větší strukturované typy, které je potřeba porovnání a řazení často, zvažte implementaci `System.IComparable` a poskytují efektivní implementace `System.IComparable.CompareTo()` metody.

`List.sortBy` používá funkce, která vrátí hodnotu, která se používá jako kritérium řazení a `List.sortWith` přijímá jako argument funkce porovnání. Tyto druhé dvě funkce jsou užitečné při práci s typy, které nepodporují porovnání nebo při porovnání vyžaduje složitější porovnání sémantiky, jako v případě řetězců zohledňující jazykovou verzi.

Následující příklad ukazuje použití `List.sort`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

Výstup vypadá takto:

```
[-2; 1; 4; 5; 8]
```

Následující příklad ukazuje použití `List.sortBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

Výstup vypadá takto:

```
[1; -2; 4; 5; 8]
```

Následující příklad ukazuje použití `List.sortWith`. V tomto příkladu vlastní funkci porovnání `compareWidgets` se používá k porovnání nejprve jedno pole z vlastního typu a pak opět v případě hodnoty první pole jsou stejné.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

Výstup vypadá takto:

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Operace hledání v seznamech

Seznamy podporují řadu operací vyhledávání. Nejjednodušší, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umožňuje najít první prvek, který odpovídá dané podmínky.

Následující příklad kódu ukazuje použití `List.find` najít první číslo, které je dělitelná 5 v seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

Výsledkem je 5.

Pokud nejprve musí transformované prvky, zavolejte [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), který by funkce, která vrátí možnost a vyhledá první možnost Hodnota, která je `Some(x)`. Místo vrácení elementu `List.pick` vrátí výsledek `x`. Pokud není nalezen žádný odpovídající element, `List.pick` vyvolá `System.Collections.Generic.KeyNotFoundException`. Následující kód ukazuje použití `List.pick`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

Výstup vypadá takto:

```
"b"
```

Jiná skupina operace hledání [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) a související funkce vrátí hodnotu možnosti. `List.tryFind` Funkce vrátí první prvek seznamu, který splňuje podmínku, pokud takový prvek neexistuje, ale hodnota možnosti `None` Pokud tomu tak není. Změna [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) vrátí index prvku, pokud ho najde, místo samotného elementu. Tyto funkce jsou znázorněné v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

Výstup vypadá takto:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Aritmetické operace v seznamech

Běžné aritmetické operace, jako je součet a průměr jsou integrované do [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Pro práci s [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), musí podporovat seznamu Typ prvku `+` operátor a mít nulovou hodnotu. Všechny vestavěné aritmetické typy splňovat tyto podmínky. Pro práci s [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musí podporovat dělení beze zbytku, která nezahrnuje celočíselných typů, ale umožňuje pro typy s plovoucí desetinnou čárkou. [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) a [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funkce přebírají funkci jako parametr a výsledky této funkce se používají k výpočtu hodnot pro součtu nebo průměru.

Následující kód demonstruje použití `List.sum`, `List.sumBy`, a `List.average`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

Výstup je `1.000000`.

Následující kód ukazuje použití `List.averageBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

Výstup je `5.5`.

### <a name="lists-and-tuples"></a>Seznamech a řazených kolekcí členů

Seznamy, které obsahují řazené kolekce členů může manipulovat zip a rozbalte funkce. Tyto funkce sloučit dva seznamy jednotlivé hodnoty do jediného seznamu řazených kolekcí členů nebo rozdělit do dvou seznamů hodnot jednoho jeden seznam řazených kolekcí členů. Nejjednodušší [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) funkce přebírá dva seznamy jednotlivé prvky a vytváří jeden seznam dvojic, přičemž řazené kolekce členů. Jiná verze [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), přebírá tři seznamy jeden prvků a vytváří jeden seznam řazených kolekcí členů, které mají tři prvky. Následující příklad kódu ukazuje použití `List.zip`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

Výstup vypadá takto:

```
[(1, -1); (2, -2); (3; -3)]
```

Následující příklad kódu ukazuje použití `List.zip3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

Výstup vypadá takto:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Odpovídající verze, rozbalte [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) a [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), používají seznamy řazených kolekcí členů a vrací seznamy v řazené kolekce členů, kde první seznam obsahuje všechny prvky, které se poprvé v každé řazené kolekce členů a druhý seznam obsahuje druhý prvek řazené kolekce členů, a tak dále.

Následující příklad kódu ukazuje použití [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

Výstup vypadá takto:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Následující příklad kódu ukazuje použití [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

Výstup vypadá takto:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Práce na seznamu elementů

Jazyk F # podporuje širokou škálu operace na seznamu elementů. Nejjednodušší je [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), což vám umožní volat funkci na každý prvek seznamu. Zahrnovat odchylky [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), což vám umožní provést operaci s prvky dvou seznamů [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), což je třeba `List.iter` s tím rozdílem, že indexu každého prvku je předán jako argument pro funkci, která je volána pro každý prvek a [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), což je kombinací funkce `List.iter2` a `List.iteri`. Následující příklad kódu ukazuje tyto funkce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

Výstup vypadá takto:

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

Další často používané funkci, která transformuje prvky seznamu je [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), což vám umožní použít funkci na každý prvek seznamu a všechny výsledky do nového seznamu. [List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) a [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) jsou změny, které provést více seznamů. Můžete také použít [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) a [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), je-li kromě elementu, funkce musí být předán indexu každého prvku. Jediným rozdílem mezi `List.mapi2` a `List.mapi` je, že `List.mapi2` pracuje se dvěma seznamy. Následující příklad ukazuje [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

Výstup vypadá takto:

```
[2; 3; 4]
```

Následující příklad ukazuje použití `List.map2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

Výstup vypadá takto:

```
[5; 7; 9]
```

Následující příklad ukazuje použití `List.map3`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

Výstup vypadá takto:

```
[7; 10; 13]
```

Následující příklad ukazuje použití `List.mapi`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

Výstup vypadá takto:

```
[1; 3; 5]
```

Následující příklad ukazuje použití `List.mapi2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

Výstup vypadá takto:

```
[0; 7; 18]
```

[List.Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) je stejná jako `List.map`, s tím rozdílem, že každý prvek vytváří seznam a tyto seznamy jsou zřetězeny do konečný seznam. V následujícím kódu generuje každý prvek v seznamu tří čísel. Všechny jsou shromážděné v jednom seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

Výstup vypadá takto:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Můžete také použít [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), který převezme logickou podmínku a vytvoří nový seznam, který se skládá pouze z prvků, které odpovídají dané podmínce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

V rozevíracím seznamu se `[2; 4; 6]`.

V kombinaci map a filtrování [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) umožňuje transformovat a vyberte prvky ve stejnou dobu. `List.choose` použije funkci, která vrací možnost na každý prvek seznamu a vrátí nový seznam výsledků pro elementy, pokud funkce vrátí hodnotu možnosti `Some`.

Následující kód demonstruje použití `List.choose` vyberte ze seznamu slov velká písmena slov.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

Výstup vypadá takto:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Provoz ve více seznamech

Seznamy lze spojit dohromady. Chcete-li připojit dva seznamy do jednoho, použijte [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Chcete-li připojit k více než dva seznamy, použijte [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Skládání a operace kontroly

Některé operace výpisu zahrnují vzájemné závislosti mezi všechny prvky seznamu. Skládání a kontroly operace jsou jako `List.iter` a `List.map` , vyvolá funkci na každý prvek, ale tyto operace poskytují další parametr s názvem *akumulátor* , která přenáší informace Výpočet.

Použití `List.fold` k provedení výpočtu v seznamu.

Následující příklad kódu ukazuje použití [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) můžete provádět různé operace.

V seznamu procházet řízený; je zásobník `acc` je hodnota, která se předají jak pokračuje výpočtu. První argument přebírá je zásobník a prvek seznamu a vrací dočasné výsledek výpočtu pro daný element seznamu. Druhý argument je počáteční hodnota proměnné je zásobník.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

Verze těchto funkcí, které mají číslici v názvu funkce pracují s více než jeden seznam. Například [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) provádí výpočty na dvou seznamů.

Následující příklad ukazuje použití `List.fold2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` a [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) se liší v, který `List.fold` vrátí poslední hodnotu speciálním parametrem, ale `List.scan` vrátí seznam pomocných hodnot (spolu s konečnou hodnotu) speciálním parametrem.

Každá z těchto funkcí zahrnuje reverzní variantu, například [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), navzájem se liší v pořadí, ve které je v seznamu Procházet a pořadí argumentů. Navíc `List.fold` a `List.foldBack` mají varianty, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) a [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), které přebírají dva seznamy stejné délky. Funkce, která se spustí na každý prvek můžete použít odpovídající prvky obou seznamů k provedení nějaké akce. Typy prvků ze dvou seznamů mohou lišit, jako v následujícím příkladu, ve kterém jeden seznam obsahuje objemy transakcí pro bankovním účtu, a seznamu obsahuje typ transakce: uložení nebo zrušení.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

Pro výpočet jako souhrn `List.fold` a `List.foldBack` mají stejný účinek, protože výsledek není závislý v řádu procházení. V následujícím příkladu `List.foldBack` se používá k přidání prvků v seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

Následující příklad vrátí v příkladu bankovním účtu. Tentokrát je přidán nový typ transakce: Výpočet úroku. Konečný zůstatek závisí nyní v řádu transakce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

Funkce [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) je něco jako `List.fold` a `List.scan`, s tím rozdílem, že namísto předání kolem samostatné akumulátor `List.reduce` používá funkce, která přebírá dva argumenty typu elementu namísto otázkou jediného a jeden z těchto argumentů funguje jako je zásobník, což znamená, že ukládá přechodný výsledek výpočtu. `List.reduce` začne pracující na prvních dvou seznam prvků a potom použije výsledek operace společně s další prvek. Protože samostatné akumulátor, který má svůj vlastní typ není `List.reduce` lze použít místo `List.fold` pouze v případě je zásobník a typ prvku máte stejného typu. Následující kód demonstruje použití `List.reduce`. `List.reduce` vyvolá výjimku, pokud v seznamu neobsahuje žádné prvky.

V následujícím kódu první volání výrazu lambda je předávat argumenty 2 a 4 a vrátí 6, a další volání dostane argumenty 6 a 10, takže výsledkem je 16.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Převod mezi seznamy a typy kolekcí

`List` Modulu poskytuje funkce pro převod do a z pořadí a pole. Chcete-li převést do nebo ze sekvence, použijte [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) nebo [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Chcete-li převést na nebo z pole, použijte [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) nebo [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).

### <a name="additional-operations"></a>Další operace

Informace o dalších operacích v seznamech, naleznete v tématu referenční dokumentace knihovny [Collections.list – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Typy F#](fsharp-types.md)
- [Sekvence](sequences.md)
- [Pole](arrays.md)
- [Možnosti](options.md)
