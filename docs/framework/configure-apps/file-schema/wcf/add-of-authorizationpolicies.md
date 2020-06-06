---
title: <add> z <authorizationPolicies>
ms.date: 03/30/2017
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
ms.openlocfilehash: e2597bc51e788c919bfe3ce3422ae2911cc6b33b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400690"
---
# <a name="add-of-authorizationpolicies"></a><span data-ttu-id="ee142-102">\<add> z \<authorizationPolicies></span><span class="sxs-lookup"><span data-stu-id="ee142-102">\<add> of \<authorizationPolicies></span></span>
<span data-ttu-id="ee142-103">Určuje zásadu autorizace pro transformaci deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="ee142-103">Specifies an authorization policy for claim transformation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceAuthorization>**](serviceauthorization-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<authorizationPolicies>**](authorizationpolicies.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="ee142-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee142-104">Syntax</span></span>  
  
```xml  
<authorizationPolicies>
  <add policyType="String" />
</authorizationPolicies>
```  
  
## <a name="type"></a><span data-ttu-id="ee142-105">Typ</span><span class="sxs-lookup"><span data-stu-id="ee142-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ee142-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ee142-106">Attributes and Elements</span></span>  
 <span data-ttu-id="ee142-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ee142-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ee142-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="ee142-108">Attributes</span></span>  
  
|<span data-ttu-id="ee142-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="ee142-109">Attribute</span></span>|<span data-ttu-id="ee142-110">Popis</span><span class="sxs-lookup"><span data-stu-id="ee142-110">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="ee142-111">Povinný atribut typu řetězec.</span><span class="sxs-lookup"><span data-stu-id="ee142-111">A required String attribute.</span></span><br /><br /> <span data-ttu-id="ee142-112">Model řízení přístupu Windows Communication Foundation (WCF) podporuje zřizování sady zásad autorizace jako typů.</span><span class="sxs-lookup"><span data-stu-id="ee142-112">The Windows Communication Foundation (WCF) access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="ee142-113">Tento atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="ee142-113">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="ee142-114">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="ee142-114">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ee142-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ee142-115">Child Elements</span></span>  
 <span data-ttu-id="ee142-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="ee142-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ee142-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ee142-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ee142-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="ee142-118">Element</span></span>|<span data-ttu-id="ee142-119">Description</span><span class="sxs-lookup"><span data-stu-id="ee142-119">Description</span></span>|  
|-------------|-----------------|  
|[\<authorizationPolicies>](authorizationpolicies.md)|<span data-ttu-id="ee142-120">Určuje kolekci typů zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="ee142-120">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee142-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee142-121">Remarks</span></span>  
 <span data-ttu-id="ee142-122">Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="ee142-122">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="ee142-123">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="ee142-123">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="ee142-124">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="ee142-124">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="ee142-125">Další informace o tom, jak zásady autorizace fungují, najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásadách autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="ee142-125">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee142-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee142-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>
- <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- [<span data-ttu-id="ee142-127">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="ee142-127">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="ee142-128">Postupy: Vytvoření vlastního správce autorizace pro službu</span><span class="sxs-lookup"><span data-stu-id="ee142-128">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [\<add>](add-of-authorizationpolicies.md)
- [<span data-ttu-id="ee142-129">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="ee142-129">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
