---
title: Yield – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 57b36bb32e1a575a645f7a15045bf0898dd10dfd
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582219"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="96a02-102">Yield – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96a02-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="96a02-103">Odešle další prvek kolekce do příkazu `For Each...Next`.</span><span class="sxs-lookup"><span data-stu-id="96a02-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96a02-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96a02-104">Syntax</span></span>  
  
```vb  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="96a02-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="96a02-105">Parameters</span></span>  
  
|<span data-ttu-id="96a02-106">Termín</span><span class="sxs-lookup"><span data-stu-id="96a02-106">Term</span></span>|<span data-ttu-id="96a02-107">Definice</span><span class="sxs-lookup"><span data-stu-id="96a02-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="96a02-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="96a02-108">Required.</span></span> <span data-ttu-id="96a02-109">Výraz, který je implicitně převoditelné na typ funkce iterátoru nebo přistupující objekt `Get`, který obsahuje příkaz `Yield`.</span><span class="sxs-lookup"><span data-stu-id="96a02-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96a02-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96a02-110">Remarks</span></span>  
 <span data-ttu-id="96a02-111">Příkaz `Yield` vrací jeden prvek kolekce v čase.</span><span class="sxs-lookup"><span data-stu-id="96a02-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="96a02-112">Příkaz `Yield` je součástí funkce iterátoru nebo přístupového objektu `Get`, který provádí vlastní iterace v kolekci.</span><span class="sxs-lookup"><span data-stu-id="96a02-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="96a02-113">Využijete funkci iterátoru [pro každý z nich... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md) nebo dotaz LINQ.</span><span class="sxs-lookup"><span data-stu-id="96a02-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="96a02-114">Každá iterace `For Each` smyčky volá funkci iterátoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="96a02-115">Když se ve funkci iterátoru dosáhne `Yield` příkazu, vrátí se `expression` a aktuální umístění v kódu se zachová.</span><span class="sxs-lookup"><span data-stu-id="96a02-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="96a02-116">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="96a02-117">Implicitní převod musí existovat v typu `expression` v příkazu `Yield` na návratový typ iterátoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="96a02-118">Chcete-li ukončit iteraci, můžete použít příkaz `Exit Function` nebo `Return`.</span><span class="sxs-lookup"><span data-stu-id="96a02-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="96a02-119">"Yield" není rezervované slovo a má zvláštní význam pouze v případě, že je použit ve funkci `Iterator` nebo přístupovém objektu `Get`.</span><span class="sxs-lookup"><span data-stu-id="96a02-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="96a02-120">Další informace o funkcích iterátoru a přístupových objektů `Get` najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="96a02-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="96a02-121">Funkce iterátoru a přistupující objekty get</span><span class="sxs-lookup"><span data-stu-id="96a02-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="96a02-122">Deklarace funkce iterátoru nebo přístupového objektu `Get` musí splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="96a02-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="96a02-123">Musí obsahovat modifikátor [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md) .</span><span class="sxs-lookup"><span data-stu-id="96a02-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="96a02-124">Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="96a02-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="96a02-125">Nemůže mít žádné parametry `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="96a02-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="96a02-126">Funkce iterátoru nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="96a02-127">Funkce iterátoru může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="96a02-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="96a02-128">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="96a02-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="96a02-129">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="96a02-129">Exception Handling</span></span>  
 <span data-ttu-id="96a02-130">Příkaz `Yield` může být uvnitř bloku `Try` [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="96a02-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="96a02-131">Blok `Try`, který má příkaz `Yield`, může mít `Catch` bloky a může mít `Finally` blok.</span><span class="sxs-lookup"><span data-stu-id="96a02-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="96a02-132">Příkaz `Yield` nemůže být uvnitř bloku `Catch` nebo bloku `Finally`.</span><span class="sxs-lookup"><span data-stu-id="96a02-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="96a02-133">Pokud `For Each` tělo (mimo funkci iterátoru) vyvolá výjimku, není proveden blok `Catch` ve funkci iterátoru, ale je spuštěn blok `Finally` ve funkci iterátoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="96a02-134">@No__t_0 blok uvnitř funkce iterátoru zachytává pouze výjimky, ke kterým dojde uvnitř funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="96a02-135">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="96a02-135">Technical Implementation</span></span>  
 <span data-ttu-id="96a02-136">Následující kód vrátí `IEnumerable (Of String)` z funkce iterátoru a poté provede iteraci prvky `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="96a02-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="96a02-137">Volání `MyIteratorFunction` nespustí tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="96a02-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="96a02-138">Místo toho volání vrátí `IEnumerable(Of String)` do proměnné `elements`.</span><span class="sxs-lookup"><span data-stu-id="96a02-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="96a02-139">V iteraci `For Each` smyčky je <xref:System.Collections.IEnumerator.MoveNext%2A> metoda volána pro `elements`.</span><span class="sxs-lookup"><span data-stu-id="96a02-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="96a02-140">Toto volání provede text `MyIteratorFunction` až do chvíle, kdy se dosáhne dalšího příkazu `Yield`.</span><span class="sxs-lookup"><span data-stu-id="96a02-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="96a02-141">Příkaz `Yield` vrací výraz, který určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také vlastnost <xref:System.Collections.Generic.IEnumerator%601.Current%2A> prvků, což je `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="96a02-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="96a02-142">Při každé následující iteraci `For Each` smyčky pokračuje v provádění tohoto textu iterátoru, kde se nachází, a znovu se zastaví, až dosáhne příkazu `Yield`.</span><span class="sxs-lookup"><span data-stu-id="96a02-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="96a02-143">@No__t_0 cyklus dokončí, když je dosaženo konce funkce iterátoru nebo příkazu `Return` nebo `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="96a02-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96a02-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="96a02-144">Example</span></span>  
 <span data-ttu-id="96a02-145">Následující příklad obsahuje příkaz `Yield`, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka</span><span class="sxs-lookup"><span data-stu-id="96a02-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="96a02-146">Každá iterace [pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) text příkazu v `Main` vytvoří volání funkce `Power` iterátoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="96a02-147">Každé volání funkce iterátoru pokračuje na další provedení příkazu `Yield`, ke kterému dojde během další iterace `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="96a02-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="96a02-148">Návratový typ metody iterátoru je <xref:System.Collections.Generic.IEnumerable%601>, typ rozhraní iterátoru.</span><span class="sxs-lookup"><span data-stu-id="96a02-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="96a02-149">Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.</span><span class="sxs-lookup"><span data-stu-id="96a02-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="96a02-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="96a02-150">Example</span></span>  
 <span data-ttu-id="96a02-151">Následující příklad ukazuje přistupující objekt `Get`, který je iterátorem.</span><span class="sxs-lookup"><span data-stu-id="96a02-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="96a02-152">Deklarace vlastnosti obsahuje modifikátor `Iterator`.</span><span class="sxs-lookup"><span data-stu-id="96a02-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="96a02-153">Další příklady naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="96a02-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96a02-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96a02-154">See also</span></span>

- [<span data-ttu-id="96a02-155">Příkazy</span><span class="sxs-lookup"><span data-stu-id="96a02-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
