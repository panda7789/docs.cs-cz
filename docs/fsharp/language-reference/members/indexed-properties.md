---
title: Indexované vlastnosti (F#)
description: 'Další informace o F # indexované vlastnosti, které jsou vlastnosti, které poskytují přístup jako pole k datům seřazené.'
ms.date: 05/16/2016
ms.openlocfilehash: e56e4e2ea3f35df4c8ec46012357242cb6ce69f3
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "45994257"
---
# <a name="indexed-properties"></a><span data-ttu-id="4a0aa-103">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4a0aa-103">Indexed Properties</span></span>

<span data-ttu-id="4a0aa-104">*Indexované vlastnosti* jsou uspořádány ve vlastnosti, které poskytují přístup jako pole na data.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span> <span data-ttu-id="4a0aa-105">Přišli v tři formuláře:</span><span class="sxs-lookup"><span data-stu-id="4a0aa-105">They come in three forms:</span></span>

* `Item`
* `Ordinal`
* `Cardinal`

<span data-ttu-id="4a0aa-106">Člen F # musí mít název jedné z těchto tří názvů a zajistit tak přístup jako pole.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-106">An F# member must be named one of these three names to provide array-like access.</span></span> <span data-ttu-id="4a0aa-107">`IndexerName` se používá k reprezentování některý z následujících tří možností:</span><span class="sxs-lookup"><span data-stu-id="4a0aa-107">`IndexerName` is used to represent any of the three options below:</span></span>

## <a name="syntax"></a><span data-ttu-id="4a0aa-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a0aa-108">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.IndexerName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.IndexerName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.IndexerName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.IndexerName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="4a0aa-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a0aa-109">Remarks</span></span>

<span data-ttu-id="4a0aa-110">Formy syntaxe předchozí ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metodu, mají `get` metoda pouze, nebo mít `set` pouze metody.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-110">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="4a0aa-111">Můžete také zkombinovat obojí tomu syntaxe uvedená jenom příkaz get a syntaxi pro sadu pouze a vytvoří vlastnost, která má get a set.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-111">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="4a0aa-112">Tento druhý formulář umožňuje umístit různou přístupností. modifikátorů a vlastností atributy na get a set metod.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-112">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="4a0aa-113">Když *IndexerName* je `Item`, kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-113">When the *IndexerName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="4a0aa-114">A *výchozí indexovanou vlastnost* vlastností, která může získat přístup pomocí syntaxe pro pole na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-114">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="4a0aa-115">Například pokud `obj` je objekt typu, který definuje tato vlastnost syntaxe `obj.[index]` slouží k přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-115">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="4a0aa-116">Syntaxe pro přístup k nevýchozí indexované vlastnosti je název vlastnosti a index v závorkách.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-116">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="4a0aa-117">Například, pokud je vlastnost `Ordinal`, psaní `obj.Ordinal(index)` k němu přistupovat.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-117">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="4a0aa-118">Bez ohledu na to, jaký tvar použijete, byste měli vždy používat curryfikované formulář pro `set` metoda indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-118">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="4a0aa-119">Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="4a0aa-119">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="4a0aa-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a0aa-120">Example</span></span>

<span data-ttu-id="4a0aa-121">Následující příklad kódu ukazuje definice a používání výchozích a jiné než výchozí indexované vlastnosti, které mají get a set metod.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-121">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="4a0aa-122">Výstup</span><span class="sxs-lookup"><span data-stu-id="4a0aa-122">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="4a0aa-123">Indexované vlastnosti v případě více proměnných indexu</span><span class="sxs-lookup"><span data-stu-id="4a0aa-123">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="4a0aa-124">Indexované vlastnosti můžou mít více než jeden indexovaná proměnná.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-124">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="4a0aa-125">Proměnné v takovém případě jsou odděleny čárkami, pokud se vlastnost používá.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-125">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="4a0aa-126">Metoda set v těchto vlastností musí mít dva curryfikované argumenty, první z nich je řazená kolekce členů obsahující klíče a druhý z nich je hodnota nastavena.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-126">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="4a0aa-127">Následující kód ukazuje použití indexovaná vlastnost s několika proměnnými indexu.</span><span class="sxs-lookup"><span data-stu-id="4a0aa-127">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="4a0aa-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a0aa-128">See also</span></span>

- [<span data-ttu-id="4a0aa-129">Členové</span><span class="sxs-lookup"><span data-stu-id="4a0aa-129">Members</span></span>](index.md)
