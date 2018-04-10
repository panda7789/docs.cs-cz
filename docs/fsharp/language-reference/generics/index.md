---
title: Obecné typy (F#)
description: 'Další informace o použití F # obecné funkce a typy, které vám umožní napsat kód, který funguje s různými typy bez opakování kódu.'
keywords: 'Visual f #, f #, funkční programování'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a9f2e2ee-bcb1-4ce3-8531-850aa183040f
ms.openlocfilehash: e7a5712fddf4d372d1ada86927f50e394a59a410
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="generics"></a><span data-ttu-id="8b115-104">Obecné typy</span><span class="sxs-lookup"><span data-stu-id="8b115-104">Generics</span></span>

<span data-ttu-id="8b115-105">Funkce F # hodnoty, metody, vlastnosti a typy agregace, jako jsou třídy, zaznamenává a může být rozlišovaná sjednocení *Obecné*.</span><span class="sxs-lookup"><span data-stu-id="8b115-105">F# function values, methods, properties, and aggregate types such as classes, records, and discriminated unions can be *generic*.</span></span> <span data-ttu-id="8b115-106">Obecné konstrukce obsahovat alespoň jeden parametr typu, který je obvykle zadaný uživatelem obecné konstrukce.</span><span class="sxs-lookup"><span data-stu-id="8b115-106">Generic constructs contain at least one type parameter, which is usually supplied by the user of the generic construct.</span></span> <span data-ttu-id="8b115-107">Obecné funkce a typy umožňují napsat kód, který funguje s různými typy bez opakování kód pro každý typ.</span><span class="sxs-lookup"><span data-stu-id="8b115-107">Generic functions and types enable you to write code that works with a variety of types without repeating the code for each type.</span></span> <span data-ttu-id="8b115-108">Vytváření kódu Obecné může být jednoduchý v F #, protože často kódu je implicitně odvodit jako obecný odvození typu kompilátoru a Automatická generalizace mechanismy.</span><span class="sxs-lookup"><span data-stu-id="8b115-108">Making your code generic can be simple in F#, because often your code is implicitly inferred to be generic by the compiler's type inference and automatic generalization mechanisms.</span></span>


## <a name="syntax"></a><span data-ttu-id="8b115-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b115-109">Syntax</span></span>

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a><span data-ttu-id="8b115-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b115-110">Remarks</span></span>
<span data-ttu-id="8b115-111">Prohlášení explicitně obecné funkce nebo typu mnohem je třeba u funkce neobecnou nebo typu, s výjimkou specifikace (a použití) parametry typu, v lomených závorkách po název funkce nebo typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-111">The declaration of an explicitly generic function or type is much like that of a non-generic function or type, except for the specification (and use) of the type parameters, in angle brackets after the function or type name.</span></span>

<span data-ttu-id="8b115-112">Deklarace jsou často implicitně Obecné.</span><span class="sxs-lookup"><span data-stu-id="8b115-112">Declarations are often implicitly generic.</span></span> <span data-ttu-id="8b115-113">Pokud nezadáte plně typ každý parametr, který se používá k vytvoření funkce nebo typu, pokusí se kompilátor odvození typu každý parametr, hodnoty a proměnné z kódu, kterou píšete.</span><span class="sxs-lookup"><span data-stu-id="8b115-113">If you do not fully specify the type of every parameter that is used to compose a function or type, the compiler attempts to infer the type of each parameter, value, and variable from the code you write.</span></span> <span data-ttu-id="8b115-114">Další informace najdete v tématu [odvození typu](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="8b115-114">For more information, see [Type Inference](../type-inference.md).</span></span> <span data-ttu-id="8b115-115">Pokud kód pro typ nebo funkci jinak neuvádělo typy parametrů, je implicitně obecné funkce nebo typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-115">If the code for your type or function does not otherwise constrain the types of parameters, the function or type is implicitly generic.</span></span> <span data-ttu-id="8b115-116">Tento proces se nazývá *Automatická generalizace*.</span><span class="sxs-lookup"><span data-stu-id="8b115-116">This process is named *automatic generalization*.</span></span> <span data-ttu-id="8b115-117">Existují některá omezení na automatická generalizace.</span><span class="sxs-lookup"><span data-stu-id="8b115-117">There are some limits on automatic generalization.</span></span> <span data-ttu-id="8b115-118">Například pokud kompilátor jazyka F # se nepodařilo odvodit typy pro obecné konstrukce, kompilátor ohlásí chybu, která odkazuje na omezení volat *hodnoty omezení*.</span><span class="sxs-lookup"><span data-stu-id="8b115-118">For example, if the F# compiler is unable to infer the types for a generic construct, the compiler reports an error that refers to a restriction called the *value restriction*.</span></span> <span data-ttu-id="8b115-119">V takovém případě budete muset přidat některé typu poznámky.</span><span class="sxs-lookup"><span data-stu-id="8b115-119">In that case, you may have to add some type annotations.</span></span> <span data-ttu-id="8b115-120">Další informace o Automatická Generalizace a omezení hodnoty a jak změnit svůj kód potíže vyřešit, najdete v části [Automatická generalizace](automatic-generalization.md).</span><span class="sxs-lookup"><span data-stu-id="8b115-120">For more information about automatic generalization and the value restriction, and how to change your code to address the problem, see [Automatic Generalization](automatic-generalization.md).</span></span>

<span data-ttu-id="8b115-121">V předchozích syntaxi *parametry typu* je textový soubor s oddělovači seznam parametrů, které představují neznámé typy, z nichž každá začíná jednoduché uvozovky, volitelně s klauzulí omezení, která další omezuje, co může typy použít pro tento parametr typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-121">In the previous syntax, *type-parameters* is a comma-separated list of parameters that represent unknown types, each of which starts with a single quotation mark, optionally with a constraint clause that further limits what types may be used for that type parameter.</span></span> <span data-ttu-id="8b115-122">Syntaxe pro omezení klauzulích různé typy a další informace o omezení, najdete v části [omezení](constraints.md).</span><span class="sxs-lookup"><span data-stu-id="8b115-122">For the syntax for constraint clauses of various kinds and other information about constraints, see [Constraints](constraints.md).</span></span>

<span data-ttu-id="8b115-123">*Definice typu* v syntaxi je stejná jako definice typu pro neobecný typ.</span><span class="sxs-lookup"><span data-stu-id="8b115-123">The *type-definition* in the syntax is the same as the type definition for a non-generic type.</span></span> <span data-ttu-id="8b115-124">Obsahuje parametry konstruktor pro typ třídy, volitelný `as` klauzule, rovnou symbol, pole záznamu `inherit` klauzule, volby rozlišovaná sjednocení `let` a `do` vazby, definice člena a jakékoli jiné definice typu neobecnou povoleny.</span><span class="sxs-lookup"><span data-stu-id="8b115-124">It includes the constructor parameters for a class type, an optional `as` clause, the equal symbol, the record fields, the `inherit` clause, the choices for a discriminated union, `let` and `do` bindings, member definitions, and anything else permitted in a non-generic type definition.</span></span>

<span data-ttu-id="8b115-125">Další prvky syntaxe jsou stejné jako u neobecnou funkcí a typů.</span><span class="sxs-lookup"><span data-stu-id="8b115-125">The other syntax elements are the same as those for non-generic functions and types.</span></span> <span data-ttu-id="8b115-126">Například *identifikátor objektu* je identifikátor, který představuje obsahující odkaz sám na sebe.</span><span class="sxs-lookup"><span data-stu-id="8b115-126">For example, *object-identifier* is an identifier that represents the containing object itself.</span></span>

<span data-ttu-id="8b115-127">Konstruktory, vlastnosti a pole nemůže být více obecné než nadřazených typů.</span><span class="sxs-lookup"><span data-stu-id="8b115-127">Properties, fields, and constructors cannot be more generic than the enclosing type.</span></span> <span data-ttu-id="8b115-128">Hodnoty v modulu také nemohou být obecný.</span><span class="sxs-lookup"><span data-stu-id="8b115-128">Also, values in a module cannot be generic.</span></span>


## <a name="implicitly-generic-constructs"></a><span data-ttu-id="8b115-129">Implicitně obecné konstrukce</span><span class="sxs-lookup"><span data-stu-id="8b115-129">Implicitly Generic Constructs</span></span>
<span data-ttu-id="8b115-130">Když kompilátor jazyka F # odvodí, že typy v kódu, automaticky zpracovává všechny funkce, která může být obecný jako obecný.</span><span class="sxs-lookup"><span data-stu-id="8b115-130">When the F# compiler infers the types in your code, it automatically treats any function that can be generic as generic.</span></span> <span data-ttu-id="8b115-131">Pokud zadáte typu explicitně, jako je například typ parametru, abyste zabránili Automatická generalizace.</span><span class="sxs-lookup"><span data-stu-id="8b115-131">If you specify a type explicitly, such as a parameter type, you prevent automatic generalization.</span></span>

<span data-ttu-id="8b115-132">V následujícím příkladu kódu `makeList` je obecný, i když ho ani jeho parametry jsou deklarovány explicitně jako obecný.</span><span class="sxs-lookup"><span data-stu-id="8b115-132">In the following code example, `makeList` is generic, even though neither it nor its parameters are explicitly declared as generic.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

<span data-ttu-id="8b115-133">Podpis funkce je odvodit být `'a -> 'a -> 'a list`.</span><span class="sxs-lookup"><span data-stu-id="8b115-133">The signature of the function is inferred to be `'a -> 'a -> 'a list`.</span></span> <span data-ttu-id="8b115-134">Všimněte si, že `a` a `b` v tomto příkladu jsou odvodit tak, aby měl stejného typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-134">Note that `a` and `b` in this example are inferred to have the same type.</span></span> <span data-ttu-id="8b115-135">Je to proto, že jsou zahrnuty do seznamu společně a všechny elementy v seznamu musí být stejného typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-135">This is because they are included in a list together, and all elements of a list must be of the same type.</span></span>

<span data-ttu-id="8b115-136">Můžete provést také funkci obecné pomocí syntaxe jednoduché uvozovky v anotaci typu k označení, že je typ parametru parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-136">You can also make a function generic by using the single quotation mark syntax in a type annotation to indicate that a parameter type is a generic type parameter.</span></span> <span data-ttu-id="8b115-137">V následujícím kódu `function1` je obecný, protože jeho parametry jsou deklarovány tímto způsobem, jako parametrů typů.</span><span class="sxs-lookup"><span data-stu-id="8b115-137">In the following code, `function1` is generic because its parameters are declared in this manner, as type parameters.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]
    
## <a name="explicitly-generic-constructs"></a><span data-ttu-id="8b115-138">Explicitně obecné konstrukce</span><span class="sxs-lookup"><span data-stu-id="8b115-138">Explicitly Generic Constructs</span></span>
<span data-ttu-id="8b115-139">Můžete provést také funkci obecné explicitně deklarováním jeho parametry typu v lomených závorkách (`<type-parameter>`).</span><span class="sxs-lookup"><span data-stu-id="8b115-139">You can also make a function generic by explicitly declaring its type parameters in angle brackets (`<type-parameter>`).</span></span> <span data-ttu-id="8b115-140">Následující kód to znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="8b115-140">The following code illustrates this.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]
    
## <a name="using-generic-constructs"></a><span data-ttu-id="8b115-141">Pomocí obecné konstrukce</span><span class="sxs-lookup"><span data-stu-id="8b115-141">Using Generic Constructs</span></span>
<span data-ttu-id="8b115-142">Při použití obecné funkce nebo metod, nemusí mít k určení argumenty typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-142">When you use generic functions or methods, you might not have to specify the type arguments.</span></span> <span data-ttu-id="8b115-143">Kompilátor používá odvození typu k odvození argumenty příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-143">The compiler uses type inference to infer the appropriate type arguments.</span></span> <span data-ttu-id="8b115-144">Pokud je stále to nejednoznačnost, můžete zadat argumenty typu v lomených závorkách více argumentů typu oddělíte čárkami.</span><span class="sxs-lookup"><span data-stu-id="8b115-144">If there is still an ambiguity, you can supply type arguments in angle brackets, separating multiple type arguments with commas.</span></span>

<span data-ttu-id="8b115-145">Následující kód ukazuje použití funkce, které jsou definované v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="8b115-145">The following code shows the use of the functions that are defined in the previous sections.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]
    
