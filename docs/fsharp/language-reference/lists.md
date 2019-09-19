---
title: Seznamy
description: Přečtěte F# si o seznamech, seřazené, neměnné řadě prvků stejného typu.
ms.date: 05/16/2016
ms.openlocfilehash: 72f1779d7d077da0f1f4804df93fa4ac11f9b2e3
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082913"
---
# <a name="lists"></a><span data-ttu-id="5227a-103">Seznamy</span><span class="sxs-lookup"><span data-stu-id="5227a-103">Lists</span></span>

> [!NOTE]
> <span data-ttu-id="5227a-104">Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN.</span><span class="sxs-lookup"><span data-stu-id="5227a-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="5227a-105">Reference k rozhraní docs.microsoft.com API není dokončená.</span><span class="sxs-lookup"><span data-stu-id="5227a-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="5227a-106">Seznam v F# je seřazená, neproměnlivá řada prvků stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5227a-106">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="5227a-107">K provádění základních operací na seznamech použijte funkce v [modulu seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="5227a-107">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="5227a-108">Vytváření a inicializace seznamů</span><span class="sxs-lookup"><span data-stu-id="5227a-108">Creating and Initializing Lists</span></span>

<span data-ttu-id="5227a-109">Seznam můžete definovat explicitním seznamem prvků oddělených středníky a uzavřenými do hranatých závorek, jak je znázorněno na následujícím řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="5227a-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="5227a-110">Můžete také umístit zalomení řádků mezi prvky, v takovém případě jsou středníky volitelné.</span><span class="sxs-lookup"><span data-stu-id="5227a-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="5227a-111">Druhá syntaxe může vést k čitelnějšímu kódu, když jsou inicializační výrazy prvku delší nebo pokud chcete zahrnout komentář pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="5227a-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="5227a-112">V normálním případě musí být všechny prvky seznamu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5227a-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="5227a-113">Výjimkou je, že seznam, ve kterém jsou prvky určeny jako základní typ, může mít elementy, které jsou odvozeny typy.</span><span class="sxs-lookup"><span data-stu-id="5227a-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="5227a-114">Proto je možné, že následující podmínky jsou `Button` přijatelné `CheckBox` , protože `Control`a jsou odvozeny z.</span><span class="sxs-lookup"><span data-stu-id="5227a-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="5227a-115">Můžete také definovat prvky seznamu pomocí rozsahu, který je určen pomocí celých čísel oddělených operátorem Range`..`(), jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5227a-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="5227a-116">Prázdný seznam je určený dvojicí hranatých závorek bez jakéhokoli mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="5227a-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="5227a-117">Můžete také použít výraz pořadí k vytvoření seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="5227a-118">Další informace naleznete v tématu [výrazy sekvence](sequences.md#sequence-expressions) .</span><span class="sxs-lookup"><span data-stu-id="5227a-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="5227a-119">Například následující kód vytvoří seznam čtverců celých čísel od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="5227a-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="5227a-120">Operátory pro práci se seznamy</span><span class="sxs-lookup"><span data-stu-id="5227a-120">Operators for Working with Lists</span></span>

<span data-ttu-id="5227a-121">Prvky můžete k seznamu připojit pomocí `::` operátoru (nevýhody).</span><span class="sxs-lookup"><span data-stu-id="5227a-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="5227a-122">V případě `list1` `list2` , následující kód vytvoří jako `[100; 2; 3; 4]`. `[2; 3; 4]`</span><span class="sxs-lookup"><span data-stu-id="5227a-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="5227a-123">Seznamy, které mají kompatibilní typy, lze zřetězit pomocí `@` operátoru, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5227a-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="5227a-124">Pokud `list1` je `[2; 3; 4]` a ,tento`list2` kód vytvoří`list3` jako .`[2; 3; 4; 100; 2; 3; 4]` `[100; 2; 3; 4]`</span><span class="sxs-lookup"><span data-stu-id="5227a-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="5227a-125">Funkce pro provádění operací v seznamech jsou k dispozici v [modulu seznam](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="5227a-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="5227a-126">Vzhledem k tomu F# , že seznamy v nástroji jsou neměnné, všechny úpravy operací generují nové seznamy místo úprav existujících seznamů.</span><span class="sxs-lookup"><span data-stu-id="5227a-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="5227a-127">Seznamy v F# aplikaci jsou implementovány jako jednotlivě propojené seznamy, což znamená, že operace, které mají přístup pouze k hlavnímu seznamu, mají hodnotu o (1) a přístup k prvkům je o (*n*).</span><span class="sxs-lookup"><span data-stu-id="5227a-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="5227a-128">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5227a-128">Properties</span></span>

<span data-ttu-id="5227a-129">Typ seznamu podporuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5227a-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="5227a-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="5227a-130">Property</span></span>|<span data-ttu-id="5227a-131">Typ</span><span class="sxs-lookup"><span data-stu-id="5227a-131">Type</span></span>|<span data-ttu-id="5227a-132">Popis</span><span class="sxs-lookup"><span data-stu-id="5227a-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="5227a-133">Záhlaví</span><span class="sxs-lookup"><span data-stu-id="5227a-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="5227a-134">První prvek.</span><span class="sxs-lookup"><span data-stu-id="5227a-134">The first element.</span></span>|
|[<span data-ttu-id="5227a-135">prázdný</span><span class="sxs-lookup"><span data-stu-id="5227a-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="5227a-136">Statická vlastnost, která vrací prázdný seznam příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="5227a-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="5227a-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="5227a-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="5227a-138">`true`Pokud seznam neobsahuje žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="5227a-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="5227a-139">Položka</span><span class="sxs-lookup"><span data-stu-id="5227a-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="5227a-140">Prvek na zadaném indexu (založený na nule).</span><span class="sxs-lookup"><span data-stu-id="5227a-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="5227a-141">Časový</span><span class="sxs-lookup"><span data-stu-id="5227a-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="5227a-142">Počet elementů.</span><span class="sxs-lookup"><span data-stu-id="5227a-142">The number of elements.</span></span>|
|[<span data-ttu-id="5227a-143">Kompatibilní</span><span class="sxs-lookup"><span data-stu-id="5227a-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="5227a-144">Seznam bez prvního prvku</span><span class="sxs-lookup"><span data-stu-id="5227a-144">The list without the first element.</span></span>|

<span data-ttu-id="5227a-145">Níže jsou uvedeny některé příklady použití těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="5227a-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="5227a-146">Používání seznamů</span><span class="sxs-lookup"><span data-stu-id="5227a-146">Using Lists</span></span>

<span data-ttu-id="5227a-147">Programování se seznamy vám umožňuje provádět komplexní operace s malým množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="5227a-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="5227a-148">Tato část popisuje běžné operace se seznamy, které jsou důležité pro funkční programování.</span><span class="sxs-lookup"><span data-stu-id="5227a-148">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="5227a-149">Rekurze se seznamy</span><span class="sxs-lookup"><span data-stu-id="5227a-149">Recursion with Lists</span></span>

<span data-ttu-id="5227a-150">Seznamy jsou jedinečně uzpůsobeny rekurzivním programovacím technikům.</span><span class="sxs-lookup"><span data-stu-id="5227a-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="5227a-151">Zvažte operaci, která musí být provedena u každého prvku seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="5227a-152">To lze provést rekurzivně na začátku seznamu a následným předáním konce seznamu, který je menší seznam, který se skládá z původního seznamu bez prvního prvku, zpět na další úroveň rekurze.</span><span class="sxs-lookup"><span data-stu-id="5227a-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="5227a-153">Chcete-li zapsat takovou rekurzivní funkci, použijte operátor nevýhody (`::`) v porovnávání vzorů, což umožňuje oddělit záhlaví seznamu od konce.</span><span class="sxs-lookup"><span data-stu-id="5227a-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="5227a-154">Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro implementaci rekurzivní funkce, která provádí operace na seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="5227a-155">Předchozí kód funguje dobře u malých seznamů, ale u větších seznamů může přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5227a-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="5227a-156">Následující kód vylepšuje tento kód pomocí argumentu Akumulovaná, standardní technika pro práci s rekurzivními funkcemi.</span><span class="sxs-lookup"><span data-stu-id="5227a-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="5227a-157">Použití argumentu akumulátoru způsobí rekurzivní funkci na konci, která šetří místo v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5227a-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="5227a-158">Funkce `RemoveAllMultiples` je rekurzivní funkce, která přijímá dva seznamy.</span><span class="sxs-lookup"><span data-stu-id="5227a-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="5227a-159">První seznam obsahuje čísla, jejichž násobky budou odebrány, a druhý seznam je seznam, ze kterého mají být čísla odebrána.</span><span class="sxs-lookup"><span data-stu-id="5227a-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="5227a-160">Kód v následujícím příkladě používá tuto rekurzivní funkci k vyloučení všech nekoncových čísel ze seznamu, přičemž seznam koncových čísel se vynechává jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="5227a-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="5227a-161">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-161">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="5227a-162">Funkce modulu</span><span class="sxs-lookup"><span data-stu-id="5227a-162">Module Functions</span></span>

<span data-ttu-id="5227a-163">[Modul seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) poskytuje funkce, které přistupují k prvkům seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="5227a-164">Hlavní prvek je nejrychlejší a nejjednodušší pro přístup.</span><span class="sxs-lookup"><span data-stu-id="5227a-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="5227a-165">Použijte [záhlaví](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) vlastnosti nebo seznam funkcí modulu [. Head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span><span class="sxs-lookup"><span data-stu-id="5227a-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="5227a-166">K zakončení seznamu můžete přistupovat pomocí vlastnosti [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) nebo funkce [list. tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) .</span><span class="sxs-lookup"><span data-stu-id="5227a-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="5227a-167">Chcete-li najít element podle indexu, použijte funkci [list. n](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) .</span><span class="sxs-lookup"><span data-stu-id="5227a-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="5227a-168">`List.nth`projde seznam.</span><span class="sxs-lookup"><span data-stu-id="5227a-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="5227a-169">Proto má hodnotu O (*n*).</span><span class="sxs-lookup"><span data-stu-id="5227a-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="5227a-170">Pokud váš kód používá `List.nth` často, možná budete chtít zvážit použití pole namísto seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="5227a-171">Přístup k prvkům v polích je O (1).</span><span class="sxs-lookup"><span data-stu-id="5227a-171">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="5227a-172">Logické operace na seznamech</span><span class="sxs-lookup"><span data-stu-id="5227a-172">Boolean Operations on Lists</span></span>

<span data-ttu-id="5227a-173">Funkce [list... Empty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) určuje, zda má seznam nějaké prvky.</span><span class="sxs-lookup"><span data-stu-id="5227a-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="5227a-174">Funkce [list. Exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) používá logický test na prvky seznamu a vrací `true` , pokud některý prvek splňuje podmínky testu.</span><span class="sxs-lookup"><span data-stu-id="5227a-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="5227a-175">[List. exists2 –](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) je podobný, ale pracuje na po sobě jdoucích dvojic prvků ve dvou seznamech.</span><span class="sxs-lookup"><span data-stu-id="5227a-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="5227a-176">Následující kód demonstruje použití `List.exists`.</span><span class="sxs-lookup"><span data-stu-id="5227a-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="5227a-177">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-177">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="5227a-178">Následující příklad ukazuje použití `List.exists2`.</span><span class="sxs-lookup"><span data-stu-id="5227a-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="5227a-179">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-179">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="5227a-180">[Seznam. ForAll](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) můžete použít, pokud chcete otestovat, zda všechny prvky seznamu splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="5227a-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="5227a-181">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-181">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="5227a-182">Podobně [seznam. forall2 –](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) určuje, zda všechny prvky v odpovídajících pozicích ve dvou seznamech odpovídají logickému výrazu, který zahrnuje každou dvojici prvků.</span><span class="sxs-lookup"><span data-stu-id="5227a-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="5227a-183">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-183">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="5227a-184">Seřadit operace v seznamech</span><span class="sxs-lookup"><span data-stu-id="5227a-184">Sort Operations on Lists</span></span>

<span data-ttu-id="5227a-185">Seznam. [Sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [list. sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)a [list. sortWith –](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) Functions Sort lists.</span><span class="sxs-lookup"><span data-stu-id="5227a-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="5227a-186">Funkce řazení určuje, které z těchto tří funkcí použít.</span><span class="sxs-lookup"><span data-stu-id="5227a-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="5227a-187">`List.sort`používá výchozí obecné porovnání.</span><span class="sxs-lookup"><span data-stu-id="5227a-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="5227a-188">Obecné porovnání používá pro porovnání hodnot globální operátory založené na funkci Generic Compare.</span><span class="sxs-lookup"><span data-stu-id="5227a-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="5227a-189">Funguje efektivně s širokou škálou typů prvků, jako jsou jednoduché číselné typy, řazené kolekce členů, záznamy, rozlišené sjednocení, seznamy, pole a jakýkoli typ, který `System.IComparable`implementuje.</span><span class="sxs-lookup"><span data-stu-id="5227a-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="5227a-190">Pro typy, které `System.IComparable`implementují obecné porovnání, `System.IComparable.CompareTo()` používá funkci.</span><span class="sxs-lookup"><span data-stu-id="5227a-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="5227a-191">Obecné porovnání funguje také s řetězci, ale používá pořadí řazení nezávislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="5227a-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="5227a-192">Obecné porovnání by nemělo být použito pro nepodporované typy, jako například typy funkcí.</span><span class="sxs-lookup"><span data-stu-id="5227a-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="5227a-193">Také výkon výchozího obecného porovnání je nejvhodnější pro malé strukturované typy; u větších strukturovaných typů, které je třeba porovnat a seřadit často, zvažte `System.IComparable` implementaci a poskytování efektivní implementace `System.IComparable.CompareTo()` metody.</span><span class="sxs-lookup"><span data-stu-id="5227a-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="5227a-194">`List.sortBy`převezme funkci, která vrací hodnotu, která se používá jako kritérium řazení, a `List.sortWith` jako argument použije funkci porovnání.</span><span class="sxs-lookup"><span data-stu-id="5227a-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="5227a-195">Tyto dvě funkce jsou užitečné, když pracujete s typy, které nepodporují porovnání, nebo když porovnání vyžaduje složitější sémantiku porovnání, jako v případě řetězců zohledňujících jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="5227a-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="5227a-196">Následující příklad ukazuje použití `List.sort`.</span><span class="sxs-lookup"><span data-stu-id="5227a-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="5227a-197">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-197">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="5227a-198">Následující příklad ukazuje použití `List.sortBy`.</span><span class="sxs-lookup"><span data-stu-id="5227a-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="5227a-199">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-199">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="5227a-200">Další příklad ukazuje použití `List.sortWith`.</span><span class="sxs-lookup"><span data-stu-id="5227a-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="5227a-201">V tomto příkladu se vlastní srovnávací funkce `compareWidgets` používá k prvnímu porovnání jednoho pole vlastního typu a poté další, pokud jsou hodnoty prvního pole stejné.</span><span class="sxs-lookup"><span data-stu-id="5227a-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="5227a-202">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-202">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="5227a-203">Vyhledat operace v seznamech</span><span class="sxs-lookup"><span data-stu-id="5227a-203">Search Operations on Lists</span></span>

<span data-ttu-id="5227a-204">Pro seznamy se podporuje celá řada operací hledání.</span><span class="sxs-lookup"><span data-stu-id="5227a-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="5227a-205">Nejjednodušší, [list. Find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), umožňuje najít první prvek, který odpovídá dané podmínce.</span><span class="sxs-lookup"><span data-stu-id="5227a-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="5227a-206">Následující příklad kódu ukazuje použití `List.find` nástroje k nalezení prvního čísla, které je v seznamu dělitele 5.</span><span class="sxs-lookup"><span data-stu-id="5227a-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="5227a-207">Výsledek je 5.</span><span class="sxs-lookup"><span data-stu-id="5227a-207">The result is 5.</span></span>

<span data-ttu-id="5227a-208">Pokud elementy musí být transformovány jako první, zavolejte [list. vyskl](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), který převezme funkci, která vrací možnost a vyhledá první hodnotu možnosti, která je `Some(x)`.</span><span class="sxs-lookup"><span data-stu-id="5227a-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="5227a-209">Místo vrácení elementu `List.pick` vrátí výsledek `x`.</span><span class="sxs-lookup"><span data-stu-id="5227a-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="5227a-210">Pokud se nenajde žádný vyhovující prvek, `List.pick` vyvolá `System.Collections.Generic.KeyNotFoundException`.</span><span class="sxs-lookup"><span data-stu-id="5227a-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="5227a-211">Následující kód ukazuje použití `List.pick`.</span><span class="sxs-lookup"><span data-stu-id="5227a-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="5227a-212">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-212">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="5227a-213">Jiná skupina operací hledání, [list. tryFind –](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) a související funkce, vrací hodnotu možnosti.</span><span class="sxs-lookup"><span data-stu-id="5227a-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="5227a-214">Funkce vrátí první prvek seznamu, který splňuje podmínku, pokud takový prvek existuje, ale hodnota `None` možnosti, pokud není. `List.tryFind`</span><span class="sxs-lookup"><span data-stu-id="5227a-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="5227a-215">Seznam variací [. tryFindIndex –](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) vrátí index elementu, pokud je nalezen, spíše než samotný element.</span><span class="sxs-lookup"><span data-stu-id="5227a-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="5227a-216">Tyto funkce jsou znázorněny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5227a-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="5227a-217">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-217">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="5227a-218">Aritmetické operace na seznamech</span><span class="sxs-lookup"><span data-stu-id="5227a-218">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="5227a-219">Do [modulu seznamu](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)jsou integrovány běžné aritmetické operace, jako je součet a průměr.</span><span class="sxs-lookup"><span data-stu-id="5227a-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="5227a-220">Pro práci se [seznamem. Sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)musí typ elementu seznamu podporovat `+` operátor a mít nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5227a-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="5227a-221">Všechny integrované aritmetické typy tyto podmínky vyhoví.</span><span class="sxs-lookup"><span data-stu-id="5227a-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="5227a-222">Pro práci se [seznamem. Average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)musí typ elementu podporovat dělení bez zbytku, který vylučuje celočíselné typy, ale umožňuje použití typů s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="5227a-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="5227a-223">Funkce [list. sumBy –](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) a [list. averageBy –](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) přebírají funkci jako parametr a výsledky této funkce se používají k výpočtu hodnot součtu nebo průměru.</span><span class="sxs-lookup"><span data-stu-id="5227a-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="5227a-224">Následující kód demonstruje použití `List.sum`, `List.sumBy`, a `List.average`.</span><span class="sxs-lookup"><span data-stu-id="5227a-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="5227a-225">Výstup je `1.000000`.</span><span class="sxs-lookup"><span data-stu-id="5227a-225">The output is `1.000000`.</span></span>

<span data-ttu-id="5227a-226">Následující kód ukazuje použití `List.averageBy`.</span><span class="sxs-lookup"><span data-stu-id="5227a-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="5227a-227">Výstup je `5.5`.</span><span class="sxs-lookup"><span data-stu-id="5227a-227">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="5227a-228">Seznamy a řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="5227a-228">Lists and Tuples</span></span>

<span data-ttu-id="5227a-229">Seznamy, které obsahují řazené kolekce členů, mohou být manipulovány funkcemi zip a deextrahování.</span><span class="sxs-lookup"><span data-stu-id="5227a-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="5227a-230">Tyto funkce kombinují dva seznamy jednotlivých hodnot do jednoho seznamu řazených kolekcí členů nebo oddělují jeden seznam řazených kolekcí členů do dvou seznamů s jednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="5227a-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="5227a-231">Nejjednodušší funkce [list. zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) přebírá dva seznamy jednoho prvku a vytváří jeden seznam párů řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="5227a-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="5227a-232">Jiná verze, [list. zip3 –](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), používá tři seznamy jednoho prvku a vytváří jeden seznam řazených kolekcí členů, které mají tři prvky.</span><span class="sxs-lookup"><span data-stu-id="5227a-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="5227a-233">Následující příklad kódu ukazuje použití `List.zip`.</span><span class="sxs-lookup"><span data-stu-id="5227a-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="5227a-234">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-234">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="5227a-235">Následující příklad kódu ukazuje použití `List.zip3`.</span><span class="sxs-lookup"><span data-stu-id="5227a-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="5227a-236">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-236">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="5227a-237">Příslušné deunzip3 –ované verze, [list.](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) rozbalení a [list.](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), převezmou seznamy řazených kolekcí členů a návratové seznamy v řazené kolekci členů, kde první seznam obsahuje všechny prvky, které byly první v každé řazené kolekci členů, a druhý seznam obsahuje druhý prvek každého z nich. řazená kolekce členů atd.</span><span class="sxs-lookup"><span data-stu-id="5227a-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="5227a-238">Následující příklad kódu ukazuje použití [seznamu. dekomprimovat](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="5227a-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="5227a-239">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-239">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="5227a-240">Následující příklad kódu ukazuje použití [seznamu. unzip3 –](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="5227a-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="5227a-241">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-241">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="5227a-242">Provoz na prvcích seznamu</span><span class="sxs-lookup"><span data-stu-id="5227a-242">Operating on List Elements</span></span>

<span data-ttu-id="5227a-243">F#podporuje různé operace na prvcích seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="5227a-244">Nejjednodušší je [list. ITER](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), který umožňuje zavolat funkci na každý prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="5227a-245">Mezi variace patří [list. iter2 –](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), který umožňuje provést operaci na prvcích dvou seznamů, [list. ITERA](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), `List.iter` což se znamená, že index každého prvku je předán jako argument funkci, která je volána pro každý element a [list. iteri2 –](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), což je kombinace funkcí `List.iter2` a. `List.iteri`</span><span class="sxs-lookup"><span data-stu-id="5227a-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="5227a-246">Následující příklad kódu znázorňuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="5227a-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="5227a-247">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-247">The output is as follows:</span></span>

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

<span data-ttu-id="5227a-248">Další často používanou funkcí, která transformuje prvky seznamu, je [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), který umožňuje použít funkci na každý prvek seznamu a umístit všechny výsledky do nového seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="5227a-249">[List. MAP2 –](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) a [list. map3 –](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) jsou variace, které přijímají více seznamů.</span><span class="sxs-lookup"><span data-stu-id="5227a-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="5227a-250">Můžete také použít [seznam. MAPI](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) a [list. mapi2 –](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), pokud kromě prvku musí být funkce předána index každého prvku.</span><span class="sxs-lookup"><span data-stu-id="5227a-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="5227a-251">Jediný rozdíl mezi `List.mapi2` a `List.mapi` je to, `List.mapi2` že funguje se dvěma seznamy.</span><span class="sxs-lookup"><span data-stu-id="5227a-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="5227a-252">Následující příklad ukazuje [list. map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span><span class="sxs-lookup"><span data-stu-id="5227a-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="5227a-253">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-253">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="5227a-254">Následující příklad ukazuje použití `List.map2`.</span><span class="sxs-lookup"><span data-stu-id="5227a-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="5227a-255">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-255">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="5227a-256">Následující příklad ukazuje použití `List.map3`.</span><span class="sxs-lookup"><span data-stu-id="5227a-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="5227a-257">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-257">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="5227a-258">Následující příklad ukazuje použití `List.mapi`.</span><span class="sxs-lookup"><span data-stu-id="5227a-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="5227a-259">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-259">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="5227a-260">Následující příklad ukazuje použití `List.mapi2`.</span><span class="sxs-lookup"><span data-stu-id="5227a-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="5227a-261">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-261">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="5227a-262">[List. Collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) se podobá `List.map`, s tím rozdílem, že každý prvek vytvoří seznam a všechny tyto seznamy jsou zřetězené do konečného seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="5227a-263">V následujícím kódu každý prvek seznamu generuje tři čísla.</span><span class="sxs-lookup"><span data-stu-id="5227a-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="5227a-264">Všechny jsou shromažďovány v jednom seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="5227a-265">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-265">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="5227a-266">Můžete také použít [seznam. Filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), který používá logickou podmínku a vytvoří nový seznam, který se skládá pouze z prvků, které odpovídají dané podmínce.</span><span class="sxs-lookup"><span data-stu-id="5227a-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="5227a-267">Výsledný seznam je `[2; 4; 6]`.</span><span class="sxs-lookup"><span data-stu-id="5227a-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="5227a-268">Kombinace map a filtrů, [list. Volba](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) umožňuje transformovat a vybírat prvky současně.</span><span class="sxs-lookup"><span data-stu-id="5227a-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="5227a-269">`List.choose`použije funkci, která vrátí možnost na každý prvek seznamu a vrátí nový seznam výsledků pro prvky, pokud funkce vrátí hodnotu `Some`možnosti.</span><span class="sxs-lookup"><span data-stu-id="5227a-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="5227a-270">Následující kód demonstruje použití `List.choose` pro výběr slov se velkými písmeny ze seznamu slov.</span><span class="sxs-lookup"><span data-stu-id="5227a-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="5227a-271">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="5227a-271">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="5227a-272">Provoz na více seznamech</span><span class="sxs-lookup"><span data-stu-id="5227a-272">Operating on Multiple Lists</span></span>

<span data-ttu-id="5227a-273">Seznamy lze spojit dohromady.</span><span class="sxs-lookup"><span data-stu-id="5227a-273">Lists can be joined together.</span></span> <span data-ttu-id="5227a-274">Chcete-li spojit dva seznamy do jednoho, použijte příkaz [list. Append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span><span class="sxs-lookup"><span data-stu-id="5227a-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="5227a-275">Chcete-li spojit více než dva seznamy, použijte [list. Concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span><span class="sxs-lookup"><span data-stu-id="5227a-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="5227a-276">Operace skládání a skenování</span><span class="sxs-lookup"><span data-stu-id="5227a-276">Fold and Scan Operations</span></span>

<span data-ttu-id="5227a-277">Některé operace se seznamem zahrnují vzájemné závislosti mezi všemi prvky seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="5227a-278">Operace skládání a prověřování jsou podobné `List.iter` a `List.map` v tom, že vyvoláte funkci na každém elementu, ale tyto operace poskytují další parametr s názvem *akumulátor* , který přenáší informace prostřednictvím výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5227a-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="5227a-279">Slouží `List.fold` k provedení výpočtu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="5227a-280">Následující příklad kódu ukazuje použití [seznamu. skládání](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) k provádění různých operací.</span><span class="sxs-lookup"><span data-stu-id="5227a-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="5227a-281">Seznam je proprocházený. Akumulovaná `acc` je hodnota, která se předává společně s tím, jak výpočet pokračuje.</span><span class="sxs-lookup"><span data-stu-id="5227a-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="5227a-282">První argument přebírá Akumulovaná a element list a vrací průběžný výsledek výpočtu pro tento prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="5227a-283">Druhým argumentem je počáteční hodnota akumulátoru.</span><span class="sxs-lookup"><span data-stu-id="5227a-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="5227a-284">Verze těchto funkcí, které mají číslice v názvu funkce, fungují ve více než jednom seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="5227a-285">Například [list. fold2 –](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) provádí výpočty na dvou seznamech.</span><span class="sxs-lookup"><span data-stu-id="5227a-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="5227a-286">Následující příklad ukazuje použití `List.fold2`.</span><span class="sxs-lookup"><span data-stu-id="5227a-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="5227a-287">`List.fold`a [list. Scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) se liší v `List.fold` , který vrací konečnou hodnotu nadbytečného parametru, `List.scan` ale vrátí seznam mezilehlých hodnot (spolu s konečnou hodnotou) nadbytečného parametru.</span><span class="sxs-lookup"><span data-stu-id="5227a-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="5227a-288">Každá z těchto funkcí obsahuje opačnou variaci, například [list. foldBack –](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), která se liší v pořadí, ve kterém je seznam procházen, a pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="5227a-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="5227a-289">A mít také variace, [list. fold2 –](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) a [list. foldBack2 –](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), které přebírají dva seznamy stejné délky. `List.foldBack` `List.fold`</span><span class="sxs-lookup"><span data-stu-id="5227a-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="5227a-290">Funkce, která se spustí u každého prvku, může k provedení určité akce použít odpovídající prvky obou seznamů.</span><span class="sxs-lookup"><span data-stu-id="5227a-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="5227a-291">Typy prvků dvou seznamů mohou být rozdílné, jako v následujícím příkladu, ve kterém jeden seznam obsahuje částky transakcí pro bankovní účet a druhý seznam obsahuje typ transakce: vklad nebo disstoupit.</span><span class="sxs-lookup"><span data-stu-id="5227a-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="5227a-292">Pro výpočet, jako je suma `List.fold` , `List.foldBack` a mít stejný účinek, protože výsledek není závislý na pořadí procházení.</span><span class="sxs-lookup"><span data-stu-id="5227a-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="5227a-293">V následujícím příkladu `List.foldBack` se používá pro přidání prvků v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5227a-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="5227a-294">Následující příklad vrátí na příklad bankovního účtu.</span><span class="sxs-lookup"><span data-stu-id="5227a-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="5227a-295">Tentokrát se přidá nový typ transakce: výpočet úroku.</span><span class="sxs-lookup"><span data-stu-id="5227a-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="5227a-296">Koncový zůstatek nyní závisí na pořadí transakcí.</span><span class="sxs-lookup"><span data-stu-id="5227a-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="5227a-297">Seznam funkcí [. snížení](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) je poněkud podobné `List.fold` a `List.scan`, s výjimkou toho, že místo předání samostatného hromadění, `List.reduce` přebírá funkci, která přijímá dva argumenty typu elementu namísto pouze jednoho a jednoho z nich. argumenty slouží jako akumulátor, což znamená, že ukládá mezilehlé výsledky výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5227a-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="5227a-298">`List.reduce`začíná při práci na prvních dvou prvcích seznamu a poté používá výsledek operace spolu s dalším prvkem.</span><span class="sxs-lookup"><span data-stu-id="5227a-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="5227a-299">Vzhledem k tomu, že není k dispozici samostatný akumulátor, který má `List.reduce` svůj vlastní typ, lze použít `List.fold` místo pouze v případě, že je typ akumulátoru a typ elementu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="5227a-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="5227a-300">Následující kód demonstruje použití `List.reduce`.</span><span class="sxs-lookup"><span data-stu-id="5227a-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="5227a-301">`List.reduce`vyvolá výjimku, pokud zadaný seznam neobsahuje žádné elementy.</span><span class="sxs-lookup"><span data-stu-id="5227a-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="5227a-302">V následujícím kódu je první volání lambda výrazu uděleno argumenty 2 a 4 a vrátí hodnotu 6 a další volání je uděleno argumenty 6 a 10, takže výsledek je 16.</span><span class="sxs-lookup"><span data-stu-id="5227a-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="5227a-303">Převod mezi seznamy a jinými typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="5227a-303">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="5227a-304">`List` Modul poskytuje funkce pro převod do a z obou sekvencí a polí.</span><span class="sxs-lookup"><span data-stu-id="5227a-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="5227a-305">Pro převod na nebo z sekvence použijte [list. toSeq –](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) nebo [list. ofSeq –](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span><span class="sxs-lookup"><span data-stu-id="5227a-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="5227a-306">Pro převod na nebo z pole použijte [list. ToArray –](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) nebo [list. ofArray –](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span><span class="sxs-lookup"><span data-stu-id="5227a-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="5227a-307">Další operace</span><span class="sxs-lookup"><span data-stu-id="5227a-307">Additional Operations</span></span>

<span data-ttu-id="5227a-308">Další informace o dalších operacích v seznamech naleznete v tématu věnovaném [modulům Reference Library Collections. list](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="5227a-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="5227a-309">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5227a-309">See also</span></span>

- [<span data-ttu-id="5227a-310">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="5227a-310">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5227a-311">Typy F#</span><span class="sxs-lookup"><span data-stu-id="5227a-311">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="5227a-312">Sekvence</span><span class="sxs-lookup"><span data-stu-id="5227a-312">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="5227a-313">Pole</span><span class="sxs-lookup"><span data-stu-id="5227a-313">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="5227a-314">Možnosti</span><span class="sxs-lookup"><span data-stu-id="5227a-314">Options</span></span>](options.md)
