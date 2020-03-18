---
title: Příkaz C# foreach
ms.date: 05/17/2019
f1_keywords:
- foreach
- foreach_CSharpKeyword
helpviewer_keywords:
- foreach keyword [C#]
- foreach statement [C#]
- in keyword [C#]
ms.assetid: 5a9c5ddc-5fd3-457a-9bb6-9abffcd874ec
ms.openlocfilehash: dbe4f4e95c2b99f1be47885e39d51db81ba3a97d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173702"
---
# <a name="foreach-in-c-reference"></a>foreach, v (C# odkaz)

Příkaz `foreach` provede příkaz nebo blok příkazů pro každý prvek v instanci <xref:System.Collections.IEnumerable?displayProperty=nameWithType> typu, který implementuje rozhraní nebo. <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Příkaz `foreach` není omezen na tyto typy a lze použít na instanci libovolného typu, který splňuje následující podmínky:

- má metodu `GetEnumerator` public parameterless, jejíž návratový typ je buď třída, struktura nebo typ rozhraní,
- návratový typ `GetEnumerator` metody má `Current` public property a `MoveNext` public parameterless <xref:System.Boolean>metodu, jejíž návratový typ je .

Počínaje C# 7.3, `Current` pokud vlastnost čítače vrátí referenční`ref T` [vrácenou hodnotu](ref.md#reference-return-values) (kde `T` je typ prvku kolekce), `ref` `ref readonly` můžete deklarovat itidati proměnnou s modifikátorem nebo.

Počínaje C# 8.0, `await` operátor může být `foreach` použita na příkaz <xref:System.Collections.Generic.IAsyncEnumerable%601> při typ kolekce implementuje rozhraní. Každá iterace smyčky může být pozastavena, zatímco další prvek je načten asynchronně. Ve výchozím nastavení jsou prvky datového proudu zpracovány v zachyceném kontextu. Pokud chcete zakázat zachycení kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření. Další informace o kontextech synchronizace a zachycení aktuálního kontextu naleznete v článku o [využití asynchronního vzoru založeného na úlohách](../../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).

V libovolném `foreach` bodě v rámci bloku příkazu můžete vymanit ze smyčky pomocí [příkazu break](break.md) nebo krok k další iteraci ve smyčce pomocí [příkazu continue.](continue.md) `foreach` Můžete také ukončit smyčku [příkazy goto](goto.md), [return](return.md)nebo [throw.](throw.md)

Pokud `foreach` je příkaz `null`použit <xref:System.NullReferenceException> na , je vyvolána. Pokud je zdrojová `foreach` kolekce příkazu prázdná, tělo `foreach` smyčky není spuštěno a přeskočeno.

## <a name="examples"></a>Příklady

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Následující příklad ukazuje použití `foreach` příkazu s <xref:System.Collections.Generic.List%601> instancí typu, který implementuje <xref:System.Collections.Generic.IEnumerable%601> rozhraní:

[!code-csharp-interactive[list example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#1)]

Další příklad používá `foreach` příkaz s instancí typu, který neimplementuje <xref:System.Span%601?displayProperty=nameWithType> žádná rozhraní:

[!code-csharp[span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#2)]

Následující příklad používá `ref` itikovou proměnnou k nastavení hodnoty každé položky v poli stackalloc. Verze `ref readonly` iteduje kolekce vytisknout všechny hodnoty. Deklarace `readonly` používá implicitní deklaraci místní proměnné. Implicitní deklarace proměnných `ref` lze `ref readonly` použít s buď nebo deklarace, jak může explicitně zadali deklarace proměnných.

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#RefSpan)]

Následující příklad `await foreach` používá k iterační kolekci, která generuje každý prvek asynchronně:

[!code-csharp[ref span example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#AwaitForeach)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [foreach prohlášení](~/_csharplang/spec/statements.md#the-foreach-statement) [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Použití foreach s poli](../../programming-guide/arrays/using-foreach-with-arrays.md)
- [pro výpis](for.md)
