---
title: Pole
description: 'Naučte se vytvářet a používat pole v programovacím jazyce F #.'
ms.date: 08/13/2020
ms.openlocfilehash: 93d524046ff93a7f1b04e72d580d9d0e1360ba0b
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558878"
---
# <a name="arrays"></a><span data-ttu-id="cf23c-103">Pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-103">Arrays</span></span>

<span data-ttu-id="cf23c-104">Pole jsou pevná velikost, založená na nule, proměnlivé kolekce po sobě jdoucích datových prvků, které jsou všechny stejného typu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="cf23c-105">Vytváření polí</span><span class="sxs-lookup"><span data-stu-id="cf23c-105">Create arrays</span></span>

<span data-ttu-id="cf23c-106">Pole můžete vytvořit několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="cf23c-106">You can create arrays in several ways.</span></span> <span data-ttu-id="cf23c-107">Malé pole můžete vytvořit tak, že zobrazíte po sobě jdoucí hodnoty mezi `[|` a `|]` a oddělené středníky, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="cf23c-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="cf23c-108">Každý prvek lze také umístit na samostatný řádek, v takovém případě je oddělovač středník volitelný.</span><span class="sxs-lookup"><span data-stu-id="cf23c-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="cf23c-109">Typ prvků pole je odvozen z používaných literálů a musí být konzistentní.</span><span class="sxs-lookup"><span data-stu-id="cf23c-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="cf23c-110">Následující kód způsobí chybu, protože 1,0 je float a 2 a 3 jsou celá čísla.</span><span class="sxs-lookup"><span data-stu-id="cf23c-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="cf23c-111">Výrazy sekvence lze také použít k vytvoření polí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="cf23c-112">Následuje příklad, který vytvoří pole čtverců celých čísel od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="cf23c-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="cf23c-113">Chcete-li vytvořit pole, ve kterém jsou všechny prvky inicializovány na nulu, použijte `Array.zeroCreate` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="cf23c-114">Přístup k prvkům</span><span class="sxs-lookup"><span data-stu-id="cf23c-114">Access elements</span></span>

<span data-ttu-id="cf23c-115">K prvkům pole můžete přistupovat pomocí operátoru tečka ( `.` ) a závorek ( `[` a `]` ).</span><span class="sxs-lookup"><span data-stu-id="cf23c-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="cf23c-116">Indexy pole začínají na 0.</span><span class="sxs-lookup"><span data-stu-id="cf23c-116">Array indexes start at 0.</span></span>

<span data-ttu-id="cf23c-117">K prvkům pole můžete přistupovat také pomocí zápisu řezů, který umožňuje zadat dílčí rozsah pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="cf23c-118">Následují příklady zápisu řezů.</span><span class="sxs-lookup"><span data-stu-id="cf23c-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="cf23c-119">Při použití notace řezu se vytvoří nová kopie pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="cf23c-120">Typy polí a moduly</span><span class="sxs-lookup"><span data-stu-id="cf23c-120">Array types and modules</span></span>

<span data-ttu-id="cf23c-121">Typ všech polí jazyka F # je .NET Framework typ <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cf23c-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cf23c-122">Proto pole jazyka F # podporují všechny funkce, které jsou k dispozici v <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cf23c-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="cf23c-123">[ `Array` Modul](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) podporuje operace pro jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="cf23c-124">Moduly `Array2D` , `Array3D` a `Array4D` obsahují funkce, které podporují operace s poli dvou, tří a čtyř dimenzí v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="cf23c-125">Pomocí můžete vytvořit pole s pořadím větším než čtyři <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cf23c-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="cf23c-126">Jednoduché funkce</span><span class="sxs-lookup"><span data-stu-id="cf23c-126">Simple functions</span></span>

<span data-ttu-id="cf23c-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) Získá element.</span><span class="sxs-lookup"><span data-stu-id="cf23c-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="cf23c-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) poskytuje délku pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="cf23c-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) Nastaví element na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="cf23c-130">Následující příklad kódu ukazuje použití těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="cf23c-131">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="cf23c-132">Funkce, které vytvářejí pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-132">Functions that create arrays</span></span>

