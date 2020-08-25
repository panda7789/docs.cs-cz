---
title: Async – reference jazyka C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: d2c1de12a0a836fd4a7962ebbfe890f21ea3d5a7
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811727"
---
# <a name="async-c-reference"></a><span data-ttu-id="bfd54-102">async (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bfd54-102">async (C# Reference)</span></span>

<span data-ttu-id="bfd54-103">Použijte `async` Modifikátor k určení toho, že metoda, [výraz lambda](../operators/lambda-expressions.md)nebo [anonymní metoda](../operators/delegate-operator.md) je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="bfd54-103">Use the `async` modifier to specify that a method, [lambda expression](../operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="bfd54-104">Použijete-li tento modifikátor na metodu nebo výraz, je označována jako *asynchronní metoda*.</span><span class="sxs-lookup"><span data-stu-id="bfd54-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="bfd54-105">Následující příklad definuje asynchronní metodu s názvem `ExampleMethodAsync` :</span><span class="sxs-lookup"><span data-stu-id="bfd54-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>

```csharp
public async Task<int> ExampleMethodAsync()
{
    //...
}
```

<span data-ttu-id="bfd54-106">Pokud začínáte s asynchronním programováním nebo nerozumíte, jak asynchronní metoda používá [ `await` operátor](../operators/await.md) pro potenciálně dlouhotrvající práci bez blokování vlákna volajícího, přečtěte si Úvod do [asynchronního programování pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfd54-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller's thread, read the introduction in [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="bfd54-107">Následující kód byl nalezen v asynchronní metodě a volá <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metodu:</span><span class="sxs-lookup"><span data-stu-id="bfd54-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>

```csharp
string contents = await httpClient.GetStringAsync(requestUrl);
```

<span data-ttu-id="bfd54-108">Asynchronní metoda běží synchronně, dokud nedosáhne svého prvního `await` výrazu, v tomto okamžiku je metoda pozastavena, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="bfd54-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="bfd54-109">Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.</span><span class="sxs-lookup"><span data-stu-id="bfd54-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>

<span data-ttu-id="bfd54-110">Pokud metoda, kterou `async` klíčové slovo upravuje `await` , neobsahuje výraz nebo příkaz, metoda se provede synchronně.</span><span class="sxs-lookup"><span data-stu-id="bfd54-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="bfd54-111">Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují `await` příkazy, protože tato situace může znamenat chybu.</span><span class="sxs-lookup"><span data-stu-id="bfd54-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="bfd54-112">Viz [Upozornění kompilátoru (úroveň 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="bfd54-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>

 <span data-ttu-id="bfd54-113">`async`Klíčové slovo je kontextové v tom, že se jedná o klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="bfd54-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="bfd54-114">Ve všech ostatních kontextech je interpretováno jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="bfd54-114">In all other contexts, it's interpreted as an identifier.</span></span>

## <a name="example"></a><span data-ttu-id="bfd54-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfd54-115">Example</span></span>
<span data-ttu-id="bfd54-116">Následující příklad ukazuje strukturu a tok řízení mezi obslužnou rutinou asynchronní události, `StartButton_Click` a asynchronní metodou `ExampleMethodAsync` .</span><span class="sxs-lookup"><span data-stu-id="bfd54-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="bfd54-117">Výsledek z asynchronní metody je počet znaků webové stránky.</span><span class="sxs-lookup"><span data-stu-id="bfd54-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="bfd54-118">Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikaci pro Windows Store, kterou vytvoříte v aplikaci Visual Studio; Podívejte se na komentáře ke kódu pro nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="bfd54-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>

<span data-ttu-id="bfd54-119">Tento kód můžete spustit v aplikaci Visual Studio jako aplikaci Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="bfd54-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="bfd54-120">Potřebujete ovládací prvek tlačítko s názvem `StartButton` a ovládací prvek TextBox s názvem `ResultsTextBox` .</span><span class="sxs-lookup"><span data-stu-id="bfd54-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="bfd54-121">Nezapomeňte nastavit názvy a obslužné rutiny tak, abyste měli něco podobného:</span><span class="sxs-lookup"><span data-stu-id="bfd54-121">Remember to set the names and handler so that you have something like this:</span></span>

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"
        Click="StartButton_Click" Name="StartButton"/>
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>
```

<span data-ttu-id="bfd54-122">Spuštění kódu jako aplikace WPF:</span><span class="sxs-lookup"><span data-stu-id="bfd54-122">To run the code as a WPF app:</span></span>

- <span data-ttu-id="bfd54-123">Vložte tento kód do `MainWindow` třídy v MainWindow.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="bfd54-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>
- <span data-ttu-id="bfd54-124">Přidejte odkaz na System .NET. http.</span><span class="sxs-lookup"><span data-stu-id="bfd54-124">Add a reference to System.Net.Http.</span></span>
- <span data-ttu-id="bfd54-125">Přidejte `using` direktivu pro System .NET. http.</span><span class="sxs-lookup"><span data-stu-id="bfd54-125">Add a `using` directive for System.Net.Http.</span></span>

<span data-ttu-id="bfd54-126">Spuštění kódu jako aplikace pro Windows Store:</span><span class="sxs-lookup"><span data-stu-id="bfd54-126">To run the code as a Windows Store app:</span></span>

- <span data-ttu-id="bfd54-127">Vložte tento kód do `MainPage` třídy v MainPage.XAML.cs.</span><span class="sxs-lookup"><span data-stu-id="bfd54-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>
- <span data-ttu-id="bfd54-128">Přidejte direktivy using pro System .NET. http a System. Threading. Tasks.</span><span class="sxs-lookup"><span data-stu-id="bfd54-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>

[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]

> [!IMPORTANT]
> <span data-ttu-id="bfd54-129">Další informace o úlohách a kódu, který se spouští při čekání na úlohu, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="bfd54-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="bfd54-130">Úplný příklad konzoly pro použití podobných prvků naleznete v tématu [proces asynchronních úloh po dokončení (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="bfd54-130">For a full console example that uses similar elements, see [Process asynchronous tasks as they complete (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>

## <a name="return-types"></a><span data-ttu-id="bfd54-131">Návratové typy</span><span class="sxs-lookup"><span data-stu-id="bfd54-131">Return Types</span></span>
<span data-ttu-id="bfd54-132">Asynchronní metoda může mít následující návratové typy:</span><span class="sxs-lookup"><span data-stu-id="bfd54-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="bfd54-133">[void](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="bfd54-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="bfd54-134">`async void` metody se obecně nedoporučují pro jiný kód než obslužné rutiny událostí, protože volající nemůžou `await` tyto metody a musí implementovat jiný mechanismus, aby hlásili úspěšné dokončení nebo chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="bfd54-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="bfd54-135">Počínaje jazykem C# 7,0, jakýkoli typ, který má přístupnou `GetAwaiter` metodu.</span><span class="sxs-lookup"><span data-stu-id="bfd54-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="bfd54-136">`System.Threading.Tasks.ValueTask<TResult>`Typ představuje jednu takovou implementaci.</span><span class="sxs-lookup"><span data-stu-id="bfd54-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="bfd54-137">Je k dispozici přidáním balíčku NuGet `System.Threading.Tasks.Extensions` .</span><span class="sxs-lookup"><span data-stu-id="bfd54-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="bfd54-138">Asynchronní metoda nemůže deklarovat jakýkoli parametr [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md) , ani nemůže mít [odkazovou návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody, které mají tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="bfd54-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>

<span data-ttu-id="bfd54-139">Zadáte `Task<TResult>` jako návratový typ asynchronní metody, pokud příkaz [return](./return.md) metody určuje operand typu `TResult` .</span><span class="sxs-lookup"><span data-stu-id="bfd54-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="bfd54-140">Použijete, `Task` Pokud není vrácena žádná smysluplná hodnota po dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="bfd54-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="bfd54-141">To znamená, že volání metody vrátí `Task` , ale po `Task` dokončení je libovolný `await` výraz, který čeká na `Task` vyhodnotit `void` .</span><span class="sxs-lookup"><span data-stu-id="bfd54-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>

<span data-ttu-id="bfd54-142">`void`Pro definování obslužných rutin událostí, které vyžadují návratový typ, použijte primárně návratový typ.</span><span class="sxs-lookup"><span data-stu-id="bfd54-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="bfd54-143">Volající `void` asynchronní metody vracející výjimku nemůže očekávat a zachytit výjimky, které metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="bfd54-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="bfd54-144">Počínaje jazykem C# 7,0 vrátíte jiný typ, obvykle hodnotový typ, který má `GetAwaiter` metodu pro minimalizaci přidělení paměti v částech v kódu kritickém pro výkon.</span><span class="sxs-lookup"><span data-stu-id="bfd54-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="bfd54-145">Další informace a příklady naleznete v tématu [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="bfd54-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfd54-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfd54-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="bfd54-147">await</span><span class="sxs-lookup"><span data-stu-id="bfd54-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="bfd54-148">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="bfd54-148">Asynchronous programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="bfd54-149">Zpracování asynchronních úloh po dokončení</span><span class="sxs-lookup"><span data-stu-id="bfd54-149">Process asynchronous tasks as they complete</span></span>](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)
