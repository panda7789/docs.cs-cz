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
ms.openlocfilehash: 056bd0bbafe0e7dc84d8d0c532ff844370c59230
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291211"
---
# <a name="replacing-a-principal-object"></a>Nahrazení objektu zabezpečení
Aplikace, které poskytují služby ověřování, musí být schopné nahradit objekt **zabezpečení** ( <xref:System.Security.Principal.IPrincipal> ) pro dané vlákno. Kromě toho systém zabezpečení musí pomoct chránit možnost nahradit **Hlavní** objekty, protože neoprávněně připojená, nesprávná **jistina** ohrožuje zabezpečení vaší aplikace tím, že nárokuje neplatnou identitu nebo roli. Proto musí být aplikace, které vyžadují možnost nahradit **Hlavní** objekty, uděleny <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objektu pro hlavní ovládací prvek. (Upozorňujeme, že toto oprávnění není vyžadováno pro provádění kontrol zabezpečení na základě rolí nebo pro vytváření objektů **zabezpečení** .)  
  
 Aktuální objekt **zabezpečení** může být nahrazen prováděním následujících úloh:  
  
1. Vytvořte náhradní objekt **zabezpečení** a přidružený objekt **identity** .  
  
2. Připojte nový objekt **zabezpečení** k kontextu volání.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit obecný objekt zabezpečení a použít ho k nastavení objektu zabezpečení vlákna.  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [Objekty zabezpečení a identity](principal-and-identity-objects.md)
