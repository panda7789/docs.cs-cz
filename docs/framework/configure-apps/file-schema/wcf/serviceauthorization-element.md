---
title: Element &lt;serviceAuthorization&gt;
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: 49b89c17f9858c111791276fe15e4a418845c8e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622569"
---
# <a name="ltserviceauthorizationgt-element"></a><span data-ttu-id="dedc9-102">Element &lt;serviceAuthorization&gt;</span><span class="sxs-lookup"><span data-stu-id="dedc9-102">&lt;serviceAuthorization&gt; element</span></span>
<span data-ttu-id="dedc9-103">Určuje nastavení, které povolují přístup k operacím služby</span><span class="sxs-lookup"><span data-stu-id="dedc9-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="dedc9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dedc9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dedc9-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dedc9-105">\<behaviors></span></span>  
<span data-ttu-id="dedc9-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="dedc9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="dedc9-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="dedc9-107">\<behavior></span></span>  
<span data-ttu-id="dedc9-108">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="dedc9-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dedc9-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dedc9-109">Syntax</span></span>  
  
```xml  
<serviceAuthorization impersonateCallerForAllOperations="Boolean"
                      principalPermissionMode="None/UseWindowsGroups/UseAspNetRoles/Custom"
                      roleProviderName="String"
                      serviceAuthorizationManagerType="String">
  <authorizationPolicies>
    <add policyType="String" />
  </authorizationPolicies>
</serviceAuthorization>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dedc9-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dedc9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dedc9-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dedc9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dedc9-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="dedc9-112">Attributes</span></span>  
  
|<span data-ttu-id="dedc9-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="dedc9-113">Attribute</span></span>|<span data-ttu-id="dedc9-114">Popis</span><span class="sxs-lookup"><span data-stu-id="dedc9-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dedc9-115">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="dedc9-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="dedc9-116">Logická hodnota určující, pokud všechny operace služby zosobňují volajícího.</span><span class="sxs-lookup"><span data-stu-id="dedc9-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="dedc9-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="dedc9-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="dedc9-118">Když konkrétní operaci služby zosobňuje volajícího, kontext vlákna přepnutí na kontext volající před provedením zadaná služba.</span><span class="sxs-lookup"><span data-stu-id="dedc9-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="dedc9-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="dedc9-119">principalPermissionMode</span></span>|<span data-ttu-id="dedc9-120">Nastaví objekt zabezpečení použitý k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="dedc9-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="dedc9-121">Následující hodnoty:</span><span class="sxs-lookup"><span data-stu-id="dedc9-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="dedc9-122">-Žádný</span><span class="sxs-lookup"><span data-stu-id="dedc9-122">-   None</span></span><br /><span data-ttu-id="dedc9-123">-   UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="dedc9-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="dedc9-124">-UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="dedc9-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="dedc9-125">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="dedc9-125">-   Custom</span></span><br /><br /> <span data-ttu-id="dedc9-126">Výchozí hodnota je UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="dedc9-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="dedc9-127">Hodnota je typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="dedc9-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="dedc9-128">Další informace o použití tohoto atributu naleznete v tématu [jak: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="dedc9-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="dedc9-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="dedc9-129">roleProviderName</span></span>|<span data-ttu-id="dedc9-130">Řetězec určující název poskytovatele rolí, který poskytuje informace o rolích pro aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dedc9-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="dedc9-131">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="dedc9-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="dedc9-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="dedc9-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="dedc9-133">Řetězec obsahující typ správce autorizace služby.</span><span class="sxs-lookup"><span data-stu-id="dedc9-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="dedc9-134">Další informace naleznete v tématu <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="dedc9-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dedc9-135">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dedc9-135">Child Elements</span></span>  
  
|<span data-ttu-id="dedc9-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="dedc9-136">Element</span></span>|<span data-ttu-id="dedc9-137">Popis</span><span class="sxs-lookup"><span data-stu-id="dedc9-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dedc9-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="dedc9-138">authorizationPolicies</span></span>|<span data-ttu-id="dedc9-139">Obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="dedc9-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="dedc9-140">Každá zásada autorizace obsahuje jediný vyžaduje `policyType` atribut, který není řetězec.</span><span class="sxs-lookup"><span data-stu-id="dedc9-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="dedc9-141">Atribut určuje zásadu autorizace, který umožňuje transformovat jednu sadu vstupních deklarací identity do jiné sady deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="dedc9-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="dedc9-142">Může být povolen nebo odepřen řízení přístupu na základě.</span><span class="sxs-lookup"><span data-stu-id="dedc9-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="dedc9-143">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="dedc9-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dedc9-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dedc9-144">Parent Elements</span></span>  
  
|<span data-ttu-id="dedc9-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="dedc9-145">Element</span></span>|<span data-ttu-id="dedc9-146">Popis</span><span class="sxs-lookup"><span data-stu-id="dedc9-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dedc9-147">\<behavior></span><span class="sxs-lookup"><span data-stu-id="dedc9-147">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="dedc9-148">Obsahuje kolekci nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="dedc9-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dedc9-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dedc9-149">Remarks</span></span>  
 <span data-ttu-id="dedc9-150">Tato část obsahuje prvky, které by to ovlivnilo autorizace, vlastní roli zprostředkovatele a zosobnění.</span><span class="sxs-lookup"><span data-stu-id="dedc9-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="dedc9-151">`principalPermissionMode` Atribut určuje skupiny uživatelů při použití chráněné metody ověřování.</span><span class="sxs-lookup"><span data-stu-id="dedc9-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="dedc9-152">Výchozí hodnota je `UseWindowsGroups` a určuje, že skupin Windows, jako je například "Administrators" nebo "Uživatelé," se vyhledávají identitu při pokusu o přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="dedc9-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="dedc9-153">Můžete také určit `UseAspNetRoles` používat vlastní role poskytovatele, který je nakonfigurovaný pod \<system.web > element, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="dedc9-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
```xml  
<system.web>
  <membership defaultProvider="SqlProvider"
              userIsOnlineTimeWindow="15">
    <providers>
      <clear />
      <add name="SqlProvider"
           type="System.Web.Security.SqlMembershipProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipProvider"
           enablePasswordRetrieval="false"
           enablePasswordReset="false"
           requiresQuestionAndAnswer="false"
           requiresUniqueEmail="true"
           passwordFormat="Hashed" />
    </providers>
  </membership>
  <!-- Other configuration code not shown. -->
</system.web>
```  
  
 <span data-ttu-id="dedc9-154">Následující kód ukazuje `roleProviderName` použít s `principalPermissionMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="dedc9-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="dedc9-155">Podrobný příklad použití tento prvek konfigurace, najdete v části [autorizace přístupu k operacím služby](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) a [zásad autorizace](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="dedc9-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedc9-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dedc9-156">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="dedc9-157">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="dedc9-157">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="dedc9-158">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="dedc9-158">Authorizing Access to Service Operations</span></span>](../../../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="dedc9-159">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="dedc9-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="dedc9-160">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="dedc9-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="dedc9-161">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="dedc9-161">Authorization Policy</span></span>](../../../../../docs/framework/wcf/samples/authorization-policy.md)
