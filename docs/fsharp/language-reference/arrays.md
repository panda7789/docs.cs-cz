---
title: Pole (F#)
description: "Zjistěte, jak vytvořit a použít pole v programovací jazyk F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 61fa9084-abdc-4cf5-8213-91ec1211866b
ms.openlocfilehash: 7c9d8405230f4d765d3afdeaa154ddc598d0d1ec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="arrays"></a><span data-ttu-id="cd2cc-104">Pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-104">Arrays</span></span>

> [!NOTE]
<span data-ttu-id="cd2cc-105">Rozhraní API použití odkazu přejdete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-105">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="cd2cc-106">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-106">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="cd2cc-107">Pole jsou pevné velikosti, počítáno od nuly, Měnitelná kolekce po sobě jdoucích datové prvky, které jsou všechny stejného typu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-107">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="cd2cc-108">Vytváření pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-108">Creating Arrays</span></span>
<span data-ttu-id="cd2cc-109">Pole můžete vytvořit několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-109">You can create arrays in several ways.</span></span> <span data-ttu-id="cd2cc-110">Malé pole můžete vytvořit tak, že uvedete po sobě jdoucích hodnot mezi `[|` a `|]` a oddělené středníky, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-110">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="cd2cc-111">Každý prvek můžete také uveďte na samostatném řádku, ve kterém je volitelný případ oddělovací středník.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-111">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="cd2cc-112">Typ elementů pole je odvozeno z literály používá a musí být konzistentní.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-112">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="cd2cc-113">Následující kód způsobí chybu, protože 1.0 je plovoucí desetinné čárky a 2 a 3 jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-113">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="cd2cc-114">Sekvenční výrazy můžete také použít k vytvoření polí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-114">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="cd2cc-115">Následuje příklad, který vytvoří pole kvadratických celých čísel od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-115">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="cd2cc-116">Chcete-li vytvořit pole, ve kterém jsou všechny elementy jsou inicializovány na nulu, použijte `Array.zeroCreate`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-116">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]
    
## <a name="accessing-elements"></a><span data-ttu-id="cd2cc-117">Přístup k elementům</span><span class="sxs-lookup"><span data-stu-id="cd2cc-117">Accessing Elements</span></span>

<span data-ttu-id="cd2cc-118">Máte přístup k elementy pole pomocí operátoru tečka (`.`) a hranaté závorky (`[` a `]`).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-118">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="cd2cc-119">Indexy pole začínají hodnotou 0.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-119">Array indexes start at 0.</span></span>

<span data-ttu-id="cd2cc-120">Přístup k elementům pole můžete také pomocí notace řez, který umožňuje určit Podoblast sady pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-120">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="cd2cc-121">Příklady řez zápis.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-121">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="cd2cc-122">Pokud se používá zápis řez, se vytvoří novou kopii tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-122">When slice notation is used, a new copy of the array is created.</span></span>


## <a name="array-types-and-modules"></a><span data-ttu-id="cd2cc-123">Typy polí a modulů</span><span class="sxs-lookup"><span data-stu-id="cd2cc-123">Array Types and Modules</span></span>
<span data-ttu-id="cd2cc-124">Typ všechny F # pole je typ rozhraní .NET Framework <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-124">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cd2cc-125">Proto F # pole podporují všechny funkce, které jsou k dispozici v <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-125">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="cd2cc-126">Modul knihovny [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) podporuje operací na jednorozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-126">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="cd2cc-127">Moduly `Array2D`, `Array3D`, a `Array4D` obsahují funkce, které podporují operace v rámci polí dva, tři a čtyři dimenze, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-127">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="cd2cc-128">Můžete vytvořit pole pořadí větší než čtyři pomocí <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-128">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="cd2cc-129">Jednoduché funkce</span><span class="sxs-lookup"><span data-stu-id="cd2cc-129">Simple Functions</span></span>
<span data-ttu-id="cd2cc-130">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)Získá element.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-130">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="cd2cc-131">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)poskytuje délka pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-131">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="cd2cc-132">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)element se nastaví na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-132">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="cd2cc-133">Následující příklad kódu ukazuje použití těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-133">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="cd2cc-134">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-134">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="cd2cc-135">Funkce, které vytváření polí</span><span class="sxs-lookup"><span data-stu-id="cd2cc-135">Functions That Create Arrays</span></span>

