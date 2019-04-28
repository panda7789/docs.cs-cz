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
ms.openlocfilehash: a4287879bd95f7bc1e1dc99f74fa0d7cc0fe737f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769197"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Postupy: Zalomení vzoru EAP v úloze
Následující příklad ukazuje, jak vystavit libovolné pořadí operací asynchronní vzor založený na událostech (EAP) jako jednu úlohu pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601>. Tento příklad také ukazuje, jak používat <xref:System.Threading.CancellationToken> k vyvolání metody předdefinovaných zrušení na <xref:System.Net.WebClient> objekty.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Viz také:

- [TPL a tradiční asynchronní programování v .NET Framework](../../../docs/standard/parallel-programming/tpl-and-traditional-async-programming.md)
