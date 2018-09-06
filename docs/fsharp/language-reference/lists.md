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
# <a name="lists"></a><span data-ttu-id="f7bce-103">Seznamy</span><span class="sxs-lookup"><span data-stu-id="f7bce-103">Lists</span></span>

> [!NOTE]
<span data-ttu-id="f7bce-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="f7bce-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="f7bce-105">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="f7bce-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="f7bce-106">Seznam v jazyce F # je seřazený, neměnné řadu prvků stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-106">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="f7bce-107">K provádění základních operací v seznamech, použijte funkci v [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="f7bce-107">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="f7bce-108">Vytváření a inicializaci seznamy</span><span class="sxs-lookup"><span data-stu-id="f7bce-108">Creating and Initializing Lists</span></span>

<span data-ttu-id="f7bce-109">Můžete definovat seznam podle explicitně uvedete seznam rozložení elementů, oddělené středníky a uzavřený v hranatých závorkách a jak je znázorněno v následující řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="f7bce-110">Můžete také umístit zalomení mezi prvky, v takovém případě jsou volitelné středníky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="f7bce-111">Druhá syntaxe může způsobit čitelnější kód po delší dobu výrazy inicializace prvek nebo když chcete zahrnout komentář pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="f7bce-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="f7bce-112">Za normálních okolností všechny prvky seznamu musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="f7bce-113">Výjimkou je, že seznam, ve kterém jsou prvky uvedeny na základní typ může mít prvky, které jsou odvozené typy.</span><span class="sxs-lookup"><span data-stu-id="f7bce-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="f7bce-114">Proto je přijatelné, protože obě `Button` a `CheckBox` jsou odvozeny z `Control`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="f7bce-115">Můžete také definovat prvky seznamu pomocí rozsah indikovaný celých čísel oddělených operátor rozsahu (`..`), jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="f7bce-116">Pár uzavřenou do hranatých závorek není nic mezi nimi je zadaný prázdný seznam.</span><span class="sxs-lookup"><span data-stu-id="f7bce-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="f7bce-117">Můžete také použít výrazu pořadí k vytvoření seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="f7bce-118">Zobrazit [výrazech pořadí](sequences.md#sequence-expressions) Další informace.</span><span class="sxs-lookup"><span data-stu-id="f7bce-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="f7bce-119">Například následující kód vytvoří seznam druhých mocnin celých čísel od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="f7bce-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="f7bce-120">Operátory pro práci se seznamy</span><span class="sxs-lookup"><span data-stu-id="f7bce-120">Operators for Working with Lists</span></span>

<span data-ttu-id="f7bce-121">Prvky do seznamu můžete připojit pomocí `::` – operátor (nevýhody).</span><span class="sxs-lookup"><span data-stu-id="f7bce-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="f7bce-122">Pokud `list1` je `[2; 3; 4]`, následující kód vytvoří `list2` jako `[100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="f7bce-123">Můžete zřetězit seznamy, které mají nekompatibilní typy s použitím `@` operátoru, stejně jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="f7bce-124">Pokud `list1` je `[2; 3; 4]` a `list2` je `[100; 2; 3; 4 ]`, tento kód vytvoří `list3` jako `[2; 3; 4; 100; 2; 3; 4]`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4 ]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="f7bce-125">Funkce pro provádění operací na seznamy jsou k dispozici v [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="f7bce-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="f7bce-126">Protože jsou neměnné seznamy v jazyce F #, všechny změny operace generovat nové seznamy místo úpravy existujících seznamů.</span><span class="sxs-lookup"><span data-stu-id="f7bce-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="f7bce-127">Seznamy v jazyce F # jsou implementovány jako jednotlivě propojený seznam, což znamená, že operace, které přistupují k začátku seznamu jsou O(1), a je O přístup k prvkům (*n*).</span><span class="sxs-lookup"><span data-stu-id="f7bce-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="f7bce-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f7bce-128">Properties</span></span>

<span data-ttu-id="f7bce-129">Typ seznamu podporuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f7bce-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="f7bce-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="f7bce-130">Property</span></span>|<span data-ttu-id="f7bce-131">Typ</span><span class="sxs-lookup"><span data-stu-id="f7bce-131">Type</span></span>|<span data-ttu-id="f7bce-132">Popis</span><span class="sxs-lookup"><span data-stu-id="f7bce-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="f7bce-133">hlavní</span><span class="sxs-lookup"><span data-stu-id="f7bce-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="f7bce-134">První prvek.</span><span class="sxs-lookup"><span data-stu-id="f7bce-134">The first element.</span></span>|
|[<span data-ttu-id="f7bce-135">prázdný</span><span class="sxs-lookup"><span data-stu-id="f7bce-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="f7bce-136">Statické vlastnosti, která vrací prázdný seznam příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="f7bce-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="f7bce-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="f7bce-138">`true` Pokud seznam neobsahuje žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="f7bce-139">Položka</span><span class="sxs-lookup"><span data-stu-id="f7bce-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="f7bce-140">Element v zadaném indexu (počítáno od nuly).</span><span class="sxs-lookup"><span data-stu-id="f7bce-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="f7bce-141">Délka</span><span class="sxs-lookup"><span data-stu-id="f7bce-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="f7bce-142">Počet prvků.</span><span class="sxs-lookup"><span data-stu-id="f7bce-142">The number of elements.</span></span>|
|[<span data-ttu-id="f7bce-143">Funkce Tail</span><span class="sxs-lookup"><span data-stu-id="f7bce-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="f7bce-144">Seznam bez první prvek.</span><span class="sxs-lookup"><span data-stu-id="f7bce-144">The list without the first element.</span></span>|
<span data-ttu-id="f7bce-145">Následuje několik příkladů použití těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="f7bce-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="f7bce-146">Použití seznamů</span><span class="sxs-lookup"><span data-stu-id="f7bce-146">Using Lists</span></span>

<span data-ttu-id="f7bce-147">Programování se seznamy umožňuje provádět komplexní operace s menším objemem kódu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="f7bce-148">Tato část popisuje běžné operace na seznamy, které jsou důležité pro funkční programování.</span><span class="sxs-lookup"><span data-stu-id="f7bce-148">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="f7bce-149">Rekurze se seznamy</span><span class="sxs-lookup"><span data-stu-id="f7bce-149">Recursion with Lists</span></span>

<span data-ttu-id="f7bce-150">Seznamy jsou jednoznačně hodí pro rekurzivní programovacích postupech.</span><span class="sxs-lookup"><span data-stu-id="f7bce-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="f7bce-151">Vezměte v úvahu operace, která je třeba provést na každý prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="f7bce-152">Můžete udělat tento rekurzivně tak, že provoz na začátku seznamu a následným předáním konec seznamu, která je menší seznam, který se skládá z původního seznamu bez první prvek, zpátky na další úroveň rekurze.</span><span class="sxs-lookup"><span data-stu-id="f7bce-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="f7bce-153">Zápis rekurzivní funkci, použijte operátor nevýhody (`::`) v porovnávání vzorů, což vám umožní hlavní seznam nezávislá na konci.</span><span class="sxs-lookup"><span data-stu-id="f7bce-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="f7bce-154">Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro implementaci rekurzivní funkci, která provádí operace na seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="f7bce-155">Předchozí kód funguje dobře pro krátké seznamy, ale pro větší seznamy, ho může přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f7bce-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="f7bce-156">Následující kód se zvyšuje na tento kód pomocí argumentu akumulátor standardní způsob pro práci s rekurzivní funkce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="f7bce-157">Použijte argument akumulátor díky rekurzivní funkce tail, což šetří místo v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f7bce-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="f7bce-158">Funkce `RemoveAllMultiples` je rekurzivní funkci, která přijímá dva seznamy.</span><span class="sxs-lookup"><span data-stu-id="f7bce-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="f7bce-159">První seznam obsahuje čísla, jejichž násobky se odeberou a druhým seznamem je seznamu, ze kterého mají být odebrány čísla.</span><span class="sxs-lookup"><span data-stu-id="f7bce-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="f7bce-160">Kód v následujícím příkladu používá tato rekurzivní funkce pro odstranění všech jiných prvočísel ze seznamu, v důsledku byste museli opustit seznam prvočísel.</span><span class="sxs-lookup"><span data-stu-id="f7bce-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="f7bce-161">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-161">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="f7bce-162">Modul funkce</span><span class="sxs-lookup"><span data-stu-id="f7bce-162">Module Functions</span></span>

<span data-ttu-id="f7bce-163">[Modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) poskytuje funkce, které přístup k prvkům seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="f7bce-164">Head element je nejrychlejší a nejjednodušší přístup.</span><span class="sxs-lookup"><span data-stu-id="f7bce-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="f7bce-165">Použijte vlastnost [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) nebo funkci modul [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="f7bce-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="f7bce-166">Konec seznamu přístupné prostřednictvím [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) vlastnost nebo [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) funkce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="f7bce-167">Nalezení prvku podle indexu, použijte [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) funkce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="f7bce-168">`List.nth` projde seznam.</span><span class="sxs-lookup"><span data-stu-id="f7bce-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="f7bce-169">Proto se jedná O (*n*).</span><span class="sxs-lookup"><span data-stu-id="f7bce-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="f7bce-170">Pokud váš kód používá `List.nth` často, můžete chtít zvážit použití pole namísto seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="f7bce-171">Přístup k prvkům v poli je O(1).</span><span class="sxs-lookup"><span data-stu-id="f7bce-171">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="f7bce-172">Logická operace v seznamech</span><span class="sxs-lookup"><span data-stu-id="f7bce-172">Boolean Operations on Lists</span></span>

<span data-ttu-id="f7bce-173">[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) funkce určuje, zda seznam obsahuje všechny prvky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="f7bce-174">[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) funkce se vztahuje datový typ Boolean test na prvky seznam a vrátí `true` Pokud libovolný prvek splňuje testu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="f7bce-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) je podobné, ale funguje v po sobě jdoucích dvojice elementů v dva seznamy.</span><span class="sxs-lookup"><span data-stu-id="f7bce-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="f7bce-176">Následující kód demonstruje použití `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="f7bce-177">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-177">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="f7bce-178">Následující příklad ukazuje použití `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="f7bce-179">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-179">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="f7bce-180">Můžete použít [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) Pokud budete chtít otestovat, jestli všechny prvky seznamu splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="f7bce-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="f7bce-181">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-181">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="f7bce-182">Obdobně [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) Určuje, jestli splňují všechny prvky na odpovídající pozici v dva seznamy logický výraz, který zahrnuje každý pár prvků.</span><span class="sxs-lookup"><span data-stu-id="f7bce-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="f7bce-183">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-183">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="f7bce-184">Operace řazení v seznamech</span><span class="sxs-lookup"><span data-stu-id="f7bce-184">Sort Operations on Lists</span></span>

<span data-ttu-id="f7bce-185">[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), a [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) funkce řazení seznamy.</span><span class="sxs-lookup"><span data-stu-id="f7bce-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="f7bce-186">Funkce třídění určuje, které tyto tři funkce používat.</span><span class="sxs-lookup"><span data-stu-id="f7bce-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="f7bce-187">`List.sort` používá výchozí obecného porovnání.</span><span class="sxs-lookup"><span data-stu-id="f7bce-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="f7bce-188">Pro porovnání hodnot používá obecného porovnání globálních operátorů podle funkce obecného porovnání.</span><span class="sxs-lookup"><span data-stu-id="f7bce-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="f7bce-189">Funguje to pro efektivní nejrůznější typy prvků, jako je například jednoduché číselné typy, řazených kolekcí členů, záznamy, rozlišovaná sjednocení, seznamů, polí a libovolný typ, který implementuje `System.IComparable`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="f7bce-190">Pro typy, které implementují `System.IComparable`, používá obecného porovnání `System.IComparable.CompareTo()` funkce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="f7bce-191">Obecného porovnání také funguje s řetězci, ale používá pořadí řazení nezávislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="f7bce-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="f7bce-192">Obecného porovnání neměla používat pro nepodporované typy, jako jsou typy funkcí.</span><span class="sxs-lookup"><span data-stu-id="f7bce-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="f7bce-193">Navíc je nejvhodnější pro malé strukturované typy; výkonu obecného porovnání výchozí pro větší strukturované typy, které je potřeba porovnání a řazení často, zvažte implementaci `System.IComparable` a poskytují efektivní implementace `System.IComparable.CompareTo()` metody.</span><span class="sxs-lookup"><span data-stu-id="f7bce-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="f7bce-194">`List.sortBy` používá funkce, která vrátí hodnotu, která se používá jako kritérium řazení a `List.sortWith` přijímá jako argument funkce porovnání.</span><span class="sxs-lookup"><span data-stu-id="f7bce-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="f7bce-195">Tyto druhé dvě funkce jsou užitečné při práci s typy, které nepodporují porovnání nebo při porovnání vyžaduje složitější porovnání sémantiky, jako v případě řetězců zohledňující jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="f7bce-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="f7bce-196">Následující příklad ukazuje použití `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="f7bce-197">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-197">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="f7bce-198">Následující příklad ukazuje použití `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="f7bce-199">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-199">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="f7bce-200">Následující příklad ukazuje použití `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="f7bce-201">V tomto příkladu vlastní funkci porovnání `compareWidgets` se používá k porovnání nejprve jedno pole z vlastního typu a pak opět v případě hodnoty první pole jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="f7bce-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="f7bce-202">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-202">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="f7bce-203">Operace hledání v seznamech</span><span class="sxs-lookup"><span data-stu-id="f7bce-203">Search Operations on Lists</span></span>

<span data-ttu-id="f7bce-204">Seznamy podporují řadu operací vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="f7bce-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="f7bce-205">Nejjednodušší, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umožňuje najít první prvek, který odpovídá dané podmínky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="f7bce-206">Následující příklad kódu ukazuje použití `List.find` najít první číslo, které je dělitelná 5 v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="f7bce-207">Výsledkem je 5.</span><span class="sxs-lookup"><span data-stu-id="f7bce-207">The result is 5.</span></span>

<span data-ttu-id="f7bce-208">Pokud nejprve musí transformované prvky, zavolejte [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), který by funkce, která vrátí možnost a vyhledá první možnost Hodnota, která je `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="f7bce-209">Místo vrácení elementu `List.pick` vrátí výsledek `x`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="f7bce-210">Pokud není nalezen žádný odpovídající element, `List.pick` vyvolá `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="f7bce-211">Následující kód ukazuje použití `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="f7bce-212">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-212">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="f7bce-213">Jiná skupina operace hledání [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) a související funkce vrátí hodnotu možnosti.</span><span class="sxs-lookup"><span data-stu-id="f7bce-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="f7bce-214">`List.tryFind` Funkce vrátí první prvek seznamu, který splňuje podmínku, pokud takový prvek neexistuje, ale hodnota možnosti `None` Pokud tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="f7bce-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="f7bce-215">Změna [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) vrátí index prvku, pokud ho najde, místo samotného elementu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="f7bce-216">Tyto funkce jsou znázorněné v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="f7bce-217">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-217">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="f7bce-218">Aritmetické operace v seznamech</span><span class="sxs-lookup"><span data-stu-id="f7bce-218">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="f7bce-219">Běžné aritmetické operace, jako je součet a průměr jsou integrované do [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="f7bce-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="f7bce-220">Pro práci s [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), musí podporovat seznamu Typ prvku `+` operátor a mít nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="f7bce-221">Všechny vestavěné aritmetické typy splňovat tyto podmínky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="f7bce-222">Pro práci s [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), typ elementu musí podporovat dělení beze zbytku, která nezahrnuje celočíselných typů, ale umožňuje pro typy s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="f7bce-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="f7bce-223">[List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) a [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) funkce přebírají funkci jako parametr a výsledky této funkce se používají k výpočtu hodnot pro součtu nebo průměru.</span><span class="sxs-lookup"><span data-stu-id="f7bce-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="f7bce-224">Následující kód demonstruje použití `List.sum`, `List.sumBy`, a `List.average`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="f7bce-225">Výstup je `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-225">The output is `1.000000`.</span></span>

<span data-ttu-id="f7bce-226">Následující kód ukazuje použití `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="f7bce-227">Výstup je `5.5`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-227">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="f7bce-228">Seznamech a řazených kolekcí členů</span><span class="sxs-lookup"><span data-stu-id="f7bce-228">Lists and Tuples</span></span>

<span data-ttu-id="f7bce-229">Seznamy, které obsahují řazené kolekce členů může manipulovat zip a rozbalte funkce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="f7bce-230">Tyto funkce sloučit dva seznamy jednotlivé hodnoty do jediného seznamu řazených kolekcí členů nebo rozdělit do dvou seznamů hodnot jednoho jeden seznam řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="f7bce-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="f7bce-231">Nejjednodušší [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) funkce přebírá dva seznamy jednotlivé prvky a vytváří jeden seznam dvojic, přičemž řazené kolekce členů.</span><span class="sxs-lookup"><span data-stu-id="f7bce-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="f7bce-232">Jiná verze [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), přebírá tři seznamy jeden prvků a vytváří jeden seznam řazených kolekcí členů, které mají tři prvky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="f7bce-233">Následující příklad kódu ukazuje použití `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="f7bce-234">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-234">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="f7bce-235">Následující příklad kódu ukazuje použití `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="f7bce-236">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-236">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="f7bce-237">Odpovídající verze, rozbalte [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) a [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), používají seznamy řazených kolekcí členů a vrací seznamy v řazené kolekce členů, kde první seznam obsahuje všechny prvky, které se poprvé v každé řazené kolekce členů a druhý seznam obsahuje druhý prvek řazené kolekce členů, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="f7bce-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="f7bce-238">Následující příklad kódu ukazuje použití [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="f7bce-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="f7bce-239">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-239">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="f7bce-240">Následující příklad kódu ukazuje použití [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="f7bce-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="f7bce-241">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-241">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="f7bce-242">Práce na seznamu elementů</span><span class="sxs-lookup"><span data-stu-id="f7bce-242">Operating on List Elements</span></span>

<span data-ttu-id="f7bce-243">Jazyk F # podporuje širokou škálu operace na seznamu elementů.</span><span class="sxs-lookup"><span data-stu-id="f7bce-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="f7bce-244">Nejjednodušší je [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), což vám umožní volat funkci na každý prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="f7bce-245">Zahrnovat odchylky [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), což vám umožní provést operaci s prvky dvou seznamů [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), což je třeba `List.iter` s tím rozdílem, že indexu každého prvku je předán jako argument pro funkci, která je volána pro každý prvek a [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), což je kombinací funkce `List.iter2` a `List.iteri`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="f7bce-246">Následující příklad kódu ukazuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="f7bce-247">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-247">The output is as follows:</span></span>

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

<span data-ttu-id="f7bce-248">Další často používané funkci, která transformuje prvky seznamu je [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), což vám umožní použít funkci na každý prvek seznamu a všechny výsledky do nového seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="f7bce-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) a [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) jsou změny, které provést více seznamů.</span><span class="sxs-lookup"><span data-stu-id="f7bce-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="f7bce-250">Můžete také použít [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) a [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), je-li kromě elementu, funkce musí být předán indexu každého prvku.</span><span class="sxs-lookup"><span data-stu-id="f7bce-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="f7bce-251">Jediným rozdílem mezi `List.mapi2` a `List.mapi` je, že `List.mapi2` pracuje se dvěma seznamy.</span><span class="sxs-lookup"><span data-stu-id="f7bce-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="f7bce-252">Následující příklad ukazuje [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="f7bce-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="f7bce-253">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-253">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="f7bce-254">Následující příklad ukazuje použití `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="f7bce-255">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-255">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="f7bce-256">Následující příklad ukazuje použití `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="f7bce-257">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-257">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="f7bce-258">Následující příklad ukazuje použití `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="f7bce-259">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-259">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="f7bce-260">Následující příklad ukazuje použití `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="f7bce-261">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-261">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="f7bce-262">[List.Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) je stejná jako `List.map`, s tím rozdílem, že každý prvek vytváří seznam a tyto seznamy jsou zřetězeny do konečný seznam.</span><span class="sxs-lookup"><span data-stu-id="f7bce-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="f7bce-263">V následujícím kódu generuje každý prvek v seznamu tří čísel.</span><span class="sxs-lookup"><span data-stu-id="f7bce-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="f7bce-264">Všechny jsou shromážděné v jednom seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="f7bce-265">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-265">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="f7bce-266">Můžete také použít [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), který převezme logickou podmínku a vytvoří nový seznam, který se skládá pouze z prvků, které odpovídají dané podmínce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="f7bce-267">V rozevíracím seznamu se `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="f7bce-268">V kombinaci map a filtrování [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) umožňuje transformovat a vyberte prvky ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="f7bce-269">`List.choose` použije funkci, která vrací možnost na každý prvek seznamu a vrátí nový seznam výsledků pro elementy, pokud funkce vrátí hodnotu možnosti `Some`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="f7bce-270">Následující kód demonstruje použití `List.choose` vyberte ze seznamu slov velká písmena slov.</span><span class="sxs-lookup"><span data-stu-id="f7bce-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="f7bce-271">Výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7bce-271">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="f7bce-272">Provoz ve více seznamech</span><span class="sxs-lookup"><span data-stu-id="f7bce-272">Operating on Multiple Lists</span></span>

<span data-ttu-id="f7bce-273">Seznamy lze spojit dohromady.</span><span class="sxs-lookup"><span data-stu-id="f7bce-273">Lists can be joined together.</span></span> <span data-ttu-id="f7bce-274">Chcete-li připojit dva seznamy do jednoho, použijte [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="f7bce-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="f7bce-275">Chcete-li připojit k více než dva seznamy, použijte [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="f7bce-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="f7bce-276">Skládání a operace kontroly</span><span class="sxs-lookup"><span data-stu-id="f7bce-276">Fold and Scan Operations</span></span>

<span data-ttu-id="f7bce-277">Některé operace výpisu zahrnují vzájemné závislosti mezi všechny prvky seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="f7bce-278">Skládání a kontroly operace jsou jako `List.iter` a `List.map` , vyvolá funkci na každý prvek, ale tyto operace poskytují další parametr s názvem *akumulátor* , která přenáší informace Výpočet.</span><span class="sxs-lookup"><span data-stu-id="f7bce-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="f7bce-279">Použití `List.fold` k provedení výpočtu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="f7bce-280">Následující příklad kódu ukazuje použití [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) můžete provádět různé operace.</span><span class="sxs-lookup"><span data-stu-id="f7bce-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="f7bce-281">V seznamu procházet řízený; je zásobník `acc` je hodnota, která se předají jak pokračuje výpočtu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="f7bce-282">První argument přebírá je zásobník a prvek seznamu a vrací dočasné výsledek výpočtu pro daný element seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="f7bce-283">Druhý argument je počáteční hodnota proměnné je zásobník.</span><span class="sxs-lookup"><span data-stu-id="f7bce-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="f7bce-284">Verze těchto funkcí, které mají číslici v názvu funkce pracují s více než jeden seznam.</span><span class="sxs-lookup"><span data-stu-id="f7bce-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="f7bce-285">Například [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) provádí výpočty na dvou seznamů.</span><span class="sxs-lookup"><span data-stu-id="f7bce-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="f7bce-286">Následující příklad ukazuje použití `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="f7bce-287">`List.fold` a [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) se liší v, který `List.fold` vrátí poslední hodnotu speciálním parametrem, ale `List.scan` vrátí seznam pomocných hodnot (spolu s konečnou hodnotu) speciálním parametrem.</span><span class="sxs-lookup"><span data-stu-id="f7bce-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="f7bce-288">Každá z těchto funkcí zahrnuje reverzní variantu, například [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), navzájem se liší v pořadí, ve které je v seznamu Procházet a pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="f7bce-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="f7bce-289">Navíc `List.fold` a `List.foldBack` mají varianty, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) a [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), které přebírají dva seznamy stejné délky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="f7bce-290">Funkce, která se spustí na každý prvek můžete použít odpovídající prvky obou seznamů k provedení nějaké akce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="f7bce-291">Typy prvků ze dvou seznamů mohou lišit, jako v následujícím příkladu, ve kterém jeden seznam obsahuje objemy transakcí pro bankovním účtu, a seznamu obsahuje typ transakce: uložení nebo zrušení.</span><span class="sxs-lookup"><span data-stu-id="f7bce-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="f7bce-292">Pro výpočet jako souhrn `List.fold` a `List.foldBack` mají stejný účinek, protože výsledek není závislý v řádu procházení.</span><span class="sxs-lookup"><span data-stu-id="f7bce-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="f7bce-293">V následujícím příkladu `List.foldBack` se používá k přidání prvků v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="f7bce-294">Následující příklad vrátí v příkladu bankovním účtu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="f7bce-295">Tentokrát je přidán nový typ transakce: Výpočet úroku.</span><span class="sxs-lookup"><span data-stu-id="f7bce-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="f7bce-296">Konečný zůstatek závisí nyní v řádu transakce.</span><span class="sxs-lookup"><span data-stu-id="f7bce-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="f7bce-297">Funkce [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) je něco jako `List.fold` a `List.scan`, s tím rozdílem, že namísto předání kolem samostatné akumulátor `List.reduce` používá funkce, která přebírá dva argumenty typu elementu namísto otázkou jediného a jeden z těchto argumentů funguje jako je zásobník, což znamená, že ukládá přechodný výsledek výpočtu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="f7bce-298">`List.reduce` začne pracující na prvních dvou seznam prvků a potom použije výsledek operace společně s další prvek.</span><span class="sxs-lookup"><span data-stu-id="f7bce-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="f7bce-299">Protože samostatné akumulátor, který má svůj vlastní typ není `List.reduce` lze použít místo `List.fold` pouze v případě je zásobník a typ prvku máte stejného typu.</span><span class="sxs-lookup"><span data-stu-id="f7bce-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="f7bce-300">Následující kód demonstruje použití `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="f7bce-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="f7bce-301">`List.reduce` vyvolá výjimku, pokud v seznamu neobsahuje žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="f7bce-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="f7bce-302">V následujícím kódu první volání výrazu lambda je předávat argumenty 2 a 4 a vrátí 6, a další volání dostane argumenty 6 a 10, takže výsledkem je 16.</span><span class="sxs-lookup"><span data-stu-id="f7bce-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="f7bce-303">Převod mezi seznamy a typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="f7bce-303">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="f7bce-304">`List` Modulu poskytuje funkce pro převod do a z pořadí a pole.</span><span class="sxs-lookup"><span data-stu-id="f7bce-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="f7bce-305">Chcete-li převést do nebo ze sekvence, použijte [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) nebo [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="f7bce-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="f7bce-306">Chcete-li převést na nebo z pole, použijte [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) nebo [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="f7bce-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="f7bce-307">Další operace</span><span class="sxs-lookup"><span data-stu-id="f7bce-307">Additional Operations</span></span>

<span data-ttu-id="f7bce-308">Informace o dalších operacích v seznamech, naleznete v tématu referenční dokumentace knihovny [Collections.list – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f7bce-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7bce-309">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7bce-309">See also</span></span>

- [<span data-ttu-id="f7bce-310">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="f7bce-310">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f7bce-311">Typy F#</span><span class="sxs-lookup"><span data-stu-id="f7bce-311">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="f7bce-312">Sekvence</span><span class="sxs-lookup"><span data-stu-id="f7bce-312">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="f7bce-313">Pole</span><span class="sxs-lookup"><span data-stu-id="f7bce-313">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="f7bce-314">Možnosti</span><span class="sxs-lookup"><span data-stu-id="f7bce-314">Options</span></span>](options.md)
