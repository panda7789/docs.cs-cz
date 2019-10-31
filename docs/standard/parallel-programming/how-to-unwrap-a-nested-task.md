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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106906"
---
# <a name="how-to-unwrap-a-nested-task"></a>Postupy: Rozbalení vnořené úlohy
Můžete vrátit úlohu z metody a pak počkat nebo pokračovat v této úloze, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 V předchozím příkladu je vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A> typu `string` (`String` v Visual Basic).  
  
 V některých scénářích je však vhodné vytvořit úlohu v rámci jiné úlohy a pak vrátit vnořenou úlohu. V tomto případě je `TResult` ohraničující úlohy samotný úkol. V následujícím příkladu je vlastnost Result `Task<Task<string>>` v C# nebo `Task(Of Task(Of String))` v Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 I když je možné napsat kód, který rozbalí vnější úlohu a načte původní úlohu a její vlastnost <xref:System.Threading.Tasks.Task%601.Result%2A>, takový kód se nedá snadno zapsat, protože je nutné zpracovat výjimky a také požadavky na zrušení. V takové situaci doporučujeme použít jednu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřujících metod, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Metody <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> lze použít k transformaci jakýchkoli `Task<Task>` nebo `Task<Task<TResult>>` (`Task(Of Task)` nebo `Task(Of Task(Of TResult))` v Visual Basic) na `Task` nebo `Task<TResult>` (`Task(Of TResult)` v Visual Basic). Nová úloha plně reprezentuje vnitřní vnořenou úlohu a obsahuje stav zrušení a všechny výjimky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít metody rozšíření <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
