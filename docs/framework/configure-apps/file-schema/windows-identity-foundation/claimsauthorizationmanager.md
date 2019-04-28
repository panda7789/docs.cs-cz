---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 59d47eda97e97629408ece12a1d1dfbe804feb3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667311"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="16f73-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="16f73-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="16f73-102">Zaregistruje Správce autorizací deklarace identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="16f73-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="16f73-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="16f73-103">\<system.identityModel></span></span>  
<span data-ttu-id="16f73-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="16f73-104">\<identityConfiguration></span></span>  
<span data-ttu-id="16f73-105">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="16f73-105">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16f73-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16f73-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16f73-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="16f73-107">Attributes and Elements</span></span>  
 <span data-ttu-id="16f73-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="16f73-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16f73-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="16f73-109">Attributes</span></span>  
  
|<span data-ttu-id="16f73-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="16f73-110">Attribute</span></span>|<span data-ttu-id="16f73-111">Popis</span><span class="sxs-lookup"><span data-stu-id="16f73-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16f73-112"> – typ</span><span class="sxs-lookup"><span data-stu-id="16f73-112">type</span></span>|<span data-ttu-id="16f73-113">Vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="16f73-113">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="16f73-114">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="16f73-114">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16f73-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="16f73-115">Child Elements</span></span>  
 <span data-ttu-id="16f73-116">Pokud není žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthorizationManager>` element nevyužívá podřízených elementů, ale třídy odvozené z <xref:System.Security.Claims.ClaimsAuthorizationManager> můžete definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="16f73-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16f73-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="16f73-117">Parent Elements</span></span>  
  
|<span data-ttu-id="16f73-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="16f73-118">Element</span></span>|<span data-ttu-id="16f73-119">Popis</span><span class="sxs-lookup"><span data-stu-id="16f73-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16f73-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="16f73-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="16f73-121">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="16f73-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16f73-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="16f73-122">Remarks</span></span>  
 <span data-ttu-id="16f73-123">Výchozí chování zajišťována <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy vždy povolí příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="16f73-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="16f73-124">Pokud ne `type` je zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy, `<claimsAuthorizationManager>` element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="16f73-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="16f73-125">Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthorizationManager> třídu pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="16f73-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="16f73-126">Odvozené třídy může podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthorizationManager>` element tak, že přepíšete <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="16f73-126">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="16f73-127">Schéma definice pro podřízené prvky je až návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="16f73-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="16f73-128">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy k poskytování řízení přístupu na základě deklarací identity ve vašem kódu, konfigurace identity, na který odkazuje `<federationConfiguration>` element nakonfiguruje Správce autorizací deklarace identity a zásadu, která se využívá k Prognózování rozhodování o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="16f73-128">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="16f73-129">To platí dokonce i ve scénářích, které nejsou pasivní scénáře pro webové, například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založena na Web.</span><span class="sxs-lookup"><span data-stu-id="16f73-129">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="16f73-130">Pokud aplikace není pasivní webové aplikace `<claimsAuthorizationManager>` – element (a jeho podřízených elementů zásad, pokud jsou k dispozici) konfigurace odkazované identity jsou jenom nastavení, která použijí.</span><span class="sxs-lookup"><span data-stu-id="16f73-130">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="16f73-131">Všechna ostatní nastavení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="16f73-131">All other settings are ignored.</span></span> <span data-ttu-id="16f73-132">Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="16f73-132">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="16f73-133">Tento prvek nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="16f73-133">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16f73-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="16f73-134">Example</span></span>  
 <span data-ttu-id="16f73-135">Následující kód XML je znázorněna konfigurace pro autorizaci deklarací identity Manageru, který implementuje zásady skládá z dvojice akce prostředku, z nichž každý Určuje logický kombinace deklarací, které musí mít žadatele k provedení akce na prostředku.</span><span class="sxs-lookup"><span data-stu-id="16f73-135">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="16f73-136">Kód, který implementuje Správce autorizací deklarace identity nemůže použít tyto zásady najdete v `ClaimsBasedAuthorization` vzorku.</span><span class="sxs-lookup"><span data-stu-id="16f73-136">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
