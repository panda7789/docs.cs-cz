---
title: Pole (F#)
description: Zjistěte, jak vytvořit a používat v polích F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: 0f72718988ee401631c53b74f02948030e83aac1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129971"
---
# <a name="arrays"></a>Pole

> [!NOTE]
> Odkaz rozhraní API se dostanete na webu MSDN.  Reference k rozhraní API webu docs.microsoft.com není dokončena.

Pole jsou pevné velikosti, založený na nule, proměnlivé kolekce po sobě jdoucích datové prvky, které jsou všechny stejného typu.

## <a name="creating-arrays"></a>Tvorba polí

Pole lze vytvořit několika způsoby. Malé pole můžete vytvořit uvedením po sobě následujících hodnot mezi `[|` a `|]` a oddělené středníkem, jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

Každý prvek lze také umístit na samostatný řádek, ve kterém je volitelný případ oddělovač středník.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

Typ prvků pole je odvozen z použitých literál a musí být konzistentní vzhledem k aplikacím. Následující kód způsobí chybu, protože 1.0 je plovoucí desetinnou čárkou a 2 a 3 jsou celá čísla.

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

Sekvence výrazů můžete použít také k vytvoření polí. Tady je příklad, který vytvoří pole druhých mocnin celých čísel od 1 do 10.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

K vytvoření pole, ve kterém jsou všechny prvky inicializovány na nulu, použijte `Array.zeroCreate`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a>Přístup k prvkům

Můžete přistupovat k prvkům pole pomocí operátoru tečka (`.`) a hranaté závorky (`[` a `]`).

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

Indexy pole začínají od 0.

Prvky pole můžete také přistupovat pomocí zápisu řezu, který umožňuje určit dílčí řadu pole. Příklady postupu zápisu řezu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

Při použití zápisu řezu je vytvořena nový kopie pole.

## <a name="array-types-and-modules"></a>Typy polí a moduly

Typ všech F# pole je typ rozhraní .NET Framework <xref:System.Array?displayProperty=nameWithType>. Proto F# pole podporují všechny funkce dostupné v <xref:System.Array?displayProperty=nameWithType>.

Modul knihovny [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) podporuje operace pro jednorozměrné pole. Moduly `Array2D`, `Array3D`, a `Array4D` obsahují funkce, které podporují operace pro pole dvou, tří a čtyř dimenzí, v uvedeném pořadí. Můžete vytvořit pole řádu větší než čtyři pomocí <xref:System.Array?displayProperty=nameWithType>.

### <a name="simple-functions"></a>Jednoduché funkce

[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) Získá element. [`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) Udává délku pole. [`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) nastaví element na zadanou hodnotu. Následující příklad kódu ukazuje použití těchto funkcí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

Výstup je následující.

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a>Funkce, které vytvářejí pole

Několik funkcí tvoří pole bez nutnosti existujícího pole. [`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) Vytvoří nové pole, která neobsahuje žádné prvky. [`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) Vytvoří pole určené velikosti a nastaví všechny prvky na zadané hodnoty. [`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) Vytvoří pole s danou dimenzí a funkce pro generování prvků. [`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) Vytvoří pole, ve kterém jsou všechny prvky inicializovány na nulovou hodnotu pro typ pole. Následující kód demonstruje tyto funkce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

Výstup je následující.

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) Vytvoří nové pole obsahující prvky, které jsou zkopírovány z existujícího pole. Všimněte si, že kopie je Mělká, což znamená, že pokud typ elementu je typem odkazu, je zkopírován pouze odkaz, nikoli základní objekt. Následující příklad kódu to dokládá.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

Výstup předcházejícího kódu vypadá takto:

```
[|Test1; Test2; |]
[|; Test2; |]
```

Řetězec `Test1` se zobrazuje jenom v prvním poli, protože operace vytváření nového elementu přepíše odkaz v `firstArray` , ale nemá vliv na původní odkaz na prázdný řetězec, který se stále nachází `secondArray`. Řetězec `Test2` se zobrazuje v obou polích, protože `Insert` operace <xref:System.Text.StringBuilder?displayProperty=nameWithType> typu ovlivňuje základní <xref:System.Text.StringBuilder?displayProperty=nameWithType> objekt, který se odkazuje v obou polích.

[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generuje nové pole z podrozsahu pole. Zadejte dílčí sadu poskytnutím počáteční index a délka. Následující kód demonstruje použití `Array.sub`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

Výstup ukazuje, že podpole začíná prvkem 5 a obsahuje 10 prvků.

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) Vytvoří nové pole kombinací dvou existujících polí.

Následující kód ukazuje **Array.append**.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

Výstup předcházejícího kódu vypadá takto.

```
[|1; 2; 3; 4; 5; 6|]
```

