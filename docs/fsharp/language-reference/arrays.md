---
title: Pole
description: 'Naučte se vytvářet a používat pole v programovacím jazyce F #.'
ms.date: 08/13/2020
ms.openlocfilehash: 37f781ccd2c7bc2ca2c7b93bda53bbb3ea93b504
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608502"
---
# <a name="arrays"></a>Pole

Pole jsou pevná velikost, založená na nule, proměnlivé kolekce po sobě jdoucích datových prvků, které jsou všechny stejného typu.

## <a name="create-arrays"></a>Vytváření polí

Pole můžete vytvořit několika způsoby. Malé pole můžete vytvořit tak, že zobrazíte po sobě jdoucí hodnoty mezi `[|` a `|]` a oddělené středníky, jak je znázorněno v následujících příkladech.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

Každý prvek lze také umístit na samostatný řádek, v takovém případě je oddělovač středník volitelný.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

Typ prvků pole je odvozen z používaných literálů a musí být konzistentní. Následující kód způsobí chybu, protože 1,0 je float a 2 a 3 jsou celá čísla.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Výrazy sekvence lze také použít k vytvoření polí. Následuje příklad, který vytvoří pole čtverců celých čísel od 1 do 10.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

Chcete-li vytvořit pole, ve kterém jsou všechny prvky inicializovány na nulu, použijte `Array.zeroCreate` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a>Přístup k prvkům

K prvkům pole můžete přistupovat pomocí operátoru tečka ( `.` ) a závorek ( `[` a `]` ).

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

Indexy pole začínají na 0.

K prvkům pole můžete přistupovat také pomocí zápisu řezů, který umožňuje zadat dílčí rozsah pole. Následují příklady zápisu řezů.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

Při použití notace řezu se vytvoří nová kopie pole.

## <a name="array-types-and-modules"></a>Typy polí a moduly

Typ všech polí jazyka F # je .NET Framework typ <xref:System.Array?displayProperty=nameWithType> . Proto pole jazyka F # podporují všechny funkce, které jsou k dispozici v <xref:System.Array?displayProperty=nameWithType> .

[ `Array` Modul](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) podporuje operace pro jednorozměrné pole. Moduly `Array2D` , `Array3D` a `Array4D` obsahují funkce, které podporují operace s poli dvou, tří a čtyř dimenzí v uvedeném pořadí. Pomocí můžete vytvořit pole s pořadím větším než čtyři <xref:System.Array?displayProperty=nameWithType> .

### <a name="simple-functions"></a>Jednoduché funkce

[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) Získá element. [`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) poskytuje délku pole. [`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) Nastaví element na zadanou hodnotu. Následující příklad kódu ukazuje použití těchto funkcí.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

Výstup je následující.

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Funkce, které vytvářejí pole

Několik funkcí vytváří pole bez nutnosti existujícího pole. [`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) Vytvoří nové pole, které neobsahuje žádné prvky. [`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) Vytvoří pole zadané velikosti a nastaví všechny prvky na zadané hodnoty. [`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) Vytvoří pole s ohledem na dimenzi a funkci pro generování prvků. [`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) Vytvoří pole, ve kterém jsou všechny prvky inicializovány na nulovou hodnotu pro typ pole. Následující kód znázorňuje tyto funkce.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

Výstup je následující.

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) Vytvoří nové pole, které obsahuje prvky, které jsou zkopírovány z existujícího pole. Všimněte si, že kopie je bez podstruktury, což znamená, že pokud je typ elementu odkazový typ, zkopíruje se pouze odkaz, nikoli podkladový objekt. Následující příklad kódu to dokládá.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

Výstup předcházejícího kódu je následující:

```console
[|Test1; Test2; |]
[|; Test2; |]
```

Řetězec `Test1` se zobrazí pouze v prvním poli, protože operace vytvoření nového elementu přepíše odkaz v, `firstArray` ale nemá vliv na původní odkaz na prázdný řetězec, který je stále přítomen v `secondArray` . Řetězec `Test2` se zobrazí v obou polích, protože `Insert` operace s <xref:System.Text.StringBuilder?displayProperty=nameWithType> typem ovlivňuje podkladový <xref:System.Text.StringBuilder?displayProperty=nameWithType> objekt, na který je odkazováno v obou polích.

[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) vygeneruje nové pole z dílčího rozsahu pole. Dílčí rozsah můžete zadat zadáním počátečního indexu a délky. Následující kód demonstruje použití `Array.sub` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

Výstup ukazuje, že podpole začíná na elementu 5 a obsahuje 10 prvků.

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) Vytvoří nové pole kombinováním dvou existujících polí.

Následující kód demonstruje **pole Array. Append**.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

Výstup předcházejícího kódu je následující.

