---
title: YIELD – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: 7b718417fc421b9024e023964c4f29478b52c4ca
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239274"
---
# <a name="yield-c-reference"></a><span data-ttu-id="13e95-102">yield (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="13e95-102">yield (C# Reference)</span></span>
<span data-ttu-id="13e95-103">Při použití `yield` [kontextové klíčové slovo](../../../csharp/language-reference/keywords/index.md#contextual-keywords) v příkazu, dáváte tak najevo, metoda, operátor nebo `get` přístupový objekt, ve kterém se zobrazí, je iterátor.</span><span class="sxs-lookup"><span data-stu-id="13e95-103">When you use the `yield` [contextual keyword](../../../csharp/language-reference/keywords/index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="13e95-104">Pomocí `yield` k definování iterátor už není nutné explicitní extra třídy (třídy, která definuje stav výčtu, viz <xref:System.Collections.Generic.IEnumerator%601> příklad) při implementaci <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> vzor pro vlastní shromažďování Zadejte.</span><span class="sxs-lookup"><span data-stu-id="13e95-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>  
  
 <span data-ttu-id="13e95-105">Následující příklad ukazuje dvě formy `yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13e95-105">The following example shows the two forms of the `yield` statement.</span></span>  
  
```csharp  
yield return <expression>;  
yield break;  
```  
  
## <a name="remarks"></a><span data-ttu-id="13e95-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13e95-106">Remarks</span></span>  
 <span data-ttu-id="13e95-107">Můžete použít `yield return` příkaz vrátit vždy jeden prvek v čase.</span><span class="sxs-lookup"><span data-stu-id="13e95-107">You use a `yield return` statement to return each element one at a time.</span></span>  
  
 <span data-ttu-id="13e95-108">Metodu iterátoru spotřebujete pomocí [foreach](../../../csharp/language-reference/keywords/foreach-in.md) příkaz nebo dotaz LINQ.</span><span class="sxs-lookup"><span data-stu-id="13e95-108">You consume an iterator method by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="13e95-109">Každá iterace `foreach` smyčky zavolá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="13e95-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="13e95-110">Když `yield return` je v metodě iterátoru dosažen příkaz `expression` dochází, a je zachováno aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="13e95-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="13e95-111">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="13e95-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="13e95-112">Můžete použít `yield break` příkaz do konce iterace.</span><span class="sxs-lookup"><span data-stu-id="13e95-112">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="13e95-113">Další informace o iterátorech naleznete v tématu [iterátory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="13e95-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>  
  
## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="13e95-114">Iterátory a přístupové objekty get</span><span class="sxs-lookup"><span data-stu-id="13e95-114">Iterator Methods and get Accessors</span></span>  
 <span data-ttu-id="13e95-115">Deklarace iterátoru musí splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="13e95-115">The declaration of an iterator must meet the following requirements:</span></span>  
  
-   <span data-ttu-id="13e95-116">Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="13e95-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
-   <span data-ttu-id="13e95-117">Deklarace nemůže mít žádnou [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) nebo [si](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry.</span><span class="sxs-lookup"><span data-stu-id="13e95-117">The declaration can't have any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md) [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters.</span></span>  
  
 <span data-ttu-id="13e95-118">`yield` Typ iterátoru, který vrací <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.IEnumerator> je `object`.</span><span class="sxs-lookup"><span data-stu-id="13e95-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="13e95-119">Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.Generic.IEnumerator%601>, musí existovat implicitní převod z typu výrazu v `yield return` příkazu parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="13e95-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>  
  
 <span data-ttu-id="13e95-120">Není možné zahrnout `yield return` nebo `yield break` příkaz v metodách, které mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="13e95-120">You can't include a `yield return` or `yield break` statement in methods that have the following characteristics:</span></span>  
  
-   <span data-ttu-id="13e95-121">Anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="13e95-121">Anonymous methods.</span></span> <span data-ttu-id="13e95-122">Další informace najdete v tématu [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="13e95-122">For more information, see [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
-   <span data-ttu-id="13e95-123">Metody, které obsahují nebezpečné bloky.</span><span class="sxs-lookup"><span data-stu-id="13e95-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="13e95-124">Další informace najdete v tématu [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="13e95-124">For more information, see [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
## <a name="exception-handling"></a><span data-ttu-id="13e95-125">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="13e95-125">Exception Handling</span></span>  
 <span data-ttu-id="13e95-126">A `yield return` příkaz nelze umístit do bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="13e95-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="13e95-127">A `yield return` příkaz lze umístit do bloku try příkazu try-finally.</span><span class="sxs-lookup"><span data-stu-id="13e95-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>  
  
 <span data-ttu-id="13e95-128">A `yield break` příkaz lze umístit do bloku try nebo catch bloku, ale ne bloku finally.</span><span class="sxs-lookup"><span data-stu-id="13e95-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>  
  
 <span data-ttu-id="13e95-129">Pokud `foreach` text (mimo metodu iterátoru) vyvolá výjimku, `finally` je proveden blok v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="13e95-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="13e95-130">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="13e95-130">Technical Implementation</span></span>  
 <span data-ttu-id="13e95-131">V následujícím kódu vrátí `IEnumerable<string>` z metody iterátoru a poté iteruje skrz příslušné prvky.</span><span class="sxs-lookup"><span data-stu-id="13e95-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>  
  
```csharp  
IEnumerable<string> elements = MyIteratorMethod();  
foreach (string element in elements)  
{  
   ...  
}  
```  
  
 <span data-ttu-id="13e95-132">Volání `MyIteratorMethod` neprovede tělo metody.</span><span class="sxs-lookup"><span data-stu-id="13e95-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="13e95-133">Místo toho volání vrátí `IEnumerable<string>` do `elements` proměnné.</span><span class="sxs-lookup"><span data-stu-id="13e95-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>  
  
 <span data-ttu-id="13e95-134">Při iteraci `foreach` smyčky, <xref:System.Collections.IEnumerator.MoveNext%2A> metoda je volána pro `elements`.</span><span class="sxs-lookup"><span data-stu-id="13e95-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="13e95-135">Toto volání provádí tělo `MyIteratorMethod` až do další `yield return` je dosažen příkaz.</span><span class="sxs-lookup"><span data-stu-id="13e95-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="13e95-136">Výraz vrácený příkazem `yield return` příkaz určuje nejen hodnotu `element` proměnné k využití v těle smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost `elements`, což je `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="13e95-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>  
  
 <span data-ttu-id="13e95-137">Na každé další iteraci `foreach` smyčky, tělo iterátoru pokračuje odkud zastaví se opět tehdy, když se dosáhne `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="13e95-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="13e95-138">`foreach` Smyčka dokončena, jakmile konce metody iterátoru nebo `yield break` je dosažen příkaz.</span><span class="sxs-lookup"><span data-stu-id="13e95-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13e95-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="13e95-139">Example</span></span>  
 <span data-ttu-id="13e95-140">Následující příklad obsahuje `yield return` , který se nachází uvnitř `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="13e95-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="13e95-141">Každá iterace `foreach` tělo s příkazy v `Main` metoda vytvoří volání `Power` funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="13e95-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="13e95-142">Každé volání funkce iterátoru pokračuje do dalšího provedení příkazu `yield return` prohlášení, které nastane při další iteraci `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="13e95-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>  
  
 <span data-ttu-id="13e95-143">Návratový typ metody iterátoru je <xref:System.Collections.IEnumerable>, což je typ rozhraní iterátoru.</span><span class="sxs-lookup"><span data-stu-id="13e95-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="13e95-144">Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.</span><span class="sxs-lookup"><span data-stu-id="13e95-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="13e95-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="13e95-145">Example</span></span>  
 <span data-ttu-id="13e95-146">Následující příklad ukazuje `get` přístupovou metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="13e95-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="13e95-147">V tomto příkladu každá `yield return` příkazu vrátí instanci třídy definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="13e95-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/yield_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="13e95-148">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13e95-148">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13e95-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="13e95-149">See Also</span></span>

- [<span data-ttu-id="13e95-150">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="13e95-150">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="13e95-151">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="13e95-151">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="13e95-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="13e95-152">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
- [<span data-ttu-id="13e95-153">Iterátory</span><span class="sxs-lookup"><span data-stu-id="13e95-153">Iterators</span></span>](../../iterators.md)
