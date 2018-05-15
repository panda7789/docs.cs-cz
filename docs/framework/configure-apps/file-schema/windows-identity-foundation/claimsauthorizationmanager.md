---
title: '&lt;claimsAuthorizationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 06824e20286f8905ad3a8ac9d2b4a30366a6ec10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimsauthorizationmanagergt"></a><span data-ttu-id="008c8-102">&lt;claimsAuthorizationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="008c8-102">&lt;claimsAuthorizationManager&gt;</span></span>
<span data-ttu-id="008c8-103">Zaregistruje Správce autorizací příchozí deklarace identity deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="008c8-103">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="008c8-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="008c8-104">\<system.identityModel></span></span>  
<span data-ttu-id="008c8-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="008c8-105">\<identityConfiguration></span></span>  
<span data-ttu-id="008c8-106">\<claimsAuthorizationManager ></span><span class="sxs-lookup"><span data-stu-id="008c8-106">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="008c8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="008c8-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="008c8-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="008c8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="008c8-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="008c8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="008c8-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="008c8-110">Attributes</span></span>  
  
|<span data-ttu-id="008c8-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="008c8-111">Attribute</span></span>|<span data-ttu-id="008c8-112">Popis</span><span class="sxs-lookup"><span data-stu-id="008c8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="008c8-113">– typ</span><span class="sxs-lookup"><span data-stu-id="008c8-113">type</span></span>|<span data-ttu-id="008c8-114">Vlastního typu, který je odvozen od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="008c8-114">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="008c8-115">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="008c8-115">For more information about how to specify the `type` attribute, see [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="008c8-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="008c8-116">Child Elements</span></span>  
 <span data-ttu-id="008c8-117">Pokud je žádné `type` atribut, nebo, pokud `type` atribut odkazy <xref:System.Security.Claims.ClaimsAuthenticationManager> třídy, `<claimsAuthorizationManager>` element nevyužívá podřízených elementů, ale třídy odvozené od <xref:System.Security.Claims.ClaimsAuthorizationManager> můžete definovat podřízené konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="008c8-117">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="008c8-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="008c8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="008c8-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="008c8-119">Element</span></span>|<span data-ttu-id="008c8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="008c8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="008c8-121">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="008c8-121">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="008c8-122">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="008c8-122">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="008c8-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="008c8-123">Remarks</span></span>  
 <span data-ttu-id="008c8-124">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthorizationManager> třída vždycky povolí příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="008c8-124">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="008c8-125">Pokud žádné `type` zadán atribut nebo, pokud `type` Určuje atribut <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy, `<claimsAuthorizationManager>` element nemusí provádět žádné podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="008c8-125">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="008c8-126">Můžete zadat `type` atribut zaregistrovat typ odvozený z <xref:System.Security.Claims.ClaimsAuthorizationManager> třídu pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="008c8-126">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="008c8-127">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených elementů `<claimsAuthorizationManager>` element přepsáním <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metodu ke zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="008c8-127">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="008c8-128">Schéma definované pro podřízené elementy závisí návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="008c8-128">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="008c8-129">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> nebo <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třída k poskytování řízení přístupu na základě deklarace identity ve vašem kódu konfiguraci identity, která odkazuje `<federationConfiguration>` element nakonfiguruje Správce autorizací deklarace identity a zásadu, která se používá k zajištění rozhodnutí o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="008c8-129">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="008c8-130">Je to ve scénářích, které nejsou pasivní scénáře webového, například aplikace Windows Communication Foundation (WCF) nebo aplikaci, která není založené na webu.</span><span class="sxs-lookup"><span data-stu-id="008c8-130">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="008c8-131">Pokud aplikace není pasivní webové aplikace `<claimsAuthorizationManager>` – element (a jeho podřízených elementů zásad, pokud existuje) konfigurace odkazované identity jsou jenom nastavení použité.</span><span class="sxs-lookup"><span data-stu-id="008c8-131">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="008c8-132">Všechna ostatní nastavení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="008c8-132">All other settings are ignored.</span></span> <span data-ttu-id="008c8-133">Další informace najdete v tématu [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="008c8-133">For more information, see the [\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="008c8-134">Nastaví tento element <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="008c8-134">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="008c8-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="008c8-135">Example</span></span>  
 <span data-ttu-id="008c8-136">Následující kód XML zobrazí správce, který implementuje zásady skládá z dvojice akce prostředku, z nichž každý určuje boolean kombinace deklarace identity, které provést akci na prostředku musí mít žadatele o konfiguraci pro autorizaci deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="008c8-136">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="008c8-137">Kód, který implementuje Správce autorizací deklarace identity, která je schopen pomocí těchto zásad najdete v `ClaimsBasedAuthorization` ukázka.</span><span class="sxs-lookup"><span data-stu-id="008c8-137">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
