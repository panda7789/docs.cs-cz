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
# <a name="lists"></a><span data-ttu-id="71f8c-103">Seznamy</span><span class="sxs-lookup"><span data-stu-id="71f8c-103">Lists</span></span>

<span data-ttu-id="71f8c-104">Seznam v jazyce F # je seřazená, neproměnlivá řada prvků stejného typu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-104">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="71f8c-105">K provádění základních operací na seznamech použijte funkce v [modulu seznam](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="71f8c-105">To perform basic operations on lists, use the functions in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="creating-and-initializing-lists"></a><span data-ttu-id="71f8c-106">Vytváření a inicializace seznamů</span><span class="sxs-lookup"><span data-stu-id="71f8c-106">Creating and Initializing Lists</span></span>

<span data-ttu-id="71f8c-107">Seznam můžete definovat explicitním seznamem prvků oddělených středníky a uzavřenými do hranatých závorek, jak je znázorněno na následujícím řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-107">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="71f8c-108">Můžete také umístit zalomení řádků mezi prvky, v takovém případě jsou středníky volitelné.</span><span class="sxs-lookup"><span data-stu-id="71f8c-108">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="71f8c-109">Druhá syntaxe může vést k čitelnějšímu kódu, když jsou inicializační výrazy prvku delší nebo pokud chcete zahrnout komentář pro každý prvek.</span><span class="sxs-lookup"><span data-stu-id="71f8c-109">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="71f8c-110">V normálním případě musí být všechny prvky seznamu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-110">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="71f8c-111">Výjimkou je, že seznam, ve kterém jsou prvky určeny jako základní typ, může mít elementy, které jsou odvozeny typy.</span><span class="sxs-lookup"><span data-stu-id="71f8c-111">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="71f8c-112">Proto je možné, že následující podmínky jsou přijatelné, protože `Button` a `CheckBox` jsou odvozeny z `Control` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-112">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="71f8c-113">Můžete také definovat prvky seznamu pomocí rozsahu, který je určen pomocí celých čísel oddělených operátorem Range ( `..` ), jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-113">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="71f8c-114">Prázdný seznam je určený dvojicí hranatých závorek bez jakéhokoli mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="71f8c-114">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="71f8c-115">Můžete také použít výraz pořadí k vytvoření seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-115">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="71f8c-116">Další informace naleznete v tématu [výrazy sekvence](sequences.md#sequence-expressions) .</span><span class="sxs-lookup"><span data-stu-id="71f8c-116">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="71f8c-117">Například následující kód vytvoří seznam čtverců celých čísel od 1 do 10.</span><span class="sxs-lookup"><span data-stu-id="71f8c-117">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="71f8c-118">Operátory pro práci se seznamy</span><span class="sxs-lookup"><span data-stu-id="71f8c-118">Operators for Working with Lists</span></span>

<span data-ttu-id="71f8c-119">Prvky můžete k seznamu připojit pomocí `::` operátoru (nevýhody).</span><span class="sxs-lookup"><span data-stu-id="71f8c-119">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="71f8c-120">`list1`V případě `[2; 3; 4]` , následující kód vytvoří `list2` jako `[100; 2; 3; 4]` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-120">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="71f8c-121">Seznamy, které mají kompatibilní typy, lze zřetězit pomocí `@` operátoru, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-121">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="71f8c-122">Pokud `list1` je `[2; 3; 4]` a `list2` `[100; 2; 3; 4]` , tento kód vytvoří `list3` jako `[2; 3; 4; 100; 2; 3; 4]` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-122">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="71f8c-123">Funkce pro provádění operací v seznamech jsou k dispozici v [modulu seznam](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="71f8c-123">Functions for performing operations on lists are available in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

<span data-ttu-id="71f8c-124">Vzhledem k tomu, že seznamy v jazyce F # jsou neměnné, všechny úpravy operací generují nové seznamy místo úprav existujících seznamů.</span><span class="sxs-lookup"><span data-stu-id="71f8c-124">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="71f8c-125">Seznamy v jazyce F # jsou implementovány jako jednotlivě propojené seznamy, což znamená, že operace, které mají přístup pouze k hlavičce seznamu, mají hodnotu O (1) a přístup k prvkům je O (*n*).</span><span class="sxs-lookup"><span data-stu-id="71f8c-125">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>

## <a name="properties"></a><span data-ttu-id="71f8c-126">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="71f8c-126">Properties</span></span>

<span data-ttu-id="71f8c-127">Typ seznamu podporuje následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="71f8c-127">The list type supports the following properties:</span></span>

