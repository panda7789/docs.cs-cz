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
ms.openlocfilehash: 9a69fa42da41ee4a071a6571042fd96fb5a009d2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288027"
---
# <a name="how-to-unwrap-a-nested-task"></a>Postupy: Rozbalení vnořené úlohy
Můžete vrátit úlohu z metody a pak počkat nebo pokračovat v této úloze, jak je znázorněno v následujícím příkladu:  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 V předchozím příkladu <xref:System.Threading.Tasks.Task%601.Result%2A> je vlastnost typu `string` ( `String` v Visual Basic).  
  
 V některých scénářích je však vhodné vytvořit úlohu v rámci jiné úlohy a pak vrátit vnořenou úlohu. V tomto případě `TResult` je nadřazený úkol sám úkolem. V následujícím příkladu je vlastnost Result `Task<Task<string>>` v jazyce C# nebo `Task(Of Task(Of String))` v Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 I když je možné napsat kód, který rozbalí vnější úlohu a načte původní úlohu a její <xref:System.Threading.Tasks.Task%601.Result%2A> vlastnost, takový kód nelze snadno zapsat, protože je nutné zpracovat výjimky a také požadavky na zrušení. V této situaci doporučujeme použít jednu z <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřujících metod, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>Metody lze použít k transformaci libovolného `Task<Task>` nebo `Task<Task<TResult>>` ( `Task(Of Task)` nebo `Task(Of Task(Of TResult))` v Visual Basic) na `Task` nebo `Task<TResult>` ( `Task(Of TResult)` v Visual Basic). Nová úloha plně reprezentuje vnitřní vnořenou úlohu a obsahuje stav zrušení a všechny výjimky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> rozšiřující metody.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Asynchronní programování založené na úlohách](task-based-asynchronous-programming.md)
