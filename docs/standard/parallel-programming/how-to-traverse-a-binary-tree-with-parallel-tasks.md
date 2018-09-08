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
ms.openlocfilehash: 8fd937d6ce2edf0c47fce78d48a90ec1aa409eef
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135097"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="964ca-102">Postupy: Procházení binárního stromu s paralelními úlohami</span><span class="sxs-lookup"><span data-stu-id="964ca-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="964ca-103">Následující příklad ukazuje dva způsoby, ve kterých paralelní úlohy je možné procházet stromovou strukturu dat.</span><span class="sxs-lookup"><span data-stu-id="964ca-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="964ca-104">Vytvoření vlastního stromu je ponechané jako cvičení.</span><span class="sxs-lookup"><span data-stu-id="964ca-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="964ca-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="964ca-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="964ca-106">Dvě zobrazené metody jsou funkčně ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="964ca-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="964ca-107">S použitím <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> metodu pro vytvoření a spuštění úloh, můžete získat popisovače z úloh, které můžete použít k čekání na úlohy a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="964ca-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="964ca-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="964ca-108">See also</span></span>

- [<span data-ttu-id="964ca-109">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="964ca-109">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
