---
title: Výrazy lambda v PLINQ a TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 4e5be295a52edc1a7f0a0a3aa98f55335ae3e31b
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452997"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Výrazy lambda v PLINQ a TPL

Task Parallel Library (TPL) obsahuje mnoho metod, které přebírají jednu z <xref:System.Func%601?displayProperty=nameWithType> nebo <xref:System.Action?displayProperty=nameWithType> rodinu delegátů jako vstupní parametry. Tyto delegáty můžete použít k předání vlastní logiky programu do paralelní smyčky, úkolu nebo dotazu. Příklady kódu pro TPL a PLINQ používají lambda výrazy k vytváření instancí těchto delegátů jako vložené bloky kódu. Toto téma obsahuje stručný úvod do funkce Func a Action a ukazuje, jak používat výrazy lambda v Task Parallel Library a PLINQ.

> [!NOTE]
> Další informace o delegátech obecně naleznete v tématu [Delegáti](../../csharp/programming-guide/delegates/index.md) a [Delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md). Další informace o výrazech lambda v C# a Visual Basic naleznete v tématu [lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) a [lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="func-delegate"></a>Delegát Func

Delegát `Func` zapouzdřuje metodu, která vrací hodnotu. V `Func` signatura, poslední, nebo úplně vpravo, parametr Type vždy určuje návratový typ. Jednou z běžných příčin chyb kompilátoru je pokus o předání dvou vstupních parametrů <xref:System.Func%602?displayProperty=nameWithType>; ve skutečnosti tento typ používá pouze jeden vstupní parametr. Rozhraní .NET definuje 17 verzí `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>a tak dále až <xref:System.Func%6017?displayProperty=nameWithType>.

## <a name="action-delegate"></a>Delegát akce

Delegát <xref:System.Action?displayProperty=nameWithType> zapouzdřuje metodu (sub v Visual Basic), která nevrací hodnotu. V signatuře typu `Action` parametry typu reprezentují pouze vstupní parametry. Podobně jako `Func`rozhraní .NET definuje 17 verzí `Action`, od verze, která nemá parametry typu, prostřednictvím verze, která má 16 parametrů typu.

## <a name="example"></a>Příklad

Následující příklad metody <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> ukazuje, jak vyjádřit delegáty Func i akce pomocí výrazů lambda.

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
