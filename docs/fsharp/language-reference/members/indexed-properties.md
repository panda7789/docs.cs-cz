---
title: Indexované vlastnosti
description: Další informace o indexované vlastnosti v F#, které umožňují pro přístup jako pole k datům seřazené.
ms.date: 10/17/2018
ms.openlocfilehash: 7fc8f46e029255c6ed985a43b92c8f7c2908c428
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489487"
---
# <a name="indexed-properties"></a><span data-ttu-id="ce8ab-103">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ce8ab-103">Indexed Properties</span></span>

<span data-ttu-id="ce8ab-104">Při definování třídy, který získává přes seřazených dat, může být někdy užitečné poskytnout indexovaný přístup k těmto datům bez vystavení se základní implementací.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="ce8ab-105">Používá se k tomu `Item` člena.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="ce8ab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce8ab-106">Syntax</span></span>

```fsharp
// Indexed property that can be read and written to
member self-identifier.Item
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property can only be read
member self-identifier.Item
    with get(index-values) =
        get-member-body

// Indexed property that can only be set
member self-identifier.Item
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="ce8ab-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce8ab-107">Remarks</span></span>

<span data-ttu-id="ce8ab-108">Formy syntaxe předchozí ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metodu, mají `get` metoda pouze, nebo mít `set` pouze metody.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="ce8ab-109">Můžete také zkombinovat obojí tomu syntaxe uvedená jenom příkaz get a syntaxi pro sadu pouze a vytvoří vlastnost, která má get a set.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="ce8ab-110">Tento druhý formulář umožňuje umístit různou přístupností. modifikátorů a vlastností atributy na get a set metod.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="ce8ab-111">Pomocí názvu `Item`, kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="ce8ab-112">A *výchozí indexovanou vlastnost* vlastností, která může získat přístup pomocí syntaxe pro pole na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="ce8ab-113">Například pokud `o` je objekt typu, který definuje tato vlastnost syntaxe `o.[index]` slouží k přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="ce8ab-114">Syntaxe pro přístup k jiné než výchozí indexovaná vlastnost je k poskytnutí názvu vlastnosti a index v závorkách, stejně jako běžný člen.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="ce8ab-115">Například pokud vlastnost `o` nazývá `Ordinal`, psaní `o.Ordinal(index)` k němu přistupovat.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="ce8ab-116">Bez ohledu na to, jaký tvar používáte měli byste použít vždy curryfikované formuláře pro metodu set indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="ce8ab-117">Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce8ab-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="ce8ab-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce8ab-118">Example</span></span>

<span data-ttu-id="ce8ab-119">Následující příklad kódu ukazuje definice a používání výchozích a jiné než výchozí indexované vlastnosti, které mají get a set metod.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="ce8ab-120">Výstup</span><span class="sxs-lookup"><span data-stu-id="ce8ab-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="ce8ab-121">Indexované vlastnosti s více hodnotami indexu</span><span class="sxs-lookup"><span data-stu-id="ce8ab-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="ce8ab-122">Indexované vlastnosti můžou mít více než jedna hodnota indexu.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="ce8ab-123">V takovém případě hodnoty jsou oddělené čárkami, když se vlastnost používá.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="ce8ab-124">Metoda set v těchto vlastností musí mít dva curryfikované argumenty, první z nich řazené kolekce členů obsahující klíče a druhá z nich hodnota k nastavení.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="ce8ab-125">Následující kód ukazuje použití indexovaná vlastnost s více hodnotami indexu.</span><span class="sxs-lookup"><span data-stu-id="ce8ab-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member __.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a><span data-ttu-id="ce8ab-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce8ab-126">See also</span></span>

- [<span data-ttu-id="ce8ab-127">Členové</span><span class="sxs-lookup"><span data-stu-id="ce8ab-127">Members</span></span>](index.md)