>[!NOTE]
<span data-ttu-id="8b115-146">Existují dva způsoby, který bude odkazovat na obecného typu podle názvu.</span><span class="sxs-lookup"><span data-stu-id="8b115-146">There are two ways to refer to a generic type by name.</span></span> <span data-ttu-id="8b115-147">Například `list<int>` a `int list` jsou dva způsoby, jak odkazovat na obecného typu `list` s argumentem jednoho typu `int`.</span><span class="sxs-lookup"><span data-stu-id="8b115-147">For example, `list<int>` and `int list` are two ways to refer to a generic type `list` that has a single type argument `int`.</span></span> <span data-ttu-id="8b115-148">Druhé formuláře se obvykle používá jenom s předdefinovaných typů F #, jako `list` a `option`.</span><span class="sxs-lookup"><span data-stu-id="8b115-148">The latter form is conventionally used only with built-in F# types such as `list` and `option`.</span></span> <span data-ttu-id="8b115-149">Pokud existují více argumentů typu, je obvykle použít syntaxi `Dictionary<int, string>` ale můžete také použít syntaxi `(int, string) Dictionary`.</span><span class="sxs-lookup"><span data-stu-id="8b115-149">If there are multiple type arguments, you normally use the syntax `Dictionary<int, string>` but you can also use the syntax `(int, string) Dictionary`.</span></span>