<span data-ttu-id="cf23c-133">Několik funkcí vytváří pole bez nutnosti existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="cf23c-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) Vytvoří nové pole, které neobsahuje žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="cf23c-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="cf23c-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) Vytvoří pole zadané velikosti a nastaví všechny prvky na zadané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cf23c-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="cf23c-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) Vytvoří pole s ohledem na dimenzi a funkci pro generování prvků.</span><span class="sxs-lookup"><span data-stu-id="cf23c-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="cf23c-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) Vytvoří pole, ve kterém jsou všechny prvky inicializovány na nulovou hodnotu pro typ pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="cf23c-138">Následující kód znázorňuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="cf23c-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="cf23c-139">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="cf23c-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) Vytvoří nové pole, které obsahuje prvky, které jsou zkopírovány z existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="cf23c-141">Všimněte si, že kopie je bez podstruktury, což znamená, že pokud je typ elementu odkazový typ, zkopíruje se pouze odkaz, nikoli podkladový objekt.</span><span class="sxs-lookup"><span data-stu-id="cf23c-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="cf23c-142">Následující příklad kódu to dokládá.</span><span class="sxs-lookup"><span data-stu-id="cf23c-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="cf23c-143">Výstup předcházejícího kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="cf23c-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="cf23c-144">Řetězec `Test1` se zobrazí pouze v prvním poli, protože operace vytvoření nového elementu přepíše odkaz v, `firstArray` ale nemá vliv na původní odkaz na prázdný řetězec, který je stále přítomen v `secondArray` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="cf23c-145">Řetězec `Test2` se zobrazí v obou polích, protože `Insert` operace s <xref:System.Text.StringBuilder?displayProperty=nameWithType> typem ovlivňuje podkladový <xref:System.Text.StringBuilder?displayProperty=nameWithType> objekt, na který je odkazováno v obou polích.</span><span class="sxs-lookup"><span data-stu-id="cf23c-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="cf23c-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) vygeneruje nové pole z dílčího rozsahu pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="cf23c-147">Dílčí rozsah můžete zadat zadáním počátečního indexu a délky.</span><span class="sxs-lookup"><span data-stu-id="cf23c-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="cf23c-148">Následující kód demonstruje použití `Array.sub` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="cf23c-149">Výstup ukazuje, že podpole začíná na elementu 5 a obsahuje 10 prvků.</span><span class="sxs-lookup"><span data-stu-id="cf23c-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="cf23c-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) Vytvoří nové pole kombinováním dvou existujících polí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="cf23c-151">Následující kód demonstruje **pole Array. Append**.</span><span class="sxs-lookup"><span data-stu-id="cf23c-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="cf23c-152">Výstup předcházejícího kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="cf23c-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) vybere prvky pole, které mají být zahrnuty do nového pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="cf23c-154">Následující kód demonstruje `Array.choose` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="cf23c-155">Všimněte si, že typ elementu pole nemusí odpovídat typu hodnoty vrácené v typu možnosti.</span><span class="sxs-lookup"><span data-stu-id="cf23c-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="cf23c-156">V tomto příkladu je typ prvku `int` a možnost je výsledkem polynomické funkce, `elem*elem - 1` jako číslo s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="cf23c-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="cf23c-157">Výstup předcházejícího kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="cf23c-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) Spustí zadanou funkci u každého prvku pole existujícího pole a poté shromáždí prvky vygenerované funkcí a zkombinuje je do nového pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="cf23c-159">Následující kód demonstruje `Array.collect` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="cf23c-160">Výstup předcházejícího kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="cf23c-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) vezme sekvenci polí a zkombinuje je do jednoho pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="cf23c-162">Následující kód demonstruje `Array.concat` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="cf23c-163">Výstup předcházejícího kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="cf23c-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) používá funkci logické podmínky a generuje nové pole, které obsahuje pouze prvky ze vstupního pole, pro které je podmínka pravdivá.</span><span class="sxs-lookup"><span data-stu-id="cf23c-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="cf23c-165">Následující kód demonstruje `Array.filter` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="cf23c-166">Výstup předcházejícího kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="cf23c-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) vygeneruje nové pole obrácením pořadí existujícího pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="cf23c-168">Následující kód demonstruje `Array.rev` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="cf23c-169">Výstup předcházejícího kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="cf23c-170">Můžete snadno kombinovat funkce v modulu Array, které transformují pole pomocí operátoru kanálu ( `|>` ), jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="cf23c-171">Výstup je</span><span class="sxs-lookup"><span data-stu-id="cf23c-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="cf23c-172">Multidimenzionální pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-172">Multidimensional arrays</span></span>

