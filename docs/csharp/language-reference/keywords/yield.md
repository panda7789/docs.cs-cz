---
title: výnos kontextové klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712777"
---
# <a name="yield-c-reference"></a><span data-ttu-id="14c27-102">yield (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="14c27-102">yield (C# Reference)</span></span>

<span data-ttu-id="14c27-103">Při použití `yield` [kontextové klíčové slovo](index.md#contextual-keywords) v příkazu, označíte, že metoda, operátor nebo `get` přistupující objekt, ve kterém se zobrazí, je iterátor.</span><span class="sxs-lookup"><span data-stu-id="14c27-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="14c27-104">Použití `yield` k definování iterátoru odebere potřebu explicitní extra třídy (třída, která obsahuje <xref:System.Collections.Generic.IEnumerator%601> stav pro výčt, <xref:System.Collections.IEnumerable> viz <xref:System.Collections.IEnumerator> příklad) při implementaci a vzor pro vlastní typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="14c27-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="14c27-105">Následující příklad ukazuje dvě formy `yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="14c27-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="14c27-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14c27-106">Remarks</span></span>

<span data-ttu-id="14c27-107">Příkaz se `yield return` používá k vrácení každého prvku po jednom.</span><span class="sxs-lookup"><span data-stu-id="14c27-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="14c27-108">Sekvence vrácená z metody iterátoru může být spotřebována pomocí příkazu [foreach](foreach-in.md) nebo dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="14c27-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="14c27-109">Každá iterace `foreach` smyčky volá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="14c27-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="14c27-110">Když `yield return` je dosaženo příkazu v metodě `expression` iterátoru, je vrácena a aktuální umístění v kódu je zachována.</span><span class="sxs-lookup"><span data-stu-id="14c27-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="14c27-111">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="14c27-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="14c27-112">K ukončení `yield break` iterace můžete použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="14c27-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="14c27-113">Další informace o iterátorech naleznete v [tématu Iterators](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="14c27-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="14c27-114">Metody Iterator a získat přístupové metody</span><span class="sxs-lookup"><span data-stu-id="14c27-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="14c27-115">Deklarace iterátoru musí splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="14c27-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="14c27-116">Návratový typ <xref:System.Collections.IEnumerable>musí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerator>být <xref:System.Collections.Generic.IEnumerator%601>, , , nebo .</span><span class="sxs-lookup"><span data-stu-id="14c27-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="14c27-117">Deklarace nemůže mít žádné [parametry v](in-parameter-modifier.md) [ref](ref.md) nebo [out.](out-parameter-modifier.md)</span><span class="sxs-lookup"><span data-stu-id="14c27-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="14c27-118">Typ `yield` iterátoru, který <xref:System.Collections.IEnumerable> vrátí <xref:System.Collections.IEnumerator> `object`nebo je .</span><span class="sxs-lookup"><span data-stu-id="14c27-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="14c27-119">Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.Generic.IEnumerator%601>nebo , musí být implicitní převod z `yield return` typu výrazu v příkazu na parametr obecného typu .</span><span class="sxs-lookup"><span data-stu-id="14c27-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="14c27-120">Nemůžete zahrnout `yield return` nebo `yield break` prohlášení v:</span><span class="sxs-lookup"><span data-stu-id="14c27-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="14c27-121">[Lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) a [anonymní metody](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="14c27-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="14c27-122">Metody, které obsahují nebezpečné bloky.</span><span class="sxs-lookup"><span data-stu-id="14c27-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="14c27-123">Další informace naleznete v tématu [nebezpečné](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="14c27-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="14c27-124">Zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="14c27-124">Exception handling</span></span>

<span data-ttu-id="14c27-125">Příkaz `yield return` nemůže být umístěn v bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="14c27-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="14c27-126">Příkaz `yield return` může být umístěn v bloku try příkazu try-finally.</span><span class="sxs-lookup"><span data-stu-id="14c27-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="14c27-127">Příkaz `yield break` může být umístěn v bloku try nebo catch bloku, ale ne nakonec bloku.</span><span class="sxs-lookup"><span data-stu-id="14c27-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="14c27-128">Pokud `foreach` tělo (mimo metodu iterátoru) vyvolá výjimku, `finally` je proveden blok v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="14c27-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="14c27-129">Technická realizace</span><span class="sxs-lookup"><span data-stu-id="14c27-129">Technical implementation</span></span>

<span data-ttu-id="14c27-130">Následující kód vrátí `IEnumerable<string>` metodu iterátoru a potom iteruje prostřednictvím jejích prvků.</span><span class="sxs-lookup"><span data-stu-id="14c27-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="14c27-131">Volání `MyIteratorMethod` neprovede tělo metody.</span><span class="sxs-lookup"><span data-stu-id="14c27-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="14c27-132">Místo toho volání `IEnumerable<string>` vrátí `elements` do proměnné.</span><span class="sxs-lookup"><span data-stu-id="14c27-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="14c27-133">V iteraci `foreach` smyčky <xref:System.Collections.IEnumerator.MoveNext%2A> je metoda `elements`volána .</span><span class="sxs-lookup"><span data-stu-id="14c27-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="14c27-134">Toto volání provede `MyIteratorMethod` tělo, `yield return` dokud není dosaženo dalšího příkazu.</span><span class="sxs-lookup"><span data-stu-id="14c27-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="14c27-135">Výraz vrácený `yield return` příkazem určuje nejen hodnotu `element` proměnné pro spotřebu podle těla <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `elements`smyčky, ale `IEnumerable<string>`také vlastnost , která je .</span><span class="sxs-lookup"><span data-stu-id="14c27-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="14c27-136">Na každé další `foreach` iteraci smyčky provádění těla iterátoru pokračuje od místa, kde `yield return` přestal, opět zastavení, když dosáhne příkazu.</span><span class="sxs-lookup"><span data-stu-id="14c27-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="14c27-137">Smyčka `foreach` je dokončena po dosažení konce metody iterátoru nebo příkazu. `yield break`</span><span class="sxs-lookup"><span data-stu-id="14c27-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="14c27-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="14c27-138">Example</span></span>

<span data-ttu-id="14c27-139">Následující příklad má `yield return` příkaz, který `for` je uvnitř smyčky.</span><span class="sxs-lookup"><span data-stu-id="14c27-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="14c27-140">Každá iterace těla příkazu `foreach` v metodě `Main` vytvoří volání funkce iterátoru. `Power`</span><span class="sxs-lookup"><span data-stu-id="14c27-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="14c27-141">Každé volání funkce iterátoru pokračuje k dalšímu `yield return` spuštění příkazu, ke kterému `for` dochází během další iterace smyčky.</span><span class="sxs-lookup"><span data-stu-id="14c27-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="14c27-142">Návratový typ metody iterátoru <xref:System.Collections.IEnumerable>je , což je typ rozhraní iterátoru.</span><span class="sxs-lookup"><span data-stu-id="14c27-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="14c27-143">Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.</span><span class="sxs-lookup"><span data-stu-id="14c27-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="14c27-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="14c27-144">Example</span></span>

<span data-ttu-id="14c27-145">Následující příklad ukazuje `get` přistupující objekt, který je iterátor.</span><span class="sxs-lookup"><span data-stu-id="14c27-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="14c27-146">V příkladu `yield return` každý příkaz vrátí instanci uživatelem definované třídy.</span><span class="sxs-lookup"><span data-stu-id="14c27-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="14c27-147">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="14c27-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="14c27-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="14c27-148">See also</span></span>

- [<span data-ttu-id="14c27-149">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="14c27-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="14c27-150">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="14c27-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="14c27-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="14c27-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="14c27-152">Iterátory</span><span class="sxs-lookup"><span data-stu-id="14c27-152">Iterators</span></span>](../../iterators.md)
