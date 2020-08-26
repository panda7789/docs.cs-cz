---
title: let – vazby
description: 'Naučte se používat vazbu "let" jazyka F #, která přidruží identifikátor k hodnotě nebo funkci.'
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812221"
---
# <a name="let-bindings"></a><span data-ttu-id="06e36-103">let – vazby</span><span class="sxs-lookup"><span data-stu-id="06e36-103">let Bindings</span></span>

<span data-ttu-id="06e36-104">*Vazba* přidruží identifikátor k hodnotě nebo funkci.</span><span class="sxs-lookup"><span data-stu-id="06e36-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="06e36-105">`let`Klíčové slovo slouží k vytvoření vazby názvu k hodnotě nebo funkci.</span><span class="sxs-lookup"><span data-stu-id="06e36-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="06e36-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="06e36-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="06e36-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06e36-107">Remarks</span></span>

<span data-ttu-id="06e36-108">`let`Klíčové slovo se používá ve výrazech vazby k definování hodnot nebo hodnot funkcí pro jeden nebo více názvů.</span><span class="sxs-lookup"><span data-stu-id="06e36-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="06e36-109">Nejjednodušší forma `let` výrazu váže název k jednoduché hodnotě, jak je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="06e36-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="06e36-110">Pokud oddělíte výraz od identifikátoru pomocí nového řádku, je nutné odsadit každý řádek výrazu, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06e36-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="06e36-111">Namísto pouze názvu lze zadat vzor, který obsahuje názvy, například řazené kolekce členů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06e36-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="06e36-112">*Výraz body* je výraz, ve kterém jsou názvy použity.</span><span class="sxs-lookup"><span data-stu-id="06e36-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="06e36-113">Výraz textu se zobrazí na vlastním řádku, odsazený tak, aby přesně odpovídal prvnímu znaku v `let` klíčovém slově:</span><span class="sxs-lookup"><span data-stu-id="06e36-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="06e36-114">`let`Vazba se může zobrazit na úrovni modulu, v definici typu třídy nebo v místních oborech, jako je například v definici funkce.</span><span class="sxs-lookup"><span data-stu-id="06e36-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="06e36-115">`let`Vazba na nejvyšší úrovni v modulu nebo v typu třídy nemusí mít výraz body, ale v jiných úrovních oboru je požadován výraz textu.</span><span class="sxs-lookup"><span data-stu-id="06e36-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="06e36-116">Vázané názvy jsou použitelné po bodě definice, ale ne v jakémkoli bodě před `let` zobrazením vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06e36-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="06e36-117">Vazby funkcí</span><span class="sxs-lookup"><span data-stu-id="06e36-117">Function Bindings</span></span>

<span data-ttu-id="06e36-118">Vazby funkcí následují pravidla pro vazby hodnot, s výjimkou, že vazby funkcí zahrnují název funkce a parametry, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06e36-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="06e36-119">Obecně platí, že parametry jsou vzory, jako je například vzor řazené kolekce členů:</span><span class="sxs-lookup"><span data-stu-id="06e36-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="06e36-120">`let`Výraz vazby se vyhodnocuje na hodnotu posledního výrazu.</span><span class="sxs-lookup"><span data-stu-id="06e36-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="06e36-121">Proto v následujícím příkladu kódu `result` je hodnota vypočítána z `100 * function3 (1, 2)` , která je vyhodnocena jako `300` .</span><span class="sxs-lookup"><span data-stu-id="06e36-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="06e36-122">Další informace najdete v tématu [funkce](index.md).</span><span class="sxs-lookup"><span data-stu-id="06e36-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="06e36-123">Anotace typu</span><span class="sxs-lookup"><span data-stu-id="06e36-123">Type Annotations</span></span>

<span data-ttu-id="06e36-124">Můžete určit typy pro parametry zahrnutím dvojtečky (:) následováno názvem typu, který je uzavřen v závorkách.</span><span class="sxs-lookup"><span data-stu-id="06e36-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="06e36-125">Můžete také zadat typ návratové hodnoty připojením dvojtečky a typu za posledním parametrem.</span><span class="sxs-lookup"><span data-stu-id="06e36-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="06e36-126">Úplné poznámky typu pro `function1` , s celými čísly jako typy parametrů, by byly následující.</span><span class="sxs-lookup"><span data-stu-id="06e36-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="06e36-127">Pokud nejsou k dispozici žádné explicitní parametry typu, použije se odvození typu k určení typů parametrů funkcí.</span><span class="sxs-lookup"><span data-stu-id="06e36-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="06e36-128">To může zahrnovat automatické generalizace typu parametru, který má být obecný.</span><span class="sxs-lookup"><span data-stu-id="06e36-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="06e36-129">Další informace naleznete v tématu [automatické generalizace](../generics/automatic-generalization.md) a [odvození typu](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="06e36-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="06e36-130">Vazby let ve třídách</span><span class="sxs-lookup"><span data-stu-id="06e36-130">let Bindings in Classes</span></span>

