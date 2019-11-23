---
title: <serviceAuthorization> – element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834012"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="06655-102">\<element > serviceAuthorization</span><span class="sxs-lookup"><span data-stu-id="06655-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="06655-103">Určuje nastavení, které autorizují přístup k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="06655-103">Specifies settings that authorize access to service operations</span></span>

<span data-ttu-id="06655-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="06655-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="06655-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="06655-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="06655-106">&nbsp;&nbsp;&nbsp;&nbsp;[**chování**](behaviors.md)\<></span><span class="sxs-lookup"><span data-stu-id="06655-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="06655-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="06655-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="06655-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<chování**](behavior-of-servicebehaviors.md) ></span><span class="sxs-lookup"><span data-stu-id="06655-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="06655-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceAuthorization >**</span><span class="sxs-lookup"><span data-stu-id="06655-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="06655-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06655-110">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="06655-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="06655-111">Attributes and elements</span></span>

<span data-ttu-id="06655-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky:</span><span class="sxs-lookup"><span data-stu-id="06655-112">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="06655-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="06655-113">Attributes</span></span>

|<span data-ttu-id="06655-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="06655-114">Attribute</span></span>|<span data-ttu-id="06655-115">Popis</span><span class="sxs-lookup"><span data-stu-id="06655-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06655-116">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="06655-116">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="06655-117">Logická hodnota, která určuje, zda všechny operace ve službě zosobňuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="06655-117">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="06655-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="06655-118">The default is `false`.</span></span><br /><br /> <span data-ttu-id="06655-119">Když konkrétní operace služby zosobňuje volajícího, kontext vlákna je přepnut na volající kontext před spuštěním zadané služby.</span><span class="sxs-lookup"><span data-stu-id="06655-119">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="06655-120">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="06655-120">principalPermissionMode</span></span>|<span data-ttu-id="06655-121">Nastaví objekt zabezpečení, který se používá k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="06655-121">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="06655-122">Mezi hodnoty patří následující:</span><span class="sxs-lookup"><span data-stu-id="06655-122">Values include the following:</span></span><br /><br /> <span data-ttu-id="06655-123">-None</span><span class="sxs-lookup"><span data-stu-id="06655-123">-   None</span></span><br /><span data-ttu-id="06655-124">-   UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="06655-124">-   UseWindowsGroups</span></span><br /><span data-ttu-id="06655-125">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="06655-125">-   UseAspNetRoles</span></span><br /><span data-ttu-id="06655-126">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="06655-126">-   Custom</span></span><br /><br /> <span data-ttu-id="06655-127">Výchozí hodnota je UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="06655-127">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="06655-128">Hodnota je typu <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span><span class="sxs-lookup"><span data-stu-id="06655-128">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="06655-129">Další informace o použití tohoto atributu naleznete v tématu [How to: restrict Access with a PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="06655-129">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="06655-130">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="06655-130">roleProviderName</span></span>|<span data-ttu-id="06655-131">Řetězec, který určuje název poskytovatele rolí, který poskytuje informace o rolích pro aplikaci Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="06655-131">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="06655-132">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="06655-132">The default is an empty string.</span></span>|  
|<span data-ttu-id="06655-133">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="06655-133">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="06655-134">Řetězec obsahující typ Správce autorizací služby.</span><span class="sxs-lookup"><span data-stu-id="06655-134">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="06655-135">Další informace najdete v tématu <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="06655-135">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="06655-136">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="06655-136">Child elements</span></span>

|<span data-ttu-id="06655-137">Prvek</span><span class="sxs-lookup"><span data-stu-id="06655-137">Element</span></span>|<span data-ttu-id="06655-138">Popis</span><span class="sxs-lookup"><span data-stu-id="06655-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06655-139">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="06655-139">authorizationPolicies</span></span>|<span data-ttu-id="06655-140">Obsahuje kolekci typů zásad autorizací, které lze přidat pomocí klíčového slova `add`.</span><span class="sxs-lookup"><span data-stu-id="06655-140">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="06655-141">Každá zásada autorizace obsahuje jeden povinný atribut `policyType`, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="06655-141">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="06655-142">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="06655-142">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="06655-143">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="06655-143">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="06655-144">Další informace najdete v tématu <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="06655-144">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="06655-145">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="06655-145">Parent elements</span></span>

|<span data-ttu-id="06655-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="06655-146">Element</span></span>|<span data-ttu-id="06655-147">Popis</span><span class="sxs-lookup"><span data-stu-id="06655-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06655-148">chování \<></span><span class="sxs-lookup"><span data-stu-id="06655-148">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="06655-149">Obsahuje kolekci nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="06655-149">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="06655-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06655-150">Remarks</span></span>

<span data-ttu-id="06655-151">Tato část obsahuje prvky ovlivňující autorizaci, vlastní poskytovatele rolí a zosobnění.</span><span class="sxs-lookup"><span data-stu-id="06655-151">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="06655-152">Atribut `principalPermissionMode` určuje skupiny uživatelů, které se mají použít při autorizaci použití chráněné metody.</span><span class="sxs-lookup"><span data-stu-id="06655-152">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="06655-153">Výchozí hodnota je `UseWindowsGroups` a určí, že se při pokusu o přístup k prostředku prohledávají skupiny systému Windows, například "správci" nebo "uživatelé".</span><span class="sxs-lookup"><span data-stu-id="06655-153">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="06655-154">Můžete také zadat `UseAspNetRoles` pro použití vlastního poskytovatele rolí, který je nakonfigurován v rámci elementu \<System. Web >, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="06655-154">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="06655-155">Následující kód ukazuje `roleProviderName` použit s atributem `principalPermissionMode`:</span><span class="sxs-lookup"><span data-stu-id="06655-155">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="06655-156">Podrobný příklad použití tohoto prvku konfigurace najdete v tématu [autorizace přístupu k operacím služby](../../../wcf/samples/authorizing-access-to-service-operations.md) a [zásadám autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="06655-156">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="06655-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06655-157">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="06655-158">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="06655-158">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="06655-159">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="06655-159">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="06655-160">Postupy: Vytvoření vlastního správce autorizace pro službu</span><span class="sxs-lookup"><span data-stu-id="06655-160">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="06655-161">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="06655-161">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="06655-162">Zásady autorizace</span><span class="sxs-lookup"><span data-stu-id="06655-162">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
