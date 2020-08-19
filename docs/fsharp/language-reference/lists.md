---
title: Seznamy
description: 'Přečtěte si o seznamech F #, seřazené a neměnných řadách prvků stejného typu.'
ms.date: 08/13/2020
ms.openlocfilehash: 16d7195039d25cf63630f5cc3be6563b1bf45c44
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559164"
---
# <a name="lists"></a>Seznamy

Seznam v jazyce F # je seřazená, neproměnlivá řada prvků stejného typu. K provádění základních operací na seznamech použijte funkce v [modulu seznam](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).

## <a name="creating-and-initializing-lists"></a>Vytváření a inicializace seznamů

Seznam můžete definovat explicitním seznamem prvků oddělených středníky a uzavřenými do hranatých závorek, jak je znázorněno na následujícím řádku kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

Můžete také umístit zalomení řádků mezi prvky, v takovém případě jsou středníky volitelné. Druhá syntaxe může vést k čitelnějšímu kódu, když jsou inicializační výrazy prvku delší nebo pokud chcete zahrnout komentář pro každý prvek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

V normálním případě musí být všechny prvky seznamu stejného typu. Výjimkou je, že seznam, ve kterém jsou prvky určeny jako základní typ, může mít elementy, které jsou odvozeny typy. Proto je možné, že následující podmínky jsou přijatelné, protože `Button` a `CheckBox` jsou odvozeny z `Control` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

Můžete také definovat prvky seznamu pomocí rozsahu, který je určen pomocí celých čísel oddělených operátorem Range ( `..` ), jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

Prázdný seznam je určený dvojicí hranatých závorek bez jakéhokoli mezi nimi.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

