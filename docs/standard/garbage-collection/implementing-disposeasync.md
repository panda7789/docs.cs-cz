---
title: Implementace metody DisposeAsync
description: Naučte se implementovat metody DisposeAsync a DisposeAsyncCore pro provádění asynchronního vyčištění prostředků.
author: IEvangelist
ms.author: dapine
ms.date: 08/25/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 268cea7584040ad92e2da75e5e03112480cda93c
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053175"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="412f1-103">Implementace metody DisposeAsync</span><span class="sxs-lookup"><span data-stu-id="412f1-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="412f1-104"><xref:System.IAsyncDisposable?displayProperty=nameWithType>Rozhraní bylo zavedeno jako součást C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="412f1-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="412f1-105">Metodu implementujete <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> , pokud potřebujete provést čištění prostředků stejným způsobem jako při [implementaci metody Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="412f1-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="412f1-106">Jedna z klíčových rozdílů však je, že tato implementace umožňuje operace asynchronního vyčištění.</span><span class="sxs-lookup"><span data-stu-id="412f1-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="412f1-107"><xref:System.IAsyncDisposable.DisposeAsync>Vrátí hodnotu <xref:System.Threading.Tasks.ValueTask> , která představuje asynchronní operaci Dispose.</span><span class="sxs-lookup"><span data-stu-id="412f1-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="412f1-108">Je typický při implementaci <xref:System.IAsyncDisposable> rozhraní, které třídy implementuje také <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="412f1-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="412f1-109">Dobrým vzorem implementace <xref:System.IAsyncDisposable> rozhraní je připravit se buď na synchronní, nebo na asynchronní vyřazení.</span><span class="sxs-lookup"><span data-stu-id="412f1-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="412f1-110">Všechny doprovodné materiály k implementaci vzoru Dispose platí také pro asynchronní implementaci.</span><span class="sxs-lookup"><span data-stu-id="412f1-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="412f1-111">V tomto článku se předpokládá, že už jste obeznámení s tím, jak [implementovat metodu Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="412f1-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="412f1-112">DisposeAsync () a DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="412f1-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="412f1-113"><xref:System.IAsyncDisposable>Rozhraní deklaruje jedinou metodu bez parametrů, <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="412f1-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="412f1-114">Jakákoliv nezapečetěná třída by měla mít další `DisposeAsyncCore()` metodu, která také vrátí <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="412f1-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="412f1-115">`public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implementace, která nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="412f1-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="412f1-116">`protected virtual ValueTask DisposeAsyncCore()`Metoda, jejíž signatura je:</span><span class="sxs-lookup"><span data-stu-id="412f1-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="412f1-117">Metoda DisposeAsync ()</span><span class="sxs-lookup"><span data-stu-id="412f1-117">The DisposeAsync() method</span></span>

