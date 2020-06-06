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
<span data-ttu-id="fec43-101">Tento oddíl konfigurace obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="fec43-101">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="fec43-102">Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="fec43-102">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="fec43-103">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="fec43-103">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="fec43-104">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="fec43-104">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="fec43-105">Další informace o tom, jak zásady autorizace fungují, najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásadách autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="fec43-105">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fec43-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="fec43-106">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="fec43-107">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="fec43-107">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="fec43-108">Postupy: Vytvoření vlastního správce autorizace pro službu</span><span class="sxs-lookup"><span data-stu-id="fec43-108">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="fec43-109">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="fec43-109">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
