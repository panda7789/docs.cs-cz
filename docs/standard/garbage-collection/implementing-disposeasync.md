---
title: Implementace metody DisposeAsync
description: ''
author: IEvangelist
ms.author: dapine
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 31c4cc9136862551e02fae030e38ebd6c2916a38
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100922"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="e1349-102">Implementace metody DisposeAsync</span><span class="sxs-lookup"><span data-stu-id="e1349-102">Implement a DisposeAsync method</span></span>

<span data-ttu-id="e1349-103"><xref:System.IAsyncDisposable?displayProperty=nameWithType>Rozhraní bylo zavedeno jako součást C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="e1349-103">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="e1349-104">Metodu implementujete <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> , pokud potřebujete provést čištění prostředků stejným způsobem jako při [implementaci metody Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="e1349-104">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="e1349-105">Jedna z klíčových rozdílů však je, že tato implementace umožňuje operace asynchronního vyčištění.</span><span class="sxs-lookup"><span data-stu-id="e1349-105">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="e1349-106"><xref:System.IAsyncDisposable.DisposeAsync>Vrátí hodnotu <xref:System.Threading.Tasks.ValueTask> , která představuje asynchronní operaci Dispose.</span><span class="sxs-lookup"><span data-stu-id="e1349-106">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="e1349-107">To je obvyklé, že při implementaci <xref:System.IAsyncDisposable> rozhraní budou třídy také implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e1349-107">It is typical that when implementing the <xref:System.IAsyncDisposable> interface, classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="e1349-108">Dobrým vzorem implementace <xref:System.IAsyncDisposable> rozhraní je připravit se buď na synchronní, nebo na asynchronní vyřazení.</span><span class="sxs-lookup"><span data-stu-id="e1349-108">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="e1349-109">Všechny pokyny pro implementaci vzoru Dispose se vztahují na asynchronní implementaci.</span><span class="sxs-lookup"><span data-stu-id="e1349-109">All of the guidance for implementing the dispose pattern applies to the asynchronous implementation.</span></span> <span data-ttu-id="e1349-110">V tomto článku se předpokládá, že už jste obeznámení s tím, jak [implementovat metodu Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="e1349-110">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="e1349-111">DisposeAsync () a DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="e1349-111">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="e1349-112"><xref:System.IAsyncDisposable>Rozhraní deklaruje jedinou metodu bez parametrů, <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="e1349-112">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="e1349-113">Jakákoliv nezapečetěná třída by měla mít další `DisposeAsyncCore()` metodu, která také vrátí <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="e1349-113">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="e1349-114">`public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implementace, která nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="e1349-114">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="e1349-115">`protected virtual ValueTask DisposeAsyncCore()`Metoda, jejíž signatura je:</span><span class="sxs-lookup"><span data-stu-id="e1349-115">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

<span data-ttu-id="e1349-116">`DisposeAsyncCore()`Metoda je `virtual` tak, že odvozené třídy mohou definovat další vyčištění v jejich přepsání.</span><span class="sxs-lookup"><span data-stu-id="e1349-116">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

### <a name="the-disposeasync-method"></a><span data-ttu-id="e1349-117">Metoda DisposeAsync ()</span><span class="sxs-lookup"><span data-stu-id="e1349-117">The DisposeAsync() method</span></span>

<span data-ttu-id="e1349-118">`public`Metoda bez parametrů `DisposeAsync()` je volána implicitně v `await using` příkazu a jejím účelem je uvolnit nespravované prostředky, provést obecné vyčištění a označit, že finalizační metoda, pokud existuje, nemusí podepisovat spustit.</span><span class="sxs-lookup"><span data-stu-id="e1349-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, needn't run.</span></span> <span data-ttu-id="e1349-119">Uvolnění paměti přidružené ke spravovanému objektu je vždy doména [uvolňování paměti](index.md).</span><span class="sxs-lookup"><span data-stu-id="e1349-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="e1349-120">Z tohoto důvodu má standardní implementaci:</span><span class="sxs-lookup"><span data-stu-id="e1349-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of managed resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="e1349-121">Jedním z hlavních rozdílů v asynchronním vzoru Dispose v porovnání se vzorem Dispose je, že volání <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` metody přetížení je zadáno `false` jako argument.</span><span class="sxs-lookup"><span data-stu-id="e1349-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="e1349-122">Při implementaci <xref:System.IDisposable.Dispose?displayProperty=nameWithType> metody se ale `true` místo toho předává.</span><span class="sxs-lookup"><span data-stu-id="e1349-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="e1349-123">To pomáhá zajistit funkční ekvivalenci se synchronním vzorem Dispose a dále zajistí, že se stále vyvolají cesty kódu finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="e1349-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="e1349-124">Jinými slovy, `DisposeAsyncCore()` Metoda vyřadí spravované prostředky asynchronně, takže je nechcete odstraňovat i synchronně.</span><span class="sxs-lookup"><span data-stu-id="e1349-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="e1349-125">Proto zavolejte `Dispose(false)` místo `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="e1349-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="e1349-126">Implementace vzorce asynchronního Dispose</span><span class="sxs-lookup"><span data-stu-id="e1349-126">Implement the async dispose pattern</span></span>

<span data-ttu-id="e1349-127">Všechny nezapečetěné třídy by měly být považovány za potenciální základní třídu, protože by mohly být děděny.</span><span class="sxs-lookup"><span data-stu-id="e1349-127">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="e1349-128">Pokud implementujete Model asynchronního Dispose pro jakoukoli potenciální základní třídu, je nutné zadat `protected virtual ValueTask DisposeAsyncCore()` metodu.</span><span class="sxs-lookup"><span data-stu-id="e1349-128">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="e1349-129">Zde je příklad implementace asynchronního vzoru Dispose, který používá <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e1349-129">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="e1349-130">Předchozí příklad používá, <xref:System.Text.Json.Utf8JsonWriter> Další informace `System.Text.Json` naleznete v tématu, [migrace z Newtonsoft.Jsna do System.Text.Jsna](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="e1349-130">The previous example used the <xref:System.Text.Json.Utf8JsonWriter>, for more information on `System.Text.Json`, see, [migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="e1349-131">Použití Async na jedno použití</span><span class="sxs-lookup"><span data-stu-id="e1349-131">Using async disposable</span></span>

<span data-ttu-id="e1349-132">Chcete-li správně spotřebovat objekt, který implementuje <xref:System.IAsyncDisposable> rozhraní, použijte [operátor await](../../csharp/language-reference/operators/await.md)a [using](../../csharp/language-reference/keywords/using.md) klíčová slova společně.</span><span class="sxs-lookup"><span data-stu-id="e1349-132">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using.md) keywords together.</span></span> <span data-ttu-id="e1349-133">Vezměte v úvahu následující příklad, kde `ExampleAsyncDisposable` je vytvořena instance třídy a poté zabalena do `await using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="e1349-133">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated, then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="e1349-134">Použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> metodu rozšíření <xref:System.IAsyncDisposable> rozhraní ke konfiguraci způsobu, jakým je pokračování úlohy zařazeno do původního kontextu nebo plánovače.</span><span class="sxs-lookup"><span data-stu-id="e1349-134">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="e1349-135">Další informace o najdete v `ConfigureAwait` tématu [ConfigureAwait – Nejčastější dotazy](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span><span class="sxs-lookup"><span data-stu-id="e1349-135">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="e1349-136">V situacích, kdy použití nástroje `ConfigureAwait` není potřeba, je `await using` možné příkaz zjednodušit takto:</span><span class="sxs-lookup"><span data-stu-id="e1349-136">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="e1349-137">Kromě toho je možné je zapsat pro použití implicitního oboru [deklarace using](../../csharp/whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="e1349-137">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="e1349-138">Skládané pomocí</span><span class="sxs-lookup"><span data-stu-id="e1349-138">Stacked usings</span></span>

<span data-ttu-id="e1349-139">V situacích, kdy vytvoříte a použijete více objektů, které implementují <xref:System.IAsyncDisposable> , je možné, že `using` výpisy zásobníku v podmínkách errant můžou zabránit volání <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="e1349-139">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="e1349-140">Aby se zabránilo potenciálním obavám, měli byste se vyhnout vrstvení a místo toho postupovat podle tohoto ukázkového vzoru:</span><span class="sxs-lookup"><span data-stu-id="e1349-140">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="e1349-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1349-141">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
