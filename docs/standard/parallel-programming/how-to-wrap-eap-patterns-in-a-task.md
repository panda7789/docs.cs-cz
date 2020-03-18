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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106825"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a><span data-ttu-id="05fc9-102">Postupy: Zalomení vzoru EAP v úloze</span><span class="sxs-lookup"><span data-stu-id="05fc9-102">How to: Wrap EAP Patterns in a Task</span></span>
<span data-ttu-id="05fc9-103">Následující příklad ukazuje, jak vystavit libovolnou posloupnost operací asynchronního vzoru založeného na <xref:System.Threading.Tasks.TaskCompletionSource%601>událostech (EAP) jako jeden úkol pomocí .</span><span class="sxs-lookup"><span data-stu-id="05fc9-103">The following example shows how to expose an arbitrary sequence of Event-Based Asynchronous Pattern (EAP) operations as one task by using a <xref:System.Threading.Tasks.TaskCompletionSource%601>.</span></span> <span data-ttu-id="05fc9-104">Příklad také ukazuje, jak <xref:System.Threading.CancellationToken> použít k vyvolání předdefinované <xref:System.Net.WebClient> metody zrušení na objekty.</span><span class="sxs-lookup"><span data-stu-id="05fc9-104">The example also shows how to use a <xref:System.Threading.CancellationToken> to invoke the built-in cancellation methods on the <xref:System.Net.WebClient> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05fc9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="05fc9-105">Example</span></span>  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="05fc9-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="05fc9-106">See also</span></span>

- [<span data-ttu-id="05fc9-107">TPL a tradiční asynchronní programování v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="05fc9-107">TPL and Traditional .NET Framework Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
