---
title: Implicitně zadané místní proměnné – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399824"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="e1cc9-102">Implicitně zadané místní proměnné (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e1cc9-102">Implicitly typed local variables (C# Programming Guide)</span></span>

<span data-ttu-id="e1cc9-103">Místní proměnné lze deklarovat bez zadání explicitního typu.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="e1cc9-104">Klíčové `var` slovo pokyn kompilátorododu odvodit typ proměnné z výrazu na pravé straně příkazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="e1cc9-105">Odvozený typ může být vestavěný typ, anonymní typ, uživatelem definovaný typ nebo typ definovaný v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="e1cc9-106">Další informace o inicializaci polí `var`pomocí naleznete [v tématu Implicitně zadaný pole](../arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="e1cc9-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../arrays/implicitly-typed-arrays.md).</span></span>

<span data-ttu-id="e1cc9-107">Následující příklady ukazují různé způsoby, kterými `var`lze deklarovat místní proměnné pomocí :</span><span class="sxs-lookup"><span data-stu-id="e1cc9-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

<span data-ttu-id="e1cc9-108">Je důležité si uvědomit, že `var` klíčové slovo neznamená "varianta" a neznamená, že proměnná je volně zadaný nebo pozdní vázaný.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="e1cc9-109">To jen znamená, že kompilátor určuje a přiřadí nejvhodnější typ.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>

<span data-ttu-id="e1cc9-110">Klíčové `var` slovo lze použít v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="e1cc9-110">The `var` keyword may be used in the following contexts:</span></span>

- <span data-ttu-id="e1cc9-111">Na místní proměnné (proměnné deklarované v oboru metody), jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>

- <span data-ttu-id="e1cc9-112">V příkazu [for](../../language-reference/keywords/for.md) inicializace.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-112">In a [for](../../language-reference/keywords/for.md) initialization statement.</span></span>

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- <span data-ttu-id="e1cc9-113">V [příkazu foreach](../../language-reference/keywords/foreach-in.md) inicializace.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-113">In a [foreach](../../language-reference/keywords/foreach-in.md) initialization statement.</span></span>

    ```csharp
    foreach (var item in list) {...}
    ```

- <span data-ttu-id="e1cc9-114">V [using](../../language-reference/keywords/using-statement.md) prohlášení.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-114">In a [using](../../language-reference/keywords/using-statement.md) statement.</span></span>

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

<span data-ttu-id="e1cc9-115">Další informace naleznete v tématu [Použití implicitně zadávaných místních proměnných a polí ve výrazu dotazu](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="e1cc9-115">For more information, see [How to use implicitly typed local variables and arrays in a query expression](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>

## <a name="var-and-anonymous-types"></a><span data-ttu-id="e1cc9-116">var a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="e1cc9-116">var and anonymous types</span></span>

<span data-ttu-id="e1cc9-117">V mnoha případech `var` je použití je volitelné a je jen syntaktické pohodlí.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="e1cc9-118">Pokud je však proměnná inicializována s `var` anonymním typem, musíte deklarovat proměnnou, jako byste potřebovali přístup k vlastnostem objektu později.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="e1cc9-119">Toto je běžný scénář ve výrazech dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-119">This is a common scenario in LINQ query expressions.</span></span> <span data-ttu-id="e1cc9-120">Další informace naleznete [v tématu Anonymní typy](anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="e1cc9-120">For more information, see [Anonymous Types](anonymous-types.md).</span></span>

<span data-ttu-id="e1cc9-121">Z hlediska zdrojového kódu anonymní typ nemá žádný název.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="e1cc9-122">Proto pokud proměnná dotazu byla `var`inicializována s , pak jediný způsob, `var` jak získat přístup k vlastnostem v vrácené posloupnosti objektů je použít jako typ iterace proměnné v příkazu. `foreach`</span><span class="sxs-lookup"><span data-stu-id="e1cc9-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a><span data-ttu-id="e1cc9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1cc9-123">Remarks</span></span>

<span data-ttu-id="e1cc9-124">Následující omezení platí pro implicitně zadané deklarace proměnných:</span><span class="sxs-lookup"><span data-stu-id="e1cc9-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>

- <span data-ttu-id="e1cc9-125">`var`lze použít pouze v případě, že je místní proměnná deklarována a inicializována ve stejném příkazu; proměnnou nelze inicializovat na hodnotu null nebo na skupinu metod nebo anonymní funkci.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>

- <span data-ttu-id="e1cc9-126">`var`nelze použít v polích v oboru třídy.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-126">`var` cannot be used on fields at class scope.</span></span>

- <span data-ttu-id="e1cc9-127">Proměnné deklarované pomocí `var` nelze použít ve výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="e1cc9-128">Jinými slovy, tento výraz `int i = (i = 20);` je legální: ale tento výraz vytváří chybu v době kompilace:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="e1cc9-128">In other words, this expression is legal: `int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>

- <span data-ttu-id="e1cc9-129">Více implicitně zadaných proměnných nelze inicializovat ve stejném příkazu.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>

- <span data-ttu-id="e1cc9-130">Pokud je `var` typ pojmenovaný v `var` oboru, bude klíčové slovo přeložit na tento název typu a nebude považováno za součást implicitně zadané deklarace místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>

<span data-ttu-id="e1cc9-131">Implicitní psaní `var` pomocí klíčového slova lze použít pouze na proměnné v oboru místní metody.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-131">Implicit typing with the `var` keyword can only be applied to variables at local method scope.</span></span> <span data-ttu-id="e1cc9-132">Implicitní psaní není k dispozici pro pole třídy jako kompilátor Jazyka C# by dojít k logickému paradoxu, protože zpracovává kód: kompilátor potřebuje znát typ pole, ale nemůže určit typ, dokud je analyzován výraz přiřazení a výraz nelze vyhodnotit bez znalosti typu.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-132">Implicit typing is not available for class fields as the C# compiler would encounter a logical paradox as it processed the code: the compiler needs to know the type of the field, but it cannot determine the type until the assignment expression is analyzed, and the expression cannot be evaluated without knowing the type.</span></span> <span data-ttu-id="e1cc9-133">Uvažujte následující kód:</span><span class="sxs-lookup"><span data-stu-id="e1cc9-133">Consider the following code:</span></span>

```csharp
private var bookTitles;
```

<span data-ttu-id="e1cc9-134">`bookTitles`je pole třídy `var`s typem .</span><span class="sxs-lookup"><span data-stu-id="e1cc9-134">`bookTitles` is a class field given the type `var`.</span></span> <span data-ttu-id="e1cc9-135">Vzhledem k tomu, že pole nemá žádný výraz k vyhodnocení, je nemožné, aby kompilátor odvodil, jaký typ `bookTitles` má být.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-135">As the field has no expression to evaluate, it is impossible for the compiler to infer what type `bookTitles` is supposed to be.</span></span> <span data-ttu-id="e1cc9-136">Kromě toho přidání výrazu do pole (stejně jako u místní proměnné) je také nedostatečné:</span><span class="sxs-lookup"><span data-stu-id="e1cc9-136">In addition, adding an expression to the field (like you would for a local variable) is also insufficient:</span></span>

```csharp
private var bookTitles = new List<string>();
```

<span data-ttu-id="e1cc9-137">Když kompilátor narazí na pole během kompilace kódu, zaznamená typ každého pole před zpracováním všech výrazů, které jsou k němu přidruženy.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-137">When the compiler encounters fields during code compilation, it records each field's type before processing any expressions associated with it.</span></span> <span data-ttu-id="e1cc9-138">Kompilátor narazí na stejný paradox `bookTitles`při pokusu o analýzu : potřebuje znát typ `var`pole, ale kompilátor by normálně určit 's typ analýzou výrazu, který není možné bez znalosti typu předem.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-138">The compiler encounters the same paradox trying to parse `bookTitles`: it needs to know the type of the field, but the compiler would normally determine `var`'s type by analyzing the expression, which isn't possible without knowing the type beforehand.</span></span>

<span data-ttu-id="e1cc9-139">Můžete zjistit, `var` že může být také užitečné s výrazy dotazu, ve kterém je obtížné určit přesný typ konstruované proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-139">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="e1cc9-140">K tomu může dojít při seskupování a řazení operací.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-140">This can occur with grouping and ordering operations.</span></span>

<span data-ttu-id="e1cc9-141">Klíčové `var` slovo může být také užitečné, pokud je konkrétní typ proměnné zdlouhavý pro psaní na klávesnici, nebo je zřejmý nebo nepřidává k čitelnosti kódu.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-141">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="e1cc9-142">Jeden příklad, kde `var` je užitečné tímto způsobem je s vnořené obecné typy, jako jsou ty, které se používají s operacemi skupiny.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-142">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="e1cc9-143">V následujícím dotazu je `IEnumerable<IGrouping<string, Student>>`typ proměnné dotazu .</span><span class="sxs-lookup"><span data-stu-id="e1cc9-143">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="e1cc9-144">Tak dlouho, dokud vy a ostatní, kteří musí udržovat váš kód pochopit, není žádný problém s použitím implicitní psaní pro pohodlí a stručnost.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-144">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

<span data-ttu-id="e1cc9-145">Použití `var` pomáhá zjednodušit kód, ale jeho použití by mělo být omezeno na případy, kde je požadováno, nebo když usnadňuje čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-145">The use of `var` helps simplify your code, but its use should be restricted to cases where it is required, or when it makes your code easier to read.</span></span> <span data-ttu-id="e1cc9-146">Další informace o tom, kdy správně používat, `var` naleznete v části [Implicitně zadané místní proměnné](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) v článku C# Coding Guidelines.</span><span class="sxs-lookup"><span data-stu-id="e1cc9-146">For more information about when to use `var` properly, see the [Implicitly typed local variables](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) section on the C# Coding Guidelines article.</span></span>

## <a name="see-also"></a><span data-ttu-id="e1cc9-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1cc9-147">See also</span></span>

- [<span data-ttu-id="e1cc9-148">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e1cc9-148">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e1cc9-149">Implicitně typovaná pole</span><span class="sxs-lookup"><span data-stu-id="e1cc9-149">Implicitly Typed Arrays</span></span>](../arrays/implicitly-typed-arrays.md)
- [<span data-ttu-id="e1cc9-150">Použití implicitně zadávaných místních proměnných a polí ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="e1cc9-150">How to use implicitly typed local variables and arrays in a query expression</span></span>](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [<span data-ttu-id="e1cc9-151">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="e1cc9-151">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="e1cc9-152">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="e1cc9-152">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
- [<span data-ttu-id="e1cc9-153">Var</span><span class="sxs-lookup"><span data-stu-id="e1cc9-153">var</span></span>](../../language-reference/keywords/var.md)
- [<span data-ttu-id="e1cc9-154">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e1cc9-154">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="e1cc9-155">LINQ (dotaz integrovaný jazykem)</span><span class="sxs-lookup"><span data-stu-id="e1cc9-155">LINQ (Language-Integrated Query)</span></span>](../../linq/index.md)
- [<span data-ttu-id="e1cc9-156">Pro</span><span class="sxs-lookup"><span data-stu-id="e1cc9-156">for</span></span>](../../language-reference/keywords/for.md)
- [<span data-ttu-id="e1cc9-157">foreach, in</span><span class="sxs-lookup"><span data-stu-id="e1cc9-157">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="e1cc9-158">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="e1cc9-158">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
