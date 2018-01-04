---
title: '&lt;authorizationPolicies&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e33dca28f11b564f622ff1c202827c693f0874c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltauthorizationpoliciesgt"></a>&lt;authorizationPolicies&gt;
Tento konfigurační oddíl obsahuje kolekci typů zásad autorizace, které lze přidat pomocí `add` – klíčové slovo. Každá zásada autorizace obsahuje jediný požadované `policyType` atribut, který obsahuje řetězec. Atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity. Řízení přístupu může být povolen nebo odepřen, na základě. Další informace o tom, jak funguje zásad autorizace najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).  
  
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
