---
title: "let – vazby (F#)"
description: "Naučte se používat F # umožní vazby, která přidruží identifikátor hodnota nebo funkce."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: bee69edc-d5ae-46bd-8b56-f02d97725d0d
ms.openlocfilehash: a57c5572e4bb5a3777c928dd572b7a84d4f0a334
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="let-bindings"></a><span data-ttu-id="d6f60-104">let – vazby</span><span class="sxs-lookup"><span data-stu-id="d6f60-104">let Bindings</span></span>

<span data-ttu-id="d6f60-105">A *vazby* přidruží identifikátor hodnota nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="d6f60-105">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="d6f60-106">Můžete použít `let` – klíčové slovo vytvořit vazbu název hodnotu nebo funkce.</span><span class="sxs-lookup"><span data-stu-id="d6f60-106">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="d6f60-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6f60-107">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="d6f60-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6f60-108">Remarks</span></span>

<span data-ttu-id="d6f60-109">`let` – Klíčové slovo se používá v vazby výrazy a definovat hodnoty nebo funkce hodnoty pro jeden nebo více názvů.</span><span class="sxs-lookup"><span data-stu-id="d6f60-109">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="d6f60-110">Nejjednodušší forma útoku `let` výraz váže název na hodnotu simple následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="d6f60-110">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="d6f60-111">Pokud oddělíte výraz z identifikátor pomocí nového řádku, musíte odsazovat každý řádek výrazu, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-111">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="d6f60-112">Místo pouze název můžete zadat vzor, který obsahuje názvy, například řazené kolekce členů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-112">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="d6f60-113">*Textu výraz* je výraz, ve kterém se používají názvy.</span><span class="sxs-lookup"><span data-stu-id="d6f60-113">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="d6f60-114">Výraz text se zobrazí na vlastním řádku odsazeny řádek až přesně s první znak argumentu `let` – klíčové slovo:</span><span class="sxs-lookup"><span data-stu-id="d6f60-114">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="d6f60-115">A `let` vazby můžete zobrazit na úrovni modulu, v definici typu třídy nebo v místní obory, například definici funkce.</span><span class="sxs-lookup"><span data-stu-id="d6f60-115">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="d6f60-116">A `let` vazba na nejvyšší úrovni v modulu nebo typ třídy nemusí obsahovat výraz text, ale na jiných úrovních oboru, je vyžadován výraz textu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-116">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="d6f60-117">Vázané názvy jsou použitelné za bod definice, ale ne v libovolném bodě před `let` vazby zobrazí se, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-117">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]
    
## <a name="function-bindings"></a><span data-ttu-id="d6f60-118">Vazby funkce</span><span class="sxs-lookup"><span data-stu-id="d6f60-118">Function Bindings</span></span>

<span data-ttu-id="d6f60-119">Vazby funkce v podle pravidla pro hodnotu vazby, s tím rozdílem, že funkce vazby obsahovat název funkce a parametry, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-119">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="d6f60-120">Parametry jsou obecně vzory, třeba vzor řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="d6f60-120">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="d6f60-121">A `let` vazby výraz vyhodnocen jako hodnota poslední výrazu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-121">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="d6f60-122">Proto v následujícím příkladu kódu, hodnota `result` se počítá z `100 * function3 (1, 2)`, který se vyhodnocuje `300`.</span><span class="sxs-lookup"><span data-stu-id="d6f60-122">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="d6f60-123">Další informace najdete v tématu [funkce](index.md).</span><span class="sxs-lookup"><span data-stu-id="d6f60-123">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="d6f60-124">Typ poznámky</span><span class="sxs-lookup"><span data-stu-id="d6f60-124">Type Annotations</span></span>

