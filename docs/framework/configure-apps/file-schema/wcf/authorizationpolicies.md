---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69926463"
---
# \<authorizationPolicies>
Tento oddíl konfigurace obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` klíčového slova. Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec. Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací. Řízení přístupu lze na základě této aplikace udělit nebo odepřít. Další informace o tom, jak zásady autorizace fungují, najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásadách autorizace](../../../wcf/samples/authorization-policy.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [Autorizace přístupu k operacím služby](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [Postupy: Vytvoření vlastního správce autorizace pro službu](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [Zásada autorizace](../../../wcf/samples/authorization-policy.md)
