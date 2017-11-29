---
title: "Implicitně typované lokální proměnné (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26a4460acf70ff3748f12d74442f0ca568a587b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a><span data-ttu-id="1ba0b-102">Implicitně typované lokální proměnné (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1ba0b-102">Implicitly Typed Local Variables (C# Programming Guide)</span></span>
<span data-ttu-id="1ba0b-103">Lokální proměnné lze deklarovat bez nutnosti poskytnutí explicitního typu.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-103">Local variables can be declared without giving an explicit type.</span></span> <span data-ttu-id="1ba0b-104">`var` – Klíčové slovo instruuje kompilátor, aby odvození typu proměnné z výrazu na pravé straně příkazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-104">The `var` keyword instructs the compiler to infer the type of the variable from the expression on the right side of the initialization statement.</span></span> <span data-ttu-id="1ba0b-105">Odvozené typ může být předdefinovaný typ, anonymní typ, uživatelem definovaný typ nebo typem definovaným v knihovně tříd rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-105">The inferred type may be a built-in type, an anonymous type, a user-defined type, or a type defined in the .NET Framework class library.</span></span> <span data-ttu-id="1ba0b-106">Další informace o tom, jak inicializovat pole s `var`, najdete v části [implicitně typované pole](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="1ba0b-106">For more information about how to initialize arrays with `var`, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
 <span data-ttu-id="1ba0b-107">Následující příklady ukazují různé způsoby, ve kterých mohou být místní proměnné deklarovány s `var`:</span><span class="sxs-lookup"><span data-stu-id="1ba0b-107">The following examples show various ways in which local variables can be declared with `var`:</span></span>  
  
 [!code-csharp[csProgGuideLINQ#43](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_1.cs)]  
  
 <span data-ttu-id="1ba0b-108">Je důležité pochopit, že `var` – klíčové slovo neznamená "variantou" a neindikuje volně je proměnná typu nebo pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-108">It is important to understand that the `var` keyword does not mean "variant" and does not indicate that the variable is loosely typed, or late-bound.</span></span> <span data-ttu-id="1ba0b-109">Právě znamená, že kompilátor určí a přiřadí nejvhodnější typ.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-109">It just means that the compiler determines and assigns the most appropriate type.</span></span>  
  
 <span data-ttu-id="1ba0b-110">`var` – Klíčové slovo je možné použít následující kontexty:</span><span class="sxs-lookup"><span data-stu-id="1ba0b-110">The `var` keyword may be used in the following contexts:</span></span>  
  
-   <span data-ttu-id="1ba0b-111">Na lokální proměnné (proměnných deklarovaných v oboru metoda) jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-111">On local variables (variables declared at method scope) as shown in the previous example.</span></span>  
  
-   <span data-ttu-id="1ba0b-112">V [pro](../../../csharp/language-reference/keywords/for.md) příkaz inicializace.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-112">In a [for](../../../csharp/language-reference/keywords/for.md) initialization statement.</span></span>  
  
    ```  
    for(var x = 1; x < 10; x++)  
    ```  
  
-   <span data-ttu-id="1ba0b-113">V [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz inicializace.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-113">In a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) initialization statement.</span></span>  
  
    ```  
    foreach(var item in list){...}  
    ```  
  
-   <span data-ttu-id="1ba0b-114">V [pomocí](../../../csharp/language-reference/keywords/using-statement.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-114">In a [using](../../../csharp/language-reference/keywords/using-statement.md) statement.</span></span>  
  
    ```  
    using (var file = new StreamReader("C:\\myfile.txt")) {...}  
    ```  
  
 <span data-ttu-id="1ba0b-115">Další informace najdete v tématu [postupy: použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span><span class="sxs-lookup"><span data-stu-id="1ba0b-115">For more information, see [How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).</span></span>  
  
## <a name="var-and-anonymous-types"></a><span data-ttu-id="1ba0b-116">var a anonymní typy</span><span class="sxs-lookup"><span data-stu-id="1ba0b-116">var and Anonymous Types</span></span>  
 <span data-ttu-id="1ba0b-117">V mnoha případech použití `var` je volitelný a je právě syntaktické pohodlí.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-117">In many cases the use of `var` is optional and is just a syntactic convenience.</span></span> <span data-ttu-id="1ba0b-118">Ale pokud proměnnou je inicializována s anonymní typ musíte deklarovat proměnnou jako `var` Pokud budete potřebovat pro přístup k vlastnosti objektu později.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-118">However, when a variable is initialized with an anonymous type you must declare the variable as `var` if you need to access the properties of the object at a later point.</span></span> <span data-ttu-id="1ba0b-119">Toto je běžný scénář v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu výrazy.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-119">This is a common scenario in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="1ba0b-120">Další informace najdete v tématu [anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="1ba0b-120">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 <span data-ttu-id="1ba0b-121">Z hlediska zdrojového kódu anonymní typ nemá název.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-121">From the perspective of your source code, an anonymous type has no name.</span></span> <span data-ttu-id="1ba0b-122">Proto pokud proměnnou dotazu byl inicializován s `var`, pak jedině pro přístup k vlastnostem v pořadí vrácených objektů, které se má používat `var` jako typ proměnné iterace ve `foreach` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-122">Therefore, if a query variable has been initialized with `var`, then the only way to access the properties in the returned sequence of objects is to use `var` as the type of the iteration variable in the `foreach` statement.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#44](../../../csharp/programming-guide/arrays/codesnippet/CSharp/implicitly-typed-local-variables_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="1ba0b-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ba0b-123">Remarks</span></span>  
 <span data-ttu-id="1ba0b-124">Implicitně typované deklarace proměnných, které se vztahují následující omezení:</span><span class="sxs-lookup"><span data-stu-id="1ba0b-124">The following restrictions apply to implicitly-typed variable declarations:</span></span>  
  
-   <span data-ttu-id="1ba0b-125">`var`lze použít pouze při místní proměnné je deklarovaná a inicializovat v jednom příkazu; proměnnou nelze inicializovat na hodnotu null nebo ke skupině metoda nebo anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-125">`var` can only be used when a local variable is declared and initialized in the same statement; the variable cannot be initialized to null, or to a method group or an anonymous function.</span></span>  
  
-   <span data-ttu-id="1ba0b-126">`var`nelze použít na pole v rozsahu třídy.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-126">`var` cannot be used on fields at class scope.</span></span>  
  
-   <span data-ttu-id="1ba0b-127">Proměnných deklarovaných pomocí `var` nelze použít ve výrazu inicializace.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-127">Variables declared by using `var` cannot be used in the initialization expression.</span></span> <span data-ttu-id="1ba0b-128">Jinými slovy, je tento výraz právní`: int i = (i = 20);` , ale tento výraz způsobí chybu kompilace:`var i = (i = 20);`</span><span class="sxs-lookup"><span data-stu-id="1ba0b-128">In other words, this expression is legal`: int i = (i = 20);` but this expression produces a compile-time error: `var i = (i = 20);`</span></span>  
  
-   <span data-ttu-id="1ba0b-129">Více implicitně typované proměnné nelze inicializovat v jednom příkazu.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-129">Multiple implicitly-typed variables cannot be initialized in the same statement.</span></span>  
  
-   <span data-ttu-id="1ba0b-130">Pokud název typu `var` nachází v oboru, pak se `var` – klíčové slovo bude odkazující na název tohoto typu a nebude považován za součást implicitně typovaná deklarace místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-130">If a type named `var` is in scope, then the `var` keyword will resolve to that type name and will not be treated as part of an implicitly typed local variable declaration.</span></span>  
  
 <span data-ttu-id="1ba0b-131">Můžete zjistit, že `var` může být také užitečná pro výrazy dotazů, ve kterých je obtížné určit přesnou vytvořený typ proměnné v dotazu.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-131">You may find that `var` can also be useful with query expressions in which the exact constructed type of the query variable is difficult to determine.</span></span> <span data-ttu-id="1ba0b-132">Tato situace může nastat s seskupování a řazení operace.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-132">This can occur with grouping and ordering operations.</span></span>  
  
 <span data-ttu-id="1ba0b-133">`var` – Klíčové slovo může také být užitečné při specifický typ proměnné je zdlouhavé na typ na klávesnici, nebo je zřejmé nebo nepřidá do čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-133">The `var` keyword can also be useful when the specific type of the variable is tedious to type on the keyboard, or is obvious, or does not add to the readability of the code.</span></span> <span data-ttu-id="1ba0b-134">Jedním z příkladů kde `var` je užitečné v tomto způsobem je s vnořené obecné typy, jako jsou ty používané s operacemi skupiny.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-134">One example where `var` is helpful in this manner is with nested generic types such as those used with group operations.</span></span> <span data-ttu-id="1ba0b-135">V následující dotaz, je typ proměnné dotazu `IEnumerable<IGrouping<string, Student>>`.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-135">In the following query, the type of the query variable is `IEnumerable<IGrouping<string, Student>>`.</span></span> <span data-ttu-id="1ba0b-136">Tak dlouho, dokud uživatelů musí zachovat kódu lepší vysvětlení, neexistuje žádný problém s použitím implicitního zadáním kvůli pohodlí a jako stručný výtah.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-136">As long as you and others who must maintain your code understand this, there is no problem with using implicit typing for convenience and brevity.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicitly-typed-local-variables_3.cs)]  
  
 <span data-ttu-id="1ba0b-137">Ale použití `var` mít minimálně potenciální, aby byl váš kód více těžko srozumitelné pro ostatní vývojáři.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-137">However, the use of `var` does have at least the potential to make your code more difficult to understand for other developers.</span></span> <span data-ttu-id="1ba0b-138">Z tohoto důvodu dokumentace jazyka C# obecně používá `var` pouze pokud je požadovaná.</span><span class="sxs-lookup"><span data-stu-id="1ba0b-138">For that reason, the C# documentation generally uses `var` only when it is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ba0b-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ba0b-139">See Also</span></span>  
 [<span data-ttu-id="1ba0b-140">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1ba0b-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1ba0b-141">Implicitně Typovaná pole</span><span class="sxs-lookup"><span data-stu-id="1ba0b-141">Implicitly Typed Arrays</span></span>](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)  
 [<span data-ttu-id="1ba0b-142">Postupy: použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="1ba0b-142">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)  
 [<span data-ttu-id="1ba0b-143">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="1ba0b-143">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)  
 [<span data-ttu-id="1ba0b-144">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="1ba0b-144">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)  
 [<span data-ttu-id="1ba0b-145">var</span><span class="sxs-lookup"><span data-stu-id="1ba0b-145">var</span></span>](../../../csharp/language-reference/keywords/var.md)  
 [<span data-ttu-id="1ba0b-146">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="1ba0b-146">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="1ba0b-147">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="1ba0b-147">LINQ (Language-Integrated Query)</span></span>](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [<span data-ttu-id="1ba0b-148">pro</span><span class="sxs-lookup"><span data-stu-id="1ba0b-148">for</span></span>](../../../csharp/language-reference/keywords/for.md)  
 [<span data-ttu-id="1ba0b-149">foreach v</span><span class="sxs-lookup"><span data-stu-id="1ba0b-149">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="1ba0b-150">Using – příkaz</span><span class="sxs-lookup"><span data-stu-id="1ba0b-150">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)
