---
title: Pole (F#)
description: 'Zjistěte, jak vytvořit a používání polí v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 27b73efc900ac2efc813fe66f81baa2e9ae1e843
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46697968"
---
# <a name="arrays"></a><span data-ttu-id="bef62-103">Pole</span><span class="sxs-lookup"><span data-stu-id="bef62-103">Arrays</span></span>

> [!NOTE]
<span data-ttu-id="bef62-104">Odkaz rozhraní API se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="bef62-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="bef62-105">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="bef62-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="bef62-106">Pole jsou pevné velikosti, založený na nule, proměnlivé kolekce po sobě jdoucích datové prvky, které jsou všechny stejného typu.</span><span class="sxs-lookup"><span data-stu-id="bef62-106">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="bef62-107">Tvorba polí</span><span class="sxs-lookup"><span data-stu-id="bef62-107">Creating Arrays</span></span>

<span data-ttu-id="bef62-108">Pole lze vytvořit několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="bef62-108">You can create arrays in several ways.</span></span> <span data-ttu-id="bef62-109">Malé pole můžete vytvořit uvedením po sobě následujících hodnot mezi `[|` a `|]` a oddělené středníkem, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bef62-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="bef62-110">Každý prvek lze také umístit na samostatný řádek, ve kterém je volitelný případ oddělovač středník.</span><span class="sxs-lookup"><span data-stu-id="bef62-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="bef62-111">Typ prvků pole je odvozen z použitých literál a musí být konzistentní vzhledem k aplikacím.</span><span class="sxs-lookup"><span data-stu-id="bef62-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="bef62-112">Následující kód způsobí chybu, protože 1.0 je plovoucí desetinnou čárkou a 2 a 3 jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="bef62-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="bef62-113">Sekvence výrazů můžete použít také k vytvoření polí.</span><span class="sxs-lookup"><span data-stu-id="bef62-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="bef62-114">Tady je příklad, který vytvoří pole druhých mocnin celých čísel od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="bef62-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="bef62-115">K vytvoření pole, ve kterém jsou všechny prvky inicializovány na nulu, použijte `Array.zeroCreate`.</span><span class="sxs-lookup"><span data-stu-id="bef62-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a><span data-ttu-id="bef62-116">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="bef62-116">Accessing Elements</span></span>

<span data-ttu-id="bef62-117">Můžete přistupovat k prvkům pole pomocí operátoru tečka (`.`) a hranaté závorky (`[` a `]`).</span><span class="sxs-lookup"><span data-stu-id="bef62-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="bef62-118">Indexy pole začínají od 0.</span><span class="sxs-lookup"><span data-stu-id="bef62-118">Array indexes start at 0.</span></span>

<span data-ttu-id="bef62-119">Prvky pole můžete také přistupovat pomocí zápisu řezu, který umožňuje určit dílčí řadu pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="bef62-120">Příklady postupu zápisu řezu.</span><span class="sxs-lookup"><span data-stu-id="bef62-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="bef62-121">Při použití zápisu řezu je vytvořena nový kopie pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-121">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="bef62-122">Typy polí a moduly</span><span class="sxs-lookup"><span data-stu-id="bef62-122">Array Types and Modules</span></span>

<span data-ttu-id="bef62-123">Typ všech polí F # je typ rozhraní .NET Framework <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bef62-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bef62-124">Proto pole F # podporují všechny funkce dostupné v <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bef62-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bef62-125">Modul knihovny [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) podporuje operace pro jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="bef62-126">Moduly `Array2D`, `Array3D`, a `Array4D` obsahují funkce, které podporují operace pro pole dvou, tří a čtyř dimenzí, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bef62-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="bef62-127">Můžete vytvořit pole řádu větší než čtyři pomocí <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bef62-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="bef62-128">Jednoduché funkce</span><span class="sxs-lookup"><span data-stu-id="bef62-128">Simple Functions</span></span>

<span data-ttu-id="bef62-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) Získá element.</span><span class="sxs-lookup"><span data-stu-id="bef62-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="bef62-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) Udává délku pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="bef62-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) nastaví element na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bef62-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="bef62-132">Následující příklad kódu ukazuje použití těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="bef62-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="bef62-133">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="bef62-133">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="bef62-134">Funkce, které vytvářejí pole</span><span class="sxs-lookup"><span data-stu-id="bef62-134">Functions That Create Arrays</span></span>

