---
title: 'Postupy: Zalomení vzoru EAP v úloze'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to wrap EAP patterns
ms.assetid: f11ed467-af2f-4504-8a2e-299a6c36d44e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 292bff13b4651b0e886abc435104edfa930f9de1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582766"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="18231-102">Postupy: Zalomení vzoru EAP v úloze</span><span class="sxs-lookup"><span data-stu-id="18231-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="18231-103">Následující příklad ukazuje, jak zpřístupnit libovolnou sekvenci operací asynchronní vzor založený na událostech (EAP) jako jednu úlohu pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span><span class="sxs-lookup"><span data-stu-id="18231-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="18231-104">Příklad také ukazuje způsob použití <xref:System.Threading.CancellationToken> k vyvolání metody předdefinované zrušení na <xref:System.Net.WebClient> objekty.</span><span class="sxs-lookup"><span data-stu-id="18231-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18231-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="18231-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="18231-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="18231-106">See Also</span></span>  
 [<span data-ttu-id="18231-107">TPL a tradiční asynchronní programování v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="18231-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
