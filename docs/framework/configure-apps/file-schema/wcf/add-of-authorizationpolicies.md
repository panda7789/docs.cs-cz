---
title: <add> z <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400690"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="9e7f6-102">\<Přidat > \<> authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="9e7f6-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="9e7f6-103">Určuje zásadu autorizace pro transformaci deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-103">Specifies an authorization policy for claim transformation.</span></span>  
  
<span data-ttu-id="9e7f6-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9e7f6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9e7f6-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9e7f6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9e7f6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9e7f6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9e7f6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9e7f6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="9e7f6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9e7f6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="9e7f6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceAuthorization >** ](serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="9e7f6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)</span></span>\
<span data-ttu-id="9e7f6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authorizationPolicies >** ](authorizationpolicies.md)</span><span class="sxs-lookup"><span data-stu-id="9e7f6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)</span></span>\
<span data-ttu-id="9e7f6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="9e7f6-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7f6-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e7f6-112">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="9e7f6-113">type</span><span class="sxs-lookup"><span data-stu-id="9e7f6-113">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e7f6-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9e7f6-114">Attributes and Elements</span></span>  
 <span data-ttu-id="9e7f6-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e7f6-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="9e7f6-116">Attributes</span></span>  
  
|<span data-ttu-id="9e7f6-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="9e7f6-117">Attribute</span></span>|<span data-ttu-id="9e7f6-118">Popis</span><span class="sxs-lookup"><span data-stu-id="9e7f6-118">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="9e7f6-119">Povinný atribut typu řetězec.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-119">A required String attribute.</span></span><br /><br /> <span data-ttu-id="9e7f6-120">Model řízení přístupu Windows Communication Foundation (WCF) podporuje zřizování sady zásad autorizace jako typů.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-120">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="9e7f6-121">Tento atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-121">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="9e7f6-122">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-122">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e7f6-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9e7f6-123">Child Elements</span></span>  
 <span data-ttu-id="9e7f6-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="9e7f6-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e7f6-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9e7f6-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9e7f6-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="9e7f6-126">Element</span></span>|<span data-ttu-id="9e7f6-127">Popis</span><span class="sxs-lookup"><span data-stu-id="9e7f6-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9e7f6-128">\<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="9e7f6-128">\<authorizationPolicies></span></span>](authorizationpolicies.md)|<span data-ttu-id="9e7f6-129">Určuje kolekci typů zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-129">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e7f6-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e7f6-130">Remarks</span></span>  
 <span data-ttu-id="9e7f6-131">Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-131">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="9e7f6-132">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-132">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="9e7f6-133">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="9e7f6-133">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="9e7f6-134">Další informace o tom, jak zásady autorizace fungují, najdete <xref:System.IdentityModel.Policy.IAuthorizationPolicy> v tématu a [zásadách autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="9e7f6-134">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e7f6-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e7f6-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="9e7f6-136">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="9e7f6-136">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="9e7f6-137">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="9e7f6-137">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="9e7f6-138">\<add></span><span class="sxs-lookup"><span data-stu-id="9e7f6-138">\<add></span></span>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="9e7f6-139">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="9e7f6-139">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
