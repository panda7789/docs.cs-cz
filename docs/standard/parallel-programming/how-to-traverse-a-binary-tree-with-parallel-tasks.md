---
title: "Postupy: Procházení binárního stromu s paralelními úlohami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0196d82dd46a105f7cf1db0f9333a5d28afe559b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="e8f0b-102">Postupy: Procházení binárního stromu s paralelními úlohami</span><span class="sxs-lookup"><span data-stu-id="e8f0b-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="e8f0b-103">Následující příklad ukazuje dva způsoby, ve kterých paralelní úlohy slouží k procházení datová struktura stromu.</span><span class="sxs-lookup"><span data-stu-id="e8f0b-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="e8f0b-104">Vytvoření vlastního stromu je ponechán jako cvičení.</span><span class="sxs-lookup"><span data-stu-id="e8f0b-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f0b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8f0b-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="e8f0b-106">Dvě zobrazené metody jsou funkčně rovnocenné.</span><span class="sxs-lookup"><span data-stu-id="e8f0b-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="e8f0b-107">Pomocí <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metodu pro vytvoření a spuštění úloh, můžete získat popisovače z úloh, které se dají použít pro čekání na úlohy a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="e8f0b-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f0b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8f0b-108">See Also</span></span>  
 [<span data-ttu-id="e8f0b-109">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="e8f0b-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
