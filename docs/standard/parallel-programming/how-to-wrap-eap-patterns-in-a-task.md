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
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Postupy: Zalomení vzoru EAP v úloze
Následující příklad ukazuje, jak vystavit libovolnou posloupnost operací asynchronního vzoru založeného na <xref:System.Threading.Tasks.TaskCompletionSource%601>událostech (EAP) jako jeden úkol pomocí . Příklad také ukazuje, jak <xref:System.Threading.CancellationToken> použít k vyvolání předdefinované <xref:System.Net.WebClient> metody zrušení na objekty.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Viz také

- [TPL a tradiční asynchronní programování v .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
