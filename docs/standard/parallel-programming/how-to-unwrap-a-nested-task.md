---
title: "Postupy: Rozbalení vnořené úlohy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2da3de912abb693c4342e1ede02f273348e4b571
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-unwrap-a-nested-task"></a>Postupy: Rozbalení vnořené úlohy
Vrátí úlohu z metody a potom můžete čekat na nebo pokračovat od této úlohy, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 V předchozím příkladu <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost je typu `string` (`String` v jazyce Visual Basic).  
  
 Ale v některých scénářích, můžete k vytvoření úlohy v rámci jiné úlohy a pak se vraťte vnořené úlohy. V takovém případě `TResult` ohraničující úlohy je sám úlohou. V následujícím příkladu je vlastnost výsledek `Task<Task<string>>` v jazyce C# nebo `Task(Of Task(Of String))` v jazyce Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Přestože je možné napsat kód pro rozbalení vnější úlohy a načtení původní úlohy a její <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost, takový kód není usnadňuje zapisovat, protože je nutné zpracovat výjimky a také žádosti o zrušení. V takovém případě doporučujeme použít jednu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metody, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> Metody lze použít k transformaci libovolného `Task<Task>` nebo `Task<Task<TResult>>` (`Task(Of Task)` nebo `Task(Of Task(Of TResult))` v jazyce Visual Basic) k `Task` nebo `Task<TResult>` (`Task(Of TResult)` v jazyce Visual Basic). Nová úloha plně představuje vnitřní vnořené úlohy a zahrnuje stav zrušení a všechny výjimky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metody.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>  
 [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