<span data-ttu-id="412f1-118">`public`Metoda bez parametrů `DisposeAsync()` je volána implicitně v `await using` příkazu a jejím účelem je uvolnit nespravované prostředky, provést obecné vyčištění a označit, že finalizační metoda, pokud existuje, není nutné spustit.</span><span class="sxs-lookup"><span data-stu-id="412f1-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="412f1-119">Uvolnění paměti přidružené ke spravovanému objektu je vždy doména [uvolňování paměti](index.md).</span><span class="sxs-lookup"><span data-stu-id="412f1-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="412f1-120">Z tohoto důvodu má standardní implementaci:</span><span class="sxs-lookup"><span data-stu-id="412f1-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of unmanaged resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="412f1-121">Jedním z hlavních rozdílů v asynchronním vzoru Dispose v porovnání se vzorem Dispose je, že volání <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` metody přetížení je zadáno `false` jako argument.</span><span class="sxs-lookup"><span data-stu-id="412f1-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="412f1-122">Při implementaci <xref:System.IDisposable.Dispose?displayProperty=nameWithType> metody se ale `true` místo toho předává.</span><span class="sxs-lookup"><span data-stu-id="412f1-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="412f1-123">To pomáhá zajistit funkční ekvivalenci se synchronním vzorem Dispose a dále zajistí, že se stále vyvolají cesty kódu finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="412f1-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="412f1-124">Jinými slovy, `DisposeAsyncCore()` Metoda vyřadí spravované prostředky asynchronně, takže je nechcete odstraňovat i synchronně.</span><span class="sxs-lookup"><span data-stu-id="412f1-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="412f1-125">Proto zavolejte `Dispose(false)` místo `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="412f1-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="412f1-126">Metoda DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="412f1-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="412f1-127">`DisposeAsyncCore()`Metoda je určena k provedení asynchronního vyčištění spravovaných prostředků nebo pro kaskádová volání `DisposeAsync()` .</span><span class="sxs-lookup"><span data-stu-id="412f1-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="412f1-128">Zapouzdřuje společné operace asynchronního čištění, pokud podtřídou dědí základní třídu, která je implementací <xref:System.IAsyncDisposable> .</span><span class="sxs-lookup"><span data-stu-id="412f1-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="412f1-129">`DisposeAsyncCore()`Metoda je `virtual` tak, že odvozené třídy mohou definovat další vyčištění v jejich přepsání.</span><span class="sxs-lookup"><span data-stu-id="412f1-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="412f1-130">Pokud implementace <xref:System.IAsyncDisposable> je `sealed` , `DisposeAsyncCore()` metoda není potřebná a asynchronní vyčištění lze provést přímo v <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="412f1-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="412f1-131">Implementace vzorce asynchronního Dispose</span><span class="sxs-lookup"><span data-stu-id="412f1-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="412f1-132">Všechny nezapečetěné třídy by měly být považovány za potenciální základní třídu, protože by mohly být děděny.</span><span class="sxs-lookup"><span data-stu-id="412f1-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="412f1-133">Pokud implementujete Model asynchronního Dispose pro jakoukoli potenciální základní třídu, je nutné zadat `protected virtual ValueTask DisposeAsyncCore()` metodu.</span><span class="sxs-lookup"><span data-stu-id="412f1-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="412f1-134">Zde je příklad implementace asynchronního vzoru Dispose, který používá <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="412f1-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="412f1-135">V předchozím příkladu se používá <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="412f1-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="412f1-136">Další informace o nástroji `System.Text.Json` najdete v tématu [Postup migrace z Newtonsoft.Jsna do System.Text.Jsna](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="412f1-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="412f1-137">Použití Async na jedno použití</span><span class="sxs-lookup"><span data-stu-id="412f1-137">Using async disposable</span></span>

<span data-ttu-id="412f1-138">Chcete-li správně spotřebovat objekt, který implementuje <xref:System.IAsyncDisposable> rozhraní, použijte [operátor await](../../csharp/language-reference/operators/await.md)a [using](../../csharp/language-reference/keywords/using-statement.md) klíčová slova společně.</span><span class="sxs-lookup"><span data-stu-id="412f1-138">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="412f1-139">Vezměte v úvahu následující příklad, kde `ExampleAsyncDisposable` je vytvořena instance třídy a poté zabalena do `await using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="412f1-139">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="412f1-140">Použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> metodu rozšíření <xref:System.IAsyncDisposable> rozhraní ke konfiguraci způsobu, jakým je pokračování úlohy zařazeno do původního kontextu nebo plánovače.</span><span class="sxs-lookup"><span data-stu-id="412f1-140">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="412f1-141">Další informace o najdete v `ConfigureAwait` tématu [ConfigureAwait – Nejčastější dotazy](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span><span class="sxs-lookup"><span data-stu-id="412f1-141">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="412f1-142">V situacích, kdy použití nástroje `ConfigureAwait` není potřeba, je `await using` možné příkaz zjednodušit takto:</span><span class="sxs-lookup"><span data-stu-id="412f1-142">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="412f1-143">Kromě toho je možné je zapsat pro použití implicitního oboru [deklarace using](../../csharp/whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="412f1-143">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="412f1-144">Skládané pomocí</span><span class="sxs-lookup"><span data-stu-id="412f1-144">Stacked usings</span></span>

<span data-ttu-id="412f1-145">V situacích, kdy vytvoříte a použijete více objektů, které implementují <xref:System.IAsyncDisposable> , je možné, že `using` výpisy zásobníku v podmínkách errant můžou zabránit volání <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="412f1-145">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="412f1-146">Aby se zabránilo potenciálním obavám, měli byste se vyhnout vrstvení a místo toho postupovat podle tohoto ukázkového vzoru:</span><span class="sxs-lookup"><span data-stu-id="412f1-146">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="412f1-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="412f1-147">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
