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
ms.openlocfilehash: eab94ac91be0c755a1da74e2f2220e3b76cc4249
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290782"
---
# <a name="how-to-wrap-eap-patterns-in-a-task"></a>Postupy: Zalomení vzoru EAP v úloze
Následující příklad ukazuje, jak vystavit libovolnou posloupnost operací asynchronního vzoru založeného na událostech (EAP) jako jeden úkol pomocí <xref:System.Threading.Tasks.TaskCompletionSource%601> . Příklad také ukazuje, jak použít <xref:System.Threading.CancellationToken> k vyvolání předdefinovaných metod zrušení u <xref:System.Net.WebClient> objektů.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[FromAsync#08](../../../samples/snippets/csharp/VS_Snippets_Misc/fromasync/cs/fromasync.cs#08)]
 [!code-vb[FromAsync#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/fromasync/vb/module1.vb#08)]  
  
## <a name="see-also"></a>Viz také

- [TPL a tradiční asynchronní programování v .NET Framework](tpl-and-traditional-async-programming.md)
