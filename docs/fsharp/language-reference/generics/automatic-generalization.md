---
title: Automatická generalizace
description: Přečtěte F# si, jak automaticky zobecnit argumenty a typy funkcí tak, aby fungovaly s více typy, pokud je to možné.
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630621"
---
# <a name="automatic-generalization"></a><span data-ttu-id="0d209-103">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="0d209-103">Automatic Generalization</span></span>

<span data-ttu-id="0d209-104">F#používá odvození typu pro vyhodnocení typů funkcí a výrazů.</span><span class="sxs-lookup"><span data-stu-id="0d209-104">F# uses type inference to evaluate the types of functions and expressions.</span></span> <span data-ttu-id="0d209-105">Toto téma popisuje, F# jak automaticky zobecnit argumenty a typy funkcí tak, aby fungovaly s více typy, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="0d209-105">This topic describes how F# automatically generalizes the arguments and types of functions so that they work with multiple types when this is possible.</span></span>

## <a name="automatic-generalization"></a><span data-ttu-id="0d209-106">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="0d209-106">Automatic Generalization</span></span>

<span data-ttu-id="0d209-107">F# Kompilátor, když provádí odvození typu na funkci, určuje, zda daný parametr může být obecný.</span><span class="sxs-lookup"><span data-stu-id="0d209-107">The F# compiler, when it performs type inference on a function, determines whether a given parameter can be generic.</span></span> <span data-ttu-id="0d209-108">Kompilátor prověřuje každý parametr a určí, zda má funkce závislost na konkrétním typu daného parametru.</span><span class="sxs-lookup"><span data-stu-id="0d209-108">The compiler examines each parameter and determines whether the function has a dependency on the specific type of that parameter.</span></span> <span data-ttu-id="0d209-109">Pokud tomu tak není, typ je odvozen jako obecný.</span><span class="sxs-lookup"><span data-stu-id="0d209-109">If it does not, the type is inferred to be generic.</span></span>

<span data-ttu-id="0d209-110">Následující příklad kódu ukazuje funkci, která kompilátor odvodí jako obecný.</span><span class="sxs-lookup"><span data-stu-id="0d209-110">The following code example illustrates a function that the compiler infers to be generic.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

<span data-ttu-id="0d209-111">Typ je odvozený `'a -> 'a -> 'a`.</span><span class="sxs-lookup"><span data-stu-id="0d209-111">The type is inferred to be `'a -> 'a -> 'a`.</span></span>

<span data-ttu-id="0d209-112">Typ označuje, že se jedná o funkci, která přijímá dva argumenty stejného neznámého typu a vrací hodnotu stejného typu.</span><span class="sxs-lookup"><span data-stu-id="0d209-112">The type indicates that this is a function that takes two arguments of the same unknown type and returns a value of that same type.</span></span> <span data-ttu-id="0d209-113">Jedním z důvodů, proč může být funkce Previous obecná, je, že operátor větší než (`>`) je obecný.</span><span class="sxs-lookup"><span data-stu-id="0d209-113">One of the reasons that the previous function can be generic is that the greater-than operator (`>`) is itself generic.</span></span> <span data-ttu-id="0d209-114">Operátor větší než má signaturu `'a -> 'a -> bool`.</span><span class="sxs-lookup"><span data-stu-id="0d209-114">The greater-than operator has the signature `'a -> 'a -> bool`.</span></span> <span data-ttu-id="0d209-115">Ne všechny operátory jsou obecné a pokud kód ve funkci používá typ parametru společně s neobecnou funkcí nebo operátorem, tento typ parametru nejde zobecnit.</span><span class="sxs-lookup"><span data-stu-id="0d209-115">Not all operators are generic, and if the code in a function uses a parameter type together with a non-generic function or operator, that parameter type cannot be generalized.</span></span>

<span data-ttu-id="0d209-116">Vzhledem `max` k tomu, že je obecný, lze použít s typy `int`, `float`jako jsou, a tak dále, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="0d209-116">Because `max` is generic, it can be used with types such as `int`, `float`, and so on, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