<span data-ttu-id="bef62-135">Několik funkcí tvoří pole bez nutnosti existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="bef62-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) Vytvoří nové pole, která neobsahuje žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="bef62-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="bef62-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) Vytvoří pole určené velikosti a nastaví všechny prvky na zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bef62-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="bef62-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) Vytvoří pole s danou dimenzí a funkce pro generování prvků.</span><span class="sxs-lookup"><span data-stu-id="bef62-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="bef62-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) Vytvoří pole, ve kterém jsou všechny prvky inicializovány na nulovou hodnotu pro typ pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="bef62-140">Následující kód demonstruje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="bef62-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="bef62-141">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="bef62-141">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="bef62-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) Vytvoří nové pole obsahující prvky, které jsou zkopírovány z existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="bef62-143">Všimněte si, že kopie je Mělká, což znamená, že pokud typ elementu je typem odkazu, je zkopírován pouze odkaz, nikoli základní objekt.</span><span class="sxs-lookup"><span data-stu-id="bef62-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="bef62-144">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="bef62-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="bef62-145">Výstup předcházejícího kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="bef62-145">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="bef62-146">Řetězec `Test1` se zobrazuje jenom v prvním poli, protože operace vytváření nového elementu přepíše odkaz v `firstArray` , ale nemá vliv na původní odkaz na prázdný řetězec, který se stále nachází `secondArray`.</span><span class="sxs-lookup"><span data-stu-id="bef62-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="bef62-147">Řetězec `Test2` se zobrazuje v obou polích, protože `Insert` operace <xref:System.Text.StringBuilder?displayProperty=nameWithType> typu ovlivňuje základní <xref:System.Text.StringBuilder?displayProperty=nameWithType> objekt, který se odkazuje v obou polích.</span><span class="sxs-lookup"><span data-stu-id="bef62-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="bef62-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generuje nové pole z podrozsahu pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="bef62-149">Zadejte dílčí sadu poskytnutím počáteční index a délka.</span><span class="sxs-lookup"><span data-stu-id="bef62-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="bef62-150">Následující kód demonstruje použití `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="bef62-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="bef62-151">Výstup ukazuje, že podpole začíná prvkem 5 a obsahuje 10 prvků.</span><span class="sxs-lookup"><span data-stu-id="bef62-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
<span data-ttu-id="bef62-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) Vytvoří nové pole kombinací dvou existujících polí.</span><span class="sxs-lookup"><span data-stu-id="bef62-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="bef62-153">Následující kód ukazuje **Array.append**.</span><span class="sxs-lookup"><span data-stu-id="bef62-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="bef62-154">Výstup předcházejícího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bef62-154">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="bef62-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) Vybere prvky pole pro zahrnutí do nového pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="bef62-156">Následující kód ukazuje `Array.choose`.</span><span class="sxs-lookup"><span data-stu-id="bef62-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="bef62-157">Všimněte si, že typ prvku pole nemusí odpovídat typu hodnoty vrácené v typu možnosti.</span><span class="sxs-lookup"><span data-stu-id="bef62-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="bef62-158">V tomto příkladu je typ prvku `int` a možnost je výsledek polynomické funkce `elem*elem - 1`, jako plovoucí číslo bodu.</span><span class="sxs-lookup"><span data-stu-id="bef62-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="bef62-159">Výstup předcházejícího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bef62-159">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="bef62-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) Spustí určenou funkci na každém elementu pole existujícího pole a poté shromáždí elementy generované funkcí a zkombinuje je do nového pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="bef62-161">Následující kód ukazuje `Array.collect`.</span><span class="sxs-lookup"><span data-stu-id="bef62-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="bef62-162">Výstup předcházejícího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bef62-162">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="bef62-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) přebírá pořadí polí a kombinuje je do jediného pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="bef62-164">Následující kód ukazuje `Array.concat`.</span><span class="sxs-lookup"><span data-stu-id="bef62-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="bef62-165">Výstup předcházejícího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bef62-165">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="bef62-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) převezme logickou podmínku funkce a generuje nové pole, která obsahuje pouze elementy z vstupního pole, pro které je podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="bef62-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="bef62-167">Následující kód ukazuje `Array.filter`.</span><span class="sxs-lookup"><span data-stu-id="bef62-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="bef62-168">Výstup předcházejícího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bef62-168">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="bef62-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generuje nové pole přehozením pořadí existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="bef62-170">Následující kód ukazuje `Array.rev`.</span><span class="sxs-lookup"><span data-stu-id="bef62-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

<span data-ttu-id="bef62-171">Výstup předcházejícího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bef62-171">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="bef62-172">Můžete snadno kombinovat funkce v modulu pole, které transformují pole pomocí operátoru kanálu (`|>`), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="bef62-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="bef62-173">Výstup je</span><span class="sxs-lookup"><span data-stu-id="bef62-173">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="bef62-174">Vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="bef62-174">Multidimensional Arrays</span></span>

<span data-ttu-id="bef62-175">Vícedimenzionální pole mohou být vytvořena, ale neexistuje žádná syntaxe zápisu vícedimenzionálního literálu pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="bef62-176">Použití operátoru [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) k vytvoření pole ze sekvence sekvencí elementů pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="bef62-177">Sekvence může být pole nebo literály seznamu.</span><span class="sxs-lookup"><span data-stu-id="bef62-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="bef62-178">Například následující kód vytvoří dvourozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="bef62-179">Můžete také použít funkci [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) k inicializaci pole dvou dimenzí a podobné funkce jsou k dispozici pro pole třemi až čtyřmi dimenzemi.</span><span class="sxs-lookup"><span data-stu-id="bef62-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="bef62-180">Tyto funkce přebírají funkci, která se používá k vytváření elementů.</span><span class="sxs-lookup"><span data-stu-id="bef62-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="bef62-181">Pokud chcete vytvořit dvojrozměrné pole obsahující elementy nastavené na počáteční hodnotu místo určení funkce, použijte [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) funkce, která je také k dispozici pro pole až do čtyř dimenzí.</span><span class="sxs-lookup"><span data-stu-id="bef62-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="bef62-182">Následující příklad kódu nejprve ukazuje, jak vytvořit pole obsahující požadované prvky a potom použije `Array2D.init` k vygenerování požadovaného dvourozměrného pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="bef62-183">Pole indexování a plátkování syntaxe jsou podporovány pro pole do pořadí 4.</span><span class="sxs-lookup"><span data-stu-id="bef62-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="bef62-184">Při zadávání indexu ve více dimenzích používáte čárky k oddělení indexů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="bef62-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="bef62-185">Typ dvourozměrného pole je zapsán jako `<type>[,]` (například `int[,]`, `double[,]`), a typ trojrozměrného pole je zapsán jako `<type>[,,]`, a tak dále pro pole vyšších rozměrů.</span><span class="sxs-lookup"><span data-stu-id="bef62-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="bef62-186">Pouze podmnožinu funkcí, které jsou k dispozici pro jednorozměrné pole je také k dispozici pro vícedimenzionální pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="bef62-187">Další informace najdete v tématu [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), a [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="bef62-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="bef62-188">Řezání rozšířené pole a vícedimenzionální pole</span><span class="sxs-lookup"><span data-stu-id="bef62-188">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="bef62-189">Dvourozměrné pole (matice) může extrahovat dílčí matici určením rozsahů a pomocí zástupného znaku (`*`) znak zadáním celého řádku nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="bef62-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

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

<span data-ttu-id="bef62-190">Od verze F # 3.1 můžete rozložit vícerozměrné pole na podpole stejné nebo nižší dimenze.</span><span class="sxs-lookup"><span data-stu-id="bef62-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="bef62-191">Vektor lze získat například z matice zadáním jednoho řádku nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="bef62-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="bef62-192">Můžete použít syntaxi dělení pro typy, které implementují operátory přístupu k elementu a přetížené `GetSlice` metody.</span><span class="sxs-lookup"><span data-stu-id="bef62-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="bef62-193">Například následující kód vytvoří typ matice, která zabalí 2D pole F #, implementuje vlastnost položky pro poskytnutí podpory pro indexování pole a implementuje tři verze `GetSlice`.</span><span class="sxs-lookup"><span data-stu-id="bef62-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="bef62-194">Pokud tento kód můžete použít jako šablonu pro vaše typy matice, můžete použít všechny operace řezů, které tato část popisuje.</span><span class="sxs-lookup"><span data-stu-id="bef62-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="bef62-195">Logické funkce pro pole</span><span class="sxs-lookup"><span data-stu-id="bef62-195">Boolean Functions on Arrays</span></span>

<span data-ttu-id="bef62-196">Funkce [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) a [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) testuje prvky v jednu nebo dvě pole, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="bef62-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="bef62-197">Tyto funkce provádějí funkci testu a vrátí `true` Pokud element (nebo dvojice elementů pro `Array.exists2`), splňující danou podmínku.</span><span class="sxs-lookup"><span data-stu-id="bef62-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="bef62-198">Následující kód demonstruje použití `Array.exists` a `Array.exists2`.</span><span class="sxs-lookup"><span data-stu-id="bef62-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="bef62-199">V těchto příkladech jsou nové funkce vytvořeny použitím pouze jednoho z argumentů v těchto případech argumentem funkce.</span><span class="sxs-lookup"><span data-stu-id="bef62-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="bef62-200">Výstup předcházejícího kódu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="bef62-200">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="bef62-201">Podobně funkce [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testuje pole a určuje, zda každý prvek splňuje logickou podmínku.</span><span class="sxs-lookup"><span data-stu-id="bef62-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="bef62-202">Změna [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) provede stejnou akci pomocí logické funkce, která zahrnuje elementy dvou polí stejné délky.</span><span class="sxs-lookup"><span data-stu-id="bef62-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="bef62-203">Následující kód ukazuje použití těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="bef62-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="bef62-204">Výstup pro tyto příklady je následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="bef62-204">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="bef62-205">Hledání v polích</span><span class="sxs-lookup"><span data-stu-id="bef62-205">Searching Arrays</span></span>

<span data-ttu-id="bef62-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) přebírá logickou funkci a vrátí první prvek, pro který funkce vrátí `true`, nebo vyvolává <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> Pokud není nalezen žádný element, který splňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="bef62-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="bef62-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) je třeba `Array.find`, s tím rozdílem, že vrátí index elementu namísto samotného elementu.</span><span class="sxs-lookup"><span data-stu-id="bef62-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="bef62-208">Následující kód používá `Array.find` a `Array.findIndex` vyhledejte číslo, které je dokonalý čtverec i dokonalá krychle.</span><span class="sxs-lookup"><span data-stu-id="bef62-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="bef62-209">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="bef62-209">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="bef62-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) je třeba `Array.find`, s tím rozdílem, že výsledek je typ možnosti a vrátí `None` Pokud není nalezen žádný element.</span><span class="sxs-lookup"><span data-stu-id="bef62-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="bef62-211">`Array.tryFind` by měl být použít namísto `Array.find` Pokud si nejste jisti, zda je odpovídající prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="bef62-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="bef62-212">Obdobně [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) je stejná jako [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) s tím rozdílem, že typ možnosti je vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bef62-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="bef62-213">Pokud není nalezen žádný element, je možnost `None`.</span><span class="sxs-lookup"><span data-stu-id="bef62-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="bef62-214">Následující kód demonstruje použití `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="bef62-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="bef62-215">Tento kód závisí na předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="bef62-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="bef62-216">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="bef62-216">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="bef62-217">Použití [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) když potřebujete transformovat element kromě vyhledání.</span><span class="sxs-lookup"><span data-stu-id="bef62-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="bef62-218">Výsledkem je první prvek, pro který funkce vrátí transformovaný prvek jako hodnotu možnosti, nebo `None` Pokud se nenajde žádný takový prvek.</span><span class="sxs-lookup"><span data-stu-id="bef62-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="bef62-219">Následující kód ukazuje použití `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="bef62-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="bef62-220">V tomto případě namísto výrazu lambda, jsou definovány několik místních pomocných funkcí pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="bef62-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="bef62-221">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="bef62-221">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="bef62-222">Provádění výpočtů v polích</span><span class="sxs-lookup"><span data-stu-id="bef62-222">Performing Computations on Arrays</span></span>

<span data-ttu-id="bef62-223">[ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) Funkce vrátí průměr z jednotlivých prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="bef62-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="bef62-224">Je omezena na typy prvků, které podporují přesné dělení celým číslem, které zahrnuje typy plovoucího bodu, ale ne integrální typy.</span><span class="sxs-lookup"><span data-stu-id="bef62-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="bef62-225">[ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) Funkce vrátí průměr z výsledků volání funkce na každý prvek.</span><span class="sxs-lookup"><span data-stu-id="bef62-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="bef62-226">Pro pole integrálního typu, můžete použít `Array.averageBy` a nechat funkce převést každý prvek na plovoucí typu pro výpočet bodu.</span><span class="sxs-lookup"><span data-stu-id="bef62-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="bef62-227">Použití [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) nebo [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) získat maximální nebo minimální element, pokud je typ elementu podporuje.</span><span class="sxs-lookup"><span data-stu-id="bef62-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="bef62-228">Obdobně [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) a [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) povolit funkce, který se spustí nejdříve, třeba tak, aby na typ, který podporuje porovnání.</span><span class="sxs-lookup"><span data-stu-id="bef62-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="bef62-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) Přidá prvky pole, a [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) volá funkci na každý element a přidá výsledky dohromady.</span><span class="sxs-lookup"><span data-stu-id="bef62-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="bef62-230">Chcete-li spustit funkci na každý prvek v poli bez uložení vrácených hodnot, použijte [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span><span class="sxs-lookup"><span data-stu-id="bef62-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="bef62-231">Pro funkci zahrnující dvě pole stejné délky, použijte [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span><span class="sxs-lookup"><span data-stu-id="bef62-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="bef62-232">Pokud potřebujete zachovat pole výsledků této funkce, použijte [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) nebo [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), jež pracuje na dvou polích najednou.</span><span class="sxs-lookup"><span data-stu-id="bef62-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="bef62-233">Variace [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) a [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) povolit indexu elementu do výpočtu, totéž platí pro [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) a [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span><span class="sxs-lookup"><span data-stu-id="bef62-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="bef62-234">Funkce [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), a [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) spouští algoritmy, které se týkají všech prvků pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="bef62-235">Podobně variace [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) a [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) provádí výpočty na dvou polích.</span><span class="sxs-lookup"><span data-stu-id="bef62-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="bef62-236">Tyto funkce pro provádění výpočtů odpovídají funkcím se stejným názvem v [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="bef62-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="bef62-237">Příklady využití naleznete v tématu [uvádí](lists.md).</span><span class="sxs-lookup"><span data-stu-id="bef62-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="bef62-238">Změna polí</span><span class="sxs-lookup"><span data-stu-id="bef62-238">Modifying Arrays</span></span>

<span data-ttu-id="bef62-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) nastaví element na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bef62-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="bef62-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) Nastaví rozsah elementů v matici na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bef62-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="bef62-241">Následující kód obsahuje příklad `Array.fill`.</span><span class="sxs-lookup"><span data-stu-id="bef62-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="bef62-242">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="bef62-242">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="bef62-243">Můžete použít [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) ke kopírování dílčí sady jednoho pole ke druhému.</span><span class="sxs-lookup"><span data-stu-id="bef62-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="bef62-244">Převod na objekty Null a z jiných typů</span><span class="sxs-lookup"><span data-stu-id="bef62-244">Converting to and from Other Types</span></span>

<span data-ttu-id="bef62-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) Vytvoří pole ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="bef62-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="bef62-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) Vytvoří pole ze sekvence.</span><span class="sxs-lookup"><span data-stu-id="bef62-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="bef62-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) a [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) převést na tyto typy kolekcí z typu pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="bef62-248">Pole třídění</span><span class="sxs-lookup"><span data-stu-id="bef62-248">Sorting Arrays</span></span>

<span data-ttu-id="bef62-249">Použití [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) seřadit pole pomocí funkce obecného porovnání.</span><span class="sxs-lookup"><span data-stu-id="bef62-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="bef62-250">Použití [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) k určení funkce, která generuje hodnotu, označuje jako *klíč*, k uspořádání pomocí funkce obecného porovnání v klíči.</span><span class="sxs-lookup"><span data-stu-id="bef62-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="bef62-251">Použití [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) Pokud byste chtěli poskytnout vlastní funkci porovnání.</span><span class="sxs-lookup"><span data-stu-id="bef62-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="bef62-252">`Array.sort`, `Array.sortBy`, a `Array.sortWith` všechny vrátí seřazené pole jako nové pole.</span><span class="sxs-lookup"><span data-stu-id="bef62-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="bef62-253">Variace [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), a [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) mění stávající pole místo vrácení nového.</span><span class="sxs-lookup"><span data-stu-id="bef62-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="bef62-254">Pole a n-tice</span><span class="sxs-lookup"><span data-stu-id="bef62-254">Arrays and Tuples</span></span>

<span data-ttu-id="bef62-255">Funkce [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) a [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) převádí pole párů n-tice pro n-tice polí a naopak.</span><span class="sxs-lookup"><span data-stu-id="bef62-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="bef62-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) a [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) jsou podobné s tím rozdílem, že pracují s n-tice tří prvků nebo n-tice tří polí.</span><span class="sxs-lookup"><span data-stu-id="bef62-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="bef62-257">Paralelní výpočty v polích</span><span class="sxs-lookup"><span data-stu-id="bef62-257">Parallel Computations on Arrays</span></span>

<span data-ttu-id="bef62-258">V modulu [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) obsahuje funkce pro provádění paralelních výpočtů v polích.</span><span class="sxs-lookup"><span data-stu-id="bef62-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="bef62-259">Tento modul není k dispozici v aplikacích, které cílové verze rozhraní .NET Framework starší než verze 4.</span><span class="sxs-lookup"><span data-stu-id="bef62-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="bef62-260">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bef62-260">See also</span></span>

- [<span data-ttu-id="bef62-261">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="bef62-261">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="bef62-262">F #. Typy</span><span class="sxs-lookup"><span data-stu-id="bef62-262">F#; Types</span></span>](fsharp-types.md)
