---
title: "Yield – příkaz (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 99f5129d5cb43cddfb17731f337a72fae22d3626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="e8070-102">Yield – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8070-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="e8070-103">Na další prvek kolekce, která se odešle `For Each...Next` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e8070-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8070-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8070-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8070-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8070-105">Parameters</span></span>  
  
|<span data-ttu-id="e8070-106">Termín</span><span class="sxs-lookup"><span data-stu-id="e8070-106">Term</span></span>|<span data-ttu-id="e8070-107">Definice</span><span class="sxs-lookup"><span data-stu-id="e8070-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="e8070-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e8070-108">Required.</span></span> <span data-ttu-id="e8070-109">Výraz, který je implicitně převést na typ funkce iterator nebo `Get` přistupujícího objektu, který obsahuje `Yield` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e8070-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8070-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8070-110">Remarks</span></span>  
 <span data-ttu-id="e8070-111">`Yield` Příkaz vrací jeden element v kolekci najednou.</span><span class="sxs-lookup"><span data-stu-id="e8070-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="e8070-112">`Yield` Příkaz je součástí funkce iterator nebo `Get` přistupujícího objektu, který provádět vlastní iterací v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e8070-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="e8070-113">Využívat funkce iterator pomocí [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md) nebo dotaz LINQ.</span><span class="sxs-lookup"><span data-stu-id="e8070-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="e8070-114">Každé iteraci `For Each` smyčky volá funkci iterator.</span><span class="sxs-lookup"><span data-stu-id="e8070-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="e8070-115">Když `Yield` příkaz je dosaženo ve funkci iterator `expression` se vrátí, a se uchovávají aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="e8070-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="e8070-116">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="e8070-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="e8070-117">Musí existovat implicitní převod z typu `expression` v `Yield` příkaz, který má návratový typ iteraci.</span><span class="sxs-lookup"><span data-stu-id="e8070-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="e8070-118">Můžete použít `Exit Function` nebo `Return` příkaz k ukončení iterace.</span><span class="sxs-lookup"><span data-stu-id="e8070-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="e8070-119">"Výnos" není vyhrazené slovo a má zvláštní význam jenom v případě, že je používán `Iterator` funkce nebo `Get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="e8070-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="e8070-120">Další informace o funkcích iterator a `Get` přístupové objekty, najdete v části [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="e8070-120">For more information about iterator functions and `Get` accessors, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="e8070-121">Iterator funkce a Get přístupové objekty</span><span class="sxs-lookup"><span data-stu-id="e8070-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="e8070-122">Deklarace funkce iterator nebo `Get` přistupujícího objektu musí splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="e8070-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="e8070-123">Musí obsahovat [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e8070-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
-   <span data-ttu-id="e8070-124">Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="e8070-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="e8070-125">Nemůže mít žádné `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="e8070-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="e8070-126">Iterator funkce nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické destruktor.</span><span class="sxs-lookup"><span data-stu-id="e8070-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="e8070-127">Iterator funkce může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="e8070-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="e8070-128">Další informace najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="e8070-128">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="e8070-129">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="e8070-129">Exception Handling</span></span>  
 <span data-ttu-id="e8070-130">A `Yield` příkaz může být uvnitř `Try` blokovat z [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e8070-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="e8070-131">A `Try` blok, který má `Yield` příkaz může mít `Catch` blokuje a může mít `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="e8070-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="e8070-132">A `Yield` příkaz nemůže být uvnitř `Catch` bloku nebo `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="e8070-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="e8070-133">Pokud `For Each` textu (mimo funkci iterator) vyvolá výjimku, `Catch` bloku ve funkci iterator není proveden, ale `Finally` bloku ve funkci iterator se spustí.</span><span class="sxs-lookup"><span data-stu-id="e8070-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="e8070-134">A `Catch` bloku uvnitř funkce iterator zachytí pouze výjimky, které nastat uvnitř funkce iterator.</span><span class="sxs-lookup"><span data-stu-id="e8070-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="e8070-135">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="e8070-135">Technical Implementation</span></span>  
 <span data-ttu-id="e8070-136">Následující kód vrátí `IEnumerable (Of String)` z funkce iterator a pak iteruje v rámci prvků `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="e8070-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="e8070-137">Volání `MyIteratorFunction` neprovede tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="e8070-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="e8070-138">Místo toho se volání vrátí `IEnumerable(Of String)` do `elements` proměnné.</span><span class="sxs-lookup"><span data-stu-id="e8070-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="e8070-139">Na iterace `For Each` smyčky, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda je volána pro `elements`.</span><span class="sxs-lookup"><span data-stu-id="e8070-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="e8070-140">Toto volání provede text `MyIteratorFunction` až do dalšího `Yield` je dosaženo příkaz.</span><span class="sxs-lookup"><span data-stu-id="e8070-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="e8070-141">`Yield` Příkaz vrací výraz, který určuje, ne jenom hodnotu `element` proměnná pro spotřeba těla smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost elementů, která je `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="e8070-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="e8070-142">Při každém opakování následné `For Each` cykly, odkud pokračuje v provádění těla iterator bylo přerušeno, znovu zastavit při dosažení `Yield` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e8070-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="e8070-143">`For Each` Dokončení smyčky, kdy konec iterator funkce nebo `Return` nebo `Exit Function` je dosaženo příkaz.</span><span class="sxs-lookup"><span data-stu-id="e8070-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8070-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8070-144">Example</span></span>  
 <span data-ttu-id="e8070-145">V následujícím příkladu má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="e8070-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="e8070-146">Každé iteraci [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) těla příkazu v `Main` vytvoří volání `Power` iterator funkce.</span><span class="sxs-lookup"><span data-stu-id="e8070-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="e8070-147">Každé volání funkce iterator pokračuje dalším spuštění `Yield` příkaz, který spadá další iterace `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="e8070-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="e8070-148">Návratový typ metody iterator <xref:System.Collections.Generic.IEnumerable%601>, typu iterator rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e8070-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="e8070-149">Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.</span><span class="sxs-lookup"><span data-stu-id="e8070-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="e8070-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8070-150">Example</span></span>  
 <span data-ttu-id="e8070-151">Následující příklad ukazuje `Get` přistupujícího objektu, který je iterátor.</span><span class="sxs-lookup"><span data-stu-id="e8070-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="e8070-152">Obsahuje deklarace vlastnosti `Iterator` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="e8070-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/yield-statement_2.vb)]  
  
 <span data-ttu-id="e8070-153">Další příklady najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="e8070-153">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8070-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8070-154">See Also</span></span>  
 [<span data-ttu-id="e8070-155">Iterátory</span><span class="sxs-lookup"><span data-stu-id="e8070-155">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="e8070-156">Příkazy</span><span class="sxs-lookup"><span data-stu-id="e8070-156">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
