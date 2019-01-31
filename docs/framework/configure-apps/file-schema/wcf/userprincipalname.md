---
title: <userPrincipalName>
ms.date: 03/30/2017
ms.assetid: 68032f69-149e-4613-bae4-18314d4fd294
ms.openlocfilehash: 19ea7e940fc7013fc526629a8aac4361ff3fb8bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275013"
---
# <a name="userprincipalname"></a>\<userPrincipalName>
Určuje, hlavní název uživatele (UPN) služby k ověření klienta.  
  
 Další informace o nastavení hlavního názvu uživatele najdete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
\<identity>  
\<userPrincipalName>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<userPrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|value|Název uživatelského účtu (někdy označované jako přihlašovací uživatelské jméno) a název domény identifikující doménu, ve kterém se nachází uživatelský účet. Toto je standardní využití pro přihlášení k doméně Windows. Formát je: someone@example.com (jako u e-mailovou adresu).|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje identitu služby k ověření klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tato identita se používá název UPN při provádění ověřování rozhraní SSPI ke koncovému bodu.  
  
## <a name="example"></a>Příklad  
 Následující kód konfigurace určuje UPN služby k ověření klienta.  
  
```xml  
<identity>
  <userPrincipalName value="someone@cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.UpnEndpointIdentity>
- [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