## <a name="wildcards-as-type-arguments"></a><span data-ttu-id="8b115-150">Zástupné znaky jako argumenty typů</span><span class="sxs-lookup"><span data-stu-id="8b115-150">Wildcards as Type Arguments</span></span>
<span data-ttu-id="8b115-151">Chcete-li určit, že argument typu událostmi kompilátorem, můžete použít podtržítko nebo zástupný znak (`_`), místo argument pojmenovaného typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-151">To specify that a type argument should be inferred by the compiler, you can use the underscore, or wildcard symbol (`_`), instead of a named type argument.</span></span> <span data-ttu-id="8b115-152">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8b115-152">This is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]
    
## <a name="constraints-in-generic-types-and-functions"></a><span data-ttu-id="8b115-153">Omezení v obecné typy a funkce</span><span class="sxs-lookup"><span data-stu-id="8b115-153">Constraints in Generic Types and Functions</span></span>
<span data-ttu-id="8b115-154">V obecného typu nebo definice funkce můžete použít pouze konstrukce, která jsou známá, mají být k dispozici na parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="8b115-154">In a generic type or function definition, you can use only those constructs that are known to be available on the generic type parameter.</span></span> <span data-ttu-id="8b115-155">To je potřeba povolit ověření volání funkce a metoda v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="8b115-155">This is required to enable the verification of function and method calls at compile time.</span></span> <span data-ttu-id="8b115-156">Pokud je výslovně deklarovat parametry typu, můžete použít explicitní omezení pro parametr obecného typu oznámit kompilátor některé metody a funkce jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8b115-156">If you declare your type parameters explicitly, you can apply an explicit constraint to a generic type parameter to notify the compiler that certain methods and functions are available.</span></span> <span data-ttu-id="8b115-157">Ale pokud povolíte kompilátoru F # odvodit vaší obecný parametr typy, zjišťuje odpovídající omezení pro vás.</span><span class="sxs-lookup"><span data-stu-id="8b115-157">However, if you allow the F# compiler to infer your generic parameter types, it will determine the appropriate constraints for you.</span></span> <span data-ttu-id="8b115-158">Další informace najdete v tématu [omezení](constraints.md).</span><span class="sxs-lookup"><span data-stu-id="8b115-158">For more information, see [Constraints](constraints.md).</span></span>


