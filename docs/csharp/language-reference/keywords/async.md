---
title: asynchronní – odkaz jazyka C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 89133339a75c70e3ac86d627065e78d555bff71d
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507201"
---
# <a name="async-c-reference"></a><span data-ttu-id="cdbc8-102">async (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cdbc8-102">async (C# Reference)</span></span>

<span data-ttu-id="cdbc8-103">Modifikátor slouží k určení, že metoda, [výraz lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo anonymní metoda je asynchronní. [anonymous method](../operators/delegate-operator.md) `async`</span><span class="sxs-lookup"><span data-stu-id="cdbc8-103">Use the `async` modifier to specify that a method, [lambda expression](../../programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="cdbc8-104">Pokud použijete tento modifikátor na metodu nebo výraz, je označován jako *asynchronní metoda*.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="cdbc8-105">Následující příklad definuje asynchronní `ExampleMethodAsync`metodu s názvem :</span><span class="sxs-lookup"><span data-stu-id="cdbc8-105">The following example defines an async method named `ExampleMethodAsync`:</span></span>
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  

<span data-ttu-id="cdbc8-106">Pokud jste novým asynchronní programování nebo nerozumíte, jak asynchronní metoda používá [ `await` operátor](../operators/await.md) k tomu potenciálně dlouhotrvající práci bez blokování volajícího vlákno, přečtěte si úvod v [asynchronní programování s asynchronní a await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="cdbc8-106">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller's thread, read the introduction in [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="cdbc8-107">Následující kód se nachází uvnitř asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metody a volá metodu:</span><span class="sxs-lookup"><span data-stu-id="cdbc8-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="cdbc8-108">Asynchronní metoda se spouští synchronně, `await` dokud nedosáhne svého prvního výrazu, kdy je metoda pozastavena, dokud není očekávaná úloha dokončena.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="cdbc8-109">Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="cdbc8-110">Pokud metoda, `async` kterou klíčové slovo upravuje, neobsahuje `await` výraz nebo příkaz, metoda se provede synchronně.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="cdbc8-111">Upozornění kompilátoru vás upozorní na všechny asynchronní metody, které neobsahují `await` příkazy, protože tato situace může znamenat chybu.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="cdbc8-112">Viz [Upozornění kompilátoru (úroveň 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="cdbc8-112">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="cdbc8-113">Klíčové `async` slovo je kontextové v tom, že je klíčové slovo pouze v případě, že upravuje metodu, výraz lambda nebo anonymní metodu.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="cdbc8-114">Ve všech ostatních kontextech je interpretováno jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cdbc8-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdbc8-115">Example</span></span>  
<span data-ttu-id="cdbc8-116">Následující příklad ukazuje strukturu a tok řízení mezi `StartButton_Click`obslužnou rutinou asynchronní události a asynchronní metodou `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="cdbc8-117">Výsledkem asynchronní metody je počet znaků webové stránky.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="cdbc8-118">Kód je vhodný pro aplikaci WPF (Windows Presentation Foundation) nebo pro Windows Store, kterou vytvoříte ve Visual Studiu. podívejte se na komentáře kódu pro nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="cdbc8-119">Tento kód můžete spustit ve Visual Studiu jako aplikaci WPF (Windows Presentation Foundation) nebo windows store.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="cdbc8-120">Potřebujete ovládací prvek `StartButton` Button s názvem `ResultsTextBox`a ovládací prvek Textové pole s názvem .</span><span class="sxs-lookup"><span data-stu-id="cdbc8-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="cdbc8-121">Nezapomeňte nastavit jména a obslužnou rutinu tak, abyste měli něco takového:</span><span class="sxs-lookup"><span data-stu-id="cdbc8-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="cdbc8-122">Spuštění kódu jako aplikace WPF:</span><span class="sxs-lookup"><span data-stu-id="cdbc8-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="cdbc8-123">Vložte tento `MainWindow` kód do třídy v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="cdbc8-124">Přidejte odkaz na System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="cdbc8-125">Přidejte `using` direktivu pro System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="cdbc8-126">Spuštění kódu jako aplikace pro Windows Store:</span><span class="sxs-lookup"><span data-stu-id="cdbc8-126">To run the code as a Windows Store app:</span></span>  

- <span data-ttu-id="cdbc8-127">Vložte tento `MainPage` kód do třídy v MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="cdbc8-128">Přidat pomocí direktiv pro System.Net.Http a System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
> <span data-ttu-id="cdbc8-129">Další informace o úkolech a kódu, který se provádí při čekání na úlohu, naleznete [v tématu Asynchronní programování s asynchronní a await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="cdbc8-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="cdbc8-130">Úplný příklad WPF, který používá podobné prvky, naleznete [v tématu Návod: Přístup k webu pomocí Async a Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="cdbc8-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="cdbc8-131">Návratové typy</span><span class="sxs-lookup"><span data-stu-id="cdbc8-131">Return Types</span></span>  
<span data-ttu-id="cdbc8-132">Asynchronní metoda může mít následující návratové typy:</span><span class="sxs-lookup"><span data-stu-id="cdbc8-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="cdbc8-133">[neplatné](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="cdbc8-133">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="cdbc8-134">`async void`Metody jsou obecně nedoporučuje pro kód než obslužné rutiny událostí, protože volající nemohou `await` tyto metody a musí implementovat jiný mechanismus pro hlášení úspěšné dokončení nebo chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-134">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="cdbc8-135">Počínaje C# 7.0, libovolný typ, `GetAwaiter` který má přístupnou metodu.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-135">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="cdbc8-136">Typ `System.Threading.Tasks.ValueTask<TResult>` je jedna taková implementace.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-136">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="cdbc8-137">Je k dispozici přidáním `System.Threading.Tasks.Extensions`balíčku NuGet .</span><span class="sxs-lookup"><span data-stu-id="cdbc8-137">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="cdbc8-138">Asynchronní metoda nemůže deklarovat žádné [parametry in](./in-parameter-modifier.md), [ref](./ref.md) nebo [out,](./out-parameter-modifier.md) ani nemůže mít [referenční vrácenou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může volat metody, které mají takové parametry.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-138">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="cdbc8-139">Jako `Task<TResult>` návratový typ asynchronní metody zadáte, pokud [příkaz return](./return.md) metody určuje `TResult`operand typu .</span><span class="sxs-lookup"><span data-stu-id="cdbc8-139">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="cdbc8-140">Můžete `Task` použít, pokud není vrácena žádná smysluplná hodnota po dokončení metody.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-140">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="cdbc8-141">To znamená, že volání metody `Task`vrátí , `Task` ale po `await` dokončení, jakýkoli výraz, který čeká na `Task` vyhodnocuje `void`.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-141">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="cdbc8-142">Návratový `void` typ slouží především k definování obslužných rutin událostí, které tento návratový typ vyžadují.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-142">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="cdbc8-143">Volající `void`-vracející asynchronní metoda nemůže čekat a nemůže zachytit výjimky, které metoda vyvolá.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-143">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="cdbc8-144">Počínaje C# 7.0 vrátíte jiný typ, obvykle typ hodnoty, který má metodu `GetAwaiter` minimalizovat přidělení paměti v části kódu kritické pro výkon.</span><span class="sxs-lookup"><span data-stu-id="cdbc8-144">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="cdbc8-145">Další informace a příklady naleznete [v tématu Asynchronní návratové typy](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="cdbc8-145">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbc8-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdbc8-146">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="cdbc8-147">await</span><span class="sxs-lookup"><span data-stu-id="cdbc8-147">await</span></span>](../operators/await.md)
- [<span data-ttu-id="cdbc8-148">Návod: Přístup k webu pomocí Async a Await</span><span class="sxs-lookup"><span data-stu-id="cdbc8-148">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="cdbc8-149">Asynchronní programování s asynchronní a čekají</span><span class="sxs-lookup"><span data-stu-id="cdbc8-149">Asynchronous Programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