|<span data-ttu-id="71f8c-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="71f8c-128">Property</span></span>|<span data-ttu-id="71f8c-129">Typ</span><span class="sxs-lookup"><span data-stu-id="71f8c-129">Type</span></span>|<span data-ttu-id="71f8c-130">Popis</span><span class="sxs-lookup"><span data-stu-id="71f8c-130">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="71f8c-131">Záhlaví</span><span class="sxs-lookup"><span data-stu-id="71f8c-131">Head</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head)|`'T`|<span data-ttu-id="71f8c-132">První prvek.</span><span class="sxs-lookup"><span data-stu-id="71f8c-132">The first element.</span></span>|
|[<span data-ttu-id="71f8c-133">Obsahovat</span><span class="sxs-lookup"><span data-stu-id="71f8c-133">Empty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Empty)|`'T list`|<span data-ttu-id="71f8c-134">Statická vlastnost, která vrací prázdný seznam příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-134">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="71f8c-135">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="71f8c-135">IsEmpty</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#IsEmpty)|`bool`|<span data-ttu-id="71f8c-136">`true` Pokud seznam neobsahuje žádné prvky.</span><span class="sxs-lookup"><span data-stu-id="71f8c-136">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="71f8c-137">Položka</span><span class="sxs-lookup"><span data-stu-id="71f8c-137">Item</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Item)|`'T`|<span data-ttu-id="71f8c-138">Prvek na zadaném indexu (založený na nule).</span><span class="sxs-lookup"><span data-stu-id="71f8c-138">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="71f8c-139">Délka</span><span class="sxs-lookup"><span data-stu-id="71f8c-139">Length</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Length)|`int`|<span data-ttu-id="71f8c-140">Počet elementů.</span><span class="sxs-lookup"><span data-stu-id="71f8c-140">The number of elements.</span></span>|
|[<span data-ttu-id="71f8c-141">Koncová část</span><span class="sxs-lookup"><span data-stu-id="71f8c-141">Tail</span></span>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail)|`'T list`|<span data-ttu-id="71f8c-142">Seznam bez prvního prvku</span><span class="sxs-lookup"><span data-stu-id="71f8c-142">The list without the first element.</span></span>|

<span data-ttu-id="71f8c-143">Níže jsou uvedeny některé příklady použití těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="71f8c-143">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]

## <a name="using-lists"></a><span data-ttu-id="71f8c-144">Používání seznamů</span><span class="sxs-lookup"><span data-stu-id="71f8c-144">Using Lists</span></span>

<span data-ttu-id="71f8c-145">Programování se seznamy vám umožňuje provádět komplexní operace s malým množstvím kódu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-145">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="71f8c-146">Tato část popisuje běžné operace se seznamy, které jsou důležité pro funkční programování.</span><span class="sxs-lookup"><span data-stu-id="71f8c-146">This section describes common operations on lists that are important to functional programming.</span></span>

### <a name="recursion-with-lists"></a><span data-ttu-id="71f8c-147">Rekurze se seznamy</span><span class="sxs-lookup"><span data-stu-id="71f8c-147">Recursion with Lists</span></span>

<span data-ttu-id="71f8c-148">Seznamy jsou jedinečně uzpůsobeny rekurzivním programovacím technikům.</span><span class="sxs-lookup"><span data-stu-id="71f8c-148">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="71f8c-149">Zvažte operaci, která musí být provedena u každého prvku seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-149">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="71f8c-150">To lze provést rekurzivně na začátku seznamu a následným předáním konce seznamu, který je menší seznam, který se skládá z původního seznamu bez prvního prvku, zpět na další úroveň rekurze.</span><span class="sxs-lookup"><span data-stu-id="71f8c-150">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="71f8c-151">Chcete-li zapsat takovou rekurzivní funkci, použijte operátor nevýhody ( `::` ) v porovnávání vzorů, což umožňuje oddělit záhlaví seznamu od konce.</span><span class="sxs-lookup"><span data-stu-id="71f8c-151">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="71f8c-152">Následující příklad kódu ukazuje, jak použít porovnávání vzorů pro implementaci rekurzivní funkce, která provádí operace na seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-152">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="71f8c-153">Předchozí kód funguje dobře u malých seznamů, ale u větších seznamů může přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="71f8c-153">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="71f8c-154">Následující kód vylepšuje tento kód pomocí argumentu Akumulovaná, standardní technika pro práci s rekurzivními funkcemi.</span><span class="sxs-lookup"><span data-stu-id="71f8c-154">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="71f8c-155">Použití argumentu akumulátoru způsobí rekurzivní funkci na konci, která šetří místo v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="71f8c-155">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="71f8c-156">Funkce `RemoveAllMultiples` je rekurzivní funkce, která přijímá dva seznamy.</span><span class="sxs-lookup"><span data-stu-id="71f8c-156">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="71f8c-157">První seznam obsahuje čísla, jejichž násobky budou odebrány, a druhý seznam je seznam, ze kterého mají být čísla odebrána.</span><span class="sxs-lookup"><span data-stu-id="71f8c-157">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="71f8c-158">Kód v následujícím příkladě používá tuto rekurzivní funkci k vyloučení všech nekoncových čísel ze seznamu, přičemž seznam koncových čísel se vynechává jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="71f8c-158">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="71f8c-159">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-159">The output is as follows:</span></span>