[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) Vybere prvky pole pro zahrnutí do nového pole. Následující kód ukazuje `Array.choose`. Všimněte si, že typ prvku pole nemusí odpovídat typu hodnoty vrácené v typu možnosti. V tomto příkladu je typ prvku `int` a možnost je výsledek polynomické funkce `elem*elem - 1`, jako plovoucí číslo bodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

Výstup předcházejícího kódu vypadá takto.

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) Spustí určenou funkci na každém elementu pole existujícího pole a poté shromáždí elementy generované funkcí a zkombinuje je do nového pole. Následující kód ukazuje `Array.collect`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

Výstup předcházejícího kódu vypadá takto.

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) přebírá pořadí polí a kombinuje je do jediného pole. Následující kód ukazuje `Array.concat`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

Výstup předcházejícího kódu vypadá takto.

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) převezme logickou podmínku funkce a generuje nové pole, která obsahuje pouze elementy z vstupního pole, pro které je podmínka pravdivá. Následující kód ukazuje `Array.filter`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

Výstup předcházejícího kódu vypadá takto.

```
[|2; 4; 6; 8; 10|]
```

[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generuje nové pole přehozením pořadí existujícího pole. Následující kód ukazuje `Array.rev`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

Výstup předcházejícího kódu vypadá takto.

```
"Hello world!"
```

Můžete snadno kombinovat funkce v modulu pole, které transformují pole pomocí operátoru kanálu (`|>`), jak je znázorněno v následujícím příkladu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

Výstup je

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a>Vícerozměrná pole

Vícedimenzionální pole mohou být vytvořena, ale neexistuje žádná syntaxe zápisu vícedimenzionálního literálu pole. Použití operátoru [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) k vytvoření pole ze sekvence sekvencí elementů pole. Sekvence může být pole nebo literály seznamu. Například následující kód vytvoří dvourozměrné pole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

Můžete také použít funkci [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) k inicializaci pole dvou dimenzí a podobné funkce jsou k dispozici pro pole třemi až čtyřmi dimenzemi. Tyto funkce přebírají funkci, která se používá k vytváření elementů. Pokud chcete vytvořit dvojrozměrné pole obsahující elementy nastavené na počáteční hodnotu místo určení funkce, použijte [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) funkce, která je také k dispozici pro pole až do čtyř dimenzí. Následující příklad kódu nejprve ukazuje, jak vytvořit pole obsahující požadované prvky a potom použije `Array2D.init` k vygenerování požadovaného dvourozměrného pole.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

Pole indexování a plátkování syntaxe jsou podporovány pro pole do pořadí 4. Při zadávání indexu ve více dimenzích používáte čárky k oddělení indexů, jak je znázorněno v následujícím příkladu kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]

Typ dvourozměrného pole je zapsán jako `<type>[,]` (například `int[,]`, `double[,]`), a typ trojrozměrného pole je zapsán jako `<type>[,,]`, a tak dále pro pole vyšších rozměrů.

Pouze podmnožinu funkcí, které jsou k dispozici pro jednorozměrné pole je také k dispozici pro vícedimenzionální pole. Další informace najdete v tématu [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), a [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).

### <a name="array-slicing-and-multidimensional-arrays"></a>Řezání rozšířené pole a vícedimenzionální pole

Dvourozměrné pole (matice) může extrahovat dílčí matici určením rozsahů a pomocí zástupného znaku (`*`) znak zadáním celého řádku nebo sloupce.

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

Od verze F# 3.1 můžete rozložit vícerozměrné pole na podpole stejné nebo nižší dimenze. Vektor lze získat například z matice zadáním jednoho řádku nebo sloupce.

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

Můžete použít syntaxi dělení pro typy, které implementují operátory přístupu k elementu a přetížené `GetSlice` metody. Například následující kód vytvoří typ matice, která obaluje F# 2D pole, implementuje vlastnost položky pro poskytnutí podpory pro indexování pole a implementuje tři verze `GetSlice`. Pokud tento kód můžete použít jako šablonu pro vaše typy matice, můžete použít všechny operace řezů, které tato část popisuje.

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

Funkce [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) a [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) testuje prvky v jednu nebo dvě pole, v uvedeném pořadí. Tyto funkce provádějí funkci testu a vrátí `true` Pokud element (nebo dvojice elementů pro `Array.exists2`), splňující danou podmínku.

Následující kód demonstruje použití `Array.exists` a `Array.exists2`. V těchto příkladech jsou nové funkce vytvořeny použitím pouze jednoho z argumentů v těchto případech argumentem funkce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

Výstup předcházejícího kódu vypadá takto.

```
true
false
false
true
```

