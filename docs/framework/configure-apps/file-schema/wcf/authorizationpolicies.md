---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 38d123a53b344ff1e4d781115093d0d1de5ae679
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926463"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="75be1-101">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="75be1-101">\<authorizationPolicies></span></span>
<span data-ttu-id="75be1-102">Tento oddíl konfigurace obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="75be1-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="75be1-103">Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="75be1-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="75be1-104">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="75be1-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="75be1-105">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="75be1-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="75be1-106">Další informace o tom, jak zásady autorizace fungují, najdete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> v tématu a [zásadách autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="75be1-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75be1-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75be1-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="75be1-108">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="75be1-108">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="75be1-109">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="75be1-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="75be1-110">\<add></span><span class="sxs-lookup"><span data-stu-id="75be1-110">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="75be1-111">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="75be1-111">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