<span data-ttu-id="cf23c-173">Multidimenzionální pole lze vytvořit, ale neexistuje žádná syntaxe pro zápis literálu multidimenzionálního pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="cf23c-174">Operátor lze použít [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) k vytvoření pole z sekvence sekvencí prvků pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="cf23c-175">Sekvence mohou být literály pole nebo seznamu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="cf23c-176">Například následující kód vytvoří dvourozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="cf23c-177">Funkci lze také použít [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) k inicializaci polí dvou dimenzí a podobné funkce jsou k dispozici pro pole tří a čtyř dimenzí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="cf23c-178">Tyto funkce přebírají funkci, která se používá k vytvoření prvků.</span><span class="sxs-lookup"><span data-stu-id="cf23c-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="cf23c-179">Chcete-li vytvořit dvourozměrné pole obsahující prvky nastavené na počáteční hodnotu namísto určení funkce, použijte [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) funkci, která je také k dispozici pro pole až do čtyř dimenzí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="cf23c-180">Následující příklad kódu ukazuje, jak vytvořit pole polí obsahující požadované prvky a poté používá `Array2D.init` ke generování požadovaného dvojrozměrného pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="cf23c-181">Indexace pole a syntaxe průřezu se podporují pro pole až do pořadí 4.</span><span class="sxs-lookup"><span data-stu-id="cf23c-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="cf23c-182">Při zadávání indexu ve více dimenzích použijte čárky k oddělení indexů, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="cf23c-183">Typ dvojrozměrného pole je zapsán jako `<type>[,]` (například `int[,]` , `double[,]` ) a typ trojrozměrného pole je zapsán jako `<type>[,,]` a tak dále pro pole vyšších dimenzí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="cf23c-184">Pro multidimenzionální pole je k dispozici také pouze podmnožina funkcí dostupných pro jednorozměrné pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="cf23c-185">Řezy pole a multidimenzionální pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="cf23c-186">V dvojrozměrném poli (matici) můžete extrahovat dílčí matici zadáním rozsahů a použitím `*` znaku zástupného znaku () pro zadání celých řádků nebo sloupců.</span><span class="sxs-lookup"><span data-stu-id="cf23c-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

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

<span data-ttu-id="cf23c-187">Multidimenzionální pole lze rozložit na podpole stejné nebo nižší dimenze.</span><span class="sxs-lookup"><span data-stu-id="cf23c-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="cf23c-188">Můžete například získat vektor z matice zadáním jednoho řádku nebo sloupce.</span><span class="sxs-lookup"><span data-stu-id="cf23c-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="cf23c-189">Tuto syntaxi průřezů lze použít pro typy, které implementují operátory přístupu k prvkům a přetížené `GetSlice` metody.</span><span class="sxs-lookup"><span data-stu-id="cf23c-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="cf23c-190">Například následující kód vytvoří typ matice, který zabalí 2D pole F #, implementuje vlastnost Item pro poskytnutí podpory pro indexování pole a implementuje tři verze systému `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="cf23c-191">Pokud tento kód můžete použít jako šablonu pro typy matrice, můžete použít všechny operace řezů, které tato část popisuje.</span><span class="sxs-lookup"><span data-stu-id="cf23c-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="cf23c-192">Logické funkce pro pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-192">Boolean functions on arrays</span></span>

<span data-ttu-id="cf23c-193">Funkce [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) a [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) testovací prvky buď v jednom nebo dvou polích, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="cf23c-194">Tyto funkce přebírají funkci testu a vrátí `true` , pokud existuje element (nebo pár prvků pro `Array.exists2` ), který splňuje podmínky.</span><span class="sxs-lookup"><span data-stu-id="cf23c-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="cf23c-195">Následující kód demonstruje použití `Array.exists` a `Array.exists2` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="cf23c-196">V těchto příkladech jsou vytvořeny nové funkce použitím pouze jednoho z argumentů, v těchto případech argument funkce.</span><span class="sxs-lookup"><span data-stu-id="cf23c-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="cf23c-197">Výstup předcházejícího kódu je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="cf23c-198">Podobně funkce [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) testuje pole k určení, zda každý prvek splňuje logickou podmínku.</span><span class="sxs-lookup"><span data-stu-id="cf23c-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="cf23c-199">Variace má [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) stejnou věc pomocí logické funkce, která zahrnuje prvky dvou polí stejné délky.</span><span class="sxs-lookup"><span data-stu-id="cf23c-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="cf23c-200">Následující kód ilustruje použití těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="cf23c-201">Výstup pro tyto příklady je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="cf23c-202">Hledat pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-202">Search arrays</span></span>

