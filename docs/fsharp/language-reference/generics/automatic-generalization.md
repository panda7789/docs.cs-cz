---
title: "Automatická generalizace (F#)"
description: "Zjistěte, jak F # automaticky umožňuje zobecnit argumentů a typy funkce tak, aby fungovaly s více typy, pokud je to možné."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 14a3554c-3fad-4eba-a93d-8ba07d1245b4
ms.openlocfilehash: d60831084cef76ce29f64322362b4920520f71d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="automatic-generalization"></a><span data-ttu-id="d7b6e-104">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="d7b6e-104">Automatic Generalization</span></span>

<span data-ttu-id="d7b6e-105">F # používá odvození typu k vyhodnocení typy výrazů a funkce.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-105">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="d7b6e-106">Toto téma popisuje, jak F # automaticky umožňuje zobecnit argumentů a typy funkce tak, aby pracují s více typy, když je to možné.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-106">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>


## <a name="automatic-generalization"></a><span data-ttu-id="d7b6e-107">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="d7b6e-107">Automatic Generalization</span></span>
<span data-ttu-id="d7b6e-108">Kompilátor F # při provádění odvození typu na funkce, určuje, zda daný parametr může být obecný.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-108">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="d7b6e-109">Kompilátor prozkoumá každý parametr a určuje, zda funkce má závislost na konkrétní typ tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-109">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="d7b6e-110">Pokud ne, je odvodit typ být obecný.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-110">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="d7b6e-111">Následující příklad kódu představuje funkci, která kompilátor odvodí být obecný.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-111">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="d7b6e-112">Je potřeba odvodit typ `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-112">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="d7b6e-113">Typ uvádí, že toto je funkce, která má dva argumenty stejné Neznámý typ a vrátí hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-113">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="d7b6e-114">Jedním z důvodů, které může být předchozí funkce obecné je, že delší – než – operátor (`>`) je sám Obecné.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-114">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="d7b6e-115">Delší – než operátor podpis `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-115">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="d7b6e-116">Ne všechny operátory jsou obecné, a pokud kód ve funkci používá typ parametru společně s neobecnou funkce nebo operátor, parametr typu nemůže být zobecněn.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-116">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="d7b6e-117">Protože `max` je obecný, se dá použít s typy, jako `int`, `float`a tak dále, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-117">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="d7b6e-118">Dva argumenty, ale musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-118">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="d7b6e-119">Podpis je `'a -> 'a -> 'a`, nikoli `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-119">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="d7b6e-120">Proto následující kód vytvoří chybu, protože typy se neshodují.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-120">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="d7b6e-121">`max` Funkce funguje taky s žádný typ, který podporuje větší – než – operátor.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-121">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="d7b6e-122">Proto můžete také použít ho na řetězec, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-122">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]
    
## <a name="value-restriction"></a><span data-ttu-id="d7b6e-123">Omezení hodnoty</span><span class="sxs-lookup"><span data-stu-id="d7b6e-123">Value Restriction</span></span>
<span data-ttu-id="d7b6e-124">Kompilátor provede automatická generalizace pouze na definice dokončení funkcí, které mají explicitní argumenty a na jednoduchý neměnné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-124">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="d7b6e-125">To znamená, že kompilátor problémy chybu, pokud se pokusíte zkompilovat kód, který není dostatečně omezené na konkrétní typ, ale není také generalizovatelného.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-125">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="d7b6e-126">Chybová zpráva pro tento problém odkazuje na toto omezení na automatická generalizace pro hodnoty jako *hodnoty omezení*.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-126">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="d7b6e-127">Hodnotu omezení chybě obvykle dochází, když chcete konstrukce jako obecný ale kompilátor má dostatek informací ke generalizaci ho nebo pokud nechtěně vynechat dostatek informací o typu v neobecné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-127">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="d7b6e-128">Řešení chyby omezení hodnota je poskytují podrobnější informace, které podrobněji omezit problém odvození typu, v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="d7b6e-128">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>


- <span data-ttu-id="d7b6e-129">Zadat omezení typu být neobecné přidáním anotaci typu explicitní hodnota nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-129">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="d7b6e-130">Pokud tento problém je pomocí konstrukce nongeneralizable k definování obecné funkce, jako je například funkce složení nebo úplně použili argumenty curryfikované funkce, zkuste přepisování funkce jako definici běžné funkce.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-130">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="d7b6e-131">Pokud tento problém je výraz, který je příliš složitý zobecněny, nastavte do funkce přidáním parametru navíc, nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-131">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="d7b6e-132">Přidání parametrů explicitní obecného typu.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-132">Add explicit generic type parameters.</span></span> <span data-ttu-id="d7b6e-133">Tato možnost se používá zřídka.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-133">This option is rarely used.</span></span>

- <span data-ttu-id="d7b6e-134">Následující příklady kódu ilustrují každého z těchto scénářů.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-134">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="d7b6e-135">Případ 1: Příliš složitý výraz.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-135">Case 1: Too complex an expression.</span></span> <span data-ttu-id="d7b6e-136">V tomto příkladu seznamu `counter` má být `int option ref`, ale není definován jako hodnotu simple neměnné.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-136">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="d7b6e-137">Případ 2: Definování obecné funkce pomocí nongeneralizable konstrukce.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-137">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="d7b6e-138">V tomto příkladu je konstruktu nongeneralizable, protože se týká částečné aplikace argumenty funkce.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-138">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="d7b6e-139">Případ 3: Přidání parametru navíc, nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-139">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="d7b6e-140">Protože tento výraz není dostatečně jednoduchá pro generalizace, vydá chyba omezení hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-140">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="d7b6e-141">Případ 4: Přidání parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="d7b6e-141">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="d7b6e-142">V případě poslední tato hodnota začne typ funkce, které mohou být použity k vytvoření hodnoty mnoho různých typů, například takto:</span><span class="sxs-lookup"><span data-stu-id="d7b6e-142">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="d7b6e-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7b6e-143">See Also</span></span>
[<span data-ttu-id="d7b6e-144">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="d7b6e-144">Type Inference</span></span>](../type-inference.md)

[<span data-ttu-id="d7b6e-145">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="d7b6e-145">Generics</span></span>](index.md)

[<span data-ttu-id="d7b6e-146">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="d7b6e-146">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="d7b6e-147">Omezení</span><span class="sxs-lookup"><span data-stu-id="d7b6e-147">Constraints</span></span>](constraints.md)

