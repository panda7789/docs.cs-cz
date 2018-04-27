---
title: Výrazy lambda v PLINQ a TPL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5b1739bf8d98bbee49cf3cb3d83cac27796ccf72
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Výrazy lambda v PLINQ a TPL
Task Parallel Library (TPL) obsahuje mnoho způsobů, které provést jednu z <xref:System.Func%601?displayProperty=nameWithType> nebo <xref:System.Action?displayProperty=nameWithType> rodiny delegátů jako vstupní parametry. Používání těchto delegátů předávat logika vlastní program paralelní smyčky, úlohy nebo dotazu. Příklady kódu pro TPL a také PLINQ použití výrazů lambda vytváření instancí těchto delegáti jako vložené bloky kódu. Toto téma obsahuje stručný úvod do Func a Action a ukazuje, jak použití výrazů lambda v knihovně Task Parallel Library a PLINQ.  
  
 **Poznámka:** Další informace o delegáti obecně platí, najdete v části [delegáti](../../csharp/programming-guide/delegates/index.md) a [delegáti](../../visual-basic/programming-guide/language-features/delegates/index.md). Další informace o výrazy lambda v jazyce C# a Visual Basic najdete v tématu [výrazy Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) a [výrazy Lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>Func – delegát  
 A `Func` delegáta zapouzdří metodu, která vrátí hodnotu. V Func podpis vždy parametr typu poslední nebo úplně vpravo určuje návratový typ. Jednou z běžných příčin chyb kompilátoru je pokus o předat ve dvou vstupních parametrů <xref:System.Func%602?displayProperty=nameWithType>; ve skutečnosti tento typ trvá jen jeden vstupní parametr. Knihovna tříd Framework definuje 17 verzích `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, a tak dále až prostřednictvím <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Delegát akce  
 A <xref:System.Action?displayProperty=nameWithType> delegáta zapouzdří metodu (Sub v jazyce Visual Basic), která nevrátí hodnotu nebo vrátí [void](~/docs/csharp/language-reference/keywords/void.md). Parametry typu v podpisu typ akce, představují pouze vstupní parametry. Knihovna tříd Framework jako Func, definuje 17 verze akce, na verzi, která nemá žádné parametry typu prostřednictvím na verzi, která obsahuje 16 parametrů typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> metoda ukazuje, jak express delegáty Func a Action pomocí výrazů lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
