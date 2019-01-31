---
title: <add> z <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 6a1a7d6b1ef9732e015536d8a78c058fe348113f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255494"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="3e913-102">\<Přidat > z \<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="3e913-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="3e913-103">Určuje zásadu autorizace pro transformaci deklarace.</span><span class="sxs-lookup"><span data-stu-id="3e913-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="3e913-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3e913-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3e913-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3e913-105">\<behaviors></span></span>  
<span data-ttu-id="3e913-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3e913-106">\<behavior></span></span>  
<span data-ttu-id="3e913-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="3e913-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="3e913-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="3e913-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="3e913-109">\<add></span><span class="sxs-lookup"><span data-stu-id="3e913-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e913-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e913-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="3e913-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3e913-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e913-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3e913-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3e913-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3e913-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e913-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="3e913-114">Attributes</span></span>  
  
|<span data-ttu-id="3e913-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="3e913-115">Attribute</span></span>|<span data-ttu-id="3e913-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3e913-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="3e913-117">Povinný atribut řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e913-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="3e913-118">Model řízení přístupu služby Windows Communication Foundation (WCF) podporuje vytváření sady zásad autorizace jako typů.</span><span class="sxs-lookup"><span data-stu-id="3e913-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="3e913-119">Tento atribut určuje zásadu autorizace, který umožňuje transformovat jednu sadu vstupních deklarací identity do jiné sady deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3e913-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3e913-120">Může být povolen nebo odepřen řízení přístupu na základě.</span><span class="sxs-lookup"><span data-stu-id="3e913-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e913-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3e913-121">Child Elements</span></span>  
 <span data-ttu-id="3e913-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="3e913-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e913-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3e913-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3e913-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3e913-124">Element</span></span>|<span data-ttu-id="3e913-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3e913-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e913-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="3e913-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="3e913-127">Určuje kolekci typů zásad autorizací.</span><span class="sxs-lookup"><span data-stu-id="3e913-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e913-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e913-128">Remarks</span></span>  
 <span data-ttu-id="3e913-129">Každá zásada autorizace obsahuje jediný vyžaduje `policyType` atribut, který není řetězec.</span><span class="sxs-lookup"><span data-stu-id="3e913-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="3e913-130">Atribut určuje zásadu autorizace, který umožňuje transformovat jednu sadu vstupních deklarací identity do jiné sady deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3e913-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3e913-131">Může být povolen nebo odepřen řízení přístupu na základě.</span><span class="sxs-lookup"><span data-stu-id="3e913-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="3e913-132">Další informace o tom, jak funguje zásad autorizace najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="3e913-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e913-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e913-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="3e913-134">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="3e913-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="3e913-135">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="3e913-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="3e913-136">\<add></span><span class="sxs-lookup"><span data-stu-id="3e913-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)
- [<span data-ttu-id="3e913-137">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="3e913-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
