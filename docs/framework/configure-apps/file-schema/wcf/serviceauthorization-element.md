---
title: <serviceAuthorization> – element
ms.date: 03/30/2017
ms.assetid: 18cddad5-ddcb-4839-a0ac-1d6f6ab783ca
ms.openlocfilehash: f476f754a340f52859be2986e42754cba0ef3771
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "71834012"
---
# <a name="serviceauthorization-element"></a><span data-ttu-id="26b2d-102">\<serviceAuthorization> – element</span><span class="sxs-lookup"><span data-stu-id="26b2d-102">\<serviceAuthorization> element</span></span>

<span data-ttu-id="26b2d-103">Určuje nastavení, které autorizují přístup k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="26b2d-103">Specifies settings that authorize access to service operations</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthorization>**  

## <a name="syntax"></a><span data-ttu-id="26b2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26b2d-104">Syntax</span></span>

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

## <a name="attributes-and-elements"></a><span data-ttu-id="26b2d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="26b2d-105">Attributes and elements</span></span>

<span data-ttu-id="26b2d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky:</span><span class="sxs-lookup"><span data-stu-id="26b2d-106">The following sections describe attributes, child elements, and parent elements:</span></span>

### <a name="attributes"></a><span data-ttu-id="26b2d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="26b2d-107">Attributes</span></span>

