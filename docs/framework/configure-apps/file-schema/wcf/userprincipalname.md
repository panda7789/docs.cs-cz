---
title: '&lt;userPrincipalName&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 23e2599920c0ef0ea35569ec9b0b16b0f8735f1a
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="ltuserprincipalnamegt"></a>&lt;userPrincipalName&gt;
Určuje hlavní název uživatele (UPN) služby k ověření klienta.  
  
 Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
\<identity >  
\<userPrincipalName>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<userPrincipalName value="String" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují nadřazené elementy, atributy a podřízené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|value|Název uživatelského účtu (někdy označované jako přihlašovací jméno uživatele) a název domény určujícího doménu, ve kterém se nachází uživatelský účet. Toto je standardní použití pro přihlášení k doméně systému Windows. Formát je: someone@example.com (jako u e-mailovou adresu).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje identitu služby k ověření klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Zabezpečený [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] klienta, která se připojuje k koncový bod s tuto identitu používá název UPN při ověřování rozhraní SSPI ke koncovému bodu.  
  
## <a name="example"></a>Příklad  
 Následující kód konfigurace určuje UPN služby k ověření klienta.  
  
```xml  
<identity>  
  <userPrincipalName value="someone@cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.UpnEndpointIdentity>  
 [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<identity >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
