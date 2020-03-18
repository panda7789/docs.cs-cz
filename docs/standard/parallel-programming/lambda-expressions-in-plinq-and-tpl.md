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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77452997"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Výrazy lambda v PLINQ a TPL

Paralelní knihovna úloh (TPL) obsahuje mnoho <xref:System.Func%601?displayProperty=nameWithType> metod, které berou jednu z nebo <xref:System.Action?displayProperty=nameWithType> rodiny delegátů jako vstupní parametry. Tyto delegáty slouží k předání vlastní programové logiky paralelní smyčce, úkolu nebo dotazu. Příklady kódu pro TPL, stejně jako PLINQ použít lambda výrazy k vytvoření instance těchto delegátů jako bloky vřádkový kód. Toto téma obsahuje stručný úvod do Func a akce a ukazuje, jak používat lambda výrazy v paralelní knihovny úloh a PLINQ.

> [!NOTE]
> Další informace o delegátech obecně naleznete v tématu [Delegáti](../../csharp/programming-guide/delegates/index.md) a [delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md). Další informace o výrazech lambda v jazyce C# a visual basicu naleznete v [tématu Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="func-delegate"></a>Delegát Func

Delegát `Func` zapouzdřuje metodu, která vrací hodnotu. V `Func` podpisu parametr posledního nebo zcela pravého typu vždy určuje návratový typ. Jednou z běžných příčin chyb kompilátoru je pokus <xref:System.Func%602?displayProperty=nameWithType>o předání dvou vstupních parametrů do ; ve skutečnosti tento typ trvá pouze jeden vstupní parametr. Rozhraní .NET definuje 17 `Func` <xref:System.Func%601?displayProperty=nameWithType>verzí <xref:System.Func%602?displayProperty=nameWithType> <xref:System.Func%603?displayProperty=nameWithType>aplikace : , <xref:System.Func%6017?displayProperty=nameWithType>, a tak dále až do .

## <a name="action-delegate"></a>Delegát akce

Delegát <xref:System.Action?displayProperty=nameWithType> zapouzdřuje metodu (Sub v jazyce Visual Basic), která nevrací hodnotu. V `Action` podpisu typu představují parametry typu pouze vstupní parametry. Stejně jako `Func`rozhraní .NET definuje `Action`17 verzí aplikace od verze, která nemá žádné parametry typu, až po verzi, která má 16 parametrů typu.

## <a name="example"></a>Příklad

Následující příklad pro <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metodu ukazuje, jak vyjádřit delegáty Func a Action pomocí výrazů lambda.

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