|<span data-ttu-id="26b2d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="26b2d-108">Attribute</span></span>|<span data-ttu-id="26b2d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="26b2d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="26b2d-110">impersonateCallerForAllOperations</span><span class="sxs-lookup"><span data-stu-id="26b2d-110">impersonateCallerForAllOperations</span></span>|<span data-ttu-id="26b2d-111">Logická hodnota, která určuje, zda všechny operace ve službě zosobňuje volajícího.</span><span class="sxs-lookup"><span data-stu-id="26b2d-111">A Boolean value that specifies if all the operations in the service impersonate the caller.</span></span> <span data-ttu-id="26b2d-112">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="26b2d-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="26b2d-113">Když konkrétní operace služby zosobňuje volajícího, kontext vlákna je přepnut na volající kontext před spuštěním zadané služby.</span><span class="sxs-lookup"><span data-stu-id="26b2d-113">When a specific service operation impersonates the caller, the thread context is switched to the caller context before executing the specified service.</span></span>|  
|<span data-ttu-id="26b2d-114">principalPermissionMode</span><span class="sxs-lookup"><span data-stu-id="26b2d-114">principalPermissionMode</span></span>|<span data-ttu-id="26b2d-115">Nastaví objekt zabezpečení, který se používá k provádění operací na serveru.</span><span class="sxs-lookup"><span data-stu-id="26b2d-115">Sets the principal used to carry out operations on the server.</span></span> <span data-ttu-id="26b2d-116">Mezi hodnoty patří následující:</span><span class="sxs-lookup"><span data-stu-id="26b2d-116">Values include the following:</span></span><br /><br /> <span data-ttu-id="26b2d-117">-   Žádné</span><span class="sxs-lookup"><span data-stu-id="26b2d-117">-   None</span></span><br /><span data-ttu-id="26b2d-118">- UseWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="26b2d-118">-   UseWindowsGroups</span></span><br /><span data-ttu-id="26b2d-119">- UseAspNetRoles</span><span class="sxs-lookup"><span data-stu-id="26b2d-119">-   UseAspNetRoles</span></span><br /><span data-ttu-id="26b2d-120">– Vlastní</span><span class="sxs-lookup"><span data-stu-id="26b2d-120">-   Custom</span></span><br /><br /> <span data-ttu-id="26b2d-121">Výchozí hodnota je UseWindowsGroups.</span><span class="sxs-lookup"><span data-stu-id="26b2d-121">The default value is UseWindowsGroups.</span></span> <span data-ttu-id="26b2d-122">Hodnota je typu <xref:System.ServiceModel.Description.PrincipalPermissionMode> .</span><span class="sxs-lookup"><span data-stu-id="26b2d-122">The value is of type <xref:System.ServiceModel.Description.PrincipalPermissionMode>.</span></span> <span data-ttu-id="26b2d-123">Další informace o použití tohoto atributu naleznete v tématu [How to: restrict Access with a PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span><span class="sxs-lookup"><span data-stu-id="26b2d-123">For more information on using this attribute, see [How to: Restrict Access with the PrincipalPermissionAttribute Class](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md).</span></span>|  
|<span data-ttu-id="26b2d-124">roleProviderName</span><span class="sxs-lookup"><span data-stu-id="26b2d-124">roleProviderName</span></span>|<span data-ttu-id="26b2d-125">Řetězec, který určuje název poskytovatele rolí, který poskytuje informace o rolích pro aplikaci Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="26b2d-125">A string that specifies the name of the role provider, which provides role information for a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="26b2d-126">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="26b2d-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="26b2d-127">ServiceAuthorizationManagerType</span><span class="sxs-lookup"><span data-stu-id="26b2d-127">ServiceAuthorizationManagerType</span></span>|<span data-ttu-id="26b2d-128">Řetězec obsahující typ Správce autorizací služby.</span><span class="sxs-lookup"><span data-stu-id="26b2d-128">A string containing the type of the service authorization manager.</span></span> <span data-ttu-id="26b2d-129">Další informace naleznete v tématu <xref:System.ServiceModel.ServiceAuthorizationManager>.</span><span class="sxs-lookup"><span data-stu-id="26b2d-129">For more information, see <xref:System.ServiceModel.ServiceAuthorizationManager>.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="26b2d-130">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="26b2d-130">Child elements</span></span>

|<span data-ttu-id="26b2d-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="26b2d-131">Element</span></span>|<span data-ttu-id="26b2d-132">Description</span><span class="sxs-lookup"><span data-stu-id="26b2d-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26b2d-133">authorizationPolicies</span><span class="sxs-lookup"><span data-stu-id="26b2d-133">authorizationPolicies</span></span>|<span data-ttu-id="26b2d-134">Obsahuje kolekci typů zásad autorizací, které lze přidat pomocí `add` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="26b2d-134">Contains a collection of authorization policy types, which can be added using the `add` keyword.</span></span> <span data-ttu-id="26b2d-135">Každá zásada autorizace obsahuje jeden povinný `policyType` atribut, který je řetězec.</span><span class="sxs-lookup"><span data-stu-id="26b2d-135">Each authorization policy contains a single required `policyType` attribute that is a string.</span></span> <span data-ttu-id="26b2d-136">Atribut určuje zásadu autorizace, která umožňuje transformaci jedné sady vstupních deklarací do jiné sady deklarací.</span><span class="sxs-lookup"><span data-stu-id="26b2d-136">The attribute specifies an authorization policy, which enables transformation of one set of input claims into another set of claims.</span></span> <span data-ttu-id="26b2d-137">Řízení přístupu lze na základě této aplikace udělit nebo odepřít.</span><span class="sxs-lookup"><span data-stu-id="26b2d-137">Access control can be granted or denied based on that.</span></span> <span data-ttu-id="26b2d-138">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="26b2d-138">For more information, see <xref:System.ServiceModel.Configuration.AuthorizationPolicyTypeElement>.</span></span>|  

### <a name="parent-elements"></a><span data-ttu-id="26b2d-139">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="26b2d-139">Parent elements</span></span>

|<span data-ttu-id="26b2d-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="26b2d-140">Element</span></span>|<span data-ttu-id="26b2d-141">Description</span><span class="sxs-lookup"><span data-stu-id="26b2d-141">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="26b2d-142">Obsahuje kolekci nastavení pro chování služby.</span><span class="sxs-lookup"><span data-stu-id="26b2d-142">Contains a collection of settings for the behavior of a service.</span></span>|  

## <a name="remarks"></a><span data-ttu-id="26b2d-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="26b2d-143">Remarks</span></span>

<span data-ttu-id="26b2d-144">Tato část obsahuje prvky ovlivňující autorizaci, vlastní poskytovatele rolí a zosobnění.</span><span class="sxs-lookup"><span data-stu-id="26b2d-144">This section contains elements affecting authorization, custom role providers, and impersonation.</span></span>  
  
<span data-ttu-id="26b2d-145">`principalPermissionMode`Atribut určuje skupiny uživatelů, které se mají použít při autorizaci použití chráněné metody.</span><span class="sxs-lookup"><span data-stu-id="26b2d-145">The `principalPermissionMode` attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="26b2d-146">Výchozí hodnota je `UseWindowsGroups` a určí, že se při pokusu o přístup k prostředku prohledávají skupiny systému Windows, například správci nebo uživatelé.</span><span class="sxs-lookup"><span data-stu-id="26b2d-146">The default value is `UseWindowsGroups` and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="26b2d-147">Můžete také určit, `UseAspNetRoles` že chcete použít vlastního poskytovatele rolí, který je nakonfigurován v rámci \<system.web> elementu, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="26b2d-147">You can also specify `UseAspNetRoles` to use a custom role provider that is configured under the \<system.web> element, as shown in the following code:</span></span>

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
  
<span data-ttu-id="26b2d-148">Následující kód ukazuje, že se `roleProviderName` používá s `principalPermissionMode` atributem:</span><span class="sxs-lookup"><span data-stu-id="26b2d-148">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute:</span></span>
  
```xml
<behaviors>
  <behavior name="ServiceBehaviour">
    <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                          roleProviderName ="SqlProvider" />
  </behavior>
  <!-- Other configuration code not shown. -->
</behaviors>
```

<span data-ttu-id="26b2d-149">Podrobný příklad použití tohoto prvku konfigurace najdete v tématu [autorizace přístupu k operacím služby](../../../wcf/samples/authorizing-access-to-service-operations.md) a [zásadám autorizace](../../../wcf/samples/authorization-policy.md).</span><span class="sxs-lookup"><span data-stu-id="26b2d-149">For a detailed example of using this configuration element, see [Authorizing Access to Service Operations](../../../wcf/samples/authorizing-access-to-service-operations.md) and [Authorization Policy](../../../wcf/samples/authorization-policy.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="26b2d-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="26b2d-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthorizationElement>
- <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>
- [<span data-ttu-id="26b2d-151">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="26b2d-151">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="26b2d-152">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="26b2d-152">Authorizing Access to Service Operations</span></span>](../../../wcf/samples/authorizing-access-to-service-operations.md)
- [<span data-ttu-id="26b2d-153">Postupy: Vytvoření vlastního správce autorizace pro službu</span><span class="sxs-lookup"><span data-stu-id="26b2d-153">How to: Create a Custom Authorization Manager for a Service</span></span>](../../../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)
- [<span data-ttu-id="26b2d-154">Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="26b2d-154">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [<span data-ttu-id="26b2d-155">Zásada autorizace</span><span class="sxs-lookup"><span data-stu-id="26b2d-155">Authorization Policy</span></span>](../../../wcf/samples/authorization-policy.md)
