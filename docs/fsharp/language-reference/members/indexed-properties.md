---
title: Indexované vlastnosti (F#)
description: 'Další informace o F # indexované vlastnosti, které jsou vlastnosti, které poskytují přístup jako pole k datům seřazené.'
ms.date: 05/16/2016
ms.openlocfilehash: 503cef9693cfe5e13d4e2d19a721d65bff1ce749
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235938"
---
# <a name="indexed-properties"></a><span data-ttu-id="0fe40-103">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0fe40-103">Indexed Properties</span></span>

<span data-ttu-id="0fe40-104">*Indexované vlastnosti* seřazeni vlastnosti, které poskytují přístup jako pole k data.</span><span class="sxs-lookup"><span data-stu-id="0fe40-104">*Indexed properties* are properties that provide array-like access to ordered data.</span></span> <span data-ttu-id="0fe40-105">Pocházejí ve třech formulářích:</span><span class="sxs-lookup"><span data-stu-id="0fe40-105">They come in three forms:</span></span>

* `Item`
* `Ordinal`
* `Cardinal`

<span data-ttu-id="0fe40-106">F # člen musí mít název jeden z těchto tří názvů zajistit přístup jako pole.</span><span class="sxs-lookup"><span data-stu-id="0fe40-106">An F# member must be named one of these three names to provide array-like access.</span></span> <span data-ttu-id="0fe40-107">`IndexerName` se používá k reprezentování libovolné z následujících tří možností:</span><span class="sxs-lookup"><span data-stu-id="0fe40-107">`IndexerName` is used to represent any of the three options below:</span></span>


## <a name="syntax"></a><span data-ttu-id="0fe40-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0fe40-108">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="0fe40-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0fe40-109">Remarks</span></span>
<span data-ttu-id="0fe40-110">Formuláře předchozí syntaxe ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metoda, mají `get` metoda pouze nebo mít `set` pouze metoda.</span><span class="sxs-lookup"><span data-stu-id="0fe40-110">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="0fe40-111">Můžete také kombinací obou syntaxi uvedenou jenom příkaz get a syntaxi pro sadu pouze a vytvořit vlastnost, která má get a set.</span><span class="sxs-lookup"><span data-stu-id="0fe40-111">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="0fe40-112">Tento formulář pozdější umožňuje umístit get modifikátory různých dostupnosti a atributy a nastavit metody.</span><span class="sxs-lookup"><span data-stu-id="0fe40-112">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="0fe40-113">Když *IndexerName* je `Item`, kompilátor zpracovává vlastnost jako vlastnost Výchozí indexovat.</span><span class="sxs-lookup"><span data-stu-id="0fe40-113">When the *IndexerName* is `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="0fe40-114">A *Výchozí indexované vlastnosti* je vlastnost, která můžete přistupovat pomocí syntaxe pro pole na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="0fe40-114">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="0fe40-115">Například pokud `obj` je objekt typu, který definuje tato vlastnost syntaxe `obj.[index]` se používá pro přístup k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0fe40-115">For example, if `obj` is an object of the type that defines this property, the syntax `obj.[index]` is used to access the property.</span></span>

<span data-ttu-id="0fe40-116">Syntaxe pro přístup k vlastnosti nevýchozí indexované je poskytnout název vlastnosti a index v závorkách.</span><span class="sxs-lookup"><span data-stu-id="0fe40-116">The syntax for accessing a nondefault indexed property is to provide the name of the property and the index in parentheses.</span></span> <span data-ttu-id="0fe40-117">Například, pokud je vlastnost `Ordinal`, můžete psát `obj.Ordinal(index)` k přístupu.</span><span class="sxs-lookup"><span data-stu-id="0fe40-117">For example, if the property is `Ordinal`, you write `obj.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="0fe40-118">Bez ohledu na to, jaký typ použijete, byste měli vždycky používat curryfikované formuláře pro `set` metoda indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0fe40-118">Regardless of which form you use, you should always use the curried form for the `set` method on an indexed property.</span></span> <span data-ttu-id="0fe40-119">Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="0fe40-119">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="0fe40-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="0fe40-120">Example</span></span>

<span data-ttu-id="0fe40-121">Následující příklad kódu ukazuje definice a použití výchozí a jiné než výchozí indexované vlastnosti, které mají get a nastavit metody.</span><span class="sxs-lookup"><span data-stu-id="0fe40-121">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="0fe40-122">Výstup</span><span class="sxs-lookup"><span data-stu-id="0fe40-122">Output</span></span>

```
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="0fe40-123">Indexované vlastnosti s více Index proměnné</span><span class="sxs-lookup"><span data-stu-id="0fe40-123">Indexed Properties with Multiple Index Variables</span></span>
<span data-ttu-id="0fe40-124">Indexované vlastnosti může mít více než jednu proměnnou index.</span><span class="sxs-lookup"><span data-stu-id="0fe40-124">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="0fe40-125">V takovém případě proměnné jsou oddělené čárkami, pokud je vlastnost použita.</span><span class="sxs-lookup"><span data-stu-id="0fe40-125">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="0fe40-126">Curryfikované dva argumenty, z nichž první řazené kolekce členů obsahující klíče a druhá které nastaví se hodnota musí mít metodu set v taková vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0fe40-126">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="0fe40-127">Následující kód ukazuje použití indexované vlastnosti s více index proměnné.</span><span class="sxs-lookup"><span data-stu-id="0fe40-127">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="0fe40-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="0fe40-128">See Also</span></span>
[<span data-ttu-id="0fe40-129">Členové</span><span class="sxs-lookup"><span data-stu-id="0fe40-129">Members</span></span>](index.md)
