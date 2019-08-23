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
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="4ecdc-102">\<Přidat > \<> authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="4ecdc-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="4ecdc-103">Určuje zásadu autorizace pro transformaci deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="4ecdc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4ecdc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4ecdc-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="4ecdc-105">\<behaviors></span></span>  
<span data-ttu-id="4ecdc-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="4ecdc-106">\<behavior></span></span>  
<span data-ttu-id="4ecdc-107">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="4ecdc-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="4ecdc-108">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="4ecdc-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="4ecdc-109">\<add></span><span class="sxs-lookup"><span data-stu-id="4ecdc-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ecdc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ecdc-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="4ecdc-111">type</span><span class="sxs-lookup"><span data-stu-id="4ecdc-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4ecdc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4ecdc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4ecdc-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4ecdc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="4ecdc-114">Attributes</span></span>  
  
|<span data-ttu-id="4ecdc-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="4ecdc-115">Attribute</span></span>|<span data-ttu-id="4ecdc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="4ecdc-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="4ecdc-117">Povinný atribut typu řetězec.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="4ecdc-118">Model řízení přístupu Windows Communication Foundation (WCF) podporuje zřizování sady zásad autorizace jako typů.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="4ecdc-119">Tento atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="4ecdc-120">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4ecdc-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4ecdc-121">Child Elements</span></span>  
 <span data-ttu-id="4ecdc-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="4ecdc-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4ecdc-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4ecdc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4ecdc-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="4ecdc-124">Element</span></span>|<span data-ttu-id="4ecdc-125">Popis</span><span class="sxs-lookup"><span data-stu-id="4ecdc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4ecdc-126">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="4ecdc-126">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="4ecdc-127">Určuje kolekci typů zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ecdc-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ecdc-128">Remarks</span></span>  
 <span data-ttu-id="4ecdc-129">Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="4ecdc-130">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="4ecdc-131">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="4ecdc-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="4ecdc-132">Další informace o tom, jak zásady autorizace fungují, najdete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> v tématu a [zásadách autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="4ecdc-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ecdc-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ecdc-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="4ecdc-134">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="4ecdc-134">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="4ecdc-135">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="4ecdc-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="4ecdc-136">\<add></span><span class="sxs-lookup"><span data-stu-id="4ecdc-136">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="4ecdc-137">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="4ecdc-137">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
