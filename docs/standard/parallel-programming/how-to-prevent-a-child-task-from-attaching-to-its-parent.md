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
ms.openlocfilehash: 5ff181344e6437179fa77f11872ae9a47745be93
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288157"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a>Postupy: Zabránění připojení podřízené úlohy ke své nadřazené úloze
Tento dokument ukazuje, jak zabránit tomu, aby se podřízená úloha připojila k nadřazené úloze. Zabránění podřízené úloze v připojení k nadřazenému objektu je užitečné, pokud voláte komponentu, která je napsaná třetí stranou a která také používá úkoly. Například komponenta třetí strany, která používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> možnost vytvoření <xref:System.Threading.Tasks.Task> objektu nebo, <xref:System.Threading.Tasks.Task%601> může způsobit problémy v kódu, pokud je dlouhotrvající nebo vyvolá neošetřenou výjimku.  
  
## <a name="example"></a>Příklad  
 Následující příklad porovnává účinek použití výchozích možností s vlivem na zabránění podřízené úloze v připojení k nadřazenému. Tento příklad vytvoří <xref:System.Threading.Tasks.Task> objekt, který volá do knihovny třetí strany, která také používá <xref:System.Threading.Tasks.Task> objekt. Knihovna třetí strany používá <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> možnost k vytvoření <xref:System.Threading.Tasks.Task> objektu. Aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost k vytvoření nadřazené úlohy. Tato možnost dá modulu runtime pokyn k odebrání <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specifikace v podřízených úlohách.  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 Vzhledem k tomu, že nadřazená úloha není dokončena, dokud nebudou dokončeny všechny podřízené úlohy, může dlouhodobě spuštěná podřízená úloha způsobit, že celková aplikace nebude fungovat špatně. V tomto příkladu, když aplikace používá výchozí možnosti pro vytvoření nadřazené úlohy, musí být podřízená úloha dokončena před dokončením nadřazené úlohy. Pokud aplikace používá <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> možnost, podřízená položka není připojena k nadřazenému. Proto může aplikace provést dodatečnou práci po dokončení nadřazené úlohy a předtím, než musí počkat na dokončení podřízené úlohy.  
  
## <a name="see-also"></a>Viz také

- [Asynchronní programování založené na úlohách](task-based-asynchronous-programming.md)
