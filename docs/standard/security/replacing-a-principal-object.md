---
title: "Nahrazení objektu zabezpečení"
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
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c53064ae12889df09b5259fbb7c8159cfdcd07aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="replacing-a-principal-object"></a>Nahrazení objektu zabezpečení
Aplikace, které poskytují služby ověřování musí být schopen nahradit **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) pro dané vlákno. Kromě toho musí systém zabezpečení pomáhat chránit schopnost nahradit **hlavní** objekty, protože speciálně připojený, nesprávný **hlavní** ohrožuje zabezpečení vaší aplikace nárokování role nebo PRAVDA identity. Proto aplikace, vyžadovat schopnost nahradit **hlavní** objekty musí mít udělen <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objektu pro kontrolu zabezpečení. (Všimněte si, že toto oprávnění není požadováno k provádění kontrol na základě rolí zabezpečení nebo vytváření **hlavní** objekty.)  
  
 Aktuální **hlavní** objekt lze nahradit provedením následujících úloh:  
  
1.  Vytvoření nahrazení **hlavní** objektu a související **Identity** objektu.  
  
2.  Připojit nové **hlavní** objekt, který má v kontextu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit obecný objekt zabezpečení a použít ho nastavit objekt zabezpečení vlákna.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