Podobně funkce [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testuje pole a určuje, zda každý prvek splňuje logickou podmínku. Změna [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) provede stejnou akci pomocí logické funkce, která zahrnuje elementy dvou polí stejné délky. Následující kód ukazuje použití těchto funkcí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

Výstup pro tyto příklady je následujícím způsobem.

```
false
true
true
false
```

### <a name="searching-arrays"></a>Hledání v polích

[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) přebírá logickou funkci a vrátí první prvek, pro který funkce vrátí `true`, nebo vyvolává <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> Pokud není nalezen žádný element, který splňuje podmínku. [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) je třeba `Array.find`, s tím rozdílem, že vrátí index elementu namísto samotného elementu.

Následující kód používá `Array.find` a `Array.findIndex` vyhledejte číslo, které je dokonalý čtverec i dokonalá krychle.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

Výstup je následující.

```
The first element that is both a square and a cube is 64 and its index is 62.
```

[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) je třeba `Array.find`, s tím rozdílem, že výsledek je typ možnosti a vrátí `None` Pokud není nalezen žádný element. `Array.tryFind` by měl být použít namísto `Array.find` Pokud si nejste jisti, zda je odpovídající prvek v poli. Obdobně [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) je stejná jako [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) s tím rozdílem, že typ možnosti je vrácenou hodnotu. Pokud není nalezen žádný element, je možnost `None`.

Následující kód demonstruje použití `Array.tryFind`. Tento kód závisí na předchozím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

Výstup je následující.

```
Found an element: 1
Found an element: 729
```

Použití [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) když potřebujete transformovat element kromě vyhledání. Výsledkem je první prvek, pro který funkce vrátí transformovaný prvek jako hodnotu možnosti, nebo `None` Pokud se nenajde žádný takový prvek.

Následující kód ukazuje použití `Array.tryPick`. V tomto případě namísto výrazu lambda, jsou definovány několik místních pomocných funkcí pro zjednodušení kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

Výstup je následující.

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a>Provádění výpočtů v polích

[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) Funkce vrátí průměr z jednotlivých prvků v poli. Je omezena na typy prvků, které podporují přesné dělení celým číslem, které zahrnuje typy plovoucího bodu, ale ne integrální typy. [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) Funkce vrátí průměr z výsledků volání funkce na každý prvek. Pro pole integrálního typu, můžete použít `Array.averageBy` a nechat funkce převést každý prvek na plovoucí typu pro výpočet bodu.

Použití [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) nebo [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) získat maximální nebo minimální element, pokud je typ elementu podporuje. Obdobně [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) a [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) povolit funkce, který se spustí nejdříve, třeba tak, aby na typ, který podporuje porovnání.

[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) Přidá prvky pole, a [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) volá funkci na každý element a přidá výsledky dohromady.

Chcete-li spustit funkci na každý prvek v poli bez uložení vrácených hodnot, použijte [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516). Pro funkci zahrnující dvě pole stejné délky, použijte [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc). Pokud potřebujete zachovat pole výsledků této funkce, použijte [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) nebo [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), jež pracuje na dvou polích najednou.

Variace [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) a [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) povolit indexu elementu do výpočtu, totéž platí pro [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) a [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).

Funkce [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), a [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) spouští algoritmy, které se týkají všech prvků pole. Podobně variace [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) a [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) provádí výpočty na dvou polích.

Tyto funkce pro provádění výpočtů odpovídají funkcím se stejným názvem v [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788). Příklady využití naleznete v tématu [uvádí](lists.md).

### <a name="modifying-arrays"></a>Změna polí

[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) nastaví element na zadanou hodnotu. [`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) Nastaví rozsah elementů v matici na zadanou hodnotu. Následující kód obsahuje příklad `Array.fill`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

Výstup je následující.

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

Můžete použít [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) ke kopírování dílčí sady jednoho pole ke druhému.

### <a name="converting-to-and-from-other-types"></a>Převod na objekty Null a z jiných typů

[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) Vytvoří pole ze seznamu. [`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) Vytvoří pole ze sekvence. [`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) a [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) převést na tyto typy kolekcí z typu pole.

### <a name="sorting-arrays"></a>Pole třídění

Použití [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) seřadit pole pomocí funkce obecného porovnání. Použití [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) k určení funkce, která generuje hodnotu, označuje jako *klíč*, k uspořádání pomocí funkce obecného porovnání v klíči. Použití [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) Pokud byste chtěli poskytnout vlastní funkci porovnání. `Array.sort`, `Array.sortBy`, a `Array.sortWith` všechny vrátí seřazené pole jako nové pole. Variace [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), a [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) mění stávající pole místo vrácení nového.

### <a name="arrays-and-tuples"></a>Pole a n-tice

Funkce [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) a [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) převádí pole párů n-tice pro n-tice polí a naopak. [`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) a [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) jsou podobné s tím rozdílem, že pracují s n-tice tří prvků nebo n-tice tří polí.

## <a name="parallel-computations-on-arrays"></a>Paralelní výpočty v polích

V modulu [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) obsahuje funkce pro provádění paralelních výpočtů v polích. Tento modul není k dispozici v aplikacích, které cílové verze rozhraní .NET Framework starší než verze 4.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [F#; Typy](fsharp-types.md)