<span data-ttu-id="06e36-131">`let`Vazba se může objevit v typu třídy, ale ne v typu struktury nebo záznamu.</span><span class="sxs-lookup"><span data-stu-id="06e36-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="06e36-132">Chcete-li použít vazbu let v typu třídy, třída musí mít primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="06e36-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="06e36-133">Parametry konstruktoru se musí vyskytovat za názvem typu v definici třídy.</span><span class="sxs-lookup"><span data-stu-id="06e36-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="06e36-134">`let`Vazba v typu třídy definuje soukromá pole a členy pro daný typ třídy a společně s `do` vazbami v typu tvoří kód pro primární konstruktor pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="06e36-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="06e36-135">Následující příklady kódu ukazují třídu `MyClass` s privátními poli `field1` a `field2` .</span><span class="sxs-lookup"><span data-stu-id="06e36-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="06e36-136">Obory `field1` a `field2` jsou omezeny na typ, ve kterém jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="06e36-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="06e36-137">Další informace naleznete v tématu [ `let` vazby v třídách](../members/let-bindings-in-classes.md) a [třídách](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="06e36-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="06e36-138">Parametry typu ve vazbách let</span><span class="sxs-lookup"><span data-stu-id="06e36-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="06e36-139">`let`Vazba na úrovni modulu, v typu nebo ve výrazu výpočtu může mít explicitní parametry typu.</span><span class="sxs-lookup"><span data-stu-id="06e36-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="06e36-140">Vazba let ve výrazu, například v rámci definice funkce, nemůže mít parametry typu.</span><span class="sxs-lookup"><span data-stu-id="06e36-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="06e36-141">Další informace najdete v tématu [Obecné typy](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="06e36-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="06e36-142">Atributy u vazeb let</span><span class="sxs-lookup"><span data-stu-id="06e36-142">Attributes on let Bindings</span></span>

<span data-ttu-id="06e36-143">Atributy lze použít u vazeb nejvyšší úrovně `let` v modulu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="06e36-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="06e36-144">Rozsah a přístupnost pro vazby let</span><span class="sxs-lookup"><span data-stu-id="06e36-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="06e36-145">Rozsah entity deklarované pomocí vazby let je omezen na část nadřazeného oboru (například funkce, modulu, souboru nebo třídy) Po zobrazení vazby.</span><span class="sxs-lookup"><span data-stu-id="06e36-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="06e36-146">Proto je možné říci, že vazba let zavádí název do oboru.</span><span class="sxs-lookup"><span data-stu-id="06e36-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="06e36-147">V modulu je pro klienty modulu přístupná hodnota nebo funkce s vazbou, pokud je modul dostupný, protože vazby let v modulu jsou kompilovány do veřejných funkcí modulu.</span><span class="sxs-lookup"><span data-stu-id="06e36-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="06e36-148">Naproti tomu mají vazby ve třídě pro třídu privátní.</span><span class="sxs-lookup"><span data-stu-id="06e36-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="06e36-149">Funkce v modulech musí být obvykle kvalifikovány názvem modulu při použití klientským kódem.</span><span class="sxs-lookup"><span data-stu-id="06e36-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="06e36-150">Například pokud `Module1` má modul funkci `function1` , uživatelé zadávají `Module1.function1` odkaz na funkci.</span><span class="sxs-lookup"><span data-stu-id="06e36-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="06e36-151">Uživatelé modulu mohou použít deklaraci import, aby byly funkce v rámci tohoto modulu dostupné pro použití bez kvalifikovaného názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="06e36-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="06e36-152">V příkladu, který je právě zmíněn, uživatelé modulu můžou v takovém případě otevřít modul pomocí otevřené deklarace importu `Module1` a následně na odkaz `function1` přímo.</span><span class="sxs-lookup"><span data-stu-id="06e36-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="06e36-153">Některé moduly mají atribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), což znamená, že funkce, které zveřejňují, musí být kvalifikovány názvem modulu.</span><span class="sxs-lookup"><span data-stu-id="06e36-153">Some modules have the attribute [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="06e36-154">Například modul seznamu jazyka F # má tento atribut.</span><span class="sxs-lookup"><span data-stu-id="06e36-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="06e36-155">Další informace o modulech a řízení přístupu najdete v tématech [moduly](../modules.md) a [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="06e36-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="06e36-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="06e36-156">See also</span></span>

- [<span data-ttu-id="06e36-157">Functions</span><span class="sxs-lookup"><span data-stu-id="06e36-157">Functions</span></span>](index.md)
- [<span data-ttu-id="06e36-158">`let` Vazby ve třídách</span><span class="sxs-lookup"><span data-stu-id="06e36-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
