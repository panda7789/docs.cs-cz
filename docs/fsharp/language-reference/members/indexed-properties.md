---
title: Indexované vlastnosti (F#)
description: 'Další informace o F # indexované vlastnosti, které jsou vlastnosti, které poskytují přístup jako pole k datům seřazené.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 39396b3a5ec43f9a8ab0df96afeb69e05801c752
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="indexed-properties"></a><span data-ttu-id="6a94a-103">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6a94a-103">Indexed Properties</span></span>

<span data-ttu-id="6a94a-104">*Indexované vlastnosti* seřazeni vlastnosti, které poskytují přístup jako pole k data.</span><span class="sxs-lookup"><span data-stu-id="6a94a-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span>


## <a name="syntax"></a><span data-ttu-id="6a94a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a94a-105">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.PropertyName
    with get(index-variable) =
        get-function-body
    and set index-variablesvalue-variables =
        set-function-body

// Indexed property that has get only.
member self-identifier.PropertyName(index-variable) =
    get-function-body

// Alternative syntax for indexed property with get only
member self-identifier.PropertyName
    with get(index-variables) =
        get-function-body

// Indexed property that has set only.
member self-identifier.PropertyName
    with set index-variablesvalue-variables = 
        set-function-body
```

## <a name="remarks"></a><span data-ttu-id="6a94a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a94a-106">Remarks</span></span>
<span data-ttu-id="6a94a-107">Tři formuláře předchozí syntaxe ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metoda, mají `get` metoda pouze nebo mít `set` pouze metoda.</span><span class="sxs-lookup"><span data-stu-id="6a94a-107">The three forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="6a94a-108">Můžete také kombinací obou syntaxi uvedenou jenom příkaz get a syntaxi pro sadu pouze a vytvořit vlastnost, která má get a set.</span><span class="sxs-lookup"><span data-stu-id="6a94a-108">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="6a94a-109">Tento formulář pozdější umožňuje umístit get modifikátory různých dostupnosti a atributy a nastavit metody.</span><span class="sxs-lookup"><span data-stu-id="6a94a-109">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="6a94a-110">Když *PropertyName* je `Item`, kompilátor zpracovává vlastnost jako vlastnost Výchozí indexovat.</span><span class="sxs-lookup"><span data-stu-id="6a94a-110">When the *PropertyName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="6a94a-111">A *Výchozí indexované vlastnosti* je vlastnost, která můžete přistupovat pomocí syntaxe pro pole na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="6a94a-111">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="6a94a-112">Například pokud `obj` je objekt typu, který definuje tato vlastnost syntaxe `obj.[index]` se používá pro přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a94a-112">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="6a94a-113">Syntaxe pro přístup k vlastnosti nevýchozí indexované je poskytnout název vlastnosti a index v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6a94a-113">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="6a94a-114">Například, pokud je vlastnost `Ordinal`, můžete psát `obj.Ordinal(index)` k přístupu.</span><span class="sxs-lookup"><span data-stu-id="6a94a-114">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="6a94a-115">Bez ohledu na to, jaký typ použijete, byste měli vždycky používat curryfikované formuláře pro `set` metoda indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a94a-115">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="6a94a-116">Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="6a94a-116">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a94a-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="6a94a-117">Example</span></span>

<span data-ttu-id="6a94a-118">Následující příklad kódu ukazuje definice a použití výchozí a jiné než výchozí indexované vlastnosti, které mají get a nastavit metody.</span><span class="sxs-lookup"><span data-stu-id="6a94a-118">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="6a94a-119">Výstup</span><span class="sxs-lookup"><span data-stu-id="6a94a-119">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="6a94a-120">Indexované vlastnosti s více Index proměnné</span><span class="sxs-lookup"><span data-stu-id="6a94a-120">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="6a94a-121">Indexované vlastnosti může mít více než jednu proměnnou index.</span><span class="sxs-lookup"><span data-stu-id="6a94a-121">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="6a94a-122">V takovém případě proměnné jsou oddělené čárkami, pokud je vlastnost použita.</span><span class="sxs-lookup"><span data-stu-id="6a94a-122">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="6a94a-123">Curryfikované dva argumenty, z nichž první řazené kolekce členů obsahující klíče a druhá které nastaví se hodnota musí mít metodu set v taková vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6a94a-123">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="6a94a-124">Následující kód ukazuje použití indexované vlastnosti s více index proměnné.</span><span class="sxs-lookup"><span data-stu-id="6a94a-124">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="6a94a-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a94a-125">See Also</span></span>
[<span data-ttu-id="6a94a-126">Členové</span><span class="sxs-lookup"><span data-stu-id="6a94a-126">Members</span></span>](index.md)
