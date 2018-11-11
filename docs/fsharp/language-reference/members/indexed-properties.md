---
title: Indexované vlastnosti (F#)
description: Další informace o indexované vlastnosti v F#, které umožňují pro přístup jako pole k datům seřazené.
ms.date: 10/17/2018
ms.openlocfilehash: 3dac60eba3d9e7a9c3e76ad7ee051e6b30b88636
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "49452245"
---
# <a name="indexed-properties"></a><span data-ttu-id="690b2-103">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="690b2-103">Indexed Properties</span></span>

<span data-ttu-id="690b2-104">Při definování třídy, který získává přes seřazených dat, může být někdy užitečné poskytnout indexovaný přístup k těmto datům bez vystavení se základní implementací.</span><span class="sxs-lookup"><span data-stu-id="690b2-104">When defining a class that abstracts over ordered data, it can sometimes be helpful to provide indexed access to that data without exposing the underlying implementation.</span></span> <span data-ttu-id="690b2-105">Používá se k tomu `Index` člena.</span><span class="sxs-lookup"><span data-stu-id="690b2-105">This is done with the `Index` member.</span></span>

## <a name="syntax"></a><span data-ttu-id="690b2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="690b2-106">Syntax</span></span>

```fsharp
// Indexed property that has both get and set defined.
member self-identifier.Index
    with get(index-values) =
        get-member-body
    and set index-values values-to-set =
        set-member-body

// Indexed property with get only
member self-identifier.Index
    with get(index-values) =
        get-member-body

// Indexed property that has set only.
member self-identifier.Index
    with set index-values values-to-set =
        set-member-body
```

## <a name="remarks"></a><span data-ttu-id="690b2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="690b2-107">Remarks</span></span>

<span data-ttu-id="690b2-108">Formy syntaxe předchozí ukazují, jak definovat indexované vlastnosti, které mají obě `get` a `set` metodu, mají `get` metoda pouze, nebo mít `set` pouze metody.</span><span class="sxs-lookup"><span data-stu-id="690b2-108">The forms of the previous syntax show how to define indexed properties that have both a `get` and a `set` method, have a `get` method only, or have a `set` method only.</span></span> <span data-ttu-id="690b2-109">Můžete také zkombinovat obojí tomu syntaxe uvedená jenom příkaz get a syntaxi pro sadu pouze a vytvoří vlastnost, která má get a set.</span><span class="sxs-lookup"><span data-stu-id="690b2-109">You can also combine both the syntax shown for get only and the syntax shown for set only, and produce a property that has both get and set.</span></span> <span data-ttu-id="690b2-110">Tento druhý formulář umožňuje umístit různou přístupností. modifikátorů a vlastností atributy na get a set metod.</span><span class="sxs-lookup"><span data-stu-id="690b2-110">This latter form allows you to put different accessibility modifiers and attributes on the get and set methods.</span></span>

<span data-ttu-id="690b2-111">Pomocí názvu `Item`, kompilátor zpracovává vlastnost jako výchozí indexovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="690b2-111">By using the name `Item`, the compiler treats the property as a default indexed property.</span></span> <span data-ttu-id="690b2-112">A *výchozí indexovanou vlastnost* vlastností, která může získat přístup pomocí syntaxe pro pole na instanci objektu.</span><span class="sxs-lookup"><span data-stu-id="690b2-112">A *default indexed property* is a property that you can access by using array-like syntax on the object instance.</span></span> <span data-ttu-id="690b2-113">Například pokud `o` je objekt typu, který definuje tato vlastnost syntaxe `o.[index]` slouží k přístupu k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="690b2-113">For example, if `o` is an object of the type that defines this property, the syntax `o.[index]` is used to access the property.</span></span>

<span data-ttu-id="690b2-114">Syntaxe pro přístup k jiné než výchozí indexovaná vlastnost je k poskytnutí názvu vlastnosti a index v závorkách, stejně jako běžný člen.</span><span class="sxs-lookup"><span data-stu-id="690b2-114">The syntax for accessing a non-default indexed property is to provide the name of the property and the index in parentheses, just like a regular member.</span></span> <span data-ttu-id="690b2-115">Například pokud vlastnost `o` nazývá `Ordinal`, psaní `o.Ordinal(index)` k němu přistupovat.</span><span class="sxs-lookup"><span data-stu-id="690b2-115">For example, if the property on `o` is called `Ordinal`, you write `o.Ordinal(index)` to access it.</span></span>

<span data-ttu-id="690b2-116">Bez ohledu na to, jaký tvar používáte měli byste použít vždy curryfikované formuláře pro metodu set indexované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="690b2-116">Regardless of which form you use, you should always use the curried form for the set method on an indexed property.</span></span> <span data-ttu-id="690b2-117">Informace o curryfikované funkce najdete v tématu [funkce](../functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="690b2-117">For information about curried functions, see [Functions](../functions/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="690b2-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="690b2-118">Example</span></span>

<span data-ttu-id="690b2-119">Následující příklad kódu ukazuje definice a používání výchozích a jiné než výchozí indexované vlastnosti, které mají get a set metod.</span><span class="sxs-lookup"><span data-stu-id="690b2-119">The following code example illustrates the definition and use of default and non-default indexed properties that have get and set methods.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3301.fs)]

## <a name="output"></a><span data-ttu-id="690b2-120">Výstup</span><span class="sxs-lookup"><span data-stu-id="690b2-120">Output</span></span>

```console
ONE two three four five six seven eight nine ten
ONE first two second three third four fourth five fifth six 6th
seven seventh eight eighth nine ninth ten tenth
```

## <a name="indexed-properties-with-multiple-index-variables"></a><span data-ttu-id="690b2-121">Indexované vlastnosti v případě více proměnných indexu</span><span class="sxs-lookup"><span data-stu-id="690b2-121">Indexed Properties with Multiple Index Variables</span></span>

<span data-ttu-id="690b2-122">Indexované vlastnosti můžou mít více než jeden indexovaná proměnná.</span><span class="sxs-lookup"><span data-stu-id="690b2-122">Indexed properties can have more than one index variable.</span></span> <span data-ttu-id="690b2-123">Proměnné v takovém případě jsou odděleny čárkami, pokud se vlastnost používá.</span><span class="sxs-lookup"><span data-stu-id="690b2-123">In that case, the variables are separated by commas when the property is used.</span></span> <span data-ttu-id="690b2-124">Metoda set v těchto vlastností musí mít dva curryfikované argumenty, první z nich je řazená kolekce členů obsahující klíče a druhý z nich je hodnota nastavena.</span><span class="sxs-lookup"><span data-stu-id="690b2-124">The set method in such a property must have two curried arguments, the first of which is a tuple containing the keys, and the second of which is the value being set.</span></span>

<span data-ttu-id="690b2-125">Následující kód ukazuje použití indexovaná vlastnost s několika proměnnými indexu.</span><span class="sxs-lookup"><span data-stu-id="690b2-125">The following code demonstrates the use of an indexed property with multiple index variables.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3302.fs)]

## <a name="see-also"></a><span data-ttu-id="690b2-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="690b2-126">See also</span></span>

- [<span data-ttu-id="690b2-127">Členové</span><span class="sxs-lookup"><span data-stu-id="690b2-127">Members</span></span>](index.md)
