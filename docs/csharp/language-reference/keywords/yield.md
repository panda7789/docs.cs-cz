---
description: klíčové slovo yield – referenční informace jazyka C#
title: klíčové slovo yield – referenční informace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: c8caf7e34397faf9f7085d6634287cffcb37eb08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141878"
---
# <a name="yield-c-reference"></a><span data-ttu-id="11a38-103">yield (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="11a38-103">yield (C# Reference)</span></span>

<span data-ttu-id="11a38-104">Při použití `yield` [klíčového slova kontextové](index.md#contextual-keywords) v příkazu označíte, že metoda, operátor nebo `get` přistupující objekt, ve kterém se zobrazí, je iterátor.</span><span class="sxs-lookup"><span data-stu-id="11a38-104">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="11a38-105">Použití `yield` k definování iterátoru odstraní nutnost explicitní třídy extra (třída, která obsahuje stav pro výčet, viz <xref:System.Collections.Generic.IEnumerator%601> příklad) při implementaci <xref:System.Collections.IEnumerable> <xref:System.Collections.IEnumerator> vzor a pro vlastní typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="11a38-105">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="11a38-106">Následující příklad ukazuje dva formy `yield` příkazu.</span><span class="sxs-lookup"><span data-stu-id="11a38-106">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="11a38-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="11a38-107">Remarks</span></span>

<span data-ttu-id="11a38-108">Použijete `yield return` příkaz k vrácení každého prvku v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="11a38-108">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="11a38-109">Sekvenci vrácenou metodou iterátoru lze spotřebovat pomocí příkazu [foreach](foreach-in.md) nebo dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="11a38-109">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="11a38-110">Každá iterace `foreach` smyčky volá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="11a38-110">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="11a38-111">Je-li `yield return` v metodě iterátoru dosaženo příkazu, `expression` je vráceno a aktuální umístění v kódu je uchováno.</span><span class="sxs-lookup"><span data-stu-id="11a38-111">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="11a38-112">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="11a38-112">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="11a38-113">`yield break`K ukončení iterace můžete použít příkaz.</span><span class="sxs-lookup"><span data-stu-id="11a38-113">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="11a38-114">Další informace o iterátorech naleznete v tématu [iterátory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="11a38-114">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="11a38-115">Metody iterátoru a přistupující objekty get</span><span class="sxs-lookup"><span data-stu-id="11a38-115">Iterator methods and get accessors</span></span>

<span data-ttu-id="11a38-116">Deklarace iterátoru musí splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="11a38-116">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="11a38-117">Návratový typ musí být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="11a38-117">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="11a38-118">Deklarace nemůže [mít žádné parametry](in-parameter-modifier.md) [ref](ref.md) nebo [out](out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="11a38-118">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="11a38-119">`yield`Typ iterátoru, který vrací <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.IEnumerator> je `object` .</span><span class="sxs-lookup"><span data-stu-id="11a38-119">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="11a38-120">Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.Generic.IEnumerator%601> , musí být implicitní převod z typu výrazu v `yield return` příkazu na parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="11a38-120">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="11a38-121">Nemůžete zahrnout `yield return` `yield break` příkaz ani do:</span><span class="sxs-lookup"><span data-stu-id="11a38-121">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="11a38-122">[Lambda výrazy](../operators/lambda-expressions.md) a [anonymní metody](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="11a38-122">[Lambda expressions](../operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="11a38-123">Metody, které obsahují nebezpečné bloky.</span><span class="sxs-lookup"><span data-stu-id="11a38-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="11a38-124">Další informace najdete v tématu [unsafe](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="11a38-124">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="11a38-125">Ošetření výjimek</span><span class="sxs-lookup"><span data-stu-id="11a38-125">Exception handling</span></span>

<span data-ttu-id="11a38-126">`yield return`Příkaz se nemůže nacházet v bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="11a38-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="11a38-127">`yield return`Příkaz lze umístit do bloku try příkazu try-finally.</span><span class="sxs-lookup"><span data-stu-id="11a38-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="11a38-128">`yield break`Příkaz se může nacházet v bloku try nebo bloku catch, ale ne v bloku finally.</span><span class="sxs-lookup"><span data-stu-id="11a38-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="11a38-129">Pokud `foreach` tělo (mimo metodu iterátoru) vyvolá výjimku, `finally` je spuštěn blok v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="11a38-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="11a38-130">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="11a38-130">Technical implementation</span></span>

<span data-ttu-id="11a38-131">Následující kód vrátí `IEnumerable<string>` z metody iterátoru a pak projde jeho prvky.</span><span class="sxs-lookup"><span data-stu-id="11a38-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="11a38-132">Volání `MyIteratorMethod` nespustí tělo metody.</span><span class="sxs-lookup"><span data-stu-id="11a38-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="11a38-133">Místo toho volání vrátí `IEnumerable<string>` do `elements` proměnné.</span><span class="sxs-lookup"><span data-stu-id="11a38-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="11a38-134">V iteraci `foreach` smyčky <xref:System.Collections.IEnumerator.MoveNext%2A> je metoda volána pro `elements` .</span><span class="sxs-lookup"><span data-stu-id="11a38-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="11a38-135">Toto volání provede tělo `MyIteratorMethod` až do `yield return` dosažení dalšího příkazu.</span><span class="sxs-lookup"><span data-stu-id="11a38-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="11a38-136">Výraz vrácený `yield return` příkazem určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také <xref:System.Collections.Generic.IEnumerator%601.Current%2A> vlastnost objektu `elements` , což je `IEnumerable<string>` .</span><span class="sxs-lookup"><span data-stu-id="11a38-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="11a38-137">Při každém následném opakování `foreach` smyčky pokračuje provádění textu iterátoru z místa, kde bylo ponecháno, opětovné zastavení při dosažení `yield return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="11a38-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="11a38-138">`foreach`Smyčka skončí po dosažení konce metody iterátoru nebo `yield break` příkazu.</span><span class="sxs-lookup"><span data-stu-id="11a38-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="11a38-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="11a38-139">Example</span></span>

<span data-ttu-id="11a38-140">Následující příklad obsahuje `yield return` příkaz, který je uvnitř `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="11a38-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="11a38-141">Každá iterace `foreach` těla příkazu v `Main` metodě vytvoří volání `Power` funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="11a38-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="11a38-142">Každé volání funkce iterátoru pokračuje k dalšímu provedení `yield return` příkazu, ke kterému dojde během další iterace `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="11a38-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="11a38-143">Návratový typ metody iterátoru je <xref:System.Collections.IEnumerable> , což je typ rozhraní iterátoru.</span><span class="sxs-lookup"><span data-stu-id="11a38-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="11a38-144">Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.</span><span class="sxs-lookup"><span data-stu-id="11a38-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="11a38-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="11a38-145">Example</span></span>

<span data-ttu-id="11a38-146">Následující příklad ukazuje `get` přistupující objekt, který je iterátorem.</span><span class="sxs-lookup"><span data-stu-id="11a38-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="11a38-147">V příkladu každý `yield return` příkaz vrátí instanci uživatelsky definované třídy.</span><span class="sxs-lookup"><span data-stu-id="11a38-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="11a38-148">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="11a38-148">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="11a38-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="11a38-149">See also</span></span>

- [<span data-ttu-id="11a38-150">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="11a38-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="11a38-151">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="11a38-151">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="11a38-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="11a38-152">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="11a38-153">Iterátory</span><span class="sxs-lookup"><span data-stu-id="11a38-153">Iterators</span></span>](../../iterators.md)
