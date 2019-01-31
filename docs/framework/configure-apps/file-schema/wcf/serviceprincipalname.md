---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: ba1484644c57651fc0feadcc61d71d03eec1899b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254918"
---
# <a name="serviceprincipalname"></a>\<servicePrincipalName>
Určuje identitu služby podle jeho hlavní název služby (SPN).  
  
 Další informace o nastavení hlavního názvu služby naleznete v tématu [identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<identity>  
\<servicePrincipalName>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|value|Název, kterým klient jednoznačně identifikuje instanci služby. Pokud více instancí služby nainstalovat v počítačích v rámci doménové struktury, každá instance musí mít svůj vlastní hlavní název služby. Uvedená služba instance může mít několik hlavních názvů služby, pokud existuje více názvů, které můžou klienti používat pro ověřování.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|Určuje identitu služby k ověření klienta.|  
  
## <a name="remarks"></a>Poznámky  
 Zabezpečené klienta Windows Communication Foundation (WCF), která se připojuje k koncový bod s tuto identitu použije hlavní název služby při provádění ověřování rozhraní SSPI ke koncovému bodu.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [Identita a ověřování služby](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
