---
title: Nahrazení objektu zabezpečení
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5193756861f407315ec82e4419f1d04495c7dd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606030"
---
# <a name="replacing-a-principal-object"></a>Nahrazení objektu zabezpečení
Aplikace, které poskytují služby ověřování musí být schopen nahradit **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) pro dané vlákno. Kromě toho musí systém zabezpečení pomáhají chránit možnost nahradit **instančního objektu** objekty, protože speciálně připojený, nesprávné **instančního objektu** ohrožuje zabezpečení vaší aplikace pomocí nárokování role nebo naléhavém identity. Proto se aplikace, které vyžadují možnost nahradit **hlavní** objekty musí mít udělena <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objektu pro kontrolu zabezpečení. (Všimněte si, že toto oprávnění se nevyžaduje k provádění kontrol zabezpečení na základě rolí nebo vytváření **hlavní** objekty.)  
  
 Aktuální **hlavní** objektu lze nahradit pomocí provádí následující úlohy:  
  
1.  Vytvořit náhradu **hlavní** objektů a související **Identity** objektu.  
  
2.  Připojit nový **hlavní** objekt kontextu volání.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit objekt obecný instančního objektu a nastavte hlavní vlákno.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
