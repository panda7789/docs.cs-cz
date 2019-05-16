---
title: let – vazby
description: Další informace o použití F# "let" vazby, který přidruží k identifikátoru hodnotě nebo funkci.
ms.date: 05/16/2016
ms.openlocfilehash: ac33ee761cd4881f3d82d6680a07f62a1d7e77e5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641895"
---
# <a name="let-bindings"></a><span data-ttu-id="5b8d2-103">let – vazby</span><span class="sxs-lookup"><span data-stu-id="5b8d2-103">let Bindings</span></span>

<span data-ttu-id="5b8d2-104">A *vazby* identifikátor přidruží k hodnotě nebo funkci.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="5b8d2-105">Můžete použít `let` – klíčové slovo k vytvoření vazby názvu s hodnotě nebo funkci.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b8d2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b8d2-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="5b8d2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b8d2-107">Remarks</span></span>

<span data-ttu-id="5b8d2-108">`let` – Klíčové slovo se používá ve vazbě výrazy k definování hodnot nebo funkce jednoho nebo více názvů.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="5b8d2-109">Nejjednodušší forma `let` výraz vytvoří vazbu názvu jednoduchých hodnot, následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="5b8d2-110">Pokud samostatné výrazu z identifikátoru s použitím nového řádku, musíte odsadit každý řádek výrazu, stejně jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="5b8d2-111">Namísto pouze název, můžete zadat vzor, který obsahuje názvy, například řazená kolekce členů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="5b8d2-112">*Výraz těla* je výraz, ve kterém se používají názvy.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="5b8d2-113">Výraz těla se objeví na samostatném řádku odsazen řádek nahoru přesně prvního znaku v `let` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="5b8d2-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="5b8d2-114">A `let` vazby se může zobrazit na úrovni modulu v definici typu třídy nebo v místní obory, jako je definicí funkce.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="5b8d2-115">A `let` vazby na nejvyšší úrovni v modulu nebo typ třídy není nutné mít tělo výrazu, ale na jiných úrovních oboru, je nutné tělo výrazu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="5b8d2-116">Vázané názvy jsou použitelné od chvíle, definice, ale ne v libovolném okamžiku před `let` vazby se zobrazí, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="5b8d2-117">Vazby – funkce</span><span class="sxs-lookup"><span data-stu-id="5b8d2-117">Function Bindings</span></span>

<span data-ttu-id="5b8d2-118">Vazby funkcí postupujte z pravidel pro vazby hodnoty, s tím rozdílem, že funkce zahrnují název funkce a parametry, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="5b8d2-119">Obecně platí parametry jsou vzory, třeba vzor řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="5b8d2-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="5b8d2-120">A `let` vazby výraz vyhodnocen jako hodnota posledního výrazu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="5b8d2-121">Proto v následujícím příkladu kódu, hodnota `result` je vypočítán z `100 * function3 (1, 2)`, který se hodnotí jako `300`.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="5b8d2-122">Další informace najdete v tématu [funkce](index.md).</span><span class="sxs-lookup"><span data-stu-id="5b8d2-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="5b8d2-123">Anotace typu</span><span class="sxs-lookup"><span data-stu-id="5b8d2-123">Type Annotations</span></span>

