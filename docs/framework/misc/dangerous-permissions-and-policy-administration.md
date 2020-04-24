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
ms.openlocfilehash: 15d28ff7d11b5d15ce44d9ab1f56548256850ff8
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645761"
---
# <a name="dangerous-permissions-and-policy-administration"></a>Správa nebezpečných oprávnění a zásad
Několik chráněných operací, pro které rozhraní .NET Framework poskytuje oprávnění, může potenciálně umožnit obcházení systému zabezpečení. Tato nebezpečná oprávnění by měla být udělena pouze důvěryhodnému kódu a pak pouze podle potřeby. Obvykle neexistuje žádná obrana proti škodlivému kódu, pokud je udělena tato oprávnění.  
  
> [!NOTE]
> V rozhraní .NET Framework 4 došlo k důležitým změnám modelu zabezpečení a terminologie rozhraní .NET Framework. Další informace o těchto změnách naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
 Nebezpečná oprávnění jsou vysvětlena v následující tabulce.  
  
|Oprávnění|Potenciální riziko|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Umožňuje spravovanému kódu volat do nespravovaného kódu, což je často nebezpečné.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Bez ověření může kód dělat cokoliv.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Zneplatněné důkazy mohou oklamat bezpečnostní politiku.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Možnost změny zásad zabezpečení může zakázat zabezpečení.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Použití serializace může obejít mechanismy usnadnění. Podrobnosti naleznete v [tématu Zabezpečení a serializace](security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Možnost nastavit aktuální jistinu může oklamat zabezpečení založené na rolích.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulace s vlákny je nebezpečná z důvodu stavu zabezpečení spojeného s vlákny.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Můžete použít soukromé členy porazit mechanismy usnadnění.|  
  
## <a name="see-also"></a>Viz také

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
