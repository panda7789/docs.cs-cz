---
title: kontextové klíčové slovo yield C# – referenční informace
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e3c9e37e7b543eaddae837a85604c4ba91fbc744
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712777"
---
# <a name="yield-c-reference"></a><span data-ttu-id="38bd9-102">yield (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="38bd9-102">yield (C# Reference)</span></span>

<span data-ttu-id="38bd9-103">Při použití [klíčového slova `yield` kontextové](index.md#contextual-keywords) v příkazu označíte, že metoda, operátor nebo přistupující objekt `get`, ve kterém se zobrazí, je iterátor.</span><span class="sxs-lookup"><span data-stu-id="38bd9-103">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="38bd9-104">Použití `yield` k definování iterátoru odstraní nutnost explicitní třídy navíc (třída, která obsahuje stav pro výčet, viz <xref:System.Collections.Generic.IEnumerator%601> pro příklad) při implementaci <xref:System.Collections.IEnumerable> a <xref:System.Collections.IEnumerator> vzoru pro vlastní typ kolekce.</span><span class="sxs-lookup"><span data-stu-id="38bd9-104">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="38bd9-105">Následující příklad ukazuje dva formy příkazu `yield`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-105">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="38bd9-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38bd9-106">Remarks</span></span>

<span data-ttu-id="38bd9-107">Pomocí příkazu `yield return` můžete vracet každý prvek po jednom.</span><span class="sxs-lookup"><span data-stu-id="38bd9-107">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="38bd9-108">Sekvenci vrácenou metodou iterátoru lze spotřebovat pomocí příkazu [foreach](foreach-in.md) nebo dotazu LINQ.</span><span class="sxs-lookup"><span data-stu-id="38bd9-108">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="38bd9-109">Každá iterace `foreach` smyčky volá metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="38bd9-109">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="38bd9-110">Při dosažení `yield return`ho příkazu v metodě iterátoru se vrátí `expression` a aktuální umístění v kódu je zachováno.</span><span class="sxs-lookup"><span data-stu-id="38bd9-110">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="38bd9-111">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="38bd9-111">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="38bd9-112">K ukončení iterace můžete použít příkaz `yield break`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-112">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="38bd9-113">Další informace o iterátorech naleznete v tématu [iterátory](../../iterators.md).</span><span class="sxs-lookup"><span data-stu-id="38bd9-113">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="38bd9-114">Metody iterátoru a přistupující objekty get</span><span class="sxs-lookup"><span data-stu-id="38bd9-114">Iterator methods and get accessors</span></span>

<span data-ttu-id="38bd9-115">Deklarace iterátoru musí splňovat následující požadavky:</span><span class="sxs-lookup"><span data-stu-id="38bd9-115">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="38bd9-116">Návratový typ musí být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="38bd9-116">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="38bd9-117">Deklarace nemůže [mít žádné parametry](in-parameter-modifier.md) [ref](ref.md) nebo [out](out-parameter-modifier.md) .</span><span class="sxs-lookup"><span data-stu-id="38bd9-117">The declaration can't have any [in](in-parameter-modifier.md) [ref](ref.md) or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="38bd9-118">`yield` typ iterátoru, který vrací <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.IEnumerator> je `object`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-118">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="38bd9-119">Pokud iterátor vrátí <xref:System.Collections.Generic.IEnumerable%601> nebo <xref:System.Collections.Generic.IEnumerator%601>, musí existovat implicitní převod z typu výrazu v příkazu `yield return` na parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="38bd9-119">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="38bd9-120">Do těchto příkazů nemůžete zahrnout `yield return` ani `yield break`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-120">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="38bd9-121">[Lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) a [anonymní metody](../operators/delegate-operator.md).</span><span class="sxs-lookup"><span data-stu-id="38bd9-121">[Lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="38bd9-122">Metody, které obsahují nebezpečné bloky.</span><span class="sxs-lookup"><span data-stu-id="38bd9-122">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="38bd9-123">Další informace najdete v tématu [unsafe](unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="38bd9-123">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="38bd9-124">Ošetření výjimek</span><span class="sxs-lookup"><span data-stu-id="38bd9-124">Exception handling</span></span>

<span data-ttu-id="38bd9-125">Příkaz `yield return` se nemůže nacházet v bloku try-catch.</span><span class="sxs-lookup"><span data-stu-id="38bd9-125">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="38bd9-126">Příkaz `yield return` lze umístit do bloku try příkazu try-finally.</span><span class="sxs-lookup"><span data-stu-id="38bd9-126">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="38bd9-127">Příkaz `yield break` může být umístěn v bloku try nebo bloku catch, ale ne v bloku finally.</span><span class="sxs-lookup"><span data-stu-id="38bd9-127">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="38bd9-128">Pokud `foreach` tělo (mimo metodu iterátoru) vyvolá výjimku, je spuštěn blok `finally` v metodě iterátoru.</span><span class="sxs-lookup"><span data-stu-id="38bd9-128">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="38bd9-129">Technická implementace</span><span class="sxs-lookup"><span data-stu-id="38bd9-129">Technical implementation</span></span>

<span data-ttu-id="38bd9-130">Následující kód vrátí `IEnumerable<string>` z metody iterátoru a poté projde jeho prvky.</span><span class="sxs-lookup"><span data-stu-id="38bd9-130">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="38bd9-131">Volání `MyIteratorMethod` nespustí tělo metody.</span><span class="sxs-lookup"><span data-stu-id="38bd9-131">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="38bd9-132">Místo toho volání vrátí `IEnumerable<string>` do proměnné `elements`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-132">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="38bd9-133">V iteraci `foreach` smyčky je <xref:System.Collections.IEnumerator.MoveNext%2A> metoda volána pro `elements`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-133">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="38bd9-134">Toto volání provede text `MyIteratorMethod` až do chvíle, kdy se dosáhne dalšího příkazu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-134">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="38bd9-135">Výraz vrácený příkazem `yield return` určuje nejen hodnotu `element` proměnné pro spotřebu v těle smyčky, ale také vlastnost <xref:System.Collections.Generic.IEnumerator%601.Current%2A> `elements`, což je `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-135">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="38bd9-136">Při každé následující iteraci `foreach` smyčky pokračuje v provádění tohoto textu iterátoru, kde se nachází, a znovu se zastaví, až dosáhne příkazu `yield return`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-136">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="38bd9-137">Cyklus `foreach` končí, když je dosaženo konce metody iterátoru nebo příkazu `yield break`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-137">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="38bd9-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="38bd9-138">Example</span></span>

<span data-ttu-id="38bd9-139">Následující příklad obsahuje příkaz `yield return`, který je uvnitř smyčky `for`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-139">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="38bd9-140">Každá iterace těla příkazu `foreach` v metodě `Main` vytvoří volání funkce iterátoru `Power`.</span><span class="sxs-lookup"><span data-stu-id="38bd9-140">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="38bd9-141">Každé volání funkce iterátoru pokračuje na další provedení příkazu `yield return`, ke kterému dojde během další iterace `for` smyčky.</span><span class="sxs-lookup"><span data-stu-id="38bd9-141">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="38bd9-142">Návratový typ metody iterátoru je <xref:System.Collections.IEnumerable>, což je typ rozhraní iterátoru.</span><span class="sxs-lookup"><span data-stu-id="38bd9-142">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="38bd9-143">Při volání metody iterátoru je vrácen vyčíslitelný objekt, který obsahuje mocniny čísla.</span><span class="sxs-lookup"><span data-stu-id="38bd9-143">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="38bd9-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="38bd9-144">Example</span></span>

<span data-ttu-id="38bd9-145">Následující příklad ukazuje přistupující objekt `get`, který je iterátorem.</span><span class="sxs-lookup"><span data-stu-id="38bd9-145">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="38bd9-146">V příkladu každý příkaz `yield return` vrací instanci uživatelsky definované třídy.</span><span class="sxs-lookup"><span data-stu-id="38bd9-146">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="38bd9-147">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="38bd9-147">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="38bd9-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="38bd9-148">See also</span></span>

- [<span data-ttu-id="38bd9-149">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="38bd9-149">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="38bd9-150">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="38bd9-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="38bd9-151">foreach, in</span><span class="sxs-lookup"><span data-stu-id="38bd9-151">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="38bd9-152">Iterátory</span><span class="sxs-lookup"><span data-stu-id="38bd9-152">Iterators</span></span>](../../iterators.md)
