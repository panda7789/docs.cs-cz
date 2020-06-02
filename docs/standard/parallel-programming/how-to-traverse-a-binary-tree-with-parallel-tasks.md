---
title: 'Postupy: Procházení binárního stromu s paralelními úlohami'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: 5ac81a61691ec20daafc9e18978ba5814a150383
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288066"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Postupy: Procházení binárního stromu s paralelními úlohami
Následující příklad ukazuje dva způsoby, jak lze použít paralelní úlohy pro procházení stromové struktury dat. Vytvoření samotného stromu je ponecháno jako cvičení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Tyto dvě zobrazené metody jsou funkčně ekvivalentní. Pomocí <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody k vytvoření a spuštění úkolů získáte popisovač zpátky z úloh, které lze použít k čekání na úlohy a zpracování výjimek.  
  
## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](task-parallel-library-tpl.md)
