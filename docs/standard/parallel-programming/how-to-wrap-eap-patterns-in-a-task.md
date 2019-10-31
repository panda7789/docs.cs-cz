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
ms.openlocfilehash: ac7436892c644340286bb4670bf75c9cd63a8ce5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106825"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="cbcdd-102">Postupy: Zalomení vzoru EAP v úloze</span><span class="sxs-lookup"><span data-stu-id="cbcdd-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="cbcdd-103">Následující příklad ukazuje, jak vystavit libovolnou sekvenci operací s asynchronním vzorem na základě události jako jeden úkol pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span><span class="sxs-lookup"><span data-stu-id="cbcdd-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="cbcdd-104">Příklad také ukazuje, jak použít <xref:System.Threading.CancellationToken> k vyvolání předdefinovaných metod zrušení u objektů <xref:System.Net.WebClient>.</span><span class="sxs-lookup"><span data-stu-id="cbcdd-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbcdd-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbcdd-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="cbcdd-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbcdd-106">See also</span></span>

- [<span data-ttu-id="cbcdd-107">TPL a tradiční asynchronní programování v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="cbcdd-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