```console
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="71f8c-160">Funkce modulu</span><span class="sxs-lookup"><span data-stu-id="71f8c-160">Module Functions</span></span>

<span data-ttu-id="71f8c-161">[Modul seznamu](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) poskytuje funkce, které přistupují k prvkům seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-161">The [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html) provides functions that access the elements of a list.</span></span> <span data-ttu-id="71f8c-162">Hlavní prvek je nejrychlejší a nejjednodušší pro přístup.</span><span class="sxs-lookup"><span data-stu-id="71f8c-162">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="71f8c-163">Použijte [záhlaví](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) vlastnosti nebo seznam funkcí modulu [. Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head).</span><span class="sxs-lookup"><span data-stu-id="71f8c-163">Use the property [Head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Head) or the module function [List.head](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#head).</span></span> <span data-ttu-id="71f8c-164">K zakončení seznamu můžete přistupovat pomocí vlastnosti [Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) nebo funkce [list. tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) .</span><span class="sxs-lookup"><span data-stu-id="71f8c-164">You can access the tail of a list by using the [Tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-list-1.html#Tail) property or the [List.tail](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tail) function.</span></span> <span data-ttu-id="71f8c-165">Chcete-li najít element podle indexu, použijte funkci [list. n](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) .</span><span class="sxs-lookup"><span data-stu-id="71f8c-165">To find an element by index, use the [List.nth](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#nth) function.</span></span> <span data-ttu-id="71f8c-166">`List.nth` projde seznam.</span><span class="sxs-lookup"><span data-stu-id="71f8c-166">`List.nth` traverses the list.</span></span> <span data-ttu-id="71f8c-167">Proto má hodnotu O (*n*).</span><span class="sxs-lookup"><span data-stu-id="71f8c-167">Therefore, it is O(*n*).</span></span> <span data-ttu-id="71f8c-168">Pokud váš kód používá `List.nth` často, možná budete chtít zvážit použití pole namísto seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-168">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="71f8c-169">Přístup k prvkům v polích je O (1).</span><span class="sxs-lookup"><span data-stu-id="71f8c-169">Element access in arrays is O(1).</span></span>

### <a name="boolean-operations-on-lists"></a><span data-ttu-id="71f8c-170">Logické operace na seznamech</span><span class="sxs-lookup"><span data-stu-id="71f8c-170">Boolean Operations on Lists</span></span>

<span data-ttu-id="71f8c-171">Funkce [list... Empty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) určuje, zda má seznam nějaké prvky.</span><span class="sxs-lookup"><span data-stu-id="71f8c-171">The [List.isEmpty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#isEmpty) function determines whether a list has any elements.</span></span>

<span data-ttu-id="71f8c-172">Funkce [list. Exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) používá logický test na prvky seznamu a vrací, `true` Pokud některý prvek splňuje podmínky testu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-172">The [List.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="71f8c-173">[List. exists2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) je podobný, ale pracuje na po sobě jdoucích dvojic prvků ve dvou seznamech.</span><span class="sxs-lookup"><span data-stu-id="71f8c-173">[List.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#exists2) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="71f8c-174">Následující kód demonstruje použití `List.exists` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-174">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="71f8c-175">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-175">The output is as follows:</span></span>

```console
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="71f8c-176">Následující příklad ukazuje použití `List.exists2` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-176">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="71f8c-177">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-177">The output is as follows:</span></span>

```console
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="71f8c-178">[Seznam. ForAll](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) můžete použít, pokud chcete otestovat, zda všechny prvky seznamu splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="71f8c-178">You can use [List.forall](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="71f8c-179">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-179">The output is as follows:</span></span>

```console
true
false
```

<span data-ttu-id="71f8c-180">Podobně [seznam. forall2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) určuje, zda všechny prvky v odpovídajících pozicích ve dvou seznamech odpovídají logickému výrazu, který zahrnuje každou dvojici prvků.</span><span class="sxs-lookup"><span data-stu-id="71f8c-180">Similarly, [List.forall2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#forall2) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="71f8c-181">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-181">The output is as follows:</span></span>

```console
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="71f8c-182">Seřadit operace v seznamech</span><span class="sxs-lookup"><span data-stu-id="71f8c-182">Sort Operations on Lists</span></span>

