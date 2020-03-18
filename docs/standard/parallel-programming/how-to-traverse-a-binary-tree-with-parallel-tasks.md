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
ms.openlocfilehash: b79337e6ee8057506ff87c696cecd6b038eeebfc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141639"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Postupy: Procházení binárního stromu s paralelními úlohami
Následující příklad ukazuje dva způsoby, ve kterém paralelní úkoly lze použít k procházení stromové datové struktury. Vytvoření samotného stromu je ponecháno jako cvičení.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Dvě uvedené metody jsou funkčně ekvivalentní. Pomocí <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody k vytvoření a spuštění úloh získáte popisovač zpět z úkolů, které lze použít k čekání na úkoly a zpracování výjimek.  
  
## <a name="see-also"></a>Viz také

- [Task Parallel Library (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
