---
title: Automatická generalizace
description: Zjistěte, jak F# automaticky zobecňuje argumenty a typy funkce tak, aby fungovaly s více typy, pokud je to možné.
ms.date: 05/16/2016
ms.openlocfilehash: 8fc61b5e0c227474a5e913b37f4c0dad9b235a6f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641875"
---
# <a name="automatic-generalization"></a><span data-ttu-id="1969d-103">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="1969d-103">Automatic Generalization</span></span>

<span data-ttu-id="1969d-104">F#používá typ odvození posoudíte typy vašich funkce a výrazy.</span><span class="sxs-lookup"><span data-stu-id="1969d-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="1969d-105">Toto téma popisuje, jak F# automaticky zobecňuje argumenty a typy funkce tak, aby fungovaly s více typy kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="1969d-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="1969d-106">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="1969d-106">Automatic Generalization</span></span>

<span data-ttu-id="1969d-107">F# Kompilátoru, když ji provede odvození typu na funkci, určuje, zda daný parametr může být obecný.</span><span class="sxs-lookup"><span data-stu-id="1969d-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="1969d-108">Kompilátor zkontroluje každý parametr a určuje, zda funkce má závislosti na konkrétní typ tohoto parametru.</span><span class="sxs-lookup"><span data-stu-id="1969d-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="1969d-109">Pokud tomu tak není, typ je odvozen je obecný.</span><span class="sxs-lookup"><span data-stu-id="1969d-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="1969d-110">Následující příklad kódu ukazuje funkci, která kompilátor odvodí z nich je obecný.</span><span class="sxs-lookup"><span data-stu-id="1969d-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="1969d-111">Typ je odvozen bude `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="1969d-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="1969d-112">Typ uvádí, že se jedná o funkci, která přebírá dva argumenty stejného Neznámý typ a vrátí hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="1969d-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="1969d-113">Jedním z důvodů, které mohou být předchozí funkce obecného je, že větší-než – operátor (`>`) je samotný obecný.</span><span class="sxs-lookup"><span data-stu-id="1969d-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="1969d-114">Větší-než operátor nemá podpis `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="1969d-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="1969d-115">Ne všechny operátory jsou obecné, a pokud kód ve funkci používá typ parametru spolu s neobecné funkce nebo operátoru, tento typ parametru nelze zobecněný.</span><span class="sxs-lookup"><span data-stu-id="1969d-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="1969d-116">Protože `max` je obecný, ho jde použít s typy, jako `int`, `float`, a tak dále, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1969d-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="1969d-117">Dva argumenty, ale musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="1969d-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="1969d-118">Podpis je `'a -> 'a -> 'a`, nikoli `'a -> 'b -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="1969d-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="1969d-119">Následující kód proto vygeneruje chybu, protože typy se neshodují.</span><span class="sxs-lookup"><span data-stu-id="1969d-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="1969d-120">`max` Funkce také funguje s jakýmkoli typem, který podporuje větší-než operátor.</span><span class="sxs-lookup"><span data-stu-id="1969d-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="1969d-121">Proto můžete také použít ho na řetězec, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1969d-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="1969d-122">Omezení hodnoty</span><span class="sxs-lookup"><span data-stu-id="1969d-122">Value Restriction</span></span>

<span data-ttu-id="1969d-123">Kompilátor provede automatická generalizace jenom u definic dokončení funkcí, které mají explicitní argumenty a na jednoduché neměnné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1969d-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="1969d-124">To znamená, že kompilátor vyvolá chybu při kompilaci kódu, který není dostatečně omezen na konkrétní typ, ale není také generalizovatelného.</span><span class="sxs-lookup"><span data-stu-id="1969d-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="1969d-125">Chybová zpráva pro tento problém odkazuje na toto omezení na automatická generalizace pro hodnoty jako *hodnota omezení*.</span><span class="sxs-lookup"><span data-stu-id="1969d-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="1969d-126">Na hodnotu omezení chybě obvykle dochází, když chcete použít konstrukce je obecný, ale kompilátor má dostatek informací k zobecnění ho nebo Pokud vynecháte neúmyslně dostatek informací o typu v neobecné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="1969d-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="1969d-127">Řešení tak, aby chyba omezení hodnoty má obsahují podrobnější informace, které podrobněji omezit problém odvození typu, v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="1969d-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="1969d-128">Omezení typu bude neobecné přidáním anotace explicitního typu hodnoty nebo parametr.</span><span class="sxs-lookup"><span data-stu-id="1969d-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="1969d-129">Pokud se problém nongeneralizable konstruktor používá k definování obecné funkce, jako je například funkce – složení nebo neúplně použita curryfikované argumenty, zkuste přepsání funkce jako definici běžné funkce.</span><span class="sxs-lookup"><span data-stu-id="1969d-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="1969d-130">Pokud se jedná o výraz, který je příliš složitý pro zobecnit, převeďte na funkci tak, že přidáte další, nepoužité parametr.</span><span class="sxs-lookup"><span data-stu-id="1969d-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="1969d-131">Přidáte explicitní obecné parametry typu.</span><span class="sxs-lookup"><span data-stu-id="1969d-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="1969d-132">Tato možnost se používá jen zřídka.</span><span class="sxs-lookup"><span data-stu-id="1969d-132">This option is rarely used.</span></span>

- <span data-ttu-id="1969d-133">Následující příklady kódu ukazují každý z těchto scénářů.</span><span class="sxs-lookup"><span data-stu-id="1969d-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="1969d-134">Případ 1: Příliš složitý výraz.</span><span class="sxs-lookup"><span data-stu-id="1969d-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="1969d-135">V tomto příkladu seznamu `counter` má být `int option ref`, ale není definován jako jednoduchý neměnný hodnota.</span><span class="sxs-lookup"><span data-stu-id="1969d-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="1969d-136">Případ 2: Chcete-li definovat obecnou funkci pomocí konstrukce nongeneralizable.</span><span class="sxs-lookup"><span data-stu-id="1969d-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="1969d-137">V tomto příkladu je konstrukce nongeneralizable, protože se týká částečné použití argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="1969d-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="1969d-138">Případ 3: Přidat parametr navíc, nevyužité.</span><span class="sxs-lookup"><span data-stu-id="1969d-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="1969d-139">Vzhledem k tomu, že tento výraz není dostatečně jednoduchá pro generalizaci, kompilátor vyvolá chybu omezení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1969d-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="1969d-140">Případ 4: Přidání parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="1969d-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="1969d-141">V posledním případě tato hodnota začne – funkce typu, který může být použit k vytvoření hodnot typu mnoho různých typů, třeba takto:</span><span class="sxs-lookup"><span data-stu-id="1969d-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="1969d-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1969d-142">See also</span></span>

- [<span data-ttu-id="1969d-143">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="1969d-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="1969d-144">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="1969d-144">Generics</span></span>](index.md)
- [<span data-ttu-id="1969d-145">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="1969d-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="1969d-146">Omezení</span><span class="sxs-lookup"><span data-stu-id="1969d-146">Constraints</span></span>](constraints.md)
