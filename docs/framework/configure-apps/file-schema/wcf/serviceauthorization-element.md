---
title: <serviceAuthorization> – element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: b73e2049afb460bf9be8b76ee272ba0547b61453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936401"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="7707b-102">\<serviceAuthorization – element ></span><span class="sxs-lookup"><span data-stu-id="7707b-102">\<serviceAuthorization> element</span></span>
<span data-ttu-id="7707b-103">Určuje nastavení, které autorizují přístup k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="7707b-103">Specifies settings that authorize access to service operations</span></span>  
  
 <span data-ttu-id="7707b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7707b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7707b-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="7707b-105">\<behaviors></span></span>  
<span data-ttu-id="7707b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7707b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7707b-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="7707b-107">\<behavior></span></span>  
<span data-ttu-id="7707b-108">\<serviceAuthorization></span><span class="sxs-lookup"><span data-stu-id="7707b-108">\<serviceAuthorization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7707b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7707b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7707b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7707b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7707b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7707b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7707b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7707b-112">Attributes</span></span>  
  
|<span data-ttu-id="7707b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7707b-113">Attribute</span></span>|<span data-ttu-id="7707b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7707b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7707b-115">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="7707b-115">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="7707b-116">Logická hodnota, která určuje, zda všechny operace ve službě zosobňuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="7707b-116">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="7707b-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="7707b-117">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7707b-118">Když konkrétní operace služby zosobňuje volajícího, kontext vlákna je přepnut na volající kontext před spuštěním zadané služby.</span><span class="sxs-lookup"><span data-stu-id="7707b-118">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="7707b-119">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="7707b-119">principalPermissionMode</span></span>|<span data-ttu-id="7707b-120">Nastaví objekt zabezpečení, který se používá k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="7707b-120">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="7707b-121">Mezi hodnoty patří následující:</span><span class="sxs-lookup"><span data-stu-id="7707b-121">Values include the following:</span></span><br /><br /> <span data-ttu-id="7707b-122">-None</span><span class="sxs-lookup"><span data-stu-id="7707b-122">-   None</span></span><br /><span data-ttu-id="7707b-123">-   UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="7707b-123">-   UseWindowsGroups</span></span><br /><span data-ttu-id="7707b-124">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="7707b-124">-   UseAspNetRoles</span></span><br /><span data-ttu-id="7707b-125">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="7707b-125">-   Custom</span></span><br /><br /> <span data-ttu-id="7707b-126">Výchozí hodnota je UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="7707b-126">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="7707b-127">Hodnota je typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="7707b-127">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="7707b-128">Další informace o použití tohoto atributu naleznete v tématu [How to: Omezte přístup pomocí třídy](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)PrincipalPermissionAttribute.</span><span class="sxs-lookup"><span data-stu-id="7707b-128">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="7707b-129">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="7707b-129">roleProviderName</span></span>|<span data-ttu-id="7707b-130">Řetězec, který určuje název poskytovatele rolí, který poskytuje informace o rolích pro aplikaci Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7707b-130">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="7707b-131">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="7707b-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="7707b-132">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="7707b-132">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="7707b-133">Řetězec obsahující typ Správce autorizací služby.</span><span class="sxs-lookup"><span data-stu-id="7707b-133">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="7707b-134">Další informace naleznete v tématu <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="7707b-134">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7707b-135">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7707b-135">Child Elements</span></span>  
  
|<span data-ttu-id="7707b-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="7707b-136">Element</span></span>|<span data-ttu-id="7707b-137">Popis</span><span class="sxs-lookup"><span data-stu-id="7707b-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7707b-138">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="7707b-138">authorizationPolicies</span></span>|<span data-ttu-id="7707b-139">Obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="7707b-139">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="7707b-140">Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="7707b-140">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="7707b-141">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="7707b-141">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="7707b-142">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="7707b-142">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="7707b-143">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="7707b-143">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7707b-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7707b-144">Parent Elements</span></span>  
  
|<span data-ttu-id="7707b-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="7707b-145">Element</span></span>|<span data-ttu-id="7707b-146">Popis</span><span class="sxs-lookup"><span data-stu-id="7707b-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7707b-147">\<> chování</span><span class="sxs-lookup"><span data-stu-id="7707b-147">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7707b-148">Obsahuje kolekci nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="7707b-148">Contains a collection of settings for the behavior of a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7707b-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7707b-149">Remarks</span></span>  
 <span data-ttu-id="7707b-150">Tato část obsahuje prvky ovlivňující autorizaci, vlastní poskytovatele rolí a zosobnění.</span><span class="sxs-lookup"><span data-stu-id="7707b-150">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="7707b-151">`principalPermissionMode` Atribut určuje skupiny uživatelů, které se mají použít při autorizaci použití chráněné metody.</span><span class="sxs-lookup"><span data-stu-id="7707b-151">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="7707b-152">Výchozí hodnota je `UseWindowsGroups` a určí, že se při pokusu o přístup k prostředku prohledávají skupiny systému Windows, například správci nebo uživatelé.</span><span class="sxs-lookup"><span data-stu-id="7707b-152">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="7707b-153">Můžete také určit `UseAspNetRoles` , že chcete použít vlastního poskytovatele rolí, který je nakonfigurován \<pod prvkem System. Web >, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7707b-153">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code.</span></span>  
  
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
  
 <span data-ttu-id="7707b-154">Následující kód ukazuje, že `roleProviderName` se používá `principalPermissionMode` s atributem.</span><span class="sxs-lookup"><span data-stu-id="7707b-154">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```  
  
 <span data-ttu-id="7707b-155">Podrobný příklad použití tohoto prvku konfigurace najdete v tématu [autorizace přístupu k operacím služby](../../../wcf/samples/authorizing-access-to-service-operations.md) a zásadám [autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="7707b-155">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7707b-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7707b-156">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="7707b-157">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7707b-157">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7707b-158">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="7707b-158">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="7707b-159">Postupy: Vytvoření vlastního Správce autorizací pro službu</span><span class="sxs-lookup"><span data-stu-id="7707b-159">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="7707b-160">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="7707b-160">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="7707b-161">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="7707b-161">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
