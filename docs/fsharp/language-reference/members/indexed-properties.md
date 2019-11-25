---
title: Indexované vlastnosti
description: Přečtěte si o indexovaných vlastnostech v F#, které umožňují přístup k seřazeným datům typu pole.
ms.date: 11/04/2019
ms.openlocfilehash: f6cf3bfa737d2bf458e379594be5884696cee3e1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976600"
---
# <a name="indexed-properties"></a><span data-ttu-id="d50fa-103">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d50fa-103">Indexed Properties</span></span>

<span data-ttu-id="d50fa-104">Při definování třídy, která je abstraktní nad seřazenými daty, může být někdy užitečná k poskytnutí indexovaného přístupu k těmto datům bez odhalení základní implementace.</span><span class="sxs-lookup"><span data-stu-id="d50fa-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="d50fa-105">To se provádí s členem `Item`.</span><span class="sxs-lookup"><span data-stu-id="d50fa-105">This is done with the `Item` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="d50fa-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d50fa-106">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="d50fa-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d50fa-107">Remarks</span></span>

<span data-ttu-id="d50fa-108">Formuláře předchozí syntaxe ukazují, jak definovat indexované vlastnosti, které mají jak `get`, tak `set` metoda, mají pouze `get` metodu nebo mají pouze `set` metodu.</span><span class="sxs-lookup"><span data-stu-id="d50fa-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="d50fa-109">Lze také kombinovat jak syntaxi zobrazenou pouze pro příkaz Get, syntaxi zobrazenou pouze pro sadu a vytvořit vlastnost, která má obě metody Get a set.</span><span class="sxs-lookup"><span data-stu-id="d50fa-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="d50fa-110">Tato druhá forma umožňuje umístit různé modifikátory a atributy dostupnosti do metod get a set.</span><span class="sxs-lookup"><span data-stu-id="d50fa-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="d50fa-111">Pomocí názvu `Item`kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d50fa-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="d50fa-112">*Výchozí indexovaná vlastnost* je vlastnost, ke které můžete přistupovat pomocí syntaxe typu pole v instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="d50fa-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="d50fa-113">Například pokud `o` je objekt typu, který definuje tuto vlastnost, `o.[index]` syntaxe se používá pro přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d50fa-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="d50fa-114">Syntaxe pro přístup k jiné než výchozí indexované vlastnosti je poskytnout název vlastnosti a indexu v závorkách, stejně jako regulární člen.</span><span class="sxs-lookup"><span data-stu-id="d50fa-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="d50fa-115">Například pokud je vlastnost na `o` volána `Ordinal`, zapíšete `o.Ordinal(index)` pro přístup k ní.</span><span class="sxs-lookup"><span data-stu-id="d50fa-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="d50fa-116">Bez ohledu na to, který formulář použijete, byste měli vždy použít formulář curryfikované pro metodu set pro indexovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d50fa-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="d50fa-117">Informace o funkcích curryfikované najdete v tématu [Functions](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="d50fa-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="d50fa-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d50fa-118">Example</span></span>

<span data-ttu-id="d50fa-119">Následující příklad kódu ukazuje definici a použití výchozích a nevýchozích indexovaných vlastností, které mají metody Get a set.</span><span class="sxs-lookup"><span data-stu-id="d50fa-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="d50fa-120">Výstup</span><span class="sxs-lookup"><span data-stu-id="d50fa-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-values"></a><span data-ttu-id="d50fa-121">Indexované vlastnosti s více hodnotami indexu</span><span class="sxs-lookup"><span data-stu-id="d50fa-121">Indexed Properties with multiple index values</span></span>

<span data-ttu-id="d50fa-122">Indexované vlastnosti můžou mít víc než jednu hodnotu indexu.</span><span class="sxs-lookup"><span data-stu-id="d50fa-122">Indexed properties can have more than one index value.</span></span> <span data-ttu-id="d50fa-123">V takovém případě jsou hodnoty odděleny čárkami při použití vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d50fa-123">In that case, the values are separated by commas when the property is used.</span></span> <span data-ttu-id="d50fa-124">Metoda set v takové vlastnosti musí mít dva argumenty curryfikované, první z nich je řazená kolekce členů obsahující klíče a druhá z nich je hodnota, kterou chcete nastavit.</span><span class="sxs-lookup"><span data-stu-id="d50fa-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value to set.</span></span>

<span data-ttu-id="d50fa-125">Následující kód demonstruje použití indexované vlastnosti s více hodnotami indexu.</span><span class="sxs-lookup"><span data-stu-id="d50fa-125">The following code demonstrates the use of an indexed property with multiple index values.</span></span>

```fsharp
open System.Collections.Generic

/// Basic implementation of a sparse matrix based on a dictionary
type SparseMatrix() =
    let table = new Dictionary<(int * int), float>()
    member _.Item
        // Because the key is comprised of two values, 'get' has two index values
        with get(key1, key2) = table.[(key1, key2)]

        // 'set' has two index values and a new value to place in the key's position
        and set (key1, key2) value = table.[(key1, key2)] <- value

let sm = new SparseMatrix()
for i in 1..1000 do
    sm.[i, i] <- float i * float i
```

## <a name="see-also"></a><span data-ttu-id="d50fa-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d50fa-126">See also</span></span>

- [<span data-ttu-id="d50fa-127">Členové</span><span class="sxs-lookup"><span data-stu-id="d50fa-127">Members</span></span>](index.md)
