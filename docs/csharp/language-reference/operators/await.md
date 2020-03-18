---
title: operátor await - odkaz Jazyka C#
ms.date: 11/08/2019
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: 9f541ae9c26eb12acdcf9a8c59bab98c4772c3b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173442"
---
# <a name="await-operator-c-reference"></a>await operátor (c# odkaz)

Operátor `await` pozastaví vyhodnocení ohraničující [asynchronní](../keywords/async.md) metody, dokud nebude dokončena asynchronní operace reprezentovaná jeho operandem. Po dokončení asynchronní operace `await` operátor vrátí výsledek operace, pokud existuje. Pokud `await` je operátor použit na operand, který představuje již dokončenou operaci, vrátí výsledek operace okamžitě bez pozastavení ohraničující metody. Operátor `await` neblokuje vlákno, které vyhodnocuje asynchronní metodu. Když `await` operátor pozastaví ohraničující asynchronní metodu, ovládací prvek se vrátí volajícímu metody.

V následujícím příkladu <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> metoda `Task<byte[]>` vrátí instanci, která představuje asynchronní operaci, která po dokončení vytvoří bajtové pole. Dokud operace nedokončí, `await` operátor pozastaví metodu. `DownloadDocsMainPageAsync` Když `DownloadDocsMainPageAsync` se pozastaví, ovládací `Main` prvek je vrácena `DownloadDocsMainPageAsync`na metodu, která je volající . Metoda `Main` se spustí, dokud nepotřebuje výsledek asynchronní operace `DownloadDocsMainPageAsync` prováděné metodou. Když <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> získá všechny bajty, zbytek `DownloadDocsMainPageAsync` metody je vyhodnocena. Poté se vyhodnotí `Main` zbytek metody.

[!code-csharp[await example](snippets/AwaitOperator.cs)]

Předchozí příklad používá [asynchronní `Main` metodu](../../programming-guide/main-and-command-args/index.md), která je možná začínající C# 7.1. Další informace naleznete v [operátoru await v](#await-operator-in-the-main-method) části Hlavní metoda.

> [!NOTE]
> Úvod do asynchronního programování naleznete [v tématu Asynchronní programování s asynchronní a await](../../programming-guide/concepts/async/index.md). Asynchronní programování `async` s `await` [asynchronním vzorem založeným na úlohách](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).

`await` Operátor můžete použít pouze v metodě, [výrazu lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)nebo [anonymní metodě,](delegate-operator.md) která je upravena klíčovým slovem [async.](../keywords/async.md) V rámci asynchronní metody nelze `await` použít operátor v těle synchronní funkce, uvnitř bloku [příkazu lock](../keywords/lock-statement.md)a v [nebezpečném](../keywords/unsafe.md) kontextu.

Operand operátoru `await` je obvykle jednoho z následujících <xref:System.Threading.Tasks.Task>typů <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask>.NET: , , , nebo <xref:System.Threading.Tasks.ValueTask%601>. Však všechny počkejte-li výraz může `await` být operand operátoru. Další informace naleznete v části [Počkejdné výrazy](~/_csharplang/spec/expressions.md#awaitable-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

Počínaje C# 8.0, můžete `await foreach` použít příkaz využívat asynchronní datový proud dat. Další informace naleznete [ `foreach` ](../keywords/foreach-in.md) v článku prohlášení a [asynchronní datové proudy](../../whats-new/csharp-8.md#asynchronous-streams) části [Co je nového v článku C# 8.0.](../../whats-new/csharp-8.md)

Typ výrazu `await t` `TResult` je, pokud `t` je <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.ValueTask%601>typ výrazu nebo . Pokud `t` je typ <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.ValueTask>nebo , `await t` typ `void`je . V obou případech `t` pokud vyvolá `await t` výjimku, znovu vyvolá výjimku. Další informace o zpracování výjimek naleznete v části [Výjimky v asynchronních metodách](../keywords/try-catch.md#exceptions-in-async-methods) v článku [příkazu try-catch.](../keywords/try-catch.md)

Klíčová `async` `await` slova a jsou k dispozici v C# 5 a novější.

## <a name="await-operator-in-the-main-method"></a>await operátor v Main metoda

Počínaje C# 7.1, [ `Main` metoda](../../programming-guide/main-and-command-args/index.md), která je vstupní bod `Task<int>`aplikace, může vrátit `await` `Task` nebo , povolení, aby byla asynchronní, takže můžete použít operátor v jeho těle. V dřívějších verzích jazyka C#, aby se zajistilo, že `Main` metoda čeká na dokončení <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> asynchronní <xref:System.Threading.Tasks.Task%601> operace, můžete načíst hodnotu vlastnosti instance, která je vrácena odpovídající asynchronní metodou. Pro asynchronní operace, které nevytvářejí hodnotu, <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> můžete volat metodu. Informace o výběru jazykové verze naleznete v [tématu C# language versioning](../configure-language-version.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Await výrazy](~/_csharplang/spec/expressions.md#await-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [async](../keywords/async.md)
- [Model asynchronního programování úloh](../../programming-guide/concepts/async/task-asynchronous-programming-model.md)
- [Asynchronní programování](../../async.md)
- [Asynchronní do hloubky](../../../standard/async-in-depth.md)
- [Návod: Přístup k webu pomocí asynchronní a čekat](../../programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Kurz: Generování a využívání asynchronních datových proudů pomocí c# 8.0 a .NET Core 3.0](../../tutorials/generate-consume-asynchronous-stream.md)
