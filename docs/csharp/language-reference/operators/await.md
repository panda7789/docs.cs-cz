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
ms.openlocfilehash: c2172f651dd106825680de3195e26f032225a9ab
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169390"
---
# <a name="await-operator-c-reference"></a>await – operátorC# (Referenční dokumentace)

Operátor pozastavuje vyhodnocení ohraničující asynchronní metody, dokud se nedokončí asynchronní operace reprezentované jeho operandem. [](../keywords/async.md) `await` Po dokončení `await` asynchronní operace vrátí operátor výsledek operace, pokud existuje. Při použití `await` operátoru na operand, který představuje již dokončenou operaci, vrátí výsledek operace hned bez přerušení ohraničující metody. `await` Operátor neblokuje vlákno, které vyhodnocuje asynchronní metodu. `await` Když operátor pozastaví ohraničující metodu, ovládací prvek se vrátí volajícímu metody.

V následujícím příkladu <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda `Task<byte[]>` vrátí instanci, která představuje asynchronní operaci, která při dokončení vytvoří pole bajtů. Dokud se operace nedokončí, `await` operátor tuto `DownloadDocsMainPageAsync` metodu pozastaví. Při `DownloadDocsMainPageAsync` pozastavení je ovládací prvek vrácen `Main` do metody, `DownloadDocsMainPageAsync`která je volajícím. Metoda `Main` se spustí, dokud nepotřebuje výsledek asynchronní operace prováděné `DownloadDocsMainPageAsync` metodou. Když <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> získá všechny bajty, vyhodnotí se zbytek `DownloadDocsMainPageAsync` metody. Poté je vyhodnocena zbývající část `Main` metody.

[!code-csharp[await example](~/samples/csharp/language-reference/operators/AwaitOperator.cs)]

Předchozí příklad používá [asynchronní `Main` metodu](../../programming-guide/main-and-command-args/index.md), která je možné začít od C# 7,1. Další informace naleznete v oddílu [await v části Metoda Main](#await-operator-in-the-main-method) .

> [!NOTE]
> Úvod do asynchronního programování naleznete v tématu [asynchronní programování s modifikátorem Async a operátoru await](../../programming-guide/concepts/async/index.md). Asynchronní programování pomocí `async` a `await` sleduje [asynchronní vzor založený na úlohách](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

`await` Operátor lze použít pouze v metodě, [lambda výrazu](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo [anonymní metodě](delegate-operator.md) , která je upravena pomocí klíčového slova [Async](../keywords/async.md) . V rámci asynchronní metody nelze použít `await` operátor v těle synchronní funkce uvnitř bloku [příkazu Lock](../keywords/lock-statement.md)a v nezabezpečeném kontextu. [](../keywords/unsafe.md)
  
Operandem `await` operátoru je obvykle jeden z následujících typů .NET: <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask>nebo <xref:System.Threading.Tasks.ValueTask%601>. Nicméně libovolný výraz await může být operandem `await` operátoru. Další informace naleznete v oddílu [await Expressions](~/_csharplang/spec/expressions.md#awaitable-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

Typ výrazu `await t` je `TResult` , pokud je `t` <xref:System.Threading.Tasks.Task%601> typ výrazu nebo <xref:System.Threading.Tasks.ValueTask%601>. Pokud je typ typu `t` <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.ValueTask>nebo,je typ `void`. `await t` V obou případech, pokud `t` vyvolá výjimku, `await t` znovu vyvolá výjimku. Další informace o zpracování výjimek naleznete v části [výjimky v asynchronních metodách v](../keywords/try-catch.md#exceptions-in-async-methods) článku [příkazu try-catch](../keywords/try-catch.md) .

Klíčová `await` slova C# a jsou k dispozici od 5. `async`

## <a name="await-operator-in-the-main-method"></a>await – operátor v metodě Main

Počínaje C# 7,1, [ `Main` metoda](../../programming-guide/main-and-command-args/index.md), která je vstupním bodem aplikace, může vracet `Task` nebo `Task<int>`, aby byla asynchronní, aby bylo možné použít `await` operátor v těle. V dřívějších C# verzích, abyste zajistili, `Main` že metoda čeká na dokončení asynchronní operace, můžete načíst hodnotu <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> vlastnosti <xref:System.Threading.Tasks.Task%601> instance, která je vrácena odpovídajícím asynchronním Metoda. Pro asynchronní operace, které neposkytují hodnotu, můžete zavolat <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> metodu. Informace o tom, jak vybrat jazykovou verzi, najdete v tématu [ C# výběr jazykové verze](../configure-language-version.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v oddílu [await Expressions](~/_csharplang/spec/expressions.md#await-expressions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [async](../keywords/async.md)
- [Asynchronní programování s modifikátorem Async a operátoru await](../../programming-guide/concepts/async/index.md)
- [Asynchronní programovací model úlohy](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Asynchronní programování](../../async.md)
- [Asynchronní vzor založený na úlohách](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)
- [Asynchronní v hloubkě](../../../standard/async-in-depth.md)
- [Návod: přístup k webu pomocí modifikátoru Async a operátoru await](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
