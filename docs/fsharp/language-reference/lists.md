---
title: Seznamy (F#)
description: "Další informace o F # seznamy, seřazené, neměnné řadu elementy stejného typu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a1a6075f-064d-4aee-8222-2b59ff16cc12
ms.openlocfilehash: 5802a5a1c48ad05c1765c4c0fa2e8a81a92dee8d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lists"></a>Seznamy

> [!NOTE]
Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN.  Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.

Seznam v F # je seřazený, neměnné řadu elementy stejného typu. Provádění základních operací na seznamu, pomocí funkcí v [modul seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).


## <a name="creating-and-initializing-lists"></a>Vytváření a inicializace uvádí
Můžete definovat seznam vypsáním explicitně prvky, oddělené středníky a uzavřeny do hranatých závorek, jak je znázorněno na následujícím řádku kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Můžete také vložit zalomení mezi elementy, v takovém případě jsou volitelné středníky. Druhé syntaxe může způsobit srozumitelnější kódu po delší inicializace výrazy elementu, nebo když chcete zahrnout komentář pro jednotlivé elementy.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

Za normálních okolností všechny elementy seznamu musí být stejného typu. Výjimkou je, že seznam, ve kterém jsou elementy zadaný jako základní typ měli prvky, které jsou odvozené typy. Proto je následující přijatelný, protože obě `Button` a `CheckBox` odvozena od `Control`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Seznam prvků můžete definovat i pomocí rozsah indikovaný celých čísel oddělených operátor rozsahu (`..`), jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Prázdný seznam je zadaný pár hranaté závorky stálo mezi nimi.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Výraz pořadí také můžete vytvořit seznam. V tématu [sekvenční výrazy](sequences.md#sequence-expressions) Další informace. Například následující kód vytvoří seznam kvadratických celých čísel od 1 do 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operátory pro práci s seznamy
Prvky v seznamu můžete připojit pomocí `::` – operátor (cons). Pokud `list1` je `[2; 3; 4]`, následující kód vytvoří `list2` jako `[100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Můžete řetězení seznamy, které mají kompatibilní typy pomocí `@` operátor jako v následujícím kódu. Pokud `list1` je `[2; 3; 4]` a `list2` je `[100; 2; 3; 4 ]`, tento kód vytvoří `list3` jako `[2; 3; 4; 100; 2; 3; 4]`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Funkce pro provádění operací na seznamy jsou k dispozici v [modul seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Vzhledem k tomu, že seznamy v F # jsou neměnné, všechny změny operace generovat nové seznamy místo úprava existující seznamy.

Seznamy v F # jsou implementované jako jednotlivě propojené seznamy, které znamená, že operace, které přístup pouze první pozice v seznamu jsou o(1), která, a element přístup je O (*n*).


## <a name="properties"></a>Vlastnosti
Typ seznamu podporuje následující vlastnosti:

|Vlastnost|Typ|Popis|
|--------|----|-----------|
|[HEAD](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|První prvek.|
|[Prázdný](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Statické vlastnosti, která vrací prázdný seznam příslušného typu.|
|[IsEmpty –](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true`Pokud seznam obsahuje žádné elementy.|
|[Položka](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Element v zadaném indexu (počítáno od nuly).|
|[Délka](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Počet elementů.|
|[Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Seznam bez první prvek.|
Tady jsou některé příklady použití těchto vlastností.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a>Použití seznamů
Programování s seznamy umožňuje provádět komplexní operace s malou část kódu. Tato část popisuje běžné operace na seznamy, které jsou důležité pro funkční programování.


### <a name="recursion-with-lists"></a>Rekurze se seznamy
Seznamy jsou jedinečně vhodná pro rekurzivní programování techniky. Vezměte v úvahu operace, která je potřeba provést na každý element seznamu. Můžete provést tento rekurzivně tak, že provoz na záhlaví seznamu a následné předání konec seznamu, která je menší seznam, který se skládá z původní seznam bez první prvek, znovu zpět na další úroveň rekurze.

Zápis rekurzivní funkci, použijte operátor cons (`::`) v porovnávání vzorů, což umožňuje oddělit head seznamu zadní.

Následující příklad kódu ukazuje, jak použít porovnávání vzorů k implementaci rekurzivní funkce, která provádí operace v seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Předchozí kód funguje dobře pro malé seznamy, ale pro větší seznamy ho může přetečení zásobníku. Následující kód zlepšuje na tento kód pomocí argumentu akumulátorová standardní technika pro práci s rekurzivní funkce. Použití argumentu akumulátorová díky tail rekurzivní funkce, které šetří místo zásobníku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

Funkce `RemoveAllMultiples` je rekurzivní funkce, která přebírá dva seznamy. První seznam obsahuje čísla, jejichž násobků, které se odeberou, a druhý seznam je seznam, ze kterého mají být odebrány čísla. Kód v následujícím příkladu používá k vyloučení všech jiných prime čísel ze seznamu, a seznam prvočísel v důsledku této rekurzivní funkce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Výstup vypadá takto:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Funkce modulu
[Modul seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) poskytuje funkce, které přístup k elementům seznamu. Head element je nejrychlejší a nejjednodušší přístup. Použijte vlastnost [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) nebo funkce modulu [list.HEAD –](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). Máte přístup k konec seznamu pomocí [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) vlastnost nebo [list.Tail –](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) funkce. Chcete-li při vyhledávání prvku pomocí indexu, použijte [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) funkce. `List.nth`prochází seznamu. Proto je O (*n*). Pokud váš kód používá `List.nth` často, můžete chtít zvážit použití pole místo seznam. O(1), která je element přístup v polích.


### <a name="boolean-operations-on-lists"></a>Na seznamu logických operací
[List.IsEmpty –](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) funkce určuje, zda seznam obsahuje všechny elementy.

[List.EXISTS –](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) funkce se vztahuje na booleovskou hodnotu test, který prvky seznam a vrátí `true` Pokud libovolný element, splňuje test. [List.exists2 –](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) se podobá ale funguje v následných páry elementů v dva seznamy.

Následující kód ukazuje použití `List.exists`.

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

Můžete použít [list.ForAll –](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) Pokud chcete otestovat, zda všechny elementy seznamu splňují podmínku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

Výstup vypadá takto:

```
true
false
```

Podobně [list.forall2 –](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) Určuje, zda splňují všechny elementy ve odpovídající pozice v dva seznamy logický výraz, který zahrnuje každý pár elementů.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

Výstup vypadá takto:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Operace řazení v seznamech
[List.Sort –](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list.sortby –](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), a [list.sortwith –](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funkce seřadit seznamy. Funkce třídění určuje, které z těchto tří funkcí používat. `List.sort`používá výchozí obecné porovnání. Obecné porovnání pro porovnání hodnot používá globální operátory podle funkce obecné porovnání. Efektivní funguje se širokou škálu element typy, jako je jednoduchý číselnými typy, řazené kolekce členů, záznamy, rozlišovaná sjednocení, seznamy, pole a žádný typ, který implementuje `System.IComparable`. Pro typy, které implementují `System.IComparable`, používá obecné porovnání `System.IComparable.CompareTo()` funkce. Obecné porovnání také funguje s řetězci, ale s pořadí řazení nezávislé na jazykové verzi. Obecné porovnání není vhodné používat na nepodporované typy, jako jsou typy funkce. Navíc výkon obecné výchozím porovnáním je nejvhodnější pro malé strukturovaných typy; pro větší strukturovaných typy, které třeba porovnání a seřazeny často, zvažte implementaci `System.IComparable` a zajištění efektivní provádění `System.IComparable.CompareTo()` metoda.

`List.sortBy`provede funkci, která vrátí hodnotu, která se používá jako kritérium řazení a `List.sortWith` přijímá jako argument funkce porovnání. Tyto pozdější dvě funkce jsou užitečné, když pracujete s typy, které nepodporují porovnání nebo při porovnání vyžaduje složitější sémantiku porovnání, jako v případě podporující jazykové verze řetězce.

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

Další příklad ukazuje použití `List.sortWith`. V tomto příkladu vlastní porovnání funkce `compareWidgets` se používá k porovnání nejprve do jednoho pole z vlastního typu a pak další, kdy jsou stejné hodnoty první pole.

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
Pro seznamy jsou podporovány mnoha operace hledání. Nejjednodušším, [list.find –](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umožňuje najít první prvek, který odpovídá dané podmínce.

Následující příklad kódu ukazuje použití `List.find` najít číslo, kterým dělitelná 5 v seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

Výsledkem je 5.

Elementy musí nejdřív transformuje, kontaktujte [list.Pick –](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), což trvá funkci, vrátí možnost a hledá první možnost hodnotu, která je `Some(x)`. Místo vrácení elementu `List.pick` vrátí výsledek `x`. Pokud se nenajde žádný odpovídající element, `List.pick` vyvolá `System.Collections.Generic.KeyNotFoundException`. Následující kód ukazuje použití `List.pick`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

Výstup vypadá takto:

```
"b"
```

Jiná skupina operace hledání [list.tryfind –](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) a souvisejících funkcí, vrátí hodnotu možnosti. `List.tryFind` Funkce vrátí první prvek seznamu, který splňuje podmínku, pokud takový prvek existuje, ale hodnota možnosti `None` není-li. Variaci [list.tryfindindex –](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) vrátí index elementu, pokud ho najde, místo elementu samotného. Tyto funkce jsou znázorněné v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

Výstup vypadá takto:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Aritmetické operace na seznamy
Běžné aritmetické operace, jako je sum a průměr jsou součástí [modul seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Pro práci s [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), musí podporovat typ elementu seznamu `+` operátor a mít nulovou hodnotu. Všechny vestavěné typy aritmetické splňovat tyto podmínky. Pro práci s [list.average –](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musí podporovat dělení beze zbytku, který vyloučí integrální typy, ale umožňuje plovoucí typy bodů. [List.sumby –](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) a [list.averageby –](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funkce využít funkce jako parametr a výsledky tato funkce slouží k výpočtu hodnoty pro SUMA nebo průměr.

Následující kód ukazuje použití `List.sum`, `List.sumBy`, a `List.average`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

Výstupem je `1.000000`.

Následující kód ukazuje použití `List.averageBy`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

Výstupem je `5.5`.


### <a name="lists-and-tuples"></a>Seznamy a řazených kolekcí členů
Seznamy, které obsahují řazených kolekcí členů smí uživatel manipulovat zip a rozbalte funkce. Tyto funkce sloučit dva seznamy jeden hodnot do jediného seznamu řazené kolekce členů nebo oddělení jeden seznam řazených kolekcí členů do dva seznamy jedné hodnoty. Nejjednodušším [list.zip –](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) funkce přebírá dva seznamy jednotlivé prvky a vytvoří jeden seznam dvojic řazené kolekce členů. Jiná verze [list.zip3 –](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), trvá tři seznam jednotlivé prvky a vytvoří jeden seznam záznamů, které mají tři prvky. Následující příklad kódu ukazuje použití `List.zip`.

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

Odpovídající verze, rozbalte [list.Unzip –](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) a [list.unzip3 –](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), provést seznam řazených kolekcí členů a vrátí seznamy v řazené kolekce členů, kde první seznam obsahuje všechny elementy, které byly první v každá řazená kolekce členů a druhý seznam obsahuje druhý prvkem každý řazené kolekce členů, a tak dále.

Následující příklad kódu ukazuje použití [list.Unzip –](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

Výstup vypadá takto:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Následující příklad kódu ukazuje použití [list.unzip3 –](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

Výstup vypadá takto:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Pracující na prvky seznamu
F # podporuje různé operace v seznamu elementů. Nejjednodušší je [list.ITER –](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), což umožňuje volání funkce na každý element seznamu. Zahrnout variace [list.iter2 –](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), které umožňuje provádět operace s elementy dva seznamy [list.iteri –](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), což je jako `List.iter` s tím rozdílem, že index jednotlivých prvků se předá jako argumentem této funkce, která je volána pro každý prvek a [list.iteri2 –](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), který je kombinací funkce `List.iter2` a `List.iteri`. Následující příklad kódu ukazuje tyto funkce.

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

Jiné často používané funkce, která transformuje seznamu elementů je [list.map –](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), který můžete použít funkci pro každý prvek seznamu a všechny výsledky do nového seznamu. [List.map2 –](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) a [list.map3 –](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) jsou variace, které trvat více seznamů. Můžete také použít [list.MAPI –](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) a [list.mapi2 –](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), pokud kromě elementu, musí být předán index jednotlivých prvků funkce. Jediným rozdílem mezi `List.mapi2` a `List.mapi` je, že `List.mapi2` pracuje se dvěma seznamy. Následující příklad ilustruje [list.map –](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

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

[List.Collect –](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) jako `List.map`kromě toho, že každý prvek vytváří seznamu a všechny tyto seznamy jsou zřetězeny do konečné seznamu. V následujícím kódu generuje každý element seznamu tří čísel. Všechny se shromažďují do jediného seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

Výstup vypadá takto:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Můžete také použít [list.Filter –](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), který přebírá podmínce logické a vytvoří nový seznam, který se skládá jenom z elementů, které splňují danou podmínku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

V rozevíracím seznamu je `[2; 4; 6]`.

V kombinaci mapy a filtr [list.Choose –](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) vám umožňuje transformovat a vybrat elementy ve stejnou dobu. `List.choose`funkci, která vrátí možnost každý prvek seznamu a vrátí nový seznam výsledky pro elementy při funkce vrátí hodnotu možnost se vztahuje `Some`.

Následující kód ukazuje použití `List.choose` vyberte převedených na velká písmena slova mimo seznam slov.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

Výstup vypadá takto:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Pracující na více seznamů
Seznamy je možné připojit společně. Chcete-li připojit dva seznamy do jednoho, použijte [list.Append –](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Chcete-li připojit k více než dva seznamy, použijte [list.Concat –](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a>Operace kontroly a skládání
Některé operace výpisu zahrnovat vzájemné závislosti mezi všechny elementy seznamu. Operace násobek a kontroly jsou jako `List.iter` a `List.map` v tom vyvolání funkce pro každý element, ale tyto operace poskytnout další parametr s názvem *akumulátorová* , přenáší informace Výpočet.

Použití `List.fold` provedení výpočtů v seznamu.

Následující příklad kódu ukazuje použití [list.fold –](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) provádět různé operace.

Je seznam vyčerpán; je zásobník `acc` je hodnota, která se předají jako výpočet pokračuje. První argument trvá je zásobník a element seznamu a vrátí dočasné výsledek výpočtu pro daný element seznamu. Druhý argument je počáteční hodnota je zásobník.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

Verze tyto funkce, které mají číslice v názvu funkce fungovat na více než jeden seznam. Například [list.fold2 –](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) provede výpočty dva seznamy.

Následující příklad ukazuje použití `List.fold2`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold`a [list.Scan –](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) se liší v tom, že `List.fold` vrátí poslední hodnotu speciálním parametrem, ale `List.scan` vrátí seznam pomocných hodnot (spolu s konečná hodnota) navíc parametru.

Každá z těchto funkcí zpětného variace, například zahrnuje [list.foldback –](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), který se liší v pořadí, ve které je seznam vyčerpán a pořadí argumentů. Navíc `List.fold` a `List.foldBack` mají varianty, [list.fold2 –](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) a [list.foldback2 –](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), které přebírají dva seznamy stejné délky. Funkce, která spustí pro každý element můžete použít odpovídající elementy oba seznamy k provedení několika akcí. Element typy dva seznamy může být jiné, jako v následujícím příkladu, ve kterém jeden seznam obsahuje objemy transakcí pro účet bank a další seznam obsahuje typ transakce: uložení nebo stažení.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

Výpočet jako sumarizační `List.fold` a `List.foldBack` mají stejný účinek, protože výsledek nezávisí v řádu traversal. V následujícím příkladu `List.foldBack` se používá k přidání elementů v seznamu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

Následující příklad vrátí příkladu bankovní účet. Tentokrát je přidání nového typu transakce: výpočtu vás zajímají. Konečný zůstatek teď závisí v řádu transakce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

Funkce [list.reduce –](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) je něco jako `List.fold` a `List.scan`kromě toho, že místo předávání kolem samostatné akumulátoru, `List.reduce` trvá funkci, která má dva argumenty typu prvku místo jenom jeden a jeden z těchto argumentů funguje jako je zásobník, což znamená, ukládá zprostředkující výsledek výpočet. `List.reduce`spustí na provoz na prvních dvou seznam prvků a potom pomocí výsledek operace spolu s další prvek. Protože samostatné akumulátorová, který má vlastní typ není `List.reduce` lze místě `List.fold` pouze když je zásobník a typ elementu mají stejného typu. Následující kód ukazuje použití `List.reduce`. `List.reduce`vyvolá výjimku, pokud zadaný seznam obsahuje žádné elementy.

V následujícím kódu první volání výrazu lambda získá argumenty, 2 a 4 a vrátí hodnotu 6, a další volání je zadané argumenty 6 a 10, tak, aby výsledkem 16.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a>Převod mezi seznamy a další typy kolekcí
`List` Modul poskytuje funkce pro převod do a z pořadí a pole. Chcete-li převést do nebo z sekvenci, použijte [list.toseq –](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) nebo [list.ofseq –](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Chcete-li převést do nebo z pole, použijte [list.ToArray –](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) nebo [list.ofarray –](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).


### <a name="additional-operations"></a>Další operace
Informace o dalších operacích v seznamech najdete v tématu v referenčním tématu knihovny [Collections.list – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F #](index.md)

[Typy F #](fsharp-types.md)

[Pořadí](sequences.md)

[Pole](arrays.md)

[Možnosti](options.md)