<span data-ttu-id="0d209-117">Dva argumenty však musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="0d209-117">However, the two arguments must be of the same type.</span></span> <span data-ttu-id="0d209-118">Podpis není `'a -> 'a -> 'a`. `'a -> 'b -> 'a`</span><span class="sxs-lookup"><span data-stu-id="0d209-118">The signature is `'a -> 'a -> 'a`, not `'a -> 'b -> 'a`.</span></span> <span data-ttu-id="0d209-119">Proto následující kód vytvoří chybu, protože typy se neshodují.</span><span class="sxs-lookup"><span data-stu-id="0d209-119">Therefore, the following code produces an error because the types do not match.</span></span>

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

<span data-ttu-id="0d209-120">`max` Funkce také funguje s jakýmkoli typem, který podporuje operátor větší než.</span><span class="sxs-lookup"><span data-stu-id="0d209-120">The `max` function also works with any type that supports the greater-than operator.</span></span> <span data-ttu-id="0d209-121">Proto jej můžete použít také na řetězec, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0d209-121">Therefore, you could also use it on a string, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a><span data-ttu-id="0d209-122">Omezení hodnoty</span><span class="sxs-lookup"><span data-stu-id="0d209-122">Value Restriction</span></span>

<span data-ttu-id="0d209-123">Kompilátor provádí automatickou generalizaci pouze v úplných definicích funkcí, které mají explicitní argumenty a na jednoduchých neměnných hodnotách.</span><span class="sxs-lookup"><span data-stu-id="0d209-123">The compiler performs automatic generalization only on complete function definitions that have explicit arguments, and on simple immutable values.</span></span>

<span data-ttu-id="0d209-124">To znamená, že kompilátor vyvolá chybu, pokud se pokusíte zkompilovat kód, který není dostatečně omezený na konkrétní typ, ale není možné jej zobecnit.</span><span class="sxs-lookup"><span data-stu-id="0d209-124">This means that the compiler issues an error if you try to compile code that is not sufficiently constrained to be a specific type, but is also not generalizable.</span></span> <span data-ttu-id="0d209-125">Chybová zpráva pro tento problém odkazuje na toto omezení automatické generalizace pro hodnoty jako *omezení hodnoty*.</span><span class="sxs-lookup"><span data-stu-id="0d209-125">The error message for this problem refers to this restriction on automatic generalization for values as the *value restriction*.</span></span>

<span data-ttu-id="0d209-126">Obvykle dojde k chybě omezení hodnoty, pokud chcete, aby konstrukce byla obecná, ale kompilátor nemá dostatek informací pro generalizaci, nebo Pokud neúmyslně vynecháte dostatečné informace o typu v neobecném konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0d209-126">Typically, the value restriction error occurs either when you want a construct to be generic but the compiler has insufficient information to generalize it, or when you unintentionally omit sufficient type information in a nongeneric construct.</span></span> <span data-ttu-id="0d209-127">Řešení chyby omezení hodnoty je poskytnout explicitní informace pro větší omezení problému typu odvození typu jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="0d209-127">The solution to the value restriction error is to provide more explicit information to more fully constrain the type inference problem, in one of the following ways:</span></span>

- <span data-ttu-id="0d209-128">Omezení typu na neobecný přidáním anotace explicitního typu k hodnotě nebo parametru.</span><span class="sxs-lookup"><span data-stu-id="0d209-128">Constrain a type to be nongeneric by adding an explicit type annotation to a value or parameter.</span></span>

- <span data-ttu-id="0d209-129">Pokud problém používá nezobecnitelné konstrukce k definování obecné funkce, jako je například složení funkce nebo nedokončené použití argumentů funkce curryfikované, zkuste funkci přepsat jako běžnou definici funkce.</span><span class="sxs-lookup"><span data-stu-id="0d209-129">If the problem is using a nongeneralizable construct to define a generic function, such as a function composition or incompletely applied curried function arguments, try to rewrite the function as an ordinary function definition.</span></span>

