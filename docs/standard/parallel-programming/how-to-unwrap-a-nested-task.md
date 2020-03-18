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
ms.openlocfilehash: c72654a2bc21035fe706d76018bb163d8ba01ee8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106906"
---
# <a name="how-to-unwrap-a-nested-task"></a>Postupy: Rozbalení vnořené úlohy
Můžete vrátit úkol z metody a potom čekat nebo pokračovat z tohoto úkolu, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 V předchozím příkladu <xref:System.Threading.Tasks.Task%601.Result%2A> je vlastnost `string` `String` typu ( v jazyce Visual Basic).  
  
 V některých případech však můžete chtít vytvořit úkol v rámci jiného úkolu a potom vrátit vnořený úkol. V tomto případě `TResult` je ohraničující úkol sám o sobě úkolem. V následujícím příkladu result vlastnost `Task<Task<string>>` je v `Task(Of Task(Of String))` jazyce C# nebo v jazyce Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 I když je možné napsat kód rozbalit vnější úkol a <xref:System.Threading.Tasks.Task%601.Result%2A> načíst původní úkol a jeho vlastnost, takový kód není snadné napsat, protože je nutné zpracovat výjimky a také požadavky na zrušení. V takovém případě doporučujeme použít jednu <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> z metod rozšíření, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> lze použít k `Task<Task>` transformaci `Task<Task<TResult>>` `Task(Of Task)` některé `Task(Of Task(Of TResult))` nebo ( nebo `Task` `Task<TResult>` v`Task(Of TResult)` jazyce Visual Basic) na nebo ( v jazyce Visual Basic). Nový úkol plně představuje vnitřní vnořené úlohy a zahrnuje stav zrušení a všechny výjimky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> používat metody rozšíření.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