<span data-ttu-id="cd2cc-136">Několik funkcí vytváření pole bez nutnosti existující pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-136">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="cd2cc-137">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)Vytvoří nové pole, která neobsahuje žádné elementy.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-137">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="cd2cc-138">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)Vytvoří pole zadané velikosti a nastaví všechny elementy zadaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-138">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="cd2cc-139">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)Vytvoří pole, daného dimenze a funkci, kterou chcete vygenerovat elementy.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-139">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="cd2cc-140">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)Vytvoří pole, ve kterém jsou všechny prvky inicializována tak, aby nulová hodnota pro typ tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-140">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="cd2cc-141">Následující kód ukazuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-141">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="cd2cc-142">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-142">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="cd2cc-143">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)Vytvoří nové pole, která obsahuje elementy, které jsou zkopírovány z existující pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-143">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="cd2cc-144">Všimněte si, kopie je bez podstruktury kopie, což znamená, že pokud je typ elementu typu odkazu, pouze odkaz zkopírován, není podkladových objektů.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-144">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="cd2cc-145">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-145">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="cd2cc-146">Výstup předchozí kód je následující:</span><span class="sxs-lookup"><span data-stu-id="cd2cc-146">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="cd2cc-147">Řetězec `Test1` se zobrazí jenom v prvním poli, protože operace vytváření nového elementu přepíše odkaz v `firstArray` , ale nemá vliv na původní odkaz na prázdný řetězec, který se stále nachází na `secondArray`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-147">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="cd2cc-148">Řetězec `Test2` se zobrazí v obou pole, protože `Insert` operace na <xref:System.Text.StringBuilder?displayProperty=nameWithType> typu ovlivňuje základní <xref:System.Text.StringBuilder?displayProperty=nameWithType> objekt, který se odkazuje do obou polí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-148">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="cd2cc-149">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)generuje nové pole z Podoblast sady pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-149">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="cd2cc-150">Zadáte Podoblast sady zadáním počáteční index a délka.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-150">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="cd2cc-151">Následující kód ukazuje použití `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-151">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="cd2cc-152">Výstup ukazuje, že subarray spustí v prvku 5 a obsahuje 10 elementy.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-152">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
<span data-ttu-id="cd2cc-153">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)kombinací dvou existujícím polím vytvoří nové pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-153">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="cd2cc-154">Následující kód ukazuje **Array.append**.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-154">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="cd2cc-155">Výstup předchozí kód je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-155">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="cd2cc-156">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)Vybere prvky pole pro zahrnutí do nové pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-156">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="cd2cc-157">Následující kód ukazuje `Array.choose`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-157">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="cd2cc-158">Všimněte si, že typ elementu pole nemusí být stejný typ hodnoty vrácené v typu možnost.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-158">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="cd2cc-159">V tomto příkladu je typ elementu `int` a možnost je výsledkem polynomické funkce, `elem*elem - 1`, jako plovoucí bodu číslo.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-159">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="cd2cc-160">Výstup předchozí kód je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-160">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="cd2cc-161">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)Spustí zadaný funkci pro každý element pole existující pole a shromažďuje elementy generované funkce a sloučí je do nové pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-161">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="cd2cc-162">Následující kód ukazuje `Array.collect`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-162">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="cd2cc-163">Výstup předchozí kód je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-163">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="cd2cc-164">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)trvá pořadí polí a sloučí je do jednoho pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-164">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="cd2cc-165">Následující kód ukazuje `Array.concat`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-165">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="cd2cc-166">Výstup předchozí kód je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-166">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="cd2cc-167">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)provede logickou podmínky a vygeneruje nové pole, která obsahuje pouze elementy ze vstupní pole, pro kterou je podmínka vyhodnocena jako true.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-167">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="cd2cc-168">Následující kód ukazuje `Array.filter`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-168">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="cd2cc-169">Výstup předchozí kód je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-169">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="cd2cc-170">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)vygeneruje nové pole obrácení směru existující pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-170">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="cd2cc-171">Následující kód ukazuje `Array.rev`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-171">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

<span data-ttu-id="cd2cc-172">Výstup předchozí kód je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-172">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="cd2cc-173">Snadno můžete kombinovat funkce v modulu pole, které transformace pole pomocí operátor kanálu (`|>`), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-173">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="cd2cc-174">Výstup</span><span class="sxs-lookup"><span data-stu-id="cd2cc-174">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="cd2cc-175">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-175">Multidimensional Arrays</span></span>

<span data-ttu-id="cd2cc-176">Multidimenzionální pole lze vytvořit, ale neexistuje žádné syntaxe pro zápis literálu multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-176">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="cd2cc-177">Použití operátoru [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) pro vytvoření pole z pořadí pořadí prvků pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-177">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="cd2cc-178">Pořadí, může být pole nebo seznamu literály.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-178">The sequences can be array or list literals.</span></span> <span data-ttu-id="cd2cc-179">Například následující kód vytvoří dvourozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-179">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="cd2cc-180">Můžete také použít funkci [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) k chybě při inicializaci pole dvou dimenzí a podobné funkce jsou k dispozici pro pole tři až čtyři dimenzí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-180">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="cd2cc-181">Tyto funkce trvat funkci, která se používá k vytvoření elementy.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-181">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="cd2cc-182">Chcete-li vytvořit dvourozměrná pole, která obsahuje elementy nastavený na počáteční hodnotu místo zadání funkci, použijte [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) funkce, která je také k dispozici pro maticových až čtyři dimenze.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-182">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="cd2cc-183">Následující příklad kódu nejprve ukazuje, jak vytvořit pole polí, které obsahují požadované prvky a pak použije `Array2D.init` ke generování dvourozměrná požadované pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-183">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="cd2cc-184">Podporuje se pole indexování a řezů syntaxe pro pole až pořadí 4.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-184">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="cd2cc-185">Když zadáte indexu v více dimenzí, použijete čárkami k oddělení indexy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-185">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]
    
<span data-ttu-id="cd2cc-186">Typ dvourozměrná pole zapisuje jako `<type>[,]` (například `int[,]`, `double[,]`), a typ trojrozměrné je zapsána jako `<type>[,,]`, a tak dále pro pole vyšší dimenzí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-186">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="cd2cc-187">Jenom podmnožinu funkcí, které jsou k dispozici pro jednorozměrná pole je také k dispozici pro vícerozměrná pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-187">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="cd2cc-188">Další informace najdete v tématu [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), a [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-188">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="cd2cc-189">Pole segmentování a vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-189">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="cd2cc-190">V dvojrozměrném poli (matice), můžete rozbalit dílčí matice zadáním rozsahy a pomocí zástupného znaku (`*`) znak, který má určit celé řádky a sloupce.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-190">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

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

<span data-ttu-id="cd2cc-191">Od verze F # 3.1 můžete rozložit multidimenzionálního pole na subarrays dimenze stejné nebo nižší.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-191">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="cd2cc-192">Například můžete získat vektor od matice zadáním jednoho řádku nebo sloupec.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-192">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="cd2cc-193">Můžete použít při vytváření řezů syntaxe pro typy, které implementaci operátory pro přístup ke elementu a přetížený `GetSlice` metody.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-193">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="cd2cc-194">Například následující kód vytvoří matice typ, který zabalí pole 2D F #, implementuje vlastnosti položky poskytovat podporu pro indexování pole a implementuje tři verze `GetSlice`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-194">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="cd2cc-195">Pokud tento kód můžete použít jako šablonu pro vaše typy matice, můžete řezů operace, které tato část popisuje.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-195">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="cd2cc-196">Logická hodnota funkce na pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-196">Boolean Functions on Arrays</span></span>

<span data-ttu-id="cd2cc-197">Funkce [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) a [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) testování elementy v jedno nebo dvě pole, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-197">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="cd2cc-198">Tyto funkce přijmout funkci test a vrátit `true` Pokud je element (nebo dvojici element pro `Array.exists2`), splňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-198">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="cd2cc-199">Následující kód ukazuje použití `Array.exists` a `Array.exists2`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-199">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="cd2cc-200">V těchto příkladech vytvářejí nové funkce použití pouze jednoho z argumentů, v těchto případech argument funkce.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-200">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="cd2cc-201">Výstup předchozí kód je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-201">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="cd2cc-202">Podobně funkce [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testy pole k určení, zda každý element splňuje podmínku logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-202">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="cd2cc-203">Variaci [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) provede stejnou akci pomocí logická funkce, která zahrnuje elementy dvě pole stejné délky.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-203">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="cd2cc-204">Následující kód ukazuje použití těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-204">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="cd2cc-205">Výstup těchto příkladech je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-205">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="cd2cc-206">Hledání pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-206">Searching Arrays</span></span>

<span data-ttu-id="cd2cc-207">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)přebere logická funkce a vrátí první prvek, pro kterou vrátí funkce `true`, nebo vyvolá <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> Pokud nebyl nalezen žádný prvek, který splňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-207">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="cd2cc-208">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)je třeba `Array.find`, s tím rozdílem, že vrátí index prvku místo elementu samotného.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-208">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="cd2cc-209">Následující kód používá `Array.find` a `Array.findIndex` vyhledejte číslo, které je přesně čtvercový i ideální datové krychle.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-209">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="cd2cc-210">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-210">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="cd2cc-211">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)je třeba `Array.find`kromě toho, že její výsledek je typ možnost, a vrátí `None` Pokud nebyl nalezen žádný prvek.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-211">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="cd2cc-212">`Array.tryFind`slouží místo `Array.find` Pokud si nejste jisti, zda je v poli odpovídající element.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-212">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="cd2cc-213">Podobně [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) jako [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) s tím rozdílem, že typ možnost je návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-213">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="cd2cc-214">Pokud nebyl nalezen žádný prvek, je možnost `None`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-214">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="cd2cc-215">Následující kód ukazuje použití `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-215">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="cd2cc-216">Tento kód závisí na předchozí kód.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-216">This code depends on the previous code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="cd2cc-217">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-217">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="cd2cc-218">Použití [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) když potřebujete transformace elementu kromě najít.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-218">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="cd2cc-219">Výsledkem je první prvek, pro kterou vrátí funkce transformovaného elementu jako hodnotu možnosti nebo `None` Pokud nebyl nalezen žádný takový prvek.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-219">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="cd2cc-220">Následující kód ukazuje použití `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-220">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="cd2cc-221">V takovém případě místo výrazu lambda, jsou definovány několik místní pomocných funkcí můžete zjednodušit kód.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-221">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="cd2cc-222">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-222">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="cd2cc-223">Provádění výpočtů na pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-223">Performing Computations on Arrays</span></span>

