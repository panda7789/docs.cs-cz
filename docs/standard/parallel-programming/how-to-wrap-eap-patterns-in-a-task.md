---
title: "Postupy: Zalomení vzoru EAP v úloze"
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
helpviewer_keywords: tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae9d90c9bb3d0e8d315cbef510cdfe1b54e66da4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="34e17-102">Postupy: Zalomení vzoru EAP v úloze</span><span class="sxs-lookup"><span data-stu-id="34e17-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="34e17-103">Následující příklad ukazuje, jak zpřístupnit libovolnou sekvenci operací asynchronní vzor založený na událostech (EAP) jako jednu úlohu pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span><span class="sxs-lookup"><span data-stu-id="34e17-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="34e17-104">Příklad také ukazuje způsob použití <xref:System.Threading.CancellationToken> k vyvolání metody předdefinované zrušení na <xref:System.Net.WebClient> objekty.</span><span class="sxs-lookup"><span data-stu-id="34e17-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34e17-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="34e17-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="34e17-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="34e17-106">See Also</span></span>  
 [<span data-ttu-id="34e17-107">TPL a tradiční rozhraní .NET Framework asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="34e17-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