```console
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) vybere prvky pole, které mají být zahrnuty do nového pole. Následující kód demonstruje `Array.choose` . Všimněte si, že typ elementu pole nemusí odpovídat typu hodnoty vrácené v typu možnosti. V tomto příkladu je typ prvku `int` a možnost je výsledkem polynomické funkce, `elem*elem - 1` jako číslo s plovoucí desetinnou čárkou.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

Výstup předcházejícího kódu je následující.

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) Spustí zadanou funkci u každého prvku pole existujícího pole a poté shromáždí prvky vygenerované funkcí a zkombinuje je do nového pole. Následující kód demonstruje `Array.collect` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

Výstup předcházejícího kódu je následující.

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) vezme sekvenci polí a zkombinuje je do jednoho pole. Následující kód demonstruje `Array.concat` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

Výstup předcházejícího kódu je následující.

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) používá funkci logické podmínky a generuje nové pole, které obsahuje pouze prvky ze vstupního pole, pro které je podmínka pravdivá. Následující kód demonstruje `Array.filter` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

Výstup předcházejícího kódu je následující.

```console
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) vygeneruje nové pole obrácením pořadí existujícího pole. Následující kód demonstruje `Array.rev` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

Výstup předcházejícího kódu je následující.

```console
"Hello world!"
```

Můžete snadno kombinovat funkce v modulu Array, které transformují pole pomocí operátoru kanálu ( `|>` ), jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

Výstup je

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Multidimenzionální pole

Multidimenzionální pole lze vytvořit, ale neexistuje žádná syntaxe pro zápis literálu multidimenzionálního pole. Operátor lze použít [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) k vytvoření pole z sekvence sekvencí prvků pole. Sekvence mohou být literály pole nebo seznamu. Například následující kód vytvoří dvourozměrné pole.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

Funkci lze také použít [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) k inicializaci polí dvou dimenzí a podobné funkce jsou k dispozici pro pole tří a čtyř dimenzí. Tyto funkce přebírají funkci, která se používá k vytvoření prvků. Chcete-li vytvořit dvourozměrné pole obsahující prvky nastavené na počáteční hodnotu namísto určení funkce, použijte [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) funkci, která je také k dispozici pro pole až do čtyř dimenzí. Následující příklad kódu ukazuje, jak vytvořit pole polí obsahující požadované prvky a poté používá `Array2D.init` ke generování požadovaného dvojrozměrného pole.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

Indexace pole a syntaxe průřezu se podporují pro pole až do pořadí 4. Při zadávání indexu ve více dimenzích použijte čárky k oddělení indexů, jak je znázorněno v následujícím příkladu kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

Typ dvojrozměrného pole je zapsán jako `<type>[,]` (například `int[,]` , `double[,]` ) a typ trojrozměrného pole je zapsán jako `<type>[,,]` a tak dále pro pole vyšších dimenzí.

Pro multidimenzionální pole je k dispozici také pouze podmnožina funkcí dostupných pro jednorozměrné pole.

### <a name="array-slicing-and-multidimensional-arrays"></a>Řezy pole a multidimenzionální pole

V dvojrozměrném poli (matici) můžete extrahovat dílčí matici zadáním rozsahů a použitím `*` znaku zástupného znaku () pro zadání celých řádků nebo sloupců.

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

Multidimenzionální pole lze rozložit na podpole stejné nebo nižší dimenze. Můžete například získat vektor z matice zadáním jednoho řádku nebo sloupce.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Tuto syntaxi průřezů lze použít pro typy, které implementují operátory přístupu k prvkům a přetížené `GetSlice` metody. Například následující kód vytvoří typ matice, který zabalí 2D pole F #, implementuje vlastnost Item pro poskytnutí podpory pro indexování pole a implementuje tři verze systému `GetSlice` . Pokud tento kód můžete použít jako šablonu pro typy matrice, můžete použít všechny operace řezů, které tato část popisuje.

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a>Logické funkce pro pole

Funkce [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) a [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) testovací prvky buď v jednom nebo dvou polích, v uvedeném pořadí. Tyto funkce přebírají funkci testu a vrátí `true` , pokud existuje element (nebo pár prvků pro `Array.exists2` ), který splňuje podmínky.

Následující kód demonstruje použití `Array.exists` a `Array.exists2` . V těchto příkladech jsou vytvořeny nové funkce použitím pouze jednoho z argumentů, v těchto případech argument funkce.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

Výstup předcházejícího kódu je následující.

```console
true
false
false
true
```

Podobně funkce [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) testuje pole k určení, zda každý prvek splňuje logickou podmínku. Variace má [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) stejnou věc pomocí logické funkce, která zahrnuje prvky dvou polí stejné délky. Následující kód ilustruje použití těchto funkcí.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

Výstup pro tyto příklady je následující.

```console
false
true
true
false
```

### <a name="search-arrays"></a>Hledat pole

