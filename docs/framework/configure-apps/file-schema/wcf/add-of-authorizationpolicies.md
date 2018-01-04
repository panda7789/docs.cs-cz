---
title: "&lt;add&gt; – &lt;authorizationPolicies&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72af0529cea2e6810bdb7a518874a313e3ceab40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a>&lt;add&gt; – &lt;authorizationPolicies&gt;
Určuje zásad autorizace pro transformace deklarací identity.  
  
 \<systém. ServiceModel >  
\<chování >  
\<chování >  
\<serviceAuthorization >  
\<authorizationPolicies >  
\<Přidat >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a>Typ  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`policyType`|Požadovaný atribut řetězec.<br /><br /> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Model řízení přístupu podporuje sadu zásad autorizace jako typy zřizování. Tento atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity. Řízení přístupu může být povolen nebo odepřen, na základě.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<authorizationPolicies >](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|Určuje kolekci typů zásad autorizace.|  
  
## <a name="remarks"></a>Poznámky  
 Každá zásada autorizace obsahuje jediný požadované `policyType` atribut, který obsahuje řetězec. Atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity. Řízení přístupu může být povolen nebo odepřen, na základě. Další informace o tom, jak funguje zásad autorizace najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [Autorizace přístupu k operacím služby](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [Postupy: Vytvoření vlastního správce autorizace pro službu](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [\<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [Zásady autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md)