<span data-ttu-id="71f8c-183">Seznam. [Sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [list. sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy)a [list. sortWith –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) Functions Sort lists.</span><span class="sxs-lookup"><span data-stu-id="71f8c-183">The [List.sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sort), [List.sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortBy), and [List.sortWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sortWith) functions sort lists.</span></span> <span data-ttu-id="71f8c-184">Funkce řazení určuje, které z těchto tří funkcí použít.</span><span class="sxs-lookup"><span data-stu-id="71f8c-184">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="71f8c-185">`List.sort` používá výchozí obecné porovnání.</span><span class="sxs-lookup"><span data-stu-id="71f8c-185">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="71f8c-186">Obecné porovnání používá pro porovnání hodnot globální operátory založené na funkci Generic Compare.</span><span class="sxs-lookup"><span data-stu-id="71f8c-186">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="71f8c-187">Funguje efektivně s širokou škálou typů prvků, jako jsou jednoduché číselné typy, řazené kolekce členů, záznamy, rozlišené sjednocení, seznamy, pole a jakýkoli typ, který implementuje `System.IComparable` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-187">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="71f8c-188">Pro typy, které implementují `System.IComparable` Obecné porovnání, používá `System.IComparable.CompareTo()` funkci.</span><span class="sxs-lookup"><span data-stu-id="71f8c-188">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="71f8c-189">Obecné porovnání funguje také s řetězci, ale používá pořadí řazení nezávislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="71f8c-189">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="71f8c-190">Obecné porovnání by nemělo být použito pro nepodporované typy, jako například typy funkcí.</span><span class="sxs-lookup"><span data-stu-id="71f8c-190">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="71f8c-191">Také výkon výchozího obecného porovnání je nejvhodnější pro malé strukturované typy; u větších strukturovaných typů, které je třeba porovnat a seřadit často, zvažte implementaci `System.IComparable` a poskytování efektivní implementace `System.IComparable.CompareTo()` metody.</span><span class="sxs-lookup"><span data-stu-id="71f8c-191">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="71f8c-192">`List.sortBy` převezme funkci, která vrací hodnotu, která se používá jako kritérium řazení, a `List.sortWith` jako argument použije funkci porovnání.</span><span class="sxs-lookup"><span data-stu-id="71f8c-192">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="71f8c-193">Tyto dvě funkce jsou užitečné, když pracujete s typy, které nepodporují porovnání, nebo když porovnání vyžaduje složitější sémantiku porovnání, jako v případě řetězců zohledňujících jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="71f8c-193">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="71f8c-194">Následující příklad ukazuje použití `List.sort` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-194">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="71f8c-195">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-195">The output is as follows:</span></span>

```console
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="71f8c-196">Následující příklad ukazuje použití `List.sortBy` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-196">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="71f8c-197">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-197">The output is as follows:</span></span>

```console
[1; -2; 4; 5; 8]
```

<span data-ttu-id="71f8c-198">Další příklad ukazuje použití `List.sortWith` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-198">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="71f8c-199">V tomto příkladu se vlastní srovnávací funkce `compareWidgets` používá k prvnímu porovnání jednoho pole vlastního typu a poté další, pokud jsou hodnoty prvního pole stejné.</span><span class="sxs-lookup"><span data-stu-id="71f8c-199">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="71f8c-200">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-200">The output is as follows:</span></span>

```console
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="71f8c-201">Vyhledat operace v seznamech</span><span class="sxs-lookup"><span data-stu-id="71f8c-201">Search Operations on Lists</span></span>

<span data-ttu-id="71f8c-202">Pro seznamy se podporuje celá řada operací hledání.</span><span class="sxs-lookup"><span data-stu-id="71f8c-202">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="71f8c-203">Nejjednodušší, [list. Find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), umožňuje najít první prvek, který odpovídá dané podmínce.</span><span class="sxs-lookup"><span data-stu-id="71f8c-203">The simplest, [List.find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#find), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="71f8c-204">Následující příklad kódu ukazuje použití nástroje `List.find` k nalezení prvního čísla, které je v seznamu dělitele 5.</span><span class="sxs-lookup"><span data-stu-id="71f8c-204">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="71f8c-205">Výsledek je 5.</span><span class="sxs-lookup"><span data-stu-id="71f8c-205">The result is 5.</span></span>

<span data-ttu-id="71f8c-206">Pokud elementy musí být transformovány jako první, zavolejte [list. vyskl](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), který převezme funkci, která vrací možnost a vyhledá první hodnotu možnosti, která je `Some(x)` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-206">If the elements must be transformed first, call [List.pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#pick), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="71f8c-207">Místo vrácení elementu `List.pick` vrátí výsledek `x` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-207">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="71f8c-208">Pokud se nenajde žádný vyhovující prvek, `List.pick` vyvolá `System.Collections.Generic.KeyNotFoundException` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-208">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="71f8c-209">Následující kód ukazuje použití `List.pick` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-209">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="71f8c-210">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-210">The output is as follows:</span></span>

```console
"b"
```

<span data-ttu-id="71f8c-211">Jiná skupina operací hledání, [list. tryFind –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) a související funkce, vrací hodnotu možnosti.</span><span class="sxs-lookup"><span data-stu-id="71f8c-211">Another group of search operations, [List.tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFind) and related functions, return an option value.</span></span> <span data-ttu-id="71f8c-212">`List.tryFind`Funkce vrátí první prvek seznamu, který splňuje podmínku, pokud takový prvek existuje, ale hodnota možnosti, `None` Pokud není.</span><span class="sxs-lookup"><span data-stu-id="71f8c-212">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="71f8c-213">Seznam variací [. tryFindIndex –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) vrátí index elementu, pokud je nalezen, spíše než samotný element.</span><span class="sxs-lookup"><span data-stu-id="71f8c-213">The variation [List.tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#tryFindIndex) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="71f8c-214">Tyto funkce jsou znázorněny v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-214">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="71f8c-215">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-215">The output is as follows:</span></span>

```console
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="71f8c-216">Aritmetické operace na seznamech</span><span class="sxs-lookup"><span data-stu-id="71f8c-216">Arithmetic Operations on Lists</span></span>

<span data-ttu-id="71f8c-217">Do [modulu seznamu](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)jsou integrovány běžné aritmetické operace, jako je součet a průměr.</span><span class="sxs-lookup"><span data-stu-id="71f8c-217">Common arithmetic operations such as sum and average are built into the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="71f8c-218">Pro práci se [seznamem. Sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum)musí typ elementu seznamu podporovat `+` operátor a mít nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-218">To work with [List.sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sum), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="71f8c-219">Všechny integrované aritmetické typy tyto podmínky vyhoví.</span><span class="sxs-lookup"><span data-stu-id="71f8c-219">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="71f8c-220">Pro práci se [seznamem. Average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average)musí typ elementu podporovat dělení bez zbytku, který vylučuje celočíselné typy, ale umožňuje použití typů s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="71f8c-220">To work with [List.average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#average), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="71f8c-221">Funkce [list. sumBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) a [list. averageBy –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) přebírají funkci jako parametr a výsledky této funkce se používají k výpočtu hodnot součtu nebo průměru.</span><span class="sxs-lookup"><span data-stu-id="71f8c-221">The [List.sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#sumBy) and [List.averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#averageBy) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="71f8c-222">Následující kód demonstruje použití `List.sum` , `List.sumBy` , a `List.average` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-222">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="71f8c-223">Výstup je `1.000000` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-223">The output is `1.000000`.</span></span>

<span data-ttu-id="71f8c-224">Následující kód ukazuje použití `List.averageBy` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-224">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="71f8c-225">Výstup je `5.5` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-225">The output is `5.5`.</span></span>

### <a name="lists-and-tuples"></a><span data-ttu-id="71f8c-226">Seznamy a řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="71f8c-226">Lists and Tuples</span></span>

<span data-ttu-id="71f8c-227">Seznamy, které obsahují řazené kolekce členů, mohou být manipulovány funkcemi zip a deextrahování.</span><span class="sxs-lookup"><span data-stu-id="71f8c-227">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="71f8c-228">Tyto funkce kombinují dva seznamy jednotlivých hodnot do jednoho seznamu řazených kolekcí členů nebo oddělují jeden seznam řazených kolekcí členů do dvou seznamů s jednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="71f8c-228">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="71f8c-229">Nejjednodušší funkce [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) přebírá dva seznamy jednoho prvku a vytváří jeden seznam párů řazených kolekcí členů.</span><span class="sxs-lookup"><span data-stu-id="71f8c-229">The simplest [List.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="71f8c-230">Jiná verze, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), používá tři seznamy jednoho prvku a vytváří jeden seznam řazených kolekcí členů, které mají tři prvky.</span><span class="sxs-lookup"><span data-stu-id="71f8c-230">Another version, [List.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#zip3), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="71f8c-231">Následující příklad kódu ukazuje použití `List.zip` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-231">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="71f8c-232">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-232">The output is as follows:</span></span>

```console
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="71f8c-233">Následující příklad kódu ukazuje použití `List.zip3` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-233">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="71f8c-234">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-234">The output is as follows:</span></span>

```console
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="71f8c-235">Příslušné rozbalení, [seznam.](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) rozbalení a [Výpis. unzip3 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), převezmou seznamy řazených kolekcí členů a návratové seznamy v řazené kolekci členů, kde první seznam obsahuje všechny prvky, které byly první v každé řazené kolekci členů, a druhý seznam obsahuje druhý prvek každé řazené kolekce členů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="71f8c-235">The corresponding unzip versions, [List.unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip) and [List.unzip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip3), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="71f8c-236">Následující příklad kódu ukazuje použití [seznamu. dekomprimovat](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span><span class="sxs-lookup"><span data-stu-id="71f8c-236">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="71f8c-237">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-237">The output is as follows:</span></span>

```console
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="71f8c-238">Následující příklad kódu ukazuje použití [seznamu. unzip3 –](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span><span class="sxs-lookup"><span data-stu-id="71f8c-238">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="71f8c-239">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-239">The output is as follows:</span></span>

```console
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="71f8c-240">Provoz na prvcích seznamu</span><span class="sxs-lookup"><span data-stu-id="71f8c-240">Operating on List Elements</span></span>

<span data-ttu-id="71f8c-241">Jazyk F # podporuje různé operace na prvcích seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-241">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="71f8c-242">Nejjednodušší je [list. ITER](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter), který umožňuje zavolat funkci na každý prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-242">The simplest is [List.iter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="71f8c-243">Variace zahrnují [list. iter2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), který umožňuje provést operaci na prvcích dvou seznamů, [list. iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), což se znamená `List.iter` , že index každého prvku je předán jako argument funkci, která je volána pro každý prvek, a [list. iteri2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), což je kombinace funkcí `List.iter2` a `List.iteri` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-243">Variations include [List.iter2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iter2), which enables you to perform an operation on elements of two lists, [List.iteri](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#iteri2), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="71f8c-244">Následující příklad kódu znázorňuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="71f8c-244">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="71f8c-245">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-245">The output is as follows:</span></span>

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

<span data-ttu-id="71f8c-246">Další často používanou funkcí, která transformuje prvky seznamu, je [list. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), který umožňuje použít funkci na každý prvek seznamu a umístit všechny výsledky do nového seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-246">Another frequently used function that transforms list elements is [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="71f8c-247">[List. MAP2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) a [list. map3 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) jsou variace, které přijímají více seznamů.</span><span class="sxs-lookup"><span data-stu-id="71f8c-247">[List.map2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map2) and [List.map3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map3) are variations that take multiple lists.</span></span> <span data-ttu-id="71f8c-248">Můžete také použít [seznam. MAPI](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) a [list. mapi2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), pokud kromě prvku musí být funkce předána index každého prvku.</span><span class="sxs-lookup"><span data-stu-id="71f8c-248">You can also use [List.mapi](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi) and [List.mapi2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#mapi2), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="71f8c-249">Jediný rozdíl mezi `List.mapi2` a `List.mapi` je to, že `List.mapi2` funguje se dvěma seznamy.</span><span class="sxs-lookup"><span data-stu-id="71f8c-249">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="71f8c-250">Následující příklad ukazuje [list. map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).</span><span class="sxs-lookup"><span data-stu-id="71f8c-250">The following example illustrates [List.map](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#map).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="71f8c-251">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-251">The output is as follows:</span></span>

```console
[2; 3; 4]
```

<span data-ttu-id="71f8c-252">Následující příklad ukazuje použití `List.map2` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-252">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="71f8c-253">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-253">The output is as follows:</span></span>

```console
[5; 7; 9]
```

<span data-ttu-id="71f8c-254">Následující příklad ukazuje použití `List.map3` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-254">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="71f8c-255">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-255">The output is as follows:</span></span>

```console
[7; 10; 13]
```

<span data-ttu-id="71f8c-256">Následující příklad ukazuje použití `List.mapi` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-256">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="71f8c-257">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-257">The output is as follows:</span></span>

```console
[1; 3; 5]
```

<span data-ttu-id="71f8c-258">Následující příklad ukazuje použití `List.mapi2` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-258">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="71f8c-259">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-259">The output is as follows:</span></span>

```console
[0; 7; 18]
```

<span data-ttu-id="71f8c-260">[List. Collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) se podobá `List.map` , s tím rozdílem, že každý prvek vytvoří seznam a všechny tyto seznamy jsou zřetězené do konečného seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-260">[List.collect](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#collect) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="71f8c-261">V následujícím kódu každý prvek seznamu generuje tři čísla.</span><span class="sxs-lookup"><span data-stu-id="71f8c-261">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="71f8c-262">Všechny jsou shromažďovány v jednom seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-262">These are all collected into one list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="71f8c-263">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-263">The output is as follows:</span></span>

```console
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="71f8c-264">Můžete také použít [seznam. Filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), který používá logickou podmínku a vytvoří nový seznam, který se skládá pouze z prvků, které odpovídají dané podmínce.</span><span class="sxs-lookup"><span data-stu-id="71f8c-264">You can also use [List.filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#filter), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="71f8c-265">Výsledný seznam je `[2; 4; 6]` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-265">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="71f8c-266">Kombinace map a filtrů, [list. Volba](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) umožňuje transformovat a vybírat prvky současně.</span><span class="sxs-lookup"><span data-stu-id="71f8c-266">A combination of map and filter, [List.choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#choose) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="71f8c-267">`List.choose` použije funkci, která vrátí možnost na každý prvek seznamu a vrátí nový seznam výsledků pro prvky, pokud funkce vrátí hodnotu možnosti `Some` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-267">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="71f8c-268">Následující kód demonstruje použití `List.choose` pro výběr slov se velkými písmeny ze seznamu slov.</span><span class="sxs-lookup"><span data-stu-id="71f8c-268">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="71f8c-269">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="71f8c-269">The output is as follows:</span></span>

```console
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="71f8c-270">Provoz na více seznamech</span><span class="sxs-lookup"><span data-stu-id="71f8c-270">Operating on Multiple Lists</span></span>

<span data-ttu-id="71f8c-271">Seznamy lze spojit dohromady.</span><span class="sxs-lookup"><span data-stu-id="71f8c-271">Lists can be joined together.</span></span> <span data-ttu-id="71f8c-272">Chcete-li spojit dva seznamy do jednoho, použijte příkaz [list. Append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append).</span><span class="sxs-lookup"><span data-stu-id="71f8c-272">To join two lists into one, use [List.append](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#append).</span></span> <span data-ttu-id="71f8c-273">Chcete-li spojit více než dva seznamy, použijte [list. Concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).</span><span class="sxs-lookup"><span data-stu-id="71f8c-273">To join more than two lists, use [List.concat](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#concat).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet26.fs)]

### <a name="fold-and-scan-operations"></a><span data-ttu-id="71f8c-274">Operace skládání a skenování</span><span class="sxs-lookup"><span data-stu-id="71f8c-274">Fold and Scan Operations</span></span>

<span data-ttu-id="71f8c-275">Některé operace se seznamem zahrnují vzájemné závislosti mezi všemi prvky seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-275">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="71f8c-276">Operace skládání a prověřování jsou podobné `List.iter` a `List.map` v tom, že vyvoláte funkci na každém elementu, ale tyto operace poskytují další parametr s názvem *akumulátor* , který přenáší informace prostřednictvím výpočtu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-276">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="71f8c-277">Slouží `List.fold` k provedení výpočtu v seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-277">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="71f8c-278">Následující příklad kódu ukazuje použití [seznamu. skládání](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) k provádění různých operací.</span><span class="sxs-lookup"><span data-stu-id="71f8c-278">The following code example demonstrates the use of [List.fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold) to perform various operations.</span></span>

<span data-ttu-id="71f8c-279">Seznam je proprocházený. Akumulovaná `acc` je hodnota, která se předává společně s tím, jak výpočet pokračuje.</span><span class="sxs-lookup"><span data-stu-id="71f8c-279">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="71f8c-280">První argument přebírá Akumulovaná a element list a vrací průběžný výsledek výpočtu pro tento prvek seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-280">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="71f8c-281">Druhým argumentem je počáteční hodnota akumulátoru.</span><span class="sxs-lookup"><span data-stu-id="71f8c-281">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="71f8c-282">Verze těchto funkcí, které mají číslice v názvu funkce, fungují ve více než jednom seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-282">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="71f8c-283">Například [list. fold2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) provádí výpočty na dvou seznamech.</span><span class="sxs-lookup"><span data-stu-id="71f8c-283">For example, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) performs computations on two lists.</span></span>

<span data-ttu-id="71f8c-284">Následující příklad ukazuje použití `List.fold2` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-284">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="71f8c-285">`List.fold` a [list. Scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) se liší v, který `List.fold` vrací konečnou hodnotu nadbytečného parametru, ale `List.scan` vrátí seznam mezilehlých hodnot (spolu s konečnou hodnotou) nadbytečného parametru.</span><span class="sxs-lookup"><span data-stu-id="71f8c-285">`List.fold` and [List.scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#scan) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="71f8c-286">Každá z těchto funkcí obsahuje opačnou variaci, například [list. foldBack –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), která se liší v pořadí, ve kterém je seznam procházen, a pořadí argumentů.</span><span class="sxs-lookup"><span data-stu-id="71f8c-286">Each of these functions includes a reverse variation, for example, [List.foldBack](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="71f8c-287">`List.fold`A mít také `List.foldBack` variace, [list. fold2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) a [list. foldBack2 –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), které přebírají dva seznamy stejné délky.</span><span class="sxs-lookup"><span data-stu-id="71f8c-287">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#fold2) and [List.foldBack2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#foldBack2), that take two lists of equal length.</span></span> <span data-ttu-id="71f8c-288">Funkce, která se spustí u každého prvku, může k provedení určité akce použít odpovídající prvky obou seznamů.</span><span class="sxs-lookup"><span data-stu-id="71f8c-288">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="71f8c-289">Typy prvků dvou seznamů mohou být rozdílné, jako v následujícím příkladu, ve kterém jeden seznam obsahuje částky transakcí pro bankovní účet a druhý seznam obsahuje typ transakce: vklad nebo disstoupit.</span><span class="sxs-lookup"><span data-stu-id="71f8c-289">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="71f8c-290">Pro výpočet, jako je suma, `List.fold` a `List.foldBack` mít stejný účinek, protože výsledek není závislý na pořadí procházení.</span><span class="sxs-lookup"><span data-stu-id="71f8c-290">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="71f8c-291">V následujícím příkladu `List.foldBack` se používá pro přidání prvků v seznamu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-291">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="71f8c-292">Následující příklad vrátí na příklad bankovního účtu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-292">The following example returns to the bank account example.</span></span> <span data-ttu-id="71f8c-293">Tentokrát se přidá nový typ transakce: výpočet úroku.</span><span class="sxs-lookup"><span data-stu-id="71f8c-293">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="71f8c-294">Koncový zůstatek nyní závisí na pořadí transakcí.</span><span class="sxs-lookup"><span data-stu-id="71f8c-294">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="71f8c-295">Seznam funkcí [. zmenšení](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) je trochu podobné `List.fold` a `List.scan` , s výjimkou toho, že místo předání samostatného hromadění, `List.reduce` přebírá funkci, která přijímá dva argumenty typu elementu namísto pouze jednoho a jeden z těchto argumentů funguje jako akumulátor, což znamená, že ukládá mezivýsledek výpočtu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-295">The function [List.reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#reduce) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="71f8c-296">`List.reduce` začíná při práci na prvních dvou prvcích seznamu a poté používá výsledek operace spolu s dalším prvkem.</span><span class="sxs-lookup"><span data-stu-id="71f8c-296">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="71f8c-297">Vzhledem k tomu, že není k dispozici samostatný akumulátor, který má svůj vlastní typ, `List.reduce` lze použít místo pouze v případě, že je `List.fold` typ akumulátoru a typ elementu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="71f8c-297">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="71f8c-298">Následující kód demonstruje použití `List.reduce` .</span><span class="sxs-lookup"><span data-stu-id="71f8c-298">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="71f8c-299">`List.reduce` vyvolá výjimku, pokud zadaný seznam neobsahuje žádné elementy.</span><span class="sxs-lookup"><span data-stu-id="71f8c-299">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="71f8c-300">V následujícím kódu je první volání lambda výrazu uděleno argumenty 2 a 4 a vrátí hodnotu 6 a další volání je uděleno argumenty 6 a 10, takže výsledek je 16.</span><span class="sxs-lookup"><span data-stu-id="71f8c-300">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lists/snippet33.fs)]

### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="71f8c-301">Převod mezi seznamy a jinými typy kolekcí</span><span class="sxs-lookup"><span data-stu-id="71f8c-301">Converting Between Lists and Other Collection Types</span></span>

<span data-ttu-id="71f8c-302">`List`Modul poskytuje funkce pro převod do a z obou sekvencí a polí.</span><span class="sxs-lookup"><span data-stu-id="71f8c-302">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="71f8c-303">Pro převod na nebo z sekvence použijte [list. toSeq –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) nebo [list. ofSeq –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq).</span><span class="sxs-lookup"><span data-stu-id="71f8c-303">To convert to or from a sequence, use [List.toSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toSeq) or [List.ofSeq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofSeq).</span></span> <span data-ttu-id="71f8c-304">Pro převod na nebo z pole použijte [list. ToArray –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) nebo [list. ofArray –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).</span><span class="sxs-lookup"><span data-stu-id="71f8c-304">To convert to or from an array, use [List.toArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#toArray) or [List.ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#ofArray).</span></span>

### <a name="additional-operations"></a><span data-ttu-id="71f8c-305">Další operace</span><span class="sxs-lookup"><span data-stu-id="71f8c-305">Additional Operations</span></span>

<span data-ttu-id="71f8c-306">Informace o dalších operacích v seznamech naleznete v tématu Knihovna odkazů na [modul seznam](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)témat.</span><span class="sxs-lookup"><span data-stu-id="71f8c-306">For information about additional operations on lists, see the library reference topic [List Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="71f8c-307">Viz také</span><span class="sxs-lookup"><span data-stu-id="71f8c-307">See also</span></span>

- [<span data-ttu-id="71f8c-308">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="71f8c-308">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="71f8c-309">Typy F#</span><span class="sxs-lookup"><span data-stu-id="71f8c-309">F# Types</span></span>](fsharp-types.md)
- [<span data-ttu-id="71f8c-310">Sekvence</span><span class="sxs-lookup"><span data-stu-id="71f8c-310">Sequences</span></span>](sequences.md)
- [<span data-ttu-id="71f8c-311">Pole</span><span class="sxs-lookup"><span data-stu-id="71f8c-311">Arrays</span></span>](arrays.md)
- [<span data-ttu-id="71f8c-312">Možnosti</span><span class="sxs-lookup"><span data-stu-id="71f8c-312">Options</span></span>](options.md)
