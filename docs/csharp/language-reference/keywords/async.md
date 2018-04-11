---
title: async (Referenční dokumentace jazyka C#)
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2ddbd0f7268dd5dae4095d661cf800b5b481cbbd
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="async-c-reference"></a><span data-ttu-id="e2bc7-102">async (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e2bc7-102">async (C# Reference)</span></span>
<span data-ttu-id="e2bc7-103">Použití `async` modifikátor určíte, že a metody [výrazu lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), nebo [anonymní metoda](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) je asynchronní.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="e2bc7-104">Pokud použijete tento modifikátor způsobu nebo výraz, ho se označuje jako *asynchronní metody*.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="e2bc7-105">V následujícím příkladu definuje použití asynchronní metody s názvem `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="e2bc7-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="e2bc7-106">Pokud jste ještě nikdy nepracovali do asynchronního programování nebo není srozumitelný používání asynchronní metody `await` – klíčové slovo práci potenciálně dlouhotrvající bez blokování vláken volajícího, přečtěte si úvod v [asynchronní programování s Async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2bc7-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="e2bc7-107">Následující kód je nalezena uvnitř asynchronní metody a počet volání <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> metoda:</span><span class="sxs-lookup"><span data-stu-id="e2bc7-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="e2bc7-108">Asynchronní metody spouští synchronně, dokud nebude dosaženo prvním `await` výrazu, v tomto okamžiku je metoda pozastaveno, dokud awaited úkol je dokončen.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="e2bc7-109">Během této doby se ovládací prvek vrátí volajícímu metody, stejně jako v příkladu v následující části.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="e2bc7-110">Pokud metodě, `async` upraví – klíčové slovo neobsahuje `await` výraz nebo příkaz metoda spustí synchronně.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="e2bc7-111">Upozornění kompilátoru vás upozorní na jakékoli asynchronní metody, které neobsahují žádný `await` příkazy, protože tato situace může znamenat chybu.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="e2bc7-112">V tématu [upozornění kompilátoru (úroveň 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="e2bc7-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="e2bc7-113">`async` – Klíčové slovo je kontextová v, aby se klíčové slovo jenom v případě, že upravuje metodu, výraz lambda nebo anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="e2bc7-114">Ve všech ostatních kontextech je interpretováno jako identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2bc7-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2bc7-115">Example</span></span>  
<span data-ttu-id="e2bc7-116">Následující příklad ukazuje strukturu a toku řízení mezi obslužnou rutinu události asynchronní `StartButton_Click`a použití asynchronní metody `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="e2bc7-117">Výsledek z asynchronní metody je počet znaků webové stránky.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="e2bc7-118">Kód je vhodný pro aplikaci Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store, které vytvoříte v sadě Visual Studio; Zobrazte komentáře kódu pro nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="e2bc7-119">Tento kód můžete spustit v sadě Visual Studio jako aplikace Windows Presentation Foundation (WPF) nebo aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="e2bc7-120">Je třeba ovládacího prvku tlačítko s názvem `StartButton` a ovládací prvek textové pole s názvem `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="e2bc7-121">Nezapomeňte nastavit názvy a obslužné rutiny tak, že máte přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="e2bc7-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="e2bc7-122">Kód spuštění jako aplikaci WPF:</span><span class="sxs-lookup"><span data-stu-id="e2bc7-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="e2bc7-123">Vložte tento kód do `MainWindow` třídy v MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="e2bc7-124">Přidáte odkaz na System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="e2bc7-125">Přidat `using` direktivy pro System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="e2bc7-126">Chcete-li spustit kód jako aplikace pro Windows Store:</span><span class="sxs-lookup"><span data-stu-id="e2bc7-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="e2bc7-127">Vložte tento kód do `MainPage` třídy v MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="e2bc7-128">Přidání direktivy using pro System.Net.Http a System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="e2bc7-129">Další informace o úlohách a kód, který se spustí při čekání na úlohu najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2bc7-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="e2bc7-130">Úplný příklad WPF, který používá podobným elementům, najdete v části [návod: přístup k webu pomocí modifikátoru Async a Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="e2bc7-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="e2bc7-131">Návratové typy</span><span class="sxs-lookup"><span data-stu-id="e2bc7-131">Return Types</span></span>  
<span data-ttu-id="e2bc7-132">Asynchronní metody může mít následující návratové typy:</span><span class="sxs-lookup"><span data-stu-id="e2bc7-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="e2bc7-133">[void](../../../csharp/language-reference/keywords/void.md), které musí být použit pouze pro obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-133">[void](../../../csharp/language-reference/keywords/void.md), which should only be used for event handlers.</span></span>
- <span data-ttu-id="e2bc7-134">Od verze jazyka C# 7, žádný typ, který má přístupné `GetAwaiter` metoda.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-134">Starting with C# 7, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="e2bc7-135">`System.Threading.Tasks.ValueTask<TResult>` Typ je jednou z těchto implementací.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-135">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="e2bc7-136">Je k dispozici přidáním balíček NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-136">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="e2bc7-137">Asynchronní metody nelze deklarovat všechny [v](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ani může ho mít [odkazovat návratovou hodnotu](../../programming-guide/classes-and-structs/ref-returns.md), ale může zavolat metody které mají tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-137">The async method can't declare any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="e2bc7-138">Zadáte `Task<TResult>` jako návratový typ asynchronní metody Pokud [vrátit](../../../csharp/language-reference/keywords/return.md) příkaz metody určuje operand typu `TResult`.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-138">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="e2bc7-139">Používáte `Task` Pokud žádná smysluplný hodnota je vrácena, pokud je metoda dokončena.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-139">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="e2bc7-140">To znamená, vrátí volání do metody `Task`, ale při `Task` dokončení žádné `await` výraz, který se čeká na `Task` vyhodnotí jako `void`.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-140">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="e2bc7-141">Můžete použít `void` návratový typ primárně k definování obslužné rutiny událostí, které vyžadují, které vrací typ.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-141">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="e2bc7-142">Volající `void`-vrátíte asynchronní metody nelze await a nemůže catch výjimky, které vyvolá metoda.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-142">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="e2bc7-143">Od verze jazyka C# 7, vrátíte jiného typu, obvykle hodnota typu, který má `GetAwaiter` metoda přidělení paměti miminize v výkonu kritická sekce kódu.</span><span class="sxs-lookup"><span data-stu-id="e2bc7-143">Starting with C# 7, you return another type, typically a value type, that has a `GetAwaiter` method to miminize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="e2bc7-144">Další informace a příklady naleznete v tématu [asynchronní vrátit typy](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="e2bc7-144">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2bc7-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2bc7-145">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="e2bc7-146">await</span><span class="sxs-lookup"><span data-stu-id="e2bc7-146">await</span></span>](../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="e2bc7-147">Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="e2bc7-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="e2bc7-148">Asynchronní programování pomocí modifikátoru Async a operátoru Await</span><span class="sxs-lookup"><span data-stu-id="e2bc7-148">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