<span data-ttu-id="5b8d2-124">Je-li zadat typy jako parametry, včetně dvojtečky (:), za nímž následuje název typu, všechny uzavřené v závorkách.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="5b8d2-125">Můžete také určit typ vrácené hodnoty přidáním dvojtečkou a typem po posledním parametrem.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="5b8d2-126">Poznámky typu k `function1`, s celými čísly jako typy parametrů, by měl vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="5b8d2-127">Pokud neexistují žádné explicitní parametry typu, odvození typu proměnné se používá k určení typů parametrů funkcí.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="5b8d2-128">To může zahrnovat automaticky zobecňuje typ parametru je obecný.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="5b8d2-129">Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md) a [odvození typu](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="5b8d2-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="5b8d2-130">Vazby let ve třídách</span><span class="sxs-lookup"><span data-stu-id="5b8d2-130">let Bindings in Classes</span></span>

<span data-ttu-id="5b8d2-131">A `let` vazby se může objevit v typu třídy, ale ne v struktury nebo typu záznamu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="5b8d2-132">Pokud chcete používat let vazby v typu třídy, musí mít třídu primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="5b8d2-133">Parametry konstruktoru musí následovat za názvem typu v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="5b8d2-134">A `let` vazby v typu třídy definuje privátní pole a členy typu třídy a společně s `do` vazby typu formuláře kód k primárnímu konstruktoru pro typ.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="5b8d2-135">Následující příklady kódu ukazují třídu `MyClass` s privátní pole `field1` a `field2`.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="5b8d2-136">Obory `field1` a `field2` jsou omezené na typ, ve kterém jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="5b8d2-137">Další informace najdete v tématu [ `let` vazby ve třídách](../members/let-bindings-in-classes.md) a [třídy](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="5b8d2-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="5b8d2-138">Let – vazby parametrů typu v</span><span class="sxs-lookup"><span data-stu-id="5b8d2-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="5b8d2-139">A `let` vazby na úrovni modulu, typu nebo ve výrazu výpočtu může mít explicitní parametry typu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="5b8d2-140">Umožňují vazby ve výrazu, například uvnitř definice funkce nemůže mít parametry typu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="5b8d2-141">Další informace najdete v tématu [obecných typů](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="5b8d2-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="5b8d2-142">Atributy u let – vazby</span><span class="sxs-lookup"><span data-stu-id="5b8d2-142">Attributes on let Bindings</span></span>

<span data-ttu-id="5b8d2-143">Atributy lze použít na nejvyšší úrovni `let` vazby v modulu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="5b8d2-144">Rozsah a usnadnění přístupu vám umožňují vazeb</span><span class="sxs-lookup"><span data-stu-id="5b8d2-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="5b8d2-145">Rozsah entity deklarované s vazbou let je omezen na část z nadřazeného oboru (například funkce, modulu, souboru nebo třídy), po zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="5b8d2-146">Proto lze říci, že umožňují vazby zavádí název do oboru.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="5b8d2-147">V modulu umožňují datově závislé hodnoty nebo funkce je přístupný pro klienty modulu jako modul je přístupný, protože umožňují vazby v modulu jsou kompilovány do veřejných funkcí modulu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="5b8d2-148">Vazby let ve třídě jsou naopak privátní třídy.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="5b8d2-149">Za normálních okolností funkce v modulech musí být kvalifikován názvem modulu při použití kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="5b8d2-150">Například, pokud modul `Module1` má funkci `function1`, zadejte uživatele `Module1.function1` odkazovat na funkci.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="5b8d2-151">Uživatelé modulu může používat deklarace importu Chcete-li k dispozici pro použití funkcí v rámci tohoto modulu bez je kvalifikován názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="5b8d2-152">V příkladu výše zmíněné body, můžete otevřít uživatelé modulu v takovém případě modulu s využitím open deklarace importu `Module1` a po tomto datu si `function1` přímo.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="5b8d2-153">Některé moduly mají atribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), což znamená, že funkce, které vystavují musí být kvalifikován s názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="5b8d2-154">Například F# seznamu modul nemá tento atribut.</span><span class="sxs-lookup"><span data-stu-id="5b8d2-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="5b8d2-155">Další informace o modulů a řízení přístupu najdete v tématu [moduly](../modules.md) a [řízení přístupu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="5b8d2-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b8d2-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5b8d2-156">See also</span></span>

- [<span data-ttu-id="5b8d2-157">Funkce</span><span class="sxs-lookup"><span data-stu-id="5b8d2-157">Functions</span></span>](index.md)
- [<span data-ttu-id="5b8d2-158">`let` Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="5b8d2-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