<span data-ttu-id="d6f60-125">Můžete určit typy parametrů zahrnutím dvojtečkou (:), za nímž následuje název typu, všechny uzavřený v závorkách.</span><span class="sxs-lookup"><span data-stu-id="d6f60-125">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="d6f60-126">Můžete také určit typ vrácené hodnoty připojením dvojtečkou a typ po poslední parametr.</span><span class="sxs-lookup"><span data-stu-id="d6f60-126">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="d6f60-127">Úplný typ poznámky pro `function1`, s celými čísly jako typy parametrů, vypadat takto.</span><span class="sxs-lookup"><span data-stu-id="d6f60-127">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="d6f60-128">Pokud neexistují žádné parametry explicitního typu, odvození typu slouží k určení typů parametrů funkce.</span><span class="sxs-lookup"><span data-stu-id="d6f60-128">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="d6f60-129">To může zahrnovat automaticky generalizací typ parametru být obecný.</span><span class="sxs-lookup"><span data-stu-id="d6f60-129">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="d6f60-130">Další informace najdete v tématu [Automatická generalizace](../generics/automatic-generalization.md) a [odvození typu](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="d6f60-130">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="d6f60-131">Vazby let ve třídách</span><span class="sxs-lookup"><span data-stu-id="d6f60-131">let Bindings in Classes</span></span>

<span data-ttu-id="d6f60-132">A `let` vazba může vyskytovat typu třídy, ale není v struktura nebo typu záznamu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-132">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="d6f60-133">Pokud chcete používat umožňují vazby v typu třídy, třídu musí mít primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d6f60-133">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="d6f60-134">Konstruktor parametry musí být uvedena po název typu v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d6f60-134">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="d6f60-135">A `let` vazby v typu třídy definuje privátní pole a členů pro tento typ třídy a, společně s `do` vazeb v typu, forms kód pro primární konstruktor pro typ.</span><span class="sxs-lookup"><span data-stu-id="d6f60-135">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="d6f60-136">Následující příklady kódu ukazují třídu `MyClass` s privátním polím `field1` a `field2`.</span><span class="sxs-lookup"><span data-stu-id="d6f60-136">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="d6f60-137">Obory z `field1` a `field2` jsou omezeny na typ, ve které jsou deklarované.</span><span class="sxs-lookup"><span data-stu-id="d6f60-137">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="d6f60-138">Další informace najdete v tématu [ `let` vazby do ve třídách](../members/let-bindings-in-classes.md) a [třídy](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="d6f60-138">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="d6f60-139">Parametry typu v let – vazby</span><span class="sxs-lookup"><span data-stu-id="d6f60-139">Type Parameters in let Bindings</span></span>

<span data-ttu-id="d6f60-140">A `let` vazby na úrovni modulu v typu, nebo výpočetní výraz může mít parametry explicitní typu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-140">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="d6f60-141">Umožňují vazby ve výrazu, například v definici funkce nemůže mít parametry typu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-141">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="d6f60-142">Další informace najdete v tématu [obecné typy](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="d6f60-142">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="d6f60-143">Atributy na let – vazby</span><span class="sxs-lookup"><span data-stu-id="d6f60-143">Attributes on let Bindings</span></span>

<span data-ttu-id="d6f60-144">Atributy lze použít na nejvyšší úrovni `let` vazby v modulu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-144">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]
    
## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="d6f60-145">Obor a usnadnění umožňují vazby</span><span class="sxs-lookup"><span data-stu-id="d6f60-145">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="d6f60-146">Rozsah entity deklarovat s umožňují vazba je omezený na část obsahující oboru (například funkce, modul, soubor nebo třída), jakmile se objeví vazby.</span><span class="sxs-lookup"><span data-stu-id="d6f60-146">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="d6f60-147">Proto lze říci, že umožňují vazbu představuje název do oboru.</span><span class="sxs-lookup"><span data-stu-id="d6f60-147">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="d6f60-148">V modulu umožňují vázané hodnota nebo funkce je dostupné klientům modulu tak dlouho, dokud je přístupný, modul, protože umožňují vazby v modulu se zkompiluje do veřejných funkcí modulu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-148">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="d6f60-149">Umožňují vazby v třídě jsou naopak privátní k třídě.</span><span class="sxs-lookup"><span data-stu-id="d6f60-149">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="d6f60-150">Za normálních okolností funkce v modulech musí být kvalifikovaný název modulu při použití kódem na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="d6f60-150">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="d6f60-151">Například, pokud modul `Module1` má funkci `function1`, by uživatelé zadat `Module1.function1` odkazovat na funkce.</span><span class="sxs-lookup"><span data-stu-id="d6f60-151">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="d6f60-152">Uživatelé modulu mohou využít importu deklarace, aby se funkce v rámci tohoto modulu k dispozici pro použití jako kvalifikované název modulu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-152">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="d6f60-153">V příkladu právě uvedený, můžete otevřít uživatelé modulu v takovém případě modul pomocí otevřete deklarace importu `Module1` a následně odkazovat na `function1` přímo.</span><span class="sxs-lookup"><span data-stu-id="d6f60-153">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="d6f60-154">Některé moduly mají atribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), což znamená, že funkce, které se zveřejňují musí být kvalifikovaný pomocí názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="d6f60-154">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="d6f60-155">Například modul F # seznamu má tento atribut.</span><span class="sxs-lookup"><span data-stu-id="d6f60-155">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="d6f60-156">Další informace o moduly a řízení přístupu najdete v tématu [moduly](../modules.md) a [řízení přístupu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="d6f60-156">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d6f60-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6f60-157">See Also</span></span>

[<span data-ttu-id="d6f60-158">Funkce</span><span class="sxs-lookup"><span data-stu-id="d6f60-158">Functions</span></span>](index.md)

[<span data-ttu-id="d6f60-159">`let`Vazby do ve třídách</span><span class="sxs-lookup"><span data-stu-id="d6f60-159">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
