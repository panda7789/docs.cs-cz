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
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="b36d9-102">Postupy: Procházení binárního stromu s paralelními úlohami</span><span class="sxs-lookup"><span data-stu-id="b36d9-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="b36d9-103">Následující příklad ukazuje dva způsoby, ve kterém paralelní úkoly lze použít k procházení stromové datové struktury.</span><span class="sxs-lookup"><span data-stu-id="b36d9-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="b36d9-104">Vytvoření samotného stromu je ponecháno jako cvičení.</span><span class="sxs-lookup"><span data-stu-id="b36d9-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b36d9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="b36d9-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="b36d9-106">Dvě uvedené metody jsou funkčně ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="b36d9-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="b36d9-107">Pomocí <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metody k vytvoření a spuštění úloh získáte popisovač zpět z úkolů, které lze použít k čekání na úkoly a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="b36d9-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b36d9-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b36d9-108">See also</span></span>

- [<span data-ttu-id="b36d9-109">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="b36d9-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
