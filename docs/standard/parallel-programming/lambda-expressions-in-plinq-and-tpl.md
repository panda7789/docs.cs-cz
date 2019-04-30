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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a003c96e81996e304fc4347ed05bf7a255c224
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943829"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Výrazy lambda v PLINQ a TPL
Task Parallel Library (TPL) obsahuje mnoho metod, které proveďte jednu z <xref:System.Func%601?displayProperty=nameWithType> nebo <xref:System.Action?displayProperty=nameWithType> řady delegátů jako vstupní parametry. Použijte tyto delegáty v logice vlastní programu předat paralelní smyčky, úkolu nebo dotazu. Příklady kódu pro TPL, jakož i PLINQ použití výrazů lambda pro vytvoření instancí těchto delegátů jako vložené bloky kódu. Toto téma nabízí stručný úvod do Func a Action a ukazuje, jak použít výrazy lambda v knihovně Task Parallel Library a PLINQ.  
  
 **Poznámka:** pro další informace o delegátech obecné naleznete v tématu [delegáti](../../csharp/programming-guide/delegates/index.md) a [delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md). Další informace o výrazech lambda v jazyce C# a Visual Basic najdete v tématu [výrazy Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) a [výrazy Lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>Func – delegát  
 A `Func` delegáta zapouzdřuje metodu, která vrací hodnotu. V signatuře Func určuje parametr typu poslední nebo úplně vpravo vždy návratový typ. Jednou z běžných příčin kompilátoru chyby je pokus a zajistěte tak předání dva vstupní parametry <xref:System.Func%602?displayProperty=nameWithType>; ve skutečnosti tento typ má pouze jeden vstupní parametr. Knihovna tříd rozhraní definuje 17 verzích `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, a tak dále až prostřednictvím <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Delegát akce  
 A <xref:System.Action?displayProperty=nameWithType> delegáta zapouzdřuje metody (Sub v jazyce Visual Basic), která nevrací hodnotu, nebo vrátí [void](~/docs/csharp/language-reference/keywords/void.md). Parametry typu v signatuře typu akci, představují pouze vstupní parametry. Podobně jako funkce knihovny tříd rozhraní Framework definuje 17 verze akce, verzi, která nemá žádné parametry typu prostřednictvím verze, který má 16 parametry typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metoda ukazuje, jak vyjádřit delegáty Func a Action pomocí výrazů lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
