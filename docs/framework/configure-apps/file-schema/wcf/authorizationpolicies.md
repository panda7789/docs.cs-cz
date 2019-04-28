---
title: <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 5b367489-54d7-408b-8f56-cb157dd68eaf
ms.openlocfilehash: 2910f47b85ee67694cae0c3a725c3c7c7b3803c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701720"
---
# <a name="authorizationpolicies"></a><span data-ttu-id="14725-101">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="14725-101">\<authorizationPolicies></span></span>
<span data-ttu-id="14725-102">Tento oddíl konfigurace obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="14725-102">This configuration section contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="14725-103">Každá zásada autorizace obsahuje jediný vyžaduje `policyType` atribut, který není řetězec.</span><span class="sxs-lookup"><span data-stu-id="14725-103">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="14725-104">Atribut určuje zásadu autorizace, který umožňuje transformovat jednu sadu vstupních deklarací identity do jiné sady deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="14725-104">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="14725-105">Může být povolen nebo odepřen řízení přístupu na základě.</span><span class="sxs-lookup"><span data-stu-id="14725-105">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="14725-106">Další informace o tom, jak funguje zásad autorizace najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="14725-106">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14725-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14725-107">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="14725-108">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="14725-108">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="14725-109">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="14725-109">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="14725-110">\<add></span><span class="sxs-lookup"><span data-stu-id="14725-110">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="14725-111">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="14725-111">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
