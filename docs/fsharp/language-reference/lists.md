---
title: Seznamy
description: Přečtěte F# si o seznamech, seřazené, neměnné řadě prvků stejného typu.
ms.date: 05/16/2016
ms.openlocfilehash: e8c4a464306cfedfd36a4685507684d3a1a97a2e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630725"
---
# <a name="lists"></a>Seznamy

> [!NOTE]
> Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN.  Reference k rozhraní docs.microsoft.com API není dokončená.

Seznam v F# je seřazená, neproměnlivá řada prvků stejného typu. K provádění základních operací na seznamech použijte funkce v [modulu seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

## <a name="creating-and-initializing-lists"></a>Vytváření a inicializace seznamů

Seznam můžete definovat explicitním seznamem prvků oddělených středníky a uzavřenými do hranatých závorek, jak je znázorněno na následujícím řádku kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Můžete také umístit zalomení řádků mezi prvky, v takovém případě jsou středníky volitelné. Druhá syntaxe může vést k čitelnějšímu kódu, když jsou inicializační výrazy prvku delší nebo pokud chcete zahrnout komentář pro každý prvek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

V normálním případě musí být všechny prvky seznamu stejného typu. Výjimkou je, že seznam, ve kterém jsou prvky určeny jako základní typ, může mít elementy, které jsou odvozeny typy. Proto je možné, že následující podmínky jsou `Button` přijatelné `CheckBox` , protože `Control`a jsou odvozeny z.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Můžete také definovat prvky seznamu pomocí rozsahu, který je určen pomocí celých čísel oddělených operátorem Range`..`(), jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Prázdný seznam je určený dvojicí hranatých závorek bez jakéhokoli mezi nimi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Můžete také použít výraz pořadí k vytvoření seznamu. Další informace naleznete v tématu [výrazy sekvence](sequences.md#sequence-expressions) . Například následující kód vytvoří seznam čtverců celých čísel od 1 do 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operátory pro práci se seznamy

Prvky můžete k seznamu připojit pomocí `::` operátoru (nevýhody). V případě `list1` `list2` , následující kód vytvoří jako `[100; 2; 3; 4]`. `[2; 3; 4]`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Seznamy, které mají kompatibilní typy, lze zřetězit pomocí `@` operátoru, jak je uvedeno v následujícím kódu. Pokud `list1` je `[2; 3; 4]` a ,tento`list2` kód vytvoří`list3` jako .`[2; 3; 4; 100; 2; 3; 4]` `[100; 2; 3; 4]`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Funkce pro provádění operací v seznamech jsou k dispozici v [modulu seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).

Vzhledem k tomu F# , že seznamy v nástroji jsou neměnné, všechny úpravy operací generují nové seznamy místo úprav existujících seznamů.

Seznamy v F# aplikaci jsou implementovány jako jednotlivě propojené seznamy, což znamená, že operace, které mají přístup pouze k hlavnímu seznamu, mají hodnotu o (1) a přístup k prvkům je o (*n*).

## <a name="properties"></a>Vlastnosti

Typ seznamu podporuje následující vlastnosti:

|Vlastnost|Typ|Popis|
|--------|----|-----------|
|[Záhlaví](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|První prvek.|
|[prázdný](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|Statická vlastnost, která vrací prázdný seznam příslušného typu.|
|[IsEmpty](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|`true`Pokud seznam neobsahuje žádné prvky.|
|[Položka](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|Prvek na zadaném indexu (založený na nule).|
|[Časový](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|Počet elementů.|
|[Kompatibilní](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|Seznam bez prvního prvku|

Níže jsou uvedeny některé příklady použití těchto vlastností.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Používání seznamů

Programování se seznamy vám umožňuje provádět komplexní operace s malým množstvím kódu. Tato část popisuje běžné operace se seznamy, které jsou důležité pro funkční programování.

### <a name="recursion-with-lists"></a>Rekurze se seznamy

Seznamy jsou jedinečně uzpůsobeny rekurzivním programovacím technikům. Zvažte operaci, která musí být provedena u každého prvku seznamu. To lze provést rekurzivně na začátku seznamu a následným předáním konce seznamu, který je menší seznam, který se skládá z původního seznamu bez prvního prvku, zpět na další úroveň rekurze.

Chcete-li zapsat takovou rekurzivní funkci, použijte operátor nevýhody (`::`) v porovnávání vzorů, což umožňuje oddělit záhlaví seznamu od konce.

Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro implementaci rekurzivní funkce, která provádí operace na seznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Předchozí kód funguje dobře u malých seznamů, ale u větších seznamů může přetečení zásobníku. Následující kód vylepšuje tento kód pomocí argumentu Akumulovaná, standardní technika pro práci s rekurzivními funkcemi. Použití argumentu akumulátoru způsobí rekurzivní funkci na konci, která šetří místo v zásobníku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

Funkce `RemoveAllMultiples` je rekurzivní funkce, která přijímá dva seznamy. První seznam obsahuje čísla, jejichž násobky budou odebrány, a druhý seznam je seznam, ze kterého mají být čísla odebrána. Kód v následujícím příkladě používá tuto rekurzivní funkci k vyloučení všech nekoncových čísel ze seznamu, přičemž seznam koncových čísel se vynechává jako výsledek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Výstup je následující:

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Funkce modulu

[Modul seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) poskytuje funkce, které přistupují k prvkům seznamu. Hlavní prvek je nejrychlejší a nejjednodušší pro přístup. Použijte [záhlaví](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) vlastnosti nebo seznam funkcí modulu [. Head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2). K zakončení seznamu můžete přistupovat pomocí vlastnosti [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) nebo funkce [list. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) . Chcete-li najít element podle indexu, použijte funkci [list. n](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) . `List.nth`projde seznam. Proto má hodnotu O (*n*). Pokud váš kód používá `List.nth` často, možná budete chtít zvážit použití pole namísto seznamu. Přístup k prvkům v polích je O (1).

### <a name="boolean-operations-on-lists"></a>Logické operace na seznamech

Funkce [list... Empty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) určuje, zda má seznam nějaké prvky.

Funkce [list. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) používá logický test na prvky seznamu a vrací `true` , pokud některý prvek splňuje podmínky testu. [List. exists2 –](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) je podobný, ale pracuje na po sobě jdoucích dvojic prvků ve dvou seznamech.

Následující kód demonstruje použití `List.exists`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

Výstup je následující:

```
For list [0; 1; 2; 3], contains zero is true
```

Následující příklad ukazuje použití `List.exists2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

Výstup je následující:

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

[Seznam. ForAll](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) můžete použít, pokud chcete otestovat, zda všechny prvky seznamu splňují podmínku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

Výstup je následující:

```
true
false
```

Podobně [seznam. forall2 –](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) určuje, zda všechny prvky v odpovídajících pozicích ve dvou seznamech odpovídají logickému výrazu, který zahrnuje každou dvojici prvků.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

Výstup je následující:

```
true
false
```

### <a name="sort-operations-on-lists"></a>Seřadit operace v seznamech

Seznam. [Sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list. sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)a [list. sortWith –](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) Functions Sort lists. Funkce řazení určuje, které z těchto tří funkcí použít. `List.sort`používá výchozí obecné porovnání. Obecné porovnání používá pro porovnání hodnot globální operátory založené na funkci Generic Compare. Funguje efektivně s širokou škálou typů prvků, jako jsou jednoduché číselné typy, řazené kolekce členů, záznamy, rozlišené sjednocení, seznamy, pole a jakýkoli typ, který `System.IComparable`implementuje. Pro typy, které `System.IComparable`implementují obecné porovnání, `System.IComparable.CompareTo()` používá funkci. Obecné porovnání funguje také s řetězci, ale používá pořadí řazení nezávislé na jazykové verzi. Obecné porovnání by nemělo být použito pro nepodporované typy, jako například typy funkcí. Také výkon výchozího obecného porovnání je nejvhodnější pro malé strukturované typy; u větších strukturovaných typů, které je třeba porovnat a seřadit často, zvažte `System.IComparable` implementaci a poskytování efektivní implementace `System.IComparable.CompareTo()` metody.

`List.sortBy`převezme funkci, která vrací hodnotu, která se používá jako kritérium řazení, a `List.sortWith` jako argument použije funkci porovnání. Tyto dvě funkce jsou užitečné, když pracujete s typy, které nepodporují porovnání, nebo když porovnání vyžaduje složitější sémantiku porovnání, jako v případě řetězců zohledňujících jazykovou verzi.

Následující příklad ukazuje použití `List.sort`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

Výstup je následující:

```
[-2; 1; 4; 5; 8]
```

Následující příklad ukazuje použití `List.sortBy`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

Výstup je následující:

```
[1; -2; 4; 5; 8]
```

Další příklad ukazuje použití `List.sortWith`. V tomto příkladu se vlastní srovnávací funkce `compareWidgets` používá k prvnímu porovnání jednoho pole vlastního typu a poté další, pokud jsou hodnoty prvního pole stejné.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

Výstup je následující:

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Vyhledat operace v seznamech

Pro seznamy se podporuje celá řada operací hledání. Nejjednodušší, [list. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umožňuje najít první prvek, který odpovídá dané podmínce.

Následující příklad kódu ukazuje použití `List.find` nástroje k nalezení prvního čísla, které je v seznamu dělitele 5.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

Výsledek je 5.

Pokud elementy musí být transformovány jako první, zavolejte [list. vyskl](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), který převezme funkci, která vrací možnost a vyhledá první hodnotu možnosti, která je `Some(x)`. Místo vrácení elementu `List.pick` vrátí výsledek `x`. Pokud se nenajde žádný vyhovující prvek, `List.pick` vyvolá `System.Collections.Generic.KeyNotFoundException`. Následující kód ukazuje použití `List.pick`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

Výstup je následující:

```
"b"
```

Jiná skupina operací hledání, [list. tryFind –](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) a související funkce, vrací hodnotu možnosti. Funkce vrátí první prvek seznamu, který splňuje podmínku, pokud takový prvek existuje, ale hodnota `None` možnosti, pokud není. `List.tryFind` Seznam variací [. tryFindIndex –](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) vrátí index elementu, pokud je nalezen, spíše než samotný element. Tyto funkce jsou znázorněny v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

Výstup je následující:

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Aritmetické operace na seznamech

Do [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)jsou integrovány běžné aritmetické operace, jako je součet a průměr. Pro práci se [seznamem. Sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)musí typ elementu seznamu podporovat `+` operátor a mít nulovou hodnotu. Všechny integrované aritmetické typy tyto podmínky vyhoví. Pro práci se [seznamem. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)musí typ elementu podporovat dělení bez zbytku, který vylučuje celočíselné typy, ale umožňuje použití typů s plovoucí desetinnou čárkou. Funkce [list. sumBy –](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) a [list. averageBy –](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) přebírají funkci jako parametr a výsledky této funkce se používají k výpočtu hodnot součtu nebo průměru.

Následující kód demonstruje použití `List.sum`, `List.sumBy`, a `List.average`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

Výstup je `1.000000`.

Následující kód ukazuje použití `List.averageBy`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

Výstup je `5.5`.

### <a name="lists-and-tuples"></a>Seznamy a řazené kolekce členů

Seznamy, které obsahují řazené kolekce členů, mohou být manipulovány funkcemi zip a deextrahování. Tyto funkce kombinují dva seznamy jednotlivých hodnot do jednoho seznamu řazených kolekcí členů nebo oddělují jeden seznam řazených kolekcí členů do dvou seznamů s jednou hodnotou. Nejjednodušší funkce [list. zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) přebírá dva seznamy jednoho prvku a vytváří jeden seznam párů řazených kolekcí členů. Jiná verze, [list. zip3 –](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), používá tři seznamy jednoho prvku a vytváří jeden seznam řazených kolekcí členů, které mají tři prvky. Následující příklad kódu ukazuje použití `List.zip`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

Výstup je následující:

```
[(1, -1); (2, -2); (3; -3)]
```

Následující příklad kódu ukazuje použití `List.zip3`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

Výstup je následující:

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Příslušné deunzip3 –ované verze, [list.](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) rozbalení a [list.](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), převezmou seznamy řazených kolekcí členů a návratové seznamy v řazené kolekci členů, kde první seznam obsahuje všechny prvky, které byly první v každé řazené kolekci členů, a druhý seznam obsahuje druhý prvek každého z nich. řazená kolekce členů atd.

Následující příklad kódu ukazuje použití [seznamu. dekomprimovat](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

Výstup je následující:

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Následující příklad kódu ukazuje použití [seznamu. unzip3 –](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

Výstup je následující:

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Provoz na prvcích seznamu

F#podporuje různé operace na prvcích seznamu. Nejjednodušší je [list. ITER](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), který umožňuje zavolat funkci na každý prvek seznamu. Mezi variace patří [list. iter2 –](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), který umožňuje provést operaci na prvcích dvou seznamů, [list. ITERA](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), `List.iter` což se znamená, že index každého prvku je předán jako argument funkci, která je volána pro každý element a [list. iteri2 –](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), což je kombinace funkcí `List.iter2` a. `List.iteri` Následující příklad kódu znázorňuje tyto funkce.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

Výstup je následující:

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

Další často používanou funkcí, která transformuje prvky seznamu, je [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), který umožňuje použít funkci na každý prvek seznamu a umístit všechny výsledky do nového seznamu. [List. MAP2 –](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) a [list. map3 –](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) jsou variace, které přijímají více seznamů. Můžete také použít [seznam. MAPI](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) a [list. mapi2 –](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), pokud kromě prvku musí být funkce předána index každého prvku. Jediný rozdíl mezi `List.mapi2` a `List.mapi` je to, `List.mapi2` že funguje se dvěma seznamy. Následující příklad ukazuje [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

Výstup je následující:

```
[2; 3; 4]
```

Následující příklad ukazuje použití `List.map2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

Výstup je následující:

```
[5; 7; 9]
```

Následující příklad ukazuje použití `List.map3`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

Výstup je následující:

```
[7; 10; 13]
```

Následující příklad ukazuje použití `List.mapi`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

Výstup je následující:

```
[1; 3; 5]
```

Následující příklad ukazuje použití `List.mapi2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

Výstup je následující:

```
[0; 7; 18]
```

[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) se podobá `List.map`, s tím rozdílem, že každý prvek vytvoří seznam a všechny tyto seznamy jsou zřetězené do konečného seznamu. V následujícím kódu každý prvek seznamu generuje tři čísla. Všechny jsou shromažďovány v jednom seznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

Výstup je následující:

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Můžete také použít [seznam. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), který používá logickou podmínku a vytvoří nový seznam, který se skládá pouze z prvků, které odpovídají dané podmínce.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

Výsledný seznam je `[2; 4; 6]`.

Kombinace map a filtrů, [list. Volba](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) umožňuje transformovat a vybírat prvky současně. `List.choose`použije funkci, která vrátí možnost na každý prvek seznamu a vrátí nový seznam výsledků pro prvky, pokud funkce vrátí hodnotu `Some`možnosti.

Následující kód demonstruje použití `List.choose` pro výběr slov se velkými písmeny ze seznamu slov.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

Výstup je následující:

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Provoz na více seznamech

Seznamy lze spojit dohromady. Chcete-li spojit dva seznamy do jednoho, použijte příkaz [list. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426). Chcete-li spojit více než dva seznamy, použijte [list. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Operace skládání a skenování

Některé operace se seznamem zahrnují vzájemné závislosti mezi všemi prvky seznamu. Operace skládání a prověřování jsou podobné `List.iter` a `List.map` v tom, že vyvoláte funkci na každém elementu, ale tyto operace poskytují další parametr s názvem *akumulátor* , který přenáší informace prostřednictvím výpočtu.

Slouží `List.fold` k provedení výpočtu v seznamu.

Následující příklad kódu ukazuje použití [seznamu. skládání](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) k provádění různých operací.

Seznam je proprocházený. Akumulovaná `acc` je hodnota, která se předává společně s tím, jak výpočet pokračuje. První argument přebírá Akumulovaná a element list a vrací průběžný výsledek výpočtu pro tento prvek seznamu. Druhým argumentem je počáteční hodnota akumulátoru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

Verze těchto funkcí, které mají číslice v názvu funkce, fungují ve více než jednom seznamu. Například [list. fold2 –](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) provádí výpočty na dvou seznamech.

Následující příklad ukazuje použití `List.fold2`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold`a [list. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) se liší v `List.fold` , který vrací konečnou hodnotu nadbytečného parametru, `List.scan` ale vrátí seznam mezilehlých hodnot (spolu s konečnou hodnotou) nadbytečného parametru.

Každá z těchto funkcí obsahuje opačnou variaci, například [list. foldBack –](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), která se liší v pořadí, ve kterém je seznam procházen, a pořadí argumentů. A mít také variace, [list. fold2 –](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) a [list. foldBack2 –](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), které přebírají dva seznamy stejné délky. `List.foldBack` `List.fold` Funkce, která se spustí u každého prvku, může k provedení určité akce použít odpovídající prvky obou seznamů. Typy prvků dvou seznamů mohou být rozdílné, jako v následujícím příkladu, ve kterém jeden seznam obsahuje částky transakcí pro bankovní účet a druhý seznam obsahuje typ transakce: vklad nebo disstoupit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

Pro výpočet, jako je suma `List.fold` , `List.foldBack` a mít stejný účinek, protože výsledek není závislý na pořadí procházení. V následujícím příkladu `List.foldBack` se používá pro přidání prvků v seznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

Následující příklad vrátí na příklad bankovního účtu. Tentokrát se přidá nový typ transakce: výpočet úroku. Koncový zůstatek nyní závisí na pořadí transakcí.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

Seznam funkcí [. snížení](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) je poněkud podobné `List.fold` a `List.scan`, s výjimkou toho, že místo předání samostatného hromadění, `List.reduce` přebírá funkci, která přijímá dva argumenty typu elementu namísto pouze jednoho a jednoho z nich. argumenty slouží jako akumulátor, což znamená, že ukládá mezilehlé výsledky výpočtu. `List.reduce`začíná při práci na prvních dvou prvcích seznamu a poté používá výsledek operace spolu s dalším prvkem. Vzhledem k tomu, že není k dispozici samostatný akumulátor, který má `List.reduce` svůj vlastní typ, lze použít `List.fold` místo pouze v případě, že je typ akumulátoru a typ elementu stejného typu. Následující kód demonstruje použití `List.reduce`. `List.reduce`vyvolá výjimku, pokud zadaný seznam neobsahuje žádné elementy.

V následujícím kódu je první volání lambda výrazu uděleno argumenty 2 a 4 a vrátí hodnotu 6 a další volání je uděleno argumenty 6 a 10, takže výsledek je 16.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Převod mezi seznamy a jinými typy kolekcí

`List` Modul poskytuje funkce pro převod do a z obou sekvencí a polí. Pro převod na nebo z sekvence použijte [list. toSeq –](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) nebo [list. ofSeq –](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0). Pro převod na nebo z pole použijte [list. ToArray –](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) nebo [list. ofArray –](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).

### <a name="additional-operations"></a>Další operace

Další informace o dalších operacích v seznamech naleznete v tématu věnovaném modulům Reference Library [Collections. list](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Typy F#](fsharp-types.md)
- [Sekvence](sequences.md)
- [Pole](arrays.md)
- [Možnosti](options.md)
