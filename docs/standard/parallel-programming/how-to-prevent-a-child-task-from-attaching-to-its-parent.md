---
title: 'Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
ms.openlocfilehash: 265b6d06f17a1dfbee3f009feff1ee1645e62a46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139264"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze
Tento dokument ukazuje, jak zabránit připojení podřízené úlohy k nadřazené úloze. Zabránění připojení podřízené úlohy k nadřazené úloze je užitečné při volání součásti, která je napsána třetí stranou a která také používá úkoly. Například součást jiného výrobce, <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> která používá <xref:System.Threading.Tasks.Task> možnost <xref:System.Threading.Tasks.Task%601> vytvořit nebo objekt může způsobit problémy v kódu, pokud je dlouhotrvající nebo vyvolá neošetřenou výjimku.  
  
## <a name="example"></a>Příklad  
 Následující příklad porovnává účinky použití výchozích možností s účinky zabránění připojení podřízené úlohy k nadřazené úloze. Příklad vytvoří <xref:System.Threading.Tasks.Task> objekt, který volá do knihovny jiného výrobce, který také používá <xref:System.Threading.Tasks.Task> objekt. Knihovna jiného výrobce <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> používá možnost <xref:System.Threading.Tasks.Task> k vytvoření objektu. Aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost k vytvoření nadřazené úlohy. Tato možnost instruuje za <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> běhu odebrat specifikaci v podřízených úlohách.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Vzhledem k tomu, že nadřazená úloha není dokončena, dokud nebudou dokončeny všechny podřízené úlohy, může dlouho běžící podřízená úloha způsobit, že celková aplikace bude fungovat špatně. V tomto příkladu, když aplikace používá výchozí možnosti k vytvoření nadřazené úlohy, podřízená úloha musí být dokončena před dokončením nadřazené úlohy. Pokud aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost, podřízený není připojen k nadřazené. Aplikace proto může provést další práci po dokončení nadřazené úlohy a před dokončením podřízené úlohy.  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování založené na úlohách](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