<span data-ttu-id="cd2cc-224">[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) Funkce vrátí průměrnou hodnotu každý prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-224">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="cd2cc-225">Je omezený na element typy, které podporují přesný dělení celé číslo, včetně plovoucí typy bodů, ale není integrální typy.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-225">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="cd2cc-226">[ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) Funkce vrátí průměrnou hodnotu výsledky volání funkce pro každý element.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-226">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="cd2cc-227">Pro pole integrální typu, můžete použít `Array.averageBy` a mít funkci převést každý element na plovoucí typu pro výpočet bodu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-227">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="cd2cc-228">Použití [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) nebo [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) získat maximální nebo minimální elementu, pokud ji podporuje typ elementu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-228">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="cd2cc-229">Podobně [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) a [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) povolit funkci nejprve provést, případně k transformaci na typ, který podporuje porovnání.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-229">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="cd2cc-230">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)Přidá elementy pole, a [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) volá funkci pro každý element a přidá výsledky společně.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-230">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="cd2cc-231">Chcete-li spustit funkci na každý prvek v poli bez ukládání vrácené hodnoty, použijte [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-231">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="cd2cc-232">Pro funkci zahrnující dvěma poli stejnou délku, použijte [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-232">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="cd2cc-233">Pokud potřebujete ponechat pole výsledky funkce, použijte [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) nebo [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), který funguje na dvě pole v čase.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-233">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="cd2cc-234">Variace [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) a [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) povolit index prvku podílet výpočet, platí také pro [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) a [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-234">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="cd2cc-235">Funkce [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), a [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) provést algoritmy, které zahrnují všechny elementy pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-235">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="cd2cc-236">Podobně variace [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) a [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) provádět výpočty na dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-236">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="cd2cc-237">Tyto funkce pro provádění výpočtů odpovídají funkce se stejným názvem v [modul seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-237">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="cd2cc-238">Příklady použití najdete v tématu [uvádí](lists.md).</span><span class="sxs-lookup"><span data-stu-id="cd2cc-238">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="cd2cc-239">Úprava pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-239">Modifying Arrays</span></span>

<span data-ttu-id="cd2cc-240">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)element se nastaví na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-240">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="cd2cc-241">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)Nastaví rozsah elementů v matici zadanou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-241">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="cd2cc-242">Následující kód představuje příklad `Array.fill`.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-242">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="cd2cc-243">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-243">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="cd2cc-244">Můžete použít [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) zkopírovat část jednoho pole ke druhému.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-244">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="cd2cc-245">Převod na a z dalších typů</span><span class="sxs-lookup"><span data-stu-id="cd2cc-245">Converting to and from Other Types</span></span>

<span data-ttu-id="cd2cc-246">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)Vytvoří pole ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-246">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="cd2cc-247">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)Vytvoří pole z sekvenci.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-247">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="cd2cc-248">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)a [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) převést na tyto typy kolekcí z typ pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-248">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="cd2cc-249">Řazení polí</span><span class="sxs-lookup"><span data-stu-id="cd2cc-249">Sorting Arrays</span></span>