- <span data-ttu-id="0d209-130">Pokud je problém výrazem, který je příliš složitý, aby jej bylo možné zobecnit, udělejte ho do funkce přidáním nadbytečného, nepoužívaného parametru.</span><span class="sxs-lookup"><span data-stu-id="0d209-130">If the problem is an expression that is too complex to be generalized, make it into a function by adding an extra, unused parameter.</span></span>

- <span data-ttu-id="0d209-131">Přidejte explicitní parametry obecného typu.</span><span class="sxs-lookup"><span data-stu-id="0d209-131">Add explicit generic type parameters.</span></span> <span data-ttu-id="0d209-132">Tato možnost se používá zřídka.</span><span class="sxs-lookup"><span data-stu-id="0d209-132">This option is rarely used.</span></span>

- <span data-ttu-id="0d209-133">Následující příklady kódu ilustrují každý z těchto scénářů.</span><span class="sxs-lookup"><span data-stu-id="0d209-133">The following code examples illustrate each of these scenarios.</span></span>

<span data-ttu-id="0d209-134">Případ 1: Výraz je příliš složitý.</span><span class="sxs-lookup"><span data-stu-id="0d209-134">Case 1: Too complex an expression.</span></span> <span data-ttu-id="0d209-135">V tomto příkladu je seznam `counter` určen `int option ref`jako, ale není definován jako jednoduchá neměnná hodnota.</span><span class="sxs-lookup"><span data-stu-id="0d209-135">In this example, the list `counter` is intended to be `int option ref`, but it is not defined as a simple immutable value.</span></span>

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

<span data-ttu-id="0d209-136">Případ 2: Použití negeneralizované konstrukce k definování obecné funkce.</span><span class="sxs-lookup"><span data-stu-id="0d209-136">Case 2: Using a nongeneralizable construct to define a generic function.</span></span> <span data-ttu-id="0d209-137">V tomto příkladu je konstrukce negeneralizovaná, protože zahrnuje částečnou aplikaci argumentů funkce.</span><span class="sxs-lookup"><span data-stu-id="0d209-137">In this example, the construct is nongeneralizable because it involves partial application of function arguments.</span></span>

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

<span data-ttu-id="0d209-138">Případ 3: Přidání nadbytečného, nepoužívaného parametru.</span><span class="sxs-lookup"><span data-stu-id="0d209-138">Case 3: Adding an extra, unused parameter.</span></span> <span data-ttu-id="0d209-139">Vzhledem k tomu, že tento výraz není pro generalizaci dostatečně jednoduchý, vyvolá kompilátor chybu omezení hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0d209-139">Because this expression is not simple enough for generalization, the compiler issues the value restriction error.</span></span>

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

<span data-ttu-id="0d209-140">Případ 4: Přidávání parametrů typu.</span><span class="sxs-lookup"><span data-stu-id="0d209-140">Case 4: Adding type parameters.</span></span>

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

<span data-ttu-id="0d209-141">V posledním případě se hodnota stala funkcí typu, která může být použita k vytvoření hodnot mnoha různých typů, například následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0d209-141">In the last case, the value becomes a type function, which may be used to create values of many different types, for example as follows:</span></span>

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a><span data-ttu-id="0d209-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d209-142">See also</span></span>

- [<span data-ttu-id="0d209-143">Odvození typu</span><span class="sxs-lookup"><span data-stu-id="0d209-143">Type Inference</span></span>](../type-inference.md)
- [<span data-ttu-id="0d209-144">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="0d209-144">Generics</span></span>](index.md)
- [<span data-ttu-id="0d209-145">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="0d209-145">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)
- [<span data-ttu-id="0d209-146">Omezení</span><span class="sxs-lookup"><span data-stu-id="0d209-146">Constraints</span></span>](constraints.md)
