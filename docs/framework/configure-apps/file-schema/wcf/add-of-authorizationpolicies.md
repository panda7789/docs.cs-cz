---
title: "&lt;add&gt; – &lt;authorizationPolicies&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 613a03d8-4384-4556-bce2-8c23286c0bb0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d835d96c89e8b292fc2c038794aa4056fda3a095
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltauthorizationpoliciesgt"></a><span data-ttu-id="3276c-102">&lt;add&gt; – &lt;authorizationPolicies&gt;</span><span class="sxs-lookup"><span data-stu-id="3276c-102">&lt;add&gt; of &lt;authorizationPolicies&gt;</span></span>
<span data-ttu-id="3276c-103">Určuje zásad autorizace pro transformace deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3276c-103">Specifies an authorization policy for claim transformation.</span></span>  
  
 <span data-ttu-id="3276c-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3276c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3276c-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3276c-105">\<behaviors></span></span>  
<span data-ttu-id="3276c-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="3276c-106">\<behavior></span></span>  
<span data-ttu-id="3276c-107">\<serviceAuthorization ></span><span class="sxs-lookup"><span data-stu-id="3276c-107">\<serviceAuthorization></span></span>  
<span data-ttu-id="3276c-108">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="3276c-108">\<authorizationPolicies></span></span>  
<span data-ttu-id="3276c-109">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="3276c-109">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3276c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3276c-110">Syntax</span></span>  
  
```xml  
<authorizationPolicies>  
   <add policyType="String" />  
</authorizationPolicies>  
```  
  
## <a name="type"></a><span data-ttu-id="3276c-111">Typ</span><span class="sxs-lookup"><span data-stu-id="3276c-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3276c-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3276c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="3276c-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3276c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3276c-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="3276c-114">Attributes</span></span>  
  
|<span data-ttu-id="3276c-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="3276c-115">Attribute</span></span>|<span data-ttu-id="3276c-116">Popis</span><span class="sxs-lookup"><span data-stu-id="3276c-116">Description</span></span>|  
|---------------|-----------------|  
|`policyType`|<span data-ttu-id="3276c-117">Požadovaný atribut řetězec.</span><span class="sxs-lookup"><span data-stu-id="3276c-117">A required String attribute.</span></span><br /><br /> <span data-ttu-id="3276c-118">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Model řízení přístupu podporuje sadu zásad autorizace jako typy zřizování.</span><span class="sxs-lookup"><span data-stu-id="3276c-118">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] access control model supports provisioning a set of authorization policies as types.</span></span> <span data-ttu-id="3276c-119">Tento atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3276c-119">This attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3276c-120">Řízení přístupu může být povolen nebo odepřen, na základě.</span><span class="sxs-lookup"><span data-stu-id="3276c-120">Access control can be granted or denied based on that.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3276c-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3276c-121">Child Elements</span></span>  
 <span data-ttu-id="3276c-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="3276c-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3276c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3276c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3276c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3276c-124">Element</span></span>|<span data-ttu-id="3276c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3276c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3276c-126">\<authorizationPolicies ></span><span class="sxs-lookup"><span data-stu-id="3276c-126">\<authorizationPolicies></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authorizationpolicies.md)|<span data-ttu-id="3276c-127">Určuje kolekci typů zásad autorizace.</span><span class="sxs-lookup"><span data-stu-id="3276c-127">Specifies a collection of authorization policy types.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3276c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3276c-128">Remarks</span></span>  
 <span data-ttu-id="3276c-129">Každá zásada autorizace obsahuje jediný požadované `policyType` atribut, který obsahuje řetězec.</span><span class="sxs-lookup"><span data-stu-id="3276c-129">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="3276c-130">Atribut určuje zásad autorizace, která umožňuje transformace jednu sadu vstupních deklarací identity na jinou sadu deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="3276c-130">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="3276c-131">Řízení přístupu může být povolen nebo odepřen, na základě.</span><span class="sxs-lookup"><span data-stu-id="3276c-131">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="3276c-132">Další informace o tom, jak funguje zásad autorizace najdete v tématu <xref:System.IdentityModel.Policy.IAuthorizationPolicy> a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="3276c-132">For more information on how an authorization policy works, see <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3276c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="3276c-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>  
 <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement.AuthorizationPolicies%2A>  
 <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElementCollection>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 [<span data-ttu-id="3276c-134">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="3276c-134">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)  
 [<span data-ttu-id="3276c-135">Postupy: vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="3276c-135">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [<span data-ttu-id="3276c-136">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="3276c-136">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-authorizationpolicies.md)  
 [<span data-ttu-id="3276c-137">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="3276c-137">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
