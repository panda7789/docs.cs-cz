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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6446145d34d22503697bbca59bc2cb2cd2619cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Postupy: Procházení binárního stromu s paralelními úlohami
Následující příklad ukazuje dva způsoby, ve kterých paralelní úlohy slouží k procházení datová struktura stromu. Vytvoření vlastního stromu je ponechán jako cvičení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Dvě zobrazené metody jsou funkčně rovnocenné. Pomocí <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metodu pro vytvoření a spuštění úloh, můžete získat popisovače z úloh, které se dají použít pro čekání na úlohy a zpracování výjimek.  
  
## <a name="see-also"></a>Viz také  
 [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