<span data-ttu-id="cf23c-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) převezme logickou funkci a vrátí první prvek, pro který funkce vrací `true` , nebo vyvolá, <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> Pokud není nalezen žádný element, který by splňoval podmínky.</span><span class="sxs-lookup"><span data-stu-id="cf23c-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="cf23c-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) je jako `Array.find` , s tím rozdílem, že vrátí index elementu namísto samotného prvku.</span><span class="sxs-lookup"><span data-stu-id="cf23c-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="cf23c-205">Následující kód používá `Array.find` a `Array.findIndex` k vyhledání čísla, které je dokonalým čtvercem a dokonalým datovou krychlí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="cf23c-206">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="cf23c-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) je jako `Array.find` , s tím rozdílem, že jeho výsledek je typ možnosti a vrátí, `None` Pokud není nalezen žádný element.</span><span class="sxs-lookup"><span data-stu-id="cf23c-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="cf23c-208">`Array.tryFind` by měl být použit místo toho, `Array.find` když nevíte, zda je shodný prvek v poli.</span><span class="sxs-lookup"><span data-stu-id="cf23c-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="cf23c-209">Podobně [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) je podobný jako `Array.findIndex` s tím rozdílem, že typ možnosti je vrácená hodnota.</span><span class="sxs-lookup"><span data-stu-id="cf23c-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="cf23c-210">Pokud není nalezen žádný element, možnost je `None` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="cf23c-211">Následující kód demonstruje použití `Array.tryFind` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="cf23c-212">Tento kód závisí na předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="cf23c-213">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="cf23c-214">Použijte [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) v případě, že potřebujete transformovat prvek společně s jeho hledáním.</span><span class="sxs-lookup"><span data-stu-id="cf23c-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="cf23c-215">Výsledkem je první prvek, pro který funkce vrací transformovaný prvek jako hodnotu možnosti, nebo `None` Pokud žádný takový prvek nenajde.</span><span class="sxs-lookup"><span data-stu-id="cf23c-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="cf23c-216">Následující kód ukazuje použití `Array.tryPick` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="cf23c-217">V tomto případě namísto lambda výrazu je definováno několik místních pomocných funkcí pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="cf23c-218">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="cf23c-219">Provádění výpočtů u polí</span><span class="sxs-lookup"><span data-stu-id="cf23c-219">Perform computations on arrays</span></span>