<span data-ttu-id="cd2cc-250">Použití [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) seřadit pole můžete použít funkci obecné porovnání.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-250">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="cd2cc-251">Použití [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) k určení funkci, která generuje hodnotu, označuje jako *klíč*pro použití funkce obecné porovnání na klíč.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-251">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="cd2cc-252">Použití [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) Pokud byste chtěli poskytnout vlastní porovnání funkce.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-252">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="cd2cc-253">`Array.sort`, `Array.sortBy`, a `Array.sortWith` všechny vrátí seřazené pole jako nové pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-253">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="cd2cc-254">Variace [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), a [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) upravit existující pole místo vrací nový.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-254">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="cd2cc-255">Pole a řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="cd2cc-255">Arrays and Tuples</span></span>

<span data-ttu-id="cd2cc-256">Funkce [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) a [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) převést pole párů řazené kolekce členů řazených kolekcí členů polí a naopak.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-256">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="cd2cc-257">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)a [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) jsou podobné, s tím rozdílem, že fungují s řazenými kolekcemi členů z uvedených položek nebo řazené kolekce členů tří polí.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-257">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="cd2cc-258">Paralelní výpočty na pole</span><span class="sxs-lookup"><span data-stu-id="cd2cc-258">Parallel Computations on Arrays</span></span>

<span data-ttu-id="cd2cc-259">Modul [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) obsahuje funkce pro provádění paralelní výpočty na pole.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-259">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="cd2cc-260">Tento modul není k dispozici v aplikacích, které cílové verze rozhraní .NET Framework starší než verze 4.</span><span class="sxs-lookup"><span data-stu-id="cd2cc-260">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="cd2cc-261">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd2cc-261">See Also</span></span>
[<span data-ttu-id="cd2cc-262">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="cd2cc-262">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="cd2cc-263">F #. Typy</span><span class="sxs-lookup"><span data-stu-id="cd2cc-263">F#; Types</span></span>](fsharp-types.md)