## <a name="statically-resolved-type-parameters"></a><span data-ttu-id="8b115-159">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="8b115-159">Statically Resolved Type Parameters</span></span>
<span data-ttu-id="8b115-160">Existují dva typy parametrů typu, které mohou být používány programů F #.</span><span class="sxs-lookup"><span data-stu-id="8b115-160">There are two kinds of type parameters that can be used in F# programs.</span></span> <span data-ttu-id="8b115-161">První jsou parametry obecného typu druhu popsané v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="8b115-161">The first are generic type parameters of the kind described in the previous sections.</span></span> <span data-ttu-id="8b115-162">Tento první druh parametr typu je stejná jako parametry obecného typu, které se používají v jazycích, jako je například Visual Basic a C#.</span><span class="sxs-lookup"><span data-stu-id="8b115-162">This first kind of type parameter is equivalent to the generic type parameters that are used in languages such as Visual Basic and C#.</span></span> <span data-ttu-id="8b115-163">Jiný druh parametr typu je specifický pro F # a odkazuje jako *parametr typu určené statisticky*.</span><span class="sxs-lookup"><span data-stu-id="8b115-163">Another kind of type parameter is specific to F# and is referred to as a *statically resolved type parameter*.</span></span> <span data-ttu-id="8b115-164">Informace o těchto konstrukce najdete v tématu [statisticky vyřešené parametry typu](statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="8b115-164">For information about these constructs, see [Statically Resolved Type Parameters](statically-resolved-type-parameters.md).</span></span>


## <a name="examples"></a><span data-ttu-id="8b115-165">Příklady</span><span class="sxs-lookup"><span data-stu-id="8b115-165">Examples</span></span>
[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]
    
## <a name="see-also"></a><span data-ttu-id="8b115-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b115-166">See Also</span></span>
[<span data-ttu-id="8b115-167">Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="8b115-167">Language Reference</span></span>](../index.md)

[<span data-ttu-id="8b115-168">Typy</span><span class="sxs-lookup"><span data-stu-id="8b115-168">Types</span></span>](../fsharp-types.md)

[<span data-ttu-id="8b115-169">Statisticky vyřešené parametry typu</span><span class="sxs-lookup"><span data-stu-id="8b115-169">Statically Resolved Type Parameters</span></span>](statically-resolved-type-parameters.md)

[<span data-ttu-id="8b115-170">Obecné typy v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8b115-170">Generics in the .NET Framework</span></span>](~/docs/standard/generics/index.md)

[<span data-ttu-id="8b115-171">Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="8b115-171">Automatic Generalization</span></span>](automatic-generalization.md)

[<span data-ttu-id="8b115-172">Omezení</span><span class="sxs-lookup"><span data-stu-id="8b115-172">Constraints</span></span>](constraints.md)
