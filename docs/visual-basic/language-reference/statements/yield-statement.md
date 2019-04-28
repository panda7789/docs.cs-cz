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
ms.openlocfilehash: fea91731694f18625e43c5545b353851e72234a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698613"
---
# <a name="yield-statement-visual-basic"></a><span data-ttu-id="0a65f-102">Yield – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a65f-102">Yield Statement (Visual Basic)</span></span>
<span data-ttu-id="0a65f-103">Další prvek kolekce, která se odešle `For Each...Next` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0a65f-103">Sends the next element of a collection to a `For Each...Next` statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a65f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a65f-104">Syntax</span></span>  
  
```  
Yield expression  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a65f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a65f-105">Parameters</span></span>  
  
|<span data-ttu-id="0a65f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="0a65f-106">Term</span></span>|<span data-ttu-id="0a65f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="0a65f-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="0a65f-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0a65f-108">Required.</span></span> <span data-ttu-id="0a65f-109">Výraz, který je implicitně převést na typ funkce iterátoru nebo `Get` přístupový objekt, který obsahuje `Yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0a65f-109">An expression that is implicitly convertible to the type of the iterator function or `Get` accessor that contains the `Yield` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a65f-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a65f-110">Remarks</span></span>  
 <span data-ttu-id="0a65f-111">`Yield` Příkaz vrátí jeden element v kolekci najednou.</span><span class="sxs-lookup"><span data-stu-id="0a65f-111">The `Yield` statement returns one element of a collection at a time.</span></span> <span data-ttu-id="0a65f-112">`Yield` Příkazu je součástí funkce iterátoru nebo `Get` přístupový objekt, který provedení vlastní iterace nad kolekcí.</span><span class="sxs-lookup"><span data-stu-id="0a65f-112">The `Yield` statement is included in an iterator function or `Get` accessor, which perform custom iterations over a collection.</span></span>  
  
 <span data-ttu-id="0a65f-113">Funkce iterátoru spotřebujete pomocí [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md) nebo dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="0a65f-113">You consume an iterator function by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md) or a LINQ query.</span></span> <span data-ttu-id="0a65f-114">Každá iterace `For Each` smyčky volání funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-114">Each iteration of the `For Each` loop calls the iterator function.</span></span> <span data-ttu-id="0a65f-115">Když `Yield` je ve funkci iterátoru dosažen příkaz `expression` dochází, a je zachováno aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="0a65f-115">When a `Yield` statement is reached in the iterator function, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="0a65f-116">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-116">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="0a65f-117">Musí existovat implicitní převod z typu `expression` v `Yield` příkaz a návratový typ iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-117">An implicit conversion must exist from the type of `expression` in the `Yield` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="0a65f-118">Můžete použít `Exit Function` nebo `Return` příkaz do konce iterace.</span><span class="sxs-lookup"><span data-stu-id="0a65f-118">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="0a65f-119">"Yield" není vyhrazené slovo a má zvláštní význam pouze v případě, že se používá `Iterator` funkce nebo `Get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="0a65f-119">"Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="0a65f-120">Další informace o funkcích iterátoru a `Get` přístupové objekty, najdete v článku [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0a65f-120">For more information about iterator functions and `Get` accessors, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="iterator-functions-and-get-accessors"></a><span data-ttu-id="0a65f-121">Funkce iterátorů a přístupové objekty Get</span><span class="sxs-lookup"><span data-stu-id="0a65f-121">Iterator Functions and Get Accessors</span></span>  
 <span data-ttu-id="0a65f-122">Deklarace funkce iterátoru nebo `Get` přístupový objekt, musí splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="0a65f-122">The declaration of an iterator function or `Get` accessor must meet the following requirements:</span></span>  
  
- <span data-ttu-id="0a65f-123">Musí obsahovat [iterátoru](../../../visual-basic/language-reference/modifiers/iterator.md) modifikátor.</span><span class="sxs-lookup"><span data-stu-id="0a65f-123">It must include an [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md) modifier.</span></span>  
  
- <span data-ttu-id="0a65f-124">Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="0a65f-124">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
- <span data-ttu-id="0a65f-125">Nesmí obsahovat žádné `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="0a65f-125">It cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="0a65f-126">Funkce iterátoru nelze provést v událost, konstruktor instance, statického konstruktoru nebo destruktoru statické.</span><span class="sxs-lookup"><span data-stu-id="0a65f-126">An iterator function cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="0a65f-127">Funkce iterátoru, může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="0a65f-127">An iterator function can be an anonymous function.</span></span> <span data-ttu-id="0a65f-128">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0a65f-128">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="0a65f-129">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="0a65f-129">Exception Handling</span></span>  
 <span data-ttu-id="0a65f-130">A `Yield` příkaz může být v rámci `Try` bloku [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0a65f-130">A `Yield` statement can be inside a `Try` block of a [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="0a65f-131">A `Try` blok, který má `Yield` může mít příkaz `Catch` a ostatní porty blokuje může mít `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="0a65f-131">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>  
  
 <span data-ttu-id="0a65f-132">A `Yield` příkaz nejde provést uvnitř `Catch` bloku nebo `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="0a65f-132">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>  
  
 <span data-ttu-id="0a65f-133">Pokud `For Each` text (mimo funkce iterátoru) vyvolá výjimku, `Catch` bloku funkce iterátoru není spuštěn, ale `Finally` je proveden blok v funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-133">If the `For Each` body (outside of the iterator function) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="0a65f-134">A `Catch` bloku funkce iterátoru zachytává pouze výjimky, ke kterým dochází uvnitř funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-134">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="0a65f-135">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="0a65f-135">Technical Implementation</span></span>  
 <span data-ttu-id="0a65f-136">V následujícím kódu vrátí `IEnumerable (Of String)` z funkce iterátoru a poté iteruje skrz prvky `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="0a65f-136">The following code returns an `IEnumerable (Of String)` from an iterator function and then iterates through the elements of the `IEnumerable (Of String)`.</span></span>  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 <span data-ttu-id="0a65f-137">Volání `MyIteratorFunction` neprovede tělo funkce.</span><span class="sxs-lookup"><span data-stu-id="0a65f-137">The call to `MyIteratorFunction` doesn't execute the body of the function.</span></span> <span data-ttu-id="0a65f-138">Místo toho volání vrátí `IEnumerable(Of String)` do `elements` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0a65f-138">Instead the call returns an `IEnumerable(Of String)` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="0a65f-139">Při iteraci `For Each` smyčky, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda je volána pro `elements`.</span><span class="sxs-lookup"><span data-stu-id="0a65f-139">On an iteration of the `For Each` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="0a65f-140">Toto volání provádí tělo `MyIteratorFunction` až do další `Yield` je dosažen příkaz.</span><span class="sxs-lookup"><span data-stu-id="0a65f-140">This call executes the body of `MyIteratorFunction` until the next `Yield` statement is reached.</span></span> <span data-ttu-id="0a65f-141">`Yield` Příkaz vrátí výraz, který určuje nejen hodnotu `element` proměnné k využití v těle smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnosti prvků, který je `IEnumerable (Of String)`.</span><span class="sxs-lookup"><span data-stu-id="0a65f-141">The `Yield` statement returns an expression that determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of elements, which is an `IEnumerable (Of String)`.</span></span>  
  
 <span data-ttu-id="0a65f-142">Na každé další iteraci `For Each` smyčky, tělo iterátoru pokračuje odkud zastaví se opět tehdy, když se dosáhne `Yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0a65f-142">On each subsequent iteration of the `For Each` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="0a65f-143">`For Each` Smyčky je dokončen, když na konec funkce iterátoru nebo `Return` nebo `Exit Function` je dosažen příkaz.</span><span class="sxs-lookup"><span data-stu-id="0a65f-143">The `For Each` loop completes when the end of the iterator function or a `Return` or `Exit Function` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a65f-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a65f-144">Example</span></span>  
 <span data-ttu-id="0a65f-145">Následující příklad obsahuje `Yield` , který se nachází uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="0a65f-145">The following example has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="0a65f-146">Každá iterace [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) tělo s příkazy v `Main` vytváří volání `Power` funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-146">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="0a65f-147">Každé volání funkce iterátoru pokračuje do dalšího provedení příkazu `Yield` prohlášení, které nastane při další iteraci `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="0a65f-147">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 <span data-ttu-id="0a65f-148">Návratový typ metody iterátoru je <xref:System.Collections.Generic.IEnumerable%601>, typ rozhraní iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-148">The return type of the iterator method is <xref:System.Collections.Generic.IEnumerable%601>, an iterator interface type.</span></span> <span data-ttu-id="0a65f-149">Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.</span><span class="sxs-lookup"><span data-stu-id="0a65f-149">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="0a65f-150">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a65f-150">Example</span></span>  
 <span data-ttu-id="0a65f-151">Následující příklad ukazuje `Get` přístupovou metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="0a65f-151">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="0a65f-152">Deklarace vlastnosti zahrnuje `Iterator` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="0a65f-152">The property declaration includes an `Iterator` modifier.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="0a65f-153">Další příklady najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="0a65f-153">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a65f-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a65f-154">See also</span></span>

- [<span data-ttu-id="0a65f-155">Příkazy</span><span class="sxs-lookup"><span data-stu-id="0a65f-155">Statements</span></span>](../../../visual-basic/language-reference/statements/index.md)
