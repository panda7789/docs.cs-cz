---
title: <servicePrincipalName>
ms.date: 03/30/2017
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
ms.openlocfilehash: da865a19a91d4af6221a13b53a174637d5fb8139
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854989"
---
# <a name="serviceprincipalname"></a>\<servicePrincipalName>
Určuje identitu služby podle hlavního názvu služby (SPN).  
  
Další informace o nastavení hlavního názvu služby (SPN) najdete v tématu [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> klienta**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> koncového bodu**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identity**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> servicePrincipalName**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<servicePrincipalName value="String" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|value|Název, kterým klient jednoznačně identifikuje instanci služby. Pokud instalujete více instancí služby na počítačích v rámci doménové struktury, každá instance musí mít vlastní hlavní název služby (SPN). Pokud existuje více názvů, které mohou klienti použít k ověřování, může mít daná instance služby více názvů SPN.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identity>](identity.md)|Určuje identitu služby, kterou má klient ověřit.|  
  
## <a name="remarks"></a>Poznámky  
 Klient zabezpečeného Windows Communication Foundation (WCF), který se připojuje ke koncovému bodu s touto identitou, používá hlavní název služby (SPN) při provádění ověřování SSPI s koncovým bodem.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.SpnEndpointIdentity>
- [Identita a ověřování služby](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
