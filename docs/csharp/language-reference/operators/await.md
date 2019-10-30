---
title: await – operátor C# – referenční informace
ms.custom: seodec18
ms.date: 08/30/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 5ed9d467bcbfa37a9809a530d11b3692fd2b984e
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036335"
---
# <a name="await-operator-c-reference"></a>await – operátorC# (Referenční dokumentace)

Operátor `await` pozastaví vyhodnocení ohraničující [asynchronní](../keywords/async.md) metody, dokud se nedokončí asynchronní operace reprezentované jeho operandem. Po dokončení asynchronní operace vrátí operátor `await` výsledek operace, pokud existuje. Při použití operátoru `await` na operand, který představuje již dokončenou operaci, vrátí výsledek operace hned bez přerušení ohraničující metody. Operátor `await` neblokuje vlákno, které vyhodnocuje asynchronní metodu. Když operátor `await` pozastaví ohraničující asynchronní metodu, ovládací prvek se vrátí volajícímu metody.

V následujícím příkladu metoda <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> vrátí instanci `Task<byte[]>`, která představuje asynchronní operaci, která při dokončení vytvoří bajtové pole. Dokud se operace nedokončí, operátor `await` pozastaví metodu `DownloadDocsMainPageAsync`. Když se `DownloadDocsMainPageAsync` pozastaví, vrátí se ovládací prvek do metody `Main`, která je volajícím `DownloadDocsMainPageAsync`. Metoda `Main` se spustí, dokud nepotřebuje výsledek asynchronní operace prováděné metodou `DownloadDocsMainPageAsync`. Když <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> získá všechny bajty, vyhodnotí se zbytek metody `DownloadDocsMainPageAsync`. Potom je vyhodnocena zbývající `Main` metoda.

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

Předchozí příklad používá [asynchronní metodu `Main`](../../programming-guide/main-and-command-args/index.md), která je možná od C# 7,1. Další informace naleznete v oddílu [await v části Metoda Main](#await-operator-in-the-main-method) .

> [!NOTE]
> Úvod do asynchronního programování naleznete v tématu [asynchronní programování s modifikátorem Async a operátoru await](../../programming-guide/concepts/async/index.md). Asynchronní programování pomocí `async` a `await` sleduje [asynchronní vzor založený na úlohách](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

Operátor `await` lze použít pouze v metodě, [lambda výrazu](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo [anonymní metodě](delegate-operator.md) , která je upravena pomocí klíčového slova [Async](../keywords/async.md) . V rámci asynchronní metody nelze použít operátor `await` v těle synchronní funkce uvnitř bloku [příkazu Lock](../keywords/lock-statement.md)a v [nebezpečném](../keywords/unsafe.md) kontextu.

Operand operátoru `await` je obvykle jeden z následujících typů .NET: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>nebo <xref:System.Threading.Tasks.ValueTask%601>. Nicméně libovolný výraz, který lze očekávat, může být operandem operátoru `await`. Další informace naleznete v oddílu [await Expressions](~/_csharplang/spec/expressions.md#awaitable-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

Typ výrazu `await t` je `TResult`, pokud je typ `t` výrazu <xref:System.Threading.Tasks.Task%601> nebo <xref:System.Threading.Tasks.ValueTask%601>. Pokud je typ `t` <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.ValueTask>, typ `await t` je `void`. V obou případech, pokud `t` vyvolá výjimku, `await t` znovu vyvolá výjimku. Další informace o zpracování výjimek naleznete v části [výjimky v asynchronních metodách v](../keywords/try-catch.md#exceptions-in-async-methods) článku [příkazu try-catch](../keywords/try-catch.md) .

Klíčová slova `async` a `await` jsou k C# dispozici v 5 a novějších verzích.

## <a name="await-operator-in-the-main-method"></a>await – operátor v metodě Main

Počínaje C# 7,1 [`Main` metoda](../../programming-guide/main-and-command-args/index.md), která je vstupním bodem aplikace, může vracet`Task`nebo`Task<int>`, což umožňuje, aby byla asynchronní, takže můžete použít operátor`await`ve svém těle. V dřívějších C# verzích, abyste zajistili, že`Main`metoda čeká na dokončení asynchronní operace, můžete načíst hodnotu vlastnosti<xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType>instance<xref:System.Threading.Tasks.Task%601>, která je vrácena odpovídající asynchronní metodou. Pro asynchronní operace, které neposkytují hodnotu, můžete zavolat metodu <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>. Informace o tom, jak vybrat jazykovou verzi, najdete v tématu [ C# jazyková verze](../configure-language-version.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [await Expressions](~/_csharplang/spec/expressions.md#await-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [async](../keywords/async.md)
- [Asynchronní programovací model úlohy](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Asynchronní programování](../../async.md)
- [Asynchronní v hloubkě](../../../standard/async-in-depth.md)
- [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
