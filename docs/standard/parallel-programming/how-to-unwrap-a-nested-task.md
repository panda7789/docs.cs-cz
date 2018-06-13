---
title: 'Postupy: Rozbalení vnořené úlohy'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9cee6817378503a3b98424ff4166725a46f7a29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580728"
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
