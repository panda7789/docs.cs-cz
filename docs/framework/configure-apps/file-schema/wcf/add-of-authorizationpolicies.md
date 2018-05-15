---
title: '&lt;add&gt; – &lt;authorizationPolicies&gt;'
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: 008f465134860141293776130ebd75cd39120f5e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="05916-102">&lt;add&gt; – &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="05916-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="05916-103">Určuje zásad autorizace pro transformace deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="05916-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="05916-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="05916-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="05916-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="05916-105">\<behaviors></span></span>  
<span data-ttu-id="05916-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="05916-106">\<behavior></span></span>  
<span data-ttu-id="05916-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="05916-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="05916-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="05916-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="05916-109">\<add></span><span class="sxs-lookup"><span data-stu-id="05916-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05916-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05916-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="05916-111">Typ</span><span class="sxs-lookup"><span data-stu-id="05916-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05916-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05916-112">Attributes and Elements</span></span>  
 <span data-ttu-id="05916-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05916-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05916-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="05916-114">Attributes</span></span>  
  
|<span data-ttu-id="05916-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="05916-115">Attribute</span></span>|<span data-ttu-id="05916-116">Popis</span><span class="sxs-lookup"><span data-stu-id="05916-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="05916-117">Požadovaný atribut řetězec.</span><span class="sxs-lookup"><span data-stu-id="05916-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="05916-118">Model řízení přístupu Windows Communication Foundation (WCF) podporuje sadu zásad autorizace jako typy zřizování.</span><span class="sxs-lookup"><span data-stu-id="05916-118">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="05916-119">Tento atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="05916-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="05916-120">Řízení přístupu může být povolen nebo odepřen, na základě.</span><span class="sxs-lookup"><span data-stu-id="05916-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05916-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05916-121">Child Elements</span></span>  
 <span data-ttu-id="05916-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="05916-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05916-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05916-123">Parent Elements</span></span>  
  
|<span data-ttu-id="05916-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="05916-124">Element</span></span>|<span data-ttu-id="05916-125">Popis</span><span class="sxs-lookup"><span data-stu-id="05916-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05916-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="05916-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="05916-127">Určuje kolekci typů zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="05916-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05916-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05916-128">Remarks</span></span>  
 <span data-ttu-id="05916-129">Každá zásada autorizace obsahuje jediný požadované `policyType` atribut, který obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="05916-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="05916-130">Atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="05916-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="05916-131">Řízení přístupu může být povolen nebo odepřen, na základě.</span><span class="sxs-lookup"><span data-stu-id="05916-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="05916-132">Další informace o tom, jak funguje zásad autorizace najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="05916-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05916-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="05916-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="05916-134">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="05916-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="05916-135">Postupy: Vytvoření vlastního správce autorizace pro službu</span><span class="sxs-lookup"><span data-stu-id="05916-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="05916-136">\<add></span><span class="sxs-lookup"><span data-stu-id="05916-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="05916-137">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="05916-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
