---
title: Implicitně typované lokální proměnné - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 68c0ff055c91f4f1deca6fcfada0f14577439731
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237009"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="ff498-102">Implicitně typované lokální proměnné (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ff498-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="ff498-103">Lokální proměnné mohou být deklarovány bez explicitního typu.</span><span class="sxs-lookup"><span data-stu-id="ff498-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="ff498-104">`var` – Klíčové slovo instruuje kompilátor k odvození typu proměnné z výrazu na pravé straně výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="ff498-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="ff498-105">Odvozený typ může být předdefinovaný typ, anonymního typu, uživatelem definovaný typ nebo typ definovaný v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff498-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="ff498-106">Další informace o tom, jak inicializovat pole s `var`, naleznete v tématu [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="ff498-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="ff498-107">Následující příklady znázorňují různé způsoby, jimiž lze deklarovat lokální proměnné s `var`:</span><span class="sxs-lookup"><span data-stu-id="ff498-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="ff498-108">Je důležité si uvědomit, že `var` – klíčové slovo neznamená "varianta" a neznamená, že proměnná je volně typem nebo s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="ff498-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="ff498-109">Znamená pouze to, že kompilátor zjistí a přiřadí nejvhodnější typ.</span><span class="sxs-lookup"><span data-stu-id="ff498-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="ff498-110">`var` – Klíčové slovo lze použít v následujících kontextů:</span><span class="sxs-lookup"><span data-stu-id="ff498-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="ff498-111">Na lokální proměnné (proměnné deklarované v oboru metoda) jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ff498-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="ff498-112">V [pro](../../../csharp/language-reference/keywords/for.md) příkaz inicializace.</span><span class="sxs-lookup"><span data-stu-id="ff498-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```csharp  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="ff498-113">V [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz inicializace.</span><span class="sxs-lookup"><span data-stu-id="ff498-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```csharp  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="ff498-114">V [pomocí](../../../csharp/language-reference/keywords/using-statement.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="ff498-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```csharp  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="ff498-115">Další informace najdete v tématu [jak: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="ff498-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="ff498-116">var a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="ff498-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="ff498-117">V mnoha případech použití `var` je volitelný a je právě syntaktické pohodlí.</span><span class="sxs-lookup"><span data-stu-id="ff498-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="ff498-118">Ale když proměnná je inicializována pomocí anonymního typu je třeba deklarovat jako proměnnou `var` Pokud potřebujete přístup k vlastnostem objektu později.</span><span class="sxs-lookup"><span data-stu-id="ff498-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="ff498-119">Toto je běžný scénář v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="ff498-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="ff498-120">Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="ff498-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="ff498-121">Z hlediska zdrojového kódu anonymního typu nemá žádný název.</span><span class="sxs-lookup"><span data-stu-id="ff498-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="ff498-122">Proto pokud proměnné dotazu byl inicializován s `var`, je jediný způsob, jak přistupovat k vlastnosti ve vrácené posloupnosti objekty používat `var` jako typ proměnné iterace ve `foreach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="ff498-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="ff498-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ff498-123">Remarks</span></span>  
 <span data-ttu-id="ff498-124">Implicitně typované proměnné deklaracích platí následující omezení:</span><span class="sxs-lookup"><span data-stu-id="ff498-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="ff498-125">`var` jde použít jenom při místní proměnné je deklarovat a inicializovat ve stejném příkazu; proměnnou nejde inicializovat na null nebo na skupinu metod nebo anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="ff498-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="ff498-126">`var` nelze použít na pole v oboru třídy.</span><span class="sxs-lookup"><span data-stu-id="ff498-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="ff498-127">Proměnné deklarované s použitím `var` nelze použít ve výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="ff498-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="ff498-128">Jinými slovy, tento výraz je právní`: int i = (i = 20);` , ale tento výraz způsobí chybu kompilace: `var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="ff498-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="ff498-129">Více implicitně typované proměnné nelze inicializovat ve stejném příkazu.</span><span class="sxs-lookup"><span data-stu-id="ff498-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="ff498-130">Pokud typ s názvem `var` je v oboru, pak bude `var` – klíčové slovo se přeloží název tohoto typu a se nezpracuje jako součást implicitně typované lokální proměnné deklarace.</span><span class="sxs-lookup"><span data-stu-id="ff498-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="ff498-131">Možná zjistíte, `var` může být také užitečný v případě výrazy dotazů, ve kterých je obtížné určit přesné konstruovaný typ proměnné dotazu.</span><span class="sxs-lookup"><span data-stu-id="ff498-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="ff498-132">Tato situace může nastat s seskupování a řazení operace.</span><span class="sxs-lookup"><span data-stu-id="ff498-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="ff498-133">`var` – Klíčové slovo může být také užitečné, když konkrétní typ proměnné je únavné pro psaní na klávesnici, nebo je zřejmé nebo nepřidá do čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="ff498-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="ff498-134">Jedním z příkladů kde `var` je užitečné v tomto způsob je pomocí vnořených obecných typech, jako jsou ty používané s operacemi skupiny.</span><span class="sxs-lookup"><span data-stu-id="ff498-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="ff498-135">V následující dotaz, je typ proměnné dotazu `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="ff498-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="ff498-136">Za předpokladu, můžete vy a ostatní, kteří musí udržovat váš kód pochopit, neexistuje žádný problém s použitím implicitního zápisu pro usnadnění práce a zkrácení.</span><span class="sxs-lookup"><span data-stu-id="ff498-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="ff498-137">Nicméně použití `var` mohou mít alespoň potenciálně ztížit váš kód pochopit pro jiné vývojáře.</span><span class="sxs-lookup"><span data-stu-id="ff498-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="ff498-138">Z tohoto důvodu dokumentace jazyka C# obecně používá `var` pouze pokud je povinný.</span><span class="sxs-lookup"><span data-stu-id="ff498-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff498-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="ff498-139">See Also</span></span>

- [<span data-ttu-id="ff498-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ff498-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ff498-141">Implicitně typovaná pole</span><span class="sxs-lookup"><span data-stu-id="ff498-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
- [<span data-ttu-id="ff498-142">Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="ff498-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
- [<span data-ttu-id="ff498-143">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="ff498-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
- [<span data-ttu-id="ff498-144">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="ff498-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
- [<span data-ttu-id="ff498-145">var</span><span class="sxs-lookup"><span data-stu-id="ff498-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
- [<span data-ttu-id="ff498-146">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="ff498-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="ff498-147">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="ff498-147">LINQ (Language-Integrated Query)</span></span>](../../../csharp/linq/index.md)  
- [<span data-ttu-id="ff498-148">for</span><span class="sxs-lookup"><span data-stu-id="ff498-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
- [<span data-ttu-id="ff498-149">foreach, in</span><span class="sxs-lookup"><span data-stu-id="ff498-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
- [<span data-ttu-id="ff498-150">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="ff498-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
