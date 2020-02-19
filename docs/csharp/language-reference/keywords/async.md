---
title: asynchronní C# odkaz
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 30ee13a4174a137481fbcd36ccef721958b94a12
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77450853"
---
# <a name="async-c-reference"></a><span data-ttu-id="874db-102">async (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="874db-102">async (C# Reference)</span></span>

<span data-ttu-id="874db-103">Použijte modifikátor `async` k určení, že metoda, [výraz lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo [anonymní metoda](../operators/delegate-operator.md) je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="874db-103">Use the `async` modifier to specify that a method, [lambda expression](../../programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="874db-104">Použijete-li tento modifikátor na metodu nebo výraz, je označována jako *asynchronní metoda*.</span><span class="sxs-lookup"><span data-stu-id="874db-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="874db-105">Následující příklad definuje asynchronní metodu s názvem `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="874db-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="874db-106">Pokud s asynchronním programováním začínáte a nerozumíte tomu, jak asynchronní metoda používá [operátor`await`](../operators/await.md) pro potenciálně dlouhotrvající práci bez blokování vlákna volajícího, přečtěte si Úvod do [asynchronního programování pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="874db-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="874db-107">Následující kód byl nalezen v asynchronní metodě a volá metodu <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="874db-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="874db-108">Asynchronní metoda běží synchronně, dokud nedosáhne prvního `await` výrazu, na kterém je metoda pozastavena, dokud není dokončen očekávaný úkol.</span><span class="sxs-lookup"><span data-stu-id="874db-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="874db-109">Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.</span><span class="sxs-lookup"><span data-stu-id="874db-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="874db-110">Pokud metoda, kterou klíčová slova `async` upravuje, neobsahuje výraz nebo příkaz `await`, metoda se provede synchronně.</span><span class="sxs-lookup"><span data-stu-id="874db-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="874db-111">Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují `await` příkazy, protože tato situace může znamenat chybu.</span><span class="sxs-lookup"><span data-stu-id="874db-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="874db-112">Viz [Upozornění kompilátoru (úroveň 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="874db-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="874db-113">Klíčové slovo `async` je kontextové v tom, že se jedná o klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="874db-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="874db-114">Ve všech ostatních kontextech je interpretováno jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="874db-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="874db-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="874db-115">Example</span></span>  
<span data-ttu-id="874db-116">Následující příklad ukazuje strukturu a tok řízení mezi obslužnou rutinou asynchronní události, `StartButton_Click`a asynchronní metodou `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="874db-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="874db-117">Výsledek z asynchronní metody je počet znaků webové stránky.</span><span class="sxs-lookup"><span data-stu-id="874db-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="874db-118">Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikaci pro Windows Store, kterou vytvoříte v aplikaci Visual Studio; Podívejte se na komentáře ke kódu pro nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="874db-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="874db-119">Tento kód můžete spustit v aplikaci Visual Studio jako aplikaci Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="874db-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="874db-120">Potřebujete ovládací prvek tlačítko s názvem `StartButton` a ovládací prvek TextBox s názvem `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="874db-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="874db-121">Nezapomeňte nastavit názvy a obslužné rutiny tak, abyste měli něco podobného:</span><span class="sxs-lookup"><span data-stu-id="874db-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="874db-122">Spuštění kódu jako aplikace WPF:</span><span class="sxs-lookup"><span data-stu-id="874db-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="874db-123">Vložte tento kód do třídy `MainWindow` v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="874db-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="874db-124">Přidejte odkaz na System .NET. http.</span><span class="sxs-lookup"><span data-stu-id="874db-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="874db-125">Přidejte direktivu `using` pro System .NET. http.</span><span class="sxs-lookup"><span data-stu-id="874db-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="874db-126">Spuštění kódu jako aplikace pro Windows Store:</span><span class="sxs-lookup"><span data-stu-id="874db-126">To run the code as a Windows Store app:</span></span>  

- <span data-ttu-id="874db-127">Vložte tento kód do třídy `MainPage` v MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="874db-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="874db-128">Přidejte direktivy using pro System .NET. http a System. Threading. Tasks.</span><span class="sxs-lookup"><span data-stu-id="874db-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> <span data-ttu-id="874db-129">Další informace o úlohách a kódu, který se spouští při čekání na úlohu, naleznete v tématu [asynchronní programování s modifikátorem Async a await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="874db-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="874db-130">Úplný příklad WPF, který používá podobné prvky, naleznete v tématu [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="874db-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="874db-131">Návratové typy</span><span class="sxs-lookup"><span data-stu-id="874db-131">Return Types</span></span>  
<span data-ttu-id="874db-132">Asynchronní metoda může mít následující návratové typy:</span><span class="sxs-lookup"><span data-stu-id="874db-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="874db-133">[void](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="874db-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="874db-134">metody `async void` jsou obecně nedoporučovány pro jiný kód než obslužné rutiny událostí, protože volající nemohou `await` tyto metody a musí implementovat jiný mechanismus, který bude hlásit úspěšné dokončení nebo chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="874db-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="874db-135">Počínaje C# 7,0, jakýkoli typ, který má přístupnou metodu `GetAwaiter`.</span><span class="sxs-lookup"><span data-stu-id="874db-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="874db-136">Typ `System.Threading.Tasks.ValueTask<TResult>` představuje jednu takovou implementaci.</span><span class="sxs-lookup"><span data-stu-id="874db-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="874db-137">Je k dispozici přidáním balíčku NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="874db-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="874db-138">Asynchronní metoda nemůže deklarovat jakýkoli parametr [in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out](./out-parameter-modifier.md) , ani nemůže mít [odkazovou návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody, které mají tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="874db-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="874db-139">Zadejte `Task<TResult>` jako návratový typ asynchronní metody, pokud příkaz [return](./return.md) metody určuje operand typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="874db-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="874db-140">Použijete `Task`, pokud není vrácena žádná smysluplná hodnota po dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="874db-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="874db-141">To znamená, že volání metody vrací `Task`, ale po dokončení `Task` všechny `await` výrazy, které čekají `Task`, se vyhodnotí jako `void`.</span><span class="sxs-lookup"><span data-stu-id="874db-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="874db-142">Použijte `void` návratový typ primárně k definování obslužných rutin událostí, které vyžadují návratový typ.</span><span class="sxs-lookup"><span data-stu-id="874db-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="874db-143">Volající asynchronní metody vracející `void`nemůže použít operátor await a nemůže zachytit výjimky, které metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="874db-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="874db-144">Počínaje C# 7,0 vrátíte jiný typ, obvykle hodnotový typ, který má metodu `GetAwaiter` pro minimalizaci přidělení paměti v částech kódu kritických pro výkon.</span><span class="sxs-lookup"><span data-stu-id="874db-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="874db-145">Další informace a příklady naleznete v tématu [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="874db-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="874db-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="874db-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="874db-147">await</span><span class="sxs-lookup"><span data-stu-id="874db-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="874db-148">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="874db-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="874db-149">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="874db-149">Asynchronous Programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
