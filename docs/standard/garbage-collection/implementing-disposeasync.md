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
# <a name="implement-a-disposeasync-method"></a>Implementace metody DisposeAsync

<xref:System.IAsyncDisposable?displayProperty=nameWithType>Rozhraní bylo zavedeno jako součást C# 8,0. Metodu implementujete <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> , pokud potřebujete provést čištění prostředků stejným způsobem jako při [implementaci metody Dispose](implementing-dispose.md). Jedna z klíčových rozdílů však je, že tato implementace umožňuje operace asynchronního vyčištění. <xref:System.IAsyncDisposable.DisposeAsync>Vrátí hodnotu <xref:System.Threading.Tasks.ValueTask> , která představuje asynchronní operaci Dispose.

Je typický při implementaci <xref:System.IAsyncDisposable> rozhraní, které třídy implementuje také <xref:System.IDisposable> rozhraní. Dobrým vzorem implementace <xref:System.IAsyncDisposable> rozhraní je připravit se buď na synchronní, nebo na asynchronní vyřazení. Všechny doprovodné materiály k implementaci vzoru Dispose platí také pro asynchronní implementaci. V tomto článku se předpokládá, že už jste obeznámení s tím, jak [implementovat metodu Dispose](implementing-dispose.md).

## <a name="disposeasync-and-disposeasynccore"></a>DisposeAsync () a DisposeAsyncCore ()

<xref:System.IAsyncDisposable>Rozhraní deklaruje jedinou metodu bez parametrů, <xref:System.IAsyncDisposable.DisposeAsync> . Jakákoliv nezapečetěná třída by měla mít další `DisposeAsyncCore()` metodu, která také vrátí <xref:System.Threading.Tasks.ValueTask> .

- `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> Implementace, která nemá žádné parametry.
- `protected virtual ValueTask DisposeAsyncCore()`Metoda, jejíž signatura je:

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a>Metoda DisposeAsync ()

`public`Metoda bez parametrů `DisposeAsync()` je volána implicitně v `await using` příkazu a jejím účelem je uvolnit nespravované prostředky, provést obecné vyčištění a označit, že finalizační metoda, pokud existuje, není nutné spustit. Uvolnění paměti přidružené ke spravovanému objektu je vždy doména [uvolňování paměti](index.md). Z tohoto důvodu má standardní implementaci:

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
> Jedním z hlavních rozdílů v asynchronním vzoru Dispose v porovnání se vzorem Dispose je, že volání <xref:System.IAsyncDisposable.DisposeAsync> `Dispose(bool)` metody přetížení je zadáno `false` jako argument. Při implementaci <xref:System.IDisposable.Dispose?displayProperty=nameWithType> metody se ale `true` místo toho předává. To pomáhá zajistit funkční ekvivalenci se synchronním vzorem Dispose a dále zajistí, že se stále vyvolají cesty kódu finalizační metody. Jinými slovy, `DisposeAsyncCore()` Metoda vyřadí spravované prostředky asynchronně, takže je nechcete odstraňovat i synchronně. Proto zavolejte `Dispose(false)` místo `Dispose(true)` .

### <a name="the-disposeasynccore-method"></a>Metoda DisposeAsyncCore ()

`DisposeAsyncCore()`Metoda je určena k provedení asynchronního vyčištění spravovaných prostředků nebo pro kaskádová volání `DisposeAsync()` . Zapouzdřuje společné operace asynchronního čištění, pokud podtřídou dědí základní třídu, která je implementací <xref:System.IAsyncDisposable> . `DisposeAsyncCore()`Metoda je `virtual` tak, že odvozené třídy mohou definovat další vyčištění v jejich přepsání.

> [!TIP]
> Pokud implementace <xref:System.IAsyncDisposable> je `sealed` , `DisposeAsyncCore()` metoda není potřebná a asynchronní vyčištění lze provést přímo v <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> metodě.

## <a name="implement-the-async-dispose-pattern"></a>Implementace vzorce asynchronního Dispose

Všechny nezapečetěné třídy by měly být považovány za potenciální základní třídu, protože by mohly být děděny. Pokud implementujete Model asynchronního Dispose pro jakoukoli potenciální základní třídu, je nutné zadat `protected virtual ValueTask DisposeAsyncCore()` metodu. Zde je příklad implementace asynchronního vzoru Dispose, který používá <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

V předchozím příkladu se používá <xref:System.Text.Json.Utf8JsonWriter> . Další informace o nástroji `System.Text.Json` najdete v tématu [Postup migrace z Newtonsoft.Jsna do System.Text.Jsna](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).

## <a name="using-async-disposable"></a>Použití Async na jedno použití

Chcete-li správně spotřebovat objekt, který implementuje <xref:System.IAsyncDisposable> rozhraní, použijte [operátor await](../../csharp/language-reference/operators/await.md)a [using](../../csharp/language-reference/keywords/using-statement.md) klíčová slova společně. Vezměte v úvahu následující příklad, kde `ExampleAsyncDisposable` je vytvořena instance třídy a poté zabalena do `await using` příkazu.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> Použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> metodu rozšíření <xref:System.IAsyncDisposable> rozhraní ke konfiguraci způsobu, jakým je pokračování úlohy zařazeno do původního kontextu nebo plánovače. Další informace o najdete v `ConfigureAwait` tématu [ConfigureAwait – Nejčastější dotazy](https://devblogs.microsoft.com/dotnet/configureawait-faq/).

V situacích, kdy použití nástroje `ConfigureAwait` není potřeba, je `await using` možné příkaz zjednodušit takto:

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

Kromě toho je možné je zapsat pro použití implicitního oboru [deklarace using](../../csharp/whats-new/csharp-8.md#using-declarations).

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a>Skládané pomocí

V situacích, kdy vytvoříte a použijete více objektů, které implementují <xref:System.IAsyncDisposable> , je možné, že `using` výpisy zásobníku v podmínkách errant můžou zabránit volání <xref:System.IAsyncDisposable.DisposeAsync> . Aby se zabránilo potenciálním obavám, měli byste se vyhnout vrstvení a místo toho postupovat podle tohoto ukázkového vzoru:

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a>Viz také

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
