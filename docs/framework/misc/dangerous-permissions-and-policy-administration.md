---
title: "Správa nebezpečných oprávnění a zásad"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], policy administration
- security [.NET Framework], dangerous permissions
- code security, dangerous permissions
- secure coding, dangerous permissions
- permissions [.NET Framework], dangerous
ms.assetid: 1929e854-23a0-4bb1-94be-e8aa3b609e32
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 471570aec43398b05b8678bdcf74a3ef2494e289
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="dangerous-permissions-and-policy-administration"></a>Správa nebezpečných oprávnění a zásad
Některé z chráněných operací, pro které rozhraní .NET Framework poskytuje oprávnění potenciálně můžete povolit systému zabezpečení možné obejít. Tyto nebezpečná oprávnění by měla mít pouze k důvěryhodnému kódu a pouze v případě potřeby. Je obvykle žádnou obranu proti škodlivý kód uživatelům Pokud jsou udělena tato oprávnění.  
  
> [!NOTE]
>  V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], byly důležité změny modelu zabezpečení rozhraní .NET Framework a terminologii. Další informace o těchto změnách najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
 Nebezpečná oprávnění jsou vysvětlené v následující tabulce.  
  
|Oprávnění|Potenciální riziko|  
|----------------|--------------------|  
|<xref:System.Security.Permissions.SecurityPermission>||  
|<xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode>|Umožňuje spravovaného kódu volat nespravovaný kód, který je často nebezpečný.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SkipVerification>|Bez ověřování kód dělat cokoliv.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlEvidence>|Zneplatněné důkaz může oklamat zásady zabezpečení.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPolicy>|Možnost upravit zásady zabezpečení můžete zakázat zabezpečení.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.SerializationFormatter>|Použití serializace může obejít mechanismy usnadnění. Podrobnosti najdete v tématu [zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md).|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlPrincipal>|Možnost nastavit aktuální objekt zabezpečení může oklamat na základě rolí zabezpečení.|  
|<xref:System.Security.Permissions.SecurityPermissionFlag.ControlThread>|Manipulace s vlákny je nebezpečné kvůli stavu zabezpečení přidružené k vláken.|  
|<xref:System.Security.Permissions.ReflectionPermission>||  
|<xref:System.MemberAccessException>|Můžete použít soukromé členy pro zrušení mechanismů usnadnění.|  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
