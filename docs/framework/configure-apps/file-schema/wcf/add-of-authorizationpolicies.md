---
title: <add> z <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 65398c5afa9750f215c95899bb6004cae671123a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920275"
---
# <a name="add-of-authorizationpolicies"></a>\<Přidat > \<> authorizationPolicies
Určuje zásadu autorizace pro transformaci deklarace identity.  
  
 \<system.ServiceModel>  
\<> chování  
\<> chování  
\<serviceAuthorization>  
\<authorizationPolicies>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a>type  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`policyType`|Povinný atribut typu řetězec.<br /><br /> Model řízení přístupu Windows Communication Foundation (WCF) podporuje zřizování sady zásad autorizace jako typů. Tento atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací. Řízení přístupu lze na základě této aplikace udělit nebo odepřít.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|Určuje kolekci typů zásad autorizace.|  
  
## <a name="remarks"></a>Poznámky  
 Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec. Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací. Řízení přístupu lze na základě této aplikace udělit nebo odepřít. Další informace o tom, jak zásady autorizace fungují, najdete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> v tématu a [zásadách autorizace](../../../wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Autorizace přístupu k operacím služby](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Postupy: Vytvoření vlastního Správce autorizací pro službu](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [Zásady autorizace](../../../wcf/samples/authorization-policy.md)