<span data-ttu-id="cf23c-220">[`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average)Funkce vrátí průměr každého prvku v poli.</span><span class="sxs-lookup"><span data-stu-id="cf23c-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="cf23c-221">Je omezen na typy prvků, které podporují přesné dělení podle typu Integer, což zahrnuje typy plovoucí desetinné čárky, ale ne celočíselné typy.</span><span class="sxs-lookup"><span data-stu-id="cf23c-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="cf23c-222">[`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy)Funkce vrátí průměr výsledků volání funkce na každém elementu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="cf23c-223">Pro pole integrálního typu můžete použít `Array.averageBy` a mít funkci převést každý prvek na typ s plovoucí desetinnou čárkou pro výpočet.</span><span class="sxs-lookup"><span data-stu-id="cf23c-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="cf23c-224">Použijte [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) nebo [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) k získání maximálního nebo minimálního prvku, pokud jej typ elementu podporuje.</span><span class="sxs-lookup"><span data-stu-id="cf23c-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="cf23c-225">Podobně [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) a [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) umožněte, aby byla funkce provedena jako první, možná pro transformaci na typ, který podporuje porovnání.</span><span class="sxs-lookup"><span data-stu-id="cf23c-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="cf23c-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) Přidá prvky pole a [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) zavolá funkci na každý prvek a výsledky společně přidávají.</span><span class="sxs-lookup"><span data-stu-id="cf23c-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="cf23c-227">Chcete-li spustit funkci pro každý prvek v poli bez uložení vrácených hodnot, použijte [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) .</span><span class="sxs-lookup"><span data-stu-id="cf23c-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="cf23c-228">Pro funkci, která zahrnuje dvě pole stejné délky, použijte [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) .</span><span class="sxs-lookup"><span data-stu-id="cf23c-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="cf23c-229">Pokud také potřebujete zachovat pole výsledků funkce, použijte [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) nebo [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , který pracuje na dvou polích najednou.</span><span class="sxs-lookup"><span data-stu-id="cf23c-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="cf23c-230">Variace [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) a [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) umožňují, aby index elementu byl součástí výpočtu; totéž platí pro [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) a [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .</span><span class="sxs-lookup"><span data-stu-id="cf23c-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="cf23c-231">Funkce [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) ,,,, [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) a [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) spouštějí algoritmy, které zahrnují všechny prvky pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="cf23c-232">Podobně variace [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) a [`Array.foldBack2`](foldBack2) provádění výpočtů na dvou polích.</span><span class="sxs-lookup"><span data-stu-id="cf23c-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="cf23c-233">Tyto funkce pro provádění výpočtů odpovídají funkcím stejného názvu v [modulu seznamu](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="cf23c-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="cf23c-234">Příklady použití najdete v tématu [seznam](lists.md).</span><span class="sxs-lookup"><span data-stu-id="cf23c-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="cf23c-235">Upravit pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-235">Modify arrays</span></span>

<span data-ttu-id="cf23c-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) Nastaví element na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="cf23c-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) nastaví v poli rozsah prvků na zadanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="cf23c-238">Následující kód poskytuje příklad `Array.fill` .</span><span class="sxs-lookup"><span data-stu-id="cf23c-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="cf23c-239">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="cf23c-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="cf23c-240">Můžete použít [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) ke kopírování dílčí části jednoho pole do jiného pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="cf23c-241">Převod na jiné typy a z nich</span><span class="sxs-lookup"><span data-stu-id="cf23c-241">Convert to and from other types</span></span>

<span data-ttu-id="cf23c-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) Vytvoří pole ze seznamu.</span><span class="sxs-lookup"><span data-stu-id="cf23c-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="cf23c-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) Vytvoří pole z sekvence.</span><span class="sxs-lookup"><span data-stu-id="cf23c-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="cf23c-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) a [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) převeďte je na tyto typy kolekcí z typu pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="cf23c-245">Seřadit pole</span><span class="sxs-lookup"><span data-stu-id="cf23c-245">Sort arrays</span></span>

<span data-ttu-id="cf23c-246">Slouží [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) k řazení pole pomocí generické funkce porovnání.</span><span class="sxs-lookup"><span data-stu-id="cf23c-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="cf23c-247">Použijte [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) k určení funkce, která generuje hodnotu, která je označována jako *klíč*, k seřazení pomocí generické funkce porovnání na klíč.</span><span class="sxs-lookup"><span data-stu-id="cf23c-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="cf23c-248">Použijte, [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) Pokud chcete zadat vlastní srovnávací funkci.</span><span class="sxs-lookup"><span data-stu-id="cf23c-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="cf23c-249">`Array.sort`, `Array.sortBy` a `Array.sortWith` vrátí seřazené pole jako nové pole.</span><span class="sxs-lookup"><span data-stu-id="cf23c-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="cf23c-250">Variace [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) , [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) a [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) mění existující pole místo vrácení nového.</span><span class="sxs-lookup"><span data-stu-id="cf23c-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="cf23c-251">Pole a řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="cf23c-251">Arrays and tuples</span></span>

<span data-ttu-id="cf23c-252">Funkce [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) a [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) převádí pole párů řazené kolekce členů na řazené kolekce členů a naopak.</span><span class="sxs-lookup"><span data-stu-id="cf23c-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="cf23c-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) a [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) jsou podobné s tím rozdílem, že pracují s řazenými kolekcemi členů tří prvků nebo řazenými kolekcemi členů tří polí.</span><span class="sxs-lookup"><span data-stu-id="cf23c-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="cf23c-254">Paralelní výpočty u polí</span><span class="sxs-lookup"><span data-stu-id="cf23c-254">Parallel computations on arrays</span></span>

<span data-ttu-id="cf23c-255">Modul [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) obsahuje funkce pro provádění paralelních výpočtů v polích.</span><span class="sxs-lookup"><span data-stu-id="cf23c-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="cf23c-256">Tento modul není dostupný v aplikacích, které cílí na verze .NET Framework před verzí 4.</span><span class="sxs-lookup"><span data-stu-id="cf23c-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf23c-257">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf23c-257">See also</span></span>

- [<span data-ttu-id="cf23c-258">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="cf23c-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cf23c-259">Typy F#</span><span class="sxs-lookup"><span data-stu-id="cf23c-259">F# Types</span></span>](fsharp-types.md)