Můžete také použít výraz pořadí k vytvoření seznamu. Další informace naleznete v tématu [výrazy sekvence](sequences.md#sequence-expressions) . Například následující kód vytvoří seznam čtverců celých čísel od 1 do 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a>Operátory pro práci se seznamy

Prvky můžete k seznamu připojit pomocí `::` operátoru (nevýhody). `list1`V případě `[2; 3; 4]` , následující kód vytvoří `list2` jako `[100; 2; 3; 4]` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

Seznamy, které mají kompatibilní typy, lze zřetězit pomocí `@` operátoru, jak je uvedeno v následujícím kódu. Pokud `list1` je `[2; 3; 4]` a `list2` `[100; 2; 3; 4]` , tento kód vytvoří `list3` jako `[2; 3; 4; 100; 2; 3; 4]` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

Funkce pro provádění operací v seznamech jsou k dispozici v [modulu seznam](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).

Vzhledem k tomu, že seznamy v jazyce F # jsou neměnné, všechny úpravy operací generují nové seznamy místo úprav existujících seznamů.

Seznamy v jazyce F # jsou implementovány jako jednotlivě propojené seznamy, což znamená, že operace, které mají přístup pouze k hlavičce seznamu, mají hodnotu O (1) a přístup k prvkům je O (*n*).

## <a name="properties"></a>Vlastnosti

Typ seznamu podporuje následující vlastnosti:

|Vlastnost|Typ|Popis|
|--------|----|-----------|
|[Záhlaví](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head)|`'T`|První prvek.|
|[Obsahovat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Empty)|`'T list`|Statická vlastnost, která vrací prázdný seznam příslušného typu.|
|[IsEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#IsEmpty)|`bool`|`true` Pokud seznam neobsahuje žádné prvky.|
|[Položka](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Item)|`'T`|Prvek na zadaném indexu (založený na nule).|
|[Délka](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Length)|`int`|Počet elementů.|
|[Koncová část](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail)|`'T list`|Seznam bez prvního prvku|

Níže jsou uvedeny některé příklady použití těchto vlastností.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a>Používání seznamů

Programování se seznamy vám umožňuje provádět komplexní operace s malým množstvím kódu. Tato část popisuje běžné operace se seznamy, které jsou důležité pro funkční programování.

### <a name="recursion-with-lists"></a>Rekurze se seznamy

Seznamy jsou jedinečně uzpůsobeny rekurzivním programovacím technikům. Zvažte operaci, která musí být provedena u každého prvku seznamu. To lze provést rekurzivně na začátku seznamu a následným předáním konce seznamu, který je menší seznam, který se skládá z původního seznamu bez prvního prvku, zpět na další úroveň rekurze.

Chcete-li zapsat takovou rekurzivní funkci, použijte operátor nevýhody ( `::` ) v porovnávání vzorů, což umožňuje oddělit záhlaví seznamu od konce.

Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro implementaci rekurzivní funkce, která provádí operace na seznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

Předchozí kód funguje dobře u malých seznamů, ale u větších seznamů může přetečení zásobníku. Následující kód vylepšuje tento kód pomocí argumentu Akumulovaná, standardní technika pro práci s rekurzivními funkcemi. Použití argumentu akumulátoru způsobí rekurzivní funkci na konci, která šetří místo v zásobníku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

Funkce `RemoveAllMultiples` je rekurzivní funkce, která přijímá dva seznamy. První seznam obsahuje čísla, jejichž násobky budou odebrány, a druhý seznam je seznam, ze kterého mají být čísla odebrána. Kód v následujícím příkladě používá tuto rekurzivní funkci k vyloučení všech nekoncových čísel ze seznamu, přičemž seznam koncových čísel se vynechává jako výsledek.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

Výstup je následující:

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a>Funkce modulu

[Modul seznamu](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) poskytuje funkce, které přistupují k prvkům seznamu. Hlavní prvek je nejrychlejší a nejjednodušší pro přístup. Použijte [záhlaví](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) vlastnosti nebo seznam funkcí modulu [. Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head). K zakončení seznamu můžete přistupovat pomocí vlastnosti [Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) nebo funkce [list. tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) . Chcete-li najít element podle indexu, použijte funkci [list. n](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) . `List.nth` projde seznam. Proto má hodnotu O (*n*). Pokud váš kód používá `List.nth` často, možná budete chtít zvážit použití pole namísto seznamu. Přístup k prvkům v polích je O (1).

### <a name="boolean-operations-on-lists"></a>Logické operace na seznamech

Funkce [list... Empty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) určuje, zda má seznam nějaké prvky.

Funkce [list. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) používá logický test na prvky seznamu a vrací, `true` Pokud některý prvek splňuje podmínky testu. [List. exists2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) je podobný, ale pracuje na po sobě jdoucích dvojic prvků ve dvou seznamech.

Následující kód demonstruje použití `List.exists` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

Výstup je následující:

```console
For list [0; 1; 2; 3], contains zero is true
```

Následující příklad ukazuje použití `List.exists2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

Výstup je následující:

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

[Seznam. ForAll](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) můžete použít, pokud chcete otestovat, zda všechny prvky seznamu splňují podmínku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

Výstup je následující:

```console
true
false
```

Podobně [seznam. forall2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) určuje, zda všechny prvky v odpovídajících pozicích ve dvou seznamech odpovídají logickému výrazu, který zahrnuje každou dvojici prvků.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

Výstup je následující:

```console
true
false
```

### <a name="sort-operations-on-lists"></a>Seřadit operace v seznamech

Seznam. [Sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [list. sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy)a [list. sortWith –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) Functions Sort lists. Funkce řazení určuje, které z těchto tří funkcí použít. `List.sort` používá výchozí obecné porovnání. Obecné porovnání používá pro porovnání hodnot globální operátory založené na funkci Generic Compare. Funguje efektivně s širokou škálou typů prvků, jako jsou jednoduché číselné typy, řazené kolekce členů, záznamy, rozlišené sjednocení, seznamy, pole a jakýkoli typ, který implementuje `System.IComparable` . Pro typy, které implementují `System.IComparable` Obecné porovnání, používá `System.IComparable.CompareTo()` funkci. Obecné porovnání funguje také s řetězci, ale používá pořadí řazení nezávislé na jazykové verzi. Obecné porovnání by nemělo být použito pro nepodporované typy, jako například typy funkcí. Také výkon výchozího obecného porovnání je nejvhodnější pro malé strukturované typy; u větších strukturovaných typů, které je třeba porovnat a seřadit často, zvažte implementaci `System.IComparable` a poskytování efektivní implementace `System.IComparable.CompareTo()` metody.

`List.sortBy` převezme funkci, která vrací hodnotu, která se používá jako kritérium řazení, a `List.sortWith` jako argument použije funkci porovnání. Tyto dvě funkce jsou užitečné, když pracujete s typy, které nepodporují porovnání, nebo když porovnání vyžaduje složitější sémantiku porovnání, jako v případě řetězců zohledňujících jazykovou verzi.

Následující příklad ukazuje použití `List.sort` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

Výstup je následující:

```console
[-2; 1; 4; 5; 8]
```

Následující příklad ukazuje použití `List.sortBy` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

Výstup je následující:

```console
[1; -2; 4; 5; 8]
```

Další příklad ukazuje použití `List.sortWith` . V tomto příkladu se vlastní srovnávací funkce `compareWidgets` používá k prvnímu porovnání jednoho pole vlastního typu a poté další, pokud jsou hodnoty prvního pole stejné.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

Výstup je následující:

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a>Vyhledat operace v seznamech

Pro seznamy se podporuje celá řada operací hledání. Nejjednodušší, [list. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), umožňuje najít první prvek, který odpovídá dané podmínce.

Následující příklad kódu ukazuje použití nástroje `List.find` k nalezení prvního čísla, které je v seznamu dělitele 5.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

Výsledek je 5.

Pokud elementy musí být transformovány jako první, zavolejte [list. vyskl](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), který převezme funkci, která vrací možnost a vyhledá první hodnotu možnosti, která je `Some(x)` . Místo vrácení elementu `List.pick` vrátí výsledek `x` . Pokud se nenajde žádný vyhovující prvek, `List.pick` vyvolá `System.Collections.Generic.KeyNotFoundException` . Následující kód ukazuje použití `List.pick` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

Výstup je následující:

```console
"b"
```

Jiná skupina operací hledání, [list. tryFind –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) a související funkce, vrací hodnotu možnosti. `List.tryFind`Funkce vrátí první prvek seznamu, který splňuje podmínku, pokud takový prvek existuje, ale hodnota možnosti, `None` Pokud není. Seznam variací [. tryFindIndex –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) vrátí index elementu, pokud je nalezen, spíše než samotný element. Tyto funkce jsou znázorněny v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

Výstup je následující:

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a>Aritmetické operace na seznamech

Do [modulu seznamu](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)jsou integrovány běžné aritmetické operace, jako je součet a průměr. Pro práci se [seznamem. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum)musí typ elementu seznamu podporovat `+` operátor a mít nulovou hodnotu. Všechny integrované aritmetické typy tyto podmínky vyhoví. Pro práci se [seznamem. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average)musí typ elementu podporovat dělení bez zbytku, který vylučuje celočíselné typy, ale umožňuje použití typů s plovoucí desetinnou čárkou. Funkce [list. sumBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) a [list. averageBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) přebírají funkci jako parametr a výsledky této funkce se používají k výpočtu hodnot součtu nebo průměru.

Následující kód demonstruje použití `List.sum` , `List.sumBy` , a `List.average` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

Výstup je `1.000000` .

Následující kód ukazuje použití `List.averageBy` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

Výstup je `5.5` .

### <a name="lists-and-tuples"></a>Seznamy a řazené kolekce členů

Seznamy, které obsahují řazené kolekce členů, mohou být manipulovány funkcemi zip a deextrahování. Tyto funkce kombinují dva seznamy jednotlivých hodnot do jednoho seznamu řazených kolekcí členů nebo oddělují jeden seznam řazených kolekcí členů do dvou seznamů s jednou hodnotou. Nejjednodušší funkce [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) přebírá dva seznamy jednoho prvku a vytváří jeden seznam párů řazených kolekcí členů. Jiná verze, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), používá tři seznamy jednoho prvku a vytváří jeden seznam řazených kolekcí členů, které mají tři prvky. Následující příklad kódu ukazuje použití `List.zip` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

Výstup je následující:

```console
[(1, -1); (2, -2); (3; -3)]
```

Následující příklad kódu ukazuje použití `List.zip3` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

Výstup je následující:

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

Příslušné rozbalení, [seznam.](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) rozbalení a [Výpis. unzip3 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), převezmou seznamy řazených kolekcí členů a návratové seznamy v řazené kolekci členů, kde první seznam obsahuje všechny prvky, které byly první v každé řazené kolekci členů, a druhý seznam obsahuje druhý prvek každé řazené kolekce členů a tak dále.

Následující příklad kódu ukazuje použití [seznamu. dekomprimovat](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

Výstup je následující:

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

Následující příklad kódu ukazuje použití [seznamu. unzip3 –](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

Výstup je následující:

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a>Provoz na prvcích seznamu

Jazyk F # podporuje různé operace na prvcích seznamu. Nejjednodušší je [list. ITER](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter), který umožňuje zavolat funkci na každý prvek seznamu. Variace zahrnují [list. iter2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), který umožňuje provést operaci na prvcích dvou seznamů, [list. iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), což se znamená `List.iter` , že index každého prvku je předán jako argument funkci, která je volána pro každý prvek, a [list. iteri2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), což je kombinace funkcí `List.iter2` a `List.iteri` . Následující příklad kódu znázorňuje tyto funkce.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

Výstup je následující:

```console
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

Další často používanou funkcí, která transformuje prvky seznamu, je [list. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), který umožňuje použít funkci na každý prvek seznamu a umístit všechny výsledky do nového seznamu. [List. MAP2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) a [list. map3 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) jsou variace, které přijímají více seznamů. Můžete také použít [seznam. MAPI](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) a [list. mapi2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), pokud kromě prvku musí být funkce předána index každého prvku. Jediný rozdíl mezi `List.mapi2` a `List.mapi` je to, že `List.mapi2` funguje se dvěma seznamy. Následující příklad ukazuje [list. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

Výstup je následující:

```console
[2; 3; 4]
```

Následující příklad ukazuje použití `List.map2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

Výstup je následující:

```console
[5; 7; 9]
```

Následující příklad ukazuje použití `List.map3` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

Výstup je následující:

```console
[7; 10; 13]
```

Následující příklad ukazuje použití `List.mapi` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

Výstup je následující:

```console
[1; 3; 5]
```

Následující příklad ukazuje použití `List.mapi2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

Výstup je následující:

```console
[0; 7; 18]
```

[List. Collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) se podobá `List.map` , s tím rozdílem, že každý prvek vytvoří seznam a všechny tyto seznamy jsou zřetězené do konečného seznamu. V následujícím kódu každý prvek seznamu generuje tři čísla. Všechny jsou shromažďovány v jednom seznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

Výstup je následující:

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

Můžete také použít [seznam. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), který používá logickou podmínku a vytvoří nový seznam, který se skládá pouze z prvků, které odpovídají dané podmínce.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

Výsledný seznam je `[2; 4; 6]` .

Kombinace map a filtrů, [list. Volba](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) umožňuje transformovat a vybírat prvky současně. `List.choose` použije funkci, která vrátí možnost na každý prvek seznamu a vrátí nový seznam výsledků pro prvky, pokud funkce vrátí hodnotu možnosti `Some` .

Následující kód demonstruje použití `List.choose` pro výběr slov se velkými písmeny ze seznamu slov.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

Výstup je následující:

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a>Provoz na více seznamech

Seznamy lze spojit dohromady. Chcete-li spojit dva seznamy do jednoho, použijte příkaz [list. Append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append). Chcete-li spojit více než dva seznamy, použijte [list. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a>Operace skládání a skenování

Některé operace se seznamem zahrnují vzájemné závislosti mezi všemi prvky seznamu. Operace skládání a prověřování jsou podobné `List.iter` a `List.map` v tom, že vyvoláte funkci na každém elementu, ale tyto operace poskytují další parametr s názvem *akumulátor* , který přenáší informace prostřednictvím výpočtu.

Slouží `List.fold` k provedení výpočtu v seznamu.

Následující příklad kódu ukazuje použití [seznamu. skládání](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) k provádění různých operací.

Seznam je proprocházený. Akumulovaná `acc` je hodnota, která se předává společně s tím, jak výpočet pokračuje. První argument přebírá Akumulovaná a element list a vrací průběžný výsledek výpočtu pro tento prvek seznamu. Druhým argumentem je počáteční hodnota akumulátoru.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

Verze těchto funkcí, které mají číslice v názvu funkce, fungují ve více než jednom seznamu. Například [list. fold2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) provádí výpočty na dvou seznamech.

Následující příklad ukazuje použití `List.fold2` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

`List.fold` a [list. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) se liší v, který `List.fold` vrací konečnou hodnotu nadbytečného parametru, ale `List.scan` vrátí seznam mezilehlých hodnot (spolu s konečnou hodnotou) nadbytečného parametru.

Každá z těchto funkcí obsahuje opačnou variaci, například [list. foldBack –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), která se liší v pořadí, ve kterém je seznam procházen, a pořadí argumentů. `List.fold`A mít také `List.foldBack` variace, [list. fold2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) a [list. foldBack2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), které přebírají dva seznamy stejné délky. Funkce, která se spustí u každého prvku, může k provedení určité akce použít odpovídající prvky obou seznamů. Typy prvků dvou seznamů mohou být rozdílné, jako v následujícím příkladu, ve kterém jeden seznam obsahuje částky transakcí pro bankovní účet a druhý seznam obsahuje typ transakce: vklad nebo disstoupit.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

Pro výpočet, jako je suma, `List.fold` a `List.foldBack` mít stejný účinek, protože výsledek není závislý na pořadí procházení. V následujícím příkladu `List.foldBack` se používá pro přidání prvků v seznamu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

Následující příklad vrátí na příklad bankovního účtu. Tentokrát se přidá nový typ transakce: výpočet úroku. Koncový zůstatek nyní závisí na pořadí transakcí.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

Seznam funkcí [. zmenšení](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) je trochu podobné `List.fold` a `List.scan` , s výjimkou toho, že místo předání samostatného hromadění, `List.reduce` přebírá funkci, která přijímá dva argumenty typu elementu namísto pouze jednoho a jeden z těchto argumentů funguje jako akumulátor, což znamená, že ukládá mezivýsledek výpočtu. `List.reduce` začíná při práci na prvních dvou prvcích seznamu a poté používá výsledek operace spolu s dalším prvkem. Vzhledem k tomu, že není k dispozici samostatný akumulátor, který má svůj vlastní typ, `List.reduce` lze použít místo pouze v případě, že je `List.fold` typ akumulátoru a typ elementu stejného typu. Následující kód demonstruje použití `List.reduce` . `List.reduce` vyvolá výjimku, pokud zadaný seznam neobsahuje žádné elementy.

V následujícím kódu je první volání lambda výrazu uděleno argumenty 2 a 4 a vrátí hodnotu 6 a další volání je uděleno argumenty 6 a 10, takže výsledek je 16.

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a>Převod mezi seznamy a jinými typy kolekcí

`List`Modul poskytuje funkce pro převod do a z obou sekvencí a polí. Pro převod na nebo z sekvence použijte [list. toSeq –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) nebo [list. ofSeq –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq). Pro převod na nebo z pole použijte [list. ToArray –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) nebo [list. ofArray –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).

### <a name="additional-operations"></a>Další operace

Informace o dalších operacích v seznamech naleznete v tématu Knihovna odkazů na [modul seznam](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)témat.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Typy F#](fsharp-types.md)
- [Sekvence](sequences.md)
- [Pole](arrays.md)
- [Možnosti](options.md)
