---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: 74ca031f7017d51adaa7a71593f537b64abbeae6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942895"
---
# <a name="claimsauthorizationmanager"></a><span data-ttu-id="8f3ba-101">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="8f3ba-101">\<claimsAuthorizationManager></span></span>
<span data-ttu-id="8f3ba-102">Registruje Správce autorizací deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-102">Registers a claims authorization manager for the incoming claims.</span></span>  
  
 <span data-ttu-id="8f3ba-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8f3ba-103">\<system.identityModel></span></span>  
<span data-ttu-id="8f3ba-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8f3ba-104">\<identityConfiguration></span></span>  
<span data-ttu-id="8f3ba-105">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="8f3ba-105">\<claimsAuthorizationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f3ba-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f3ba-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f3ba-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8f3ba-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8f3ba-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f3ba-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="8f3ba-109">Attributes</span></span>  
  
|<span data-ttu-id="8f3ba-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="8f3ba-110">Attribute</span></span>|<span data-ttu-id="8f3ba-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8f3ba-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f3ba-112">– typ</span><span class="sxs-lookup"><span data-stu-id="8f3ba-112">type</span></span>|<span data-ttu-id="8f3ba-113">Vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-113">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="8f3ba-114">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="8f3ba-114">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f3ba-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8f3ba-115">Child Elements</span></span>  
 <span data-ttu-id="8f3ba-116">`type` Pokud neexistuje žádný atribut, nebo <xref:System.Security.Claims.ClaimsAuthenticationManager> `type` Pokud atribut `<claimsAuthorizationManager>` odkazuje na třídu, element nebere podřízené prvky. třídy odvozené z <xref:System.Security.Claims.ClaimsAuthorizationManager> mohou však definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-116">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f3ba-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8f3ba-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8f3ba-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="8f3ba-118">Element</span></span>|<span data-ttu-id="8f3ba-119">Popis</span><span class="sxs-lookup"><span data-stu-id="8f3ba-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8f3ba-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8f3ba-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="8f3ba-121">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-121">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f3ba-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f3ba-122">Remarks</span></span>  
 <span data-ttu-id="8f3ba-123">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy vždy autorizuje příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-123">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="8f3ba-124">Pokud není `type` zadán žádný atribut nebo `type` Pokud atribut `<claimsAuthorizationManager>` specifikuje <xref:System.Security.Claims.ClaimsAuthorizationManager> třídu, element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-124">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="8f3ba-125">Můžete určit `type` atribut pro registraci typu odvozeného <xref:System.Security.Claims.ClaimsAuthorizationManager> od třídy pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-125">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="8f3ba-126">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthorizationManager>` prvku <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> přepsáním metody pro zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-126">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="8f3ba-127">Schéma definované pro podřízené prvky je až do návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-127">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8f3ba-128">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu, konfigurace identity `<federationConfiguration>` , na kterou se odkazuje element, konfiguruje správce autorizací deklarací identity a zásadu, která se používá k provedení autorizační rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-128">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="8f3ba-129">To platí i ve scénářích, které nejsou pasivními webovými scénáři, například v aplikacích Windows Communication Foundation (WCF) nebo v aplikaci, která není založená na webu.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-129">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="8f3ba-130">Pokud aplikace není pasivní webovou aplikací, `<claimsAuthorizationManager>` použije se pro daný prvek (a jeho podřízené prvky zásad, pokud jsou k dispozici) odkazovaná konfigurace identity pouze nastavení.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-130">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="8f3ba-131">Všechna ostatní nastavení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-131">All other settings are ignored.</span></span> <span data-ttu-id="8f3ba-132">Další informace naleznete v [ \<tématu federationConfiguration >](federationconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-132">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="8f3ba-133">Tento prvek nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-133">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f3ba-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f3ba-134">Example</span></span>  
 <span data-ttu-id="8f3ba-135">Následující kód XML ukazuje konfiguraci pro Správce autorizací deklarací identity, která implementuje zásady složené z párů prostředků a akcí, každý z nich určuje logické kombinace deklarací identity, které musí žadatel provést k provedení akce na prostředku.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-135">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="8f3ba-136">Kód, který implementuje Správce autorizací deklarací identity, který je schopný použít tuto zásadu, najdete `ClaimsBasedAuthorization` v ukázce.</span><span class="sxs-lookup"><span data-stu-id="8f3ba-136">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