[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) převezme logickou funkci a vrátí první prvek, pro který funkce vrací `true` , nebo vyvolá, <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> Pokud není nalezen žádný element, který by splňoval podmínky. [`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) je jako `Array.find` , s tím rozdílem, že vrátí index elementu namísto samotného prvku.

Následující kód používá `Array.find` a `Array.findIndex` k vyhledání čísla, které je dokonalým čtvercem a dokonalým datovou krychlí.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

Výstup je následující.

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) je jako `Array.find` , s tím rozdílem, že jeho výsledek je typ možnosti a vrátí, `None` Pokud není nalezen žádný element. `Array.tryFind` by měl být použit místo toho, `Array.find` když nevíte, zda je shodný prvek v poli. Podobně [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) je podobný jako `Array.findIndex` s tím rozdílem, že typ možnosti je vrácená hodnota. Pokud není nalezen žádný element, možnost je `None` .

Následující kód demonstruje použití `Array.tryFind` . Tento kód závisí na předchozím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

Výstup je následující.

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

Použijte [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) v případě, že potřebujete transformovat prvek společně s jeho hledáním. Výsledkem je první prvek, pro který funkce vrací transformovaný prvek jako hodnotu možnosti, nebo `None` Pokud žádný takový prvek nenajde.

Následující kód ukazuje použití `Array.tryPick` . V tomto případě namísto lambda výrazu je definováno několik místních pomocných funkcí pro zjednodušení kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

Výstup je následující.

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a>Provádění výpočtů u polí

[`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average)Funkce vrátí průměr každého prvku v poli. Je omezen na typy prvků, které podporují přesné dělení podle typu Integer, což zahrnuje typy plovoucí desetinné čárky, ale ne celočíselné typy. [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy)Funkce vrátí průměr výsledků volání funkce na každém elementu. Pro pole integrálního typu můžete použít `Array.averageBy` a mít funkci převést každý prvek na typ s plovoucí desetinnou čárkou pro výpočet.

Použijte [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) nebo [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) k získání maximálního nebo minimálního prvku, pokud jej typ elementu podporuje. Podobně [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) a [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) umožněte, aby byla funkce provedena jako první, možná pro transformaci na typ, který podporuje porovnání.

[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) Přidá prvky pole a [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) zavolá funkci na každý prvek a výsledky společně přidávají.

Chcete-li spustit funkci pro každý prvek v poli bez uložení vrácených hodnot, použijte [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) . Pro funkci, která zahrnuje dvě pole stejné délky, použijte [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) . Pokud také potřebujete zachovat pole výsledků funkce, použijte [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) nebo [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , který pracuje na dvou polích najednou.

Variace [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) a [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) umožňují, aby index elementu byl součástí výpočtu; totéž platí pro [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) a [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .

Funkce [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) ,,,, [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) a [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) spouštějí algoritmy, které zahrnují všechny prvky pole. Podobně variace [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) a [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) provádění výpočtů na dvou polích.

Tyto funkce pro provádění výpočtů odpovídají funkcím stejného názvu v [modulu seznamu](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html). Příklady použití najdete v tématu [seznam](lists.md).

### <a name="modify-arrays"></a>Upravit pole

[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) Nastaví element na zadanou hodnotu. [`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) nastaví v poli rozsah prvků na zadanou hodnotu. Následující kód poskytuje příklad `Array.fill` .

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

Výstup je následující.

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Můžete použít [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) ke kopírování dílčí části jednoho pole do jiného pole.

### <a name="convert-to-and-from-other-types"></a>Převod na jiné typy a z nich

[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) Vytvoří pole ze seznamu. [`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) Vytvoří pole z sekvence. [`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) a [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) převeďte je na tyto typy kolekcí z typu pole.

### <a name="sort-arrays"></a>Seřadit pole

Slouží [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) k řazení pole pomocí generické funkce porovnání. Použijte [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) k určení funkce, která generuje hodnotu, která je označována jako *klíč*, k seřazení pomocí generické funkce porovnání na klíč. Použijte, [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) Pokud chcete zadat vlastní srovnávací funkci. `Array.sort`, `Array.sortBy` a `Array.sortWith` vrátí seřazené pole jako nové pole. Variace [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) , [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) a [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) mění existující pole místo vrácení nového.

### <a name="arrays-and-tuples"></a>Pole a řazené kolekce členů

Funkce [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) a [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) převádí pole párů řazené kolekce členů na řazené kolekce členů a naopak. [`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) a [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) jsou podobné s tím rozdílem, že pracují s řazenými kolekcemi členů tří prvků nebo řazenými kolekcemi členů tří polí.

## <a name="parallel-computations-on-arrays"></a>Paralelní výpočty u polí

Modul [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) obsahuje funkce pro provádění paralelních výpočtů v polích. Tento modul není dostupný v aplikacích, které cílí na verze .NET Framework před verzí 4.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F #](index.md)
- [Typy F#](fsharp-types.md)
