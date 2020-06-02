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
ms.openlocfilehash: 3d985a003fe613699c89e38583f84be9e21b383d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290665"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Výrazy lambda v PLINQ a TPL

Task Parallel Library (TPL) obsahuje mnoho metod, které jako vstupní parametry přebírají jednu z <xref:System.Func%601?displayProperty=nameWithType> <xref:System.Action?displayProperty=nameWithType> rodiny delegátů nebo. Tyto delegáty můžete použít k předání vlastní logiky programu do paralelní smyčky, úkolu nebo dotazu. Příklady kódu pro TPL a PLINQ používají lambda výrazy k vytváření instancí těchto delegátů jako vložené bloky kódu. Toto téma obsahuje stručný úvod do funkce Func a Action a ukazuje, jak používat výrazy lambda v Task Parallel Library a PLINQ.

> [!NOTE]
> Další informace o delegátech obecně naleznete v tématu [Delegáti](../../csharp/programming-guide/delegates/index.md) a [Delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md). Další informace o výrazech lambda v jazyce C# a Visual Basic naleznete v tématu [lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) a [lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="func-delegate"></a>Delegát Func

`Func`Delegát zapouzdřuje metodu, která vrací hodnotu. V `Func` signatuře, posledním nebo pravém, parametr typu vždy určuje návratový typ. Jednou z běžných příčin chyb kompilátoru je pokus o předání dvou vstupních parametrů do <xref:System.Func%602?displayProperty=nameWithType> . ve skutečnosti tento typ používá pouze jeden vstupní parametr. Rozhraní .NET definuje 17 verzí `Func` : <xref:System.Func%601?displayProperty=nameWithType> , <xref:System.Func%602?displayProperty=nameWithType> , <xref:System.Func%603?displayProperty=nameWithType> a tak dále <xref:System.Func%6017?displayProperty=nameWithType> .

## <a name="action-delegate"></a>Delegát akce

<xref:System.Action?displayProperty=nameWithType>Delegát zapouzdřuje metodu (sub v Visual Basic), která nevrací hodnotu. V `Action` signatuře typu parametry typu reprezentují pouze vstupní parametry. Podobně jako `Func` rozhraní .NET definuje 17 verzí `Action` , od verze, která nemá parametry typu, prostřednictvím verze, která má 16 parametrů typu.

## <a name="example"></a>Příklad

Následující příklad <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metody ukazuje, jak vyjádřit delegáty Func i akce pomocí výrazů lambda.

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a>Viz také

- [Paralelní programování](index.md)
