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
ms.openlocfilehash: 89b7036215cb7998222e280ceef02073d455a1b2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705935"
---
# <a name="replacing-a-principal-object"></a>Nahrazení objektu zabezpečení
Aplikace, které poskytují ověřovací služby, musí být schopné nahradit objekt **zabezpečení** (<xref:System.Security.Principal.IPrincipal>) daného vlákna. Kromě toho systém zabezpečení musí pomoct chránit možnost nahradit **Hlavní** objekty, protože neoprávněně připojená, nesprávná **jistina** ohrožuje zabezpečení vaší aplikace tím, že nárokuje neplatnou identitu nebo roli. Proto musí být aplikacím, které vyžadují možnost nahradit **Hlavní** objekty, udělen objekt <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> pro hlavní ovládací prvek. (Upozorňujeme, že toto oprávnění není vyžadováno pro provádění kontrol zabezpečení na základě rolí nebo pro vytváření objektů **zabezpečení** .)  
  
 Aktuální objekt **zabezpečení** může být nahrazen prováděním následujících úloh:  
  
1. Vytvořte náhradní objekt **zabezpečení** a přidružený objekt **identity** .  
  
2. Připojte nový objekt **zabezpečení** k kontextu volání.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit obecný objekt zabezpečení a použít ho k nastavení objektu zabezpečení vlákna.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Objekty zabezpečení a identity](../../../docs/standard/security/principal-and-identity-objects.md)
