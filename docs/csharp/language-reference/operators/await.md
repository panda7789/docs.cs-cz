---
title: await – operátor – Referenční dokumentace jazyka C#
ms.date: 07/13/2020
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: f4b0ef501a30d3dffc1346c805ce0161ca4cac90
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555432"
---
# <a name="await-operator-c-reference"></a>await – operátor (Referenční dokumentace jazyka C#)

`await`Operátor pozastavuje vyhodnocení ohraničující [asynchronní](../keywords/async.md) metody, dokud se nedokončí asynchronní operace reprezentované jeho operandem. Po dokončení asynchronní operace `await` vrátí operátor výsledek operace, pokud existuje. Při `await` použití operátoru na operand, který představuje již dokončenou operaci, vrátí výsledek operace hned bez přerušení ohraničující metody. `await`Operátor neblokuje vlákno, které vyhodnocuje asynchronní metodu. Když `await` operátor pozastaví ohraničující asynchronní metodu, ovládací prvek se vrátí volajícímu metody.

V následujícím příkladu <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> Metoda vrátí `Task<byte[]>` instanci, která představuje asynchronní operaci, která při dokončení vytvoří pole bajtů. Dokud se operace nedokončí, `await` operátor tuto metodu pozastaví `DownloadDocsMainPageAsync` . Při `DownloadDocsMainPageAsync` pozastavení je ovládací prvek vrácen do `Main` metody, která je volajícím `DownloadDocsMainPageAsync` . `Main`Metoda se spustí, dokud nepotřebuje výsledek asynchronní operace prováděné `DownloadDocsMainPageAsync` metodou. Když <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> získá všechny bajty, `DownloadDocsMainPageAsync` vyhodnotí se zbytek metody. Poté `Main` je vyhodnocena zbývající část metody.

[!code-csharp[await example](snippets/AwaitOperator.cs)]

Předchozí příklad používá [asynchronní `Main` metodu](../../programming-guide/main-and-command-args/index.md), která je možná od verze C# 7,1. Další informace naleznete v oddílu [await v části Metoda Main](#await-operator-in-the-main-method) .

> [!NOTE]
> Úvod do asynchronního programování naleznete v tématu [asynchronní programování s modifikátorem Async a operátoru await](../../programming-guide/concepts/async/index.md). Asynchronní programování pomocí `async` a `await` sleduje [asynchronní vzor založený na úlohách](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

Operátor lze použít `await` pouze v metodě, [lambda výrazu](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo [anonymní metodě](delegate-operator.md) , která je upravena pomocí klíčového slova [Async](../keywords/async.md) . V rámci asynchronní metody nemůžete použít `await` operátor v těle synchronní funkce uvnitř bloku [příkazu Lock](../keywords/lock-statement.md)a v [nezabezpečeném](../keywords/unsafe.md) kontextu.

Operandem `await` operátoru je obvykle jeden z následujících typů .NET: <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.ValueTask> nebo <xref:System.Threading.Tasks.ValueTask%601> . Nicméně libovolný výraz await může být operandem `await` operátoru. Další informace naleznete v části [await Expressions](~/_csharplang/spec/expressions.md#awaitable-expressions) (očekávané výrazy) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Typ výrazu je, `await t` `TResult` Pokud je typ výrazu `t` <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.ValueTask%601> . Pokud je typ typu `t` <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.ValueTask> , je typ `await t` `void` . V obou případech, pokud `t` vyvolá výjimku, znovu `await t` vyvolá výjimku. Další informace o zpracování výjimek naleznete v části [výjimky v asynchronních metodách v](../keywords/try-catch.md#exceptions-in-async-methods) článku [příkazu try-catch](../keywords/try-catch.md) .

`async` `await` Klíčová slova a jsou k dispozici v C# 5 a novější.

## <a name="asynchronous-streams-and-disposables"></a>Asynchronní datové proudy a jednorázové

Počínaje jazykem C# 8,0 můžete pracovat s asynchronními datovými proudy a jednorázovými možnostmi.

Pomocí příkazu můžete `await foreach` využívat asynchronní datový proud dat. Další informace naleznete v článku [ `foreach` prohlášení](../keywords/foreach-in.md) a v části věnované [asynchronním proudům](../../whats-new/csharp-8.md#asynchronous-streams) [v článku co je nového v jazyce C# 8,0](../../whats-new/csharp-8.md) .

Použijete `await using` příkaz pro práci s asynchronně vydaným objektem, to znamená objekt typu, který implementuje <xref:System.IAsyncDisposable> rozhraní. Další informace naleznete v části [použití asynchronní](../../../standard/garbage-collection/implementing-disposeasync.md#using-async-disposable) na použití v článku [implementace metody DisposeAsync](../../../standard/garbage-collection/implementing-disposeasync.md) .

## <a name="await-operator-in-the-main-method"></a>await – operátor v metodě Main

Počínaje jazykem C# 7,1, [ `Main` Metoda](../../programming-guide/main-and-command-args/index.md), která je vstupním bodem aplikace, může vracet `Task` nebo, aby byla asynchronní, aby bylo `Task<int>` možné použít `await` operátor v těle. V dřívějších verzích jazyka C# pro zajištění, že `Main` Metoda čeká na dokončení asynchronní operace, lze načíst hodnotu <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> vlastnosti <xref:System.Threading.Tasks.Task%601> instance, která je vrácena odpovídající asynchronní metodou. Pro asynchronní operace, které neposkytují hodnotu, můžete zavolat <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodu. Informace o tom, jak vybrat jazykovou verzi, najdete v tématu [Správa verzí jazyka C#](../configure-language-version.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [await Expressions](~/_csharplang/spec/expressions.md#await-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [async](../keywords/async.md)
- [Model asynchronního programování úloh](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Asynchronní programování](../../async.md)
- [Asynchronní v hloubkě](../../../standard/async-in-depth.md)
- [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Kurz: generování a využívání asynchronních datových proudů pomocí C# 8,0 a .NET Core 3,0](../../tutorials/generate-consume-asynchronous-stream.md)
