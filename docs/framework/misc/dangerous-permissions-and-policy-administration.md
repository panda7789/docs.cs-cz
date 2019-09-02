---
title: Správa nebezpečných oprávnění a zásad
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffe4f3e000c80610d5a105dddef90f9cfd51f0dc
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205584"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Správa nebezpečných oprávnění a zásad
Některé z chráněných operací, pro které .NET Framework poskytují oprávnění, můžou potenciálně dovolit obejít systém zabezpečení. Tato nebezpečná oprávnění by měla být udělena pouze důvěryhodnému kódu a pak pouze podle potřeby. Není obvykle žádná obrana proti škodlivému kódu, pokud jim byla udělena tato oprávnění.  
  
> [!NOTE]
> V .NET Framework 4 existovaly důležité změny modelu a terminologie zabezpečení .NET Framework. Další informace o těchto změnách najdete v tématu [změny zabezpečení](../security/security-changes.md).  
  
 Nebezpečná oprávnění jsou vysvětlena v následující tabulce.  
  
|Oprávnění|Potenciální riziko|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Umožňuje spravovanému kódu volat do nespravovaného kódu, který je často nebezpečný.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Bez ověření může kód provádět cokoli.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Neověřené legitimace můžou podvést zásady zabezpečení.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Možnost upravovat zásady zabezpečení může zabezpečení zakázat.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Použití serializace může obejít mechanismy přístupnosti. Podrobnosti najdete v tématu [zabezpečení a serializace](security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Možnost nastavit aktuální objekt zabezpečení může být obtížné zabezpečení na základě rolí.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulace s vlákny je nebezpečná, protože stav zabezpečení je přidružený k vláknům.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Může použít soukromé členy k přepřipravenosti mechanismů přístupu.|  
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
