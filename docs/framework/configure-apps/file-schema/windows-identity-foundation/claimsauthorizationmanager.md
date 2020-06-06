---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252087"
---
# \<claimsAuthorizationManager>
<span data-ttu-id="44408-101">Registruje Správce autorizací deklarací identity pro příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="44408-101">Registers a claims authorization manager for the incoming claims.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="44408-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44408-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44408-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44408-103">Attributes and Elements</span></span>  
 <span data-ttu-id="44408-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44408-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44408-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="44408-105">Attributes</span></span>  
  
|<span data-ttu-id="44408-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="44408-106">Attribute</span></span>|<span data-ttu-id="44408-107">Popis</span><span class="sxs-lookup"><span data-stu-id="44408-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44408-108">typ</span><span class="sxs-lookup"><span data-stu-id="44408-108">type</span></span>|<span data-ttu-id="44408-109">Vlastní typ, který je odvozen od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="44408-109">A custom type that derives from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class.</span></span> <span data-ttu-id="44408-110">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="44408-110">For more information about how to specify the `type` attribute, see [Custom Type References](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44408-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44408-111">Child Elements</span></span>  
 <span data-ttu-id="44408-112">Pokud neexistuje žádný `type` atribut, nebo pokud `type` atribut odkazuje na <xref:System.Security.Claims.ClaimsAuthenticationManager> třídu, `<claimsAuthorizationManager>` element nebere podřízené prvky. třídy odvozené z <xref:System.Security.Claims.ClaimsAuthorizationManager> mohou však definovat podřízené prvky konfigurace.</span><span class="sxs-lookup"><span data-stu-id="44408-112">If there is no `type` attribute, or if the `type` attribute references the <xref:System.Security.Claims.ClaimsAuthenticationManager> class, the `<claimsAuthorizationManager>` element does not take child elements; however, classes derived from <xref:System.Security.Claims.ClaimsAuthorizationManager> can define child configuration elements.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44408-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44408-113">Parent Elements</span></span>  
  
|<span data-ttu-id="44408-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="44408-114">Element</span></span>|<span data-ttu-id="44408-115">Description</span><span class="sxs-lookup"><span data-stu-id="44408-115">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="44408-116">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="44408-116">Specifies service-level identity settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44408-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44408-117">Remarks</span></span>  
 <span data-ttu-id="44408-118">Výchozí chování poskytované prostřednictvím <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy vždy autorizuje příchozí deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="44408-118">The default behavior provided through the <xref:System.Security.Claims.ClaimsAuthorizationManager> class always authorizes the incoming claims.</span></span> <span data-ttu-id="44408-119">Pokud není `type` zadán žádný atribut nebo pokud `type` atribut specifikuje <xref:System.Security.Claims.ClaimsAuthorizationManager> třídu, `<claimsAuthorizationManager>` element nepřijímá podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="44408-119">If no `type` attribute is specified or if the `type` attribute specifies the <xref:System.Security.Claims.ClaimsAuthorizationManager> class, the `<claimsAuthorizationManager>` element does not take child elements.</span></span> <span data-ttu-id="44408-120">Můžete určit `type` atribut pro registraci typu odvozeného od <xref:System.Security.Claims.ClaimsAuthorizationManager> třídy pro implementaci vlastního chování.</span><span class="sxs-lookup"><span data-stu-id="44408-120">You can specify the `type` attribute to register a type derived from the <xref:System.Security.Claims.ClaimsAuthorizationManager> class to implement custom behavior.</span></span> <span data-ttu-id="44408-121">Odvozené třídy mohou podporovat konfiguraci prostřednictvím podřízených prvků `<claimsAuthorizationManager>` prvku přepsáním <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> metody pro zpracování těchto elementů.</span><span class="sxs-lookup"><span data-stu-id="44408-121">Derived classes can support configuration through child elements of the `<claimsAuthorizationManager>` element by overriding the <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> method to handle these elements.</span></span> <span data-ttu-id="44408-122">Schéma definované pro podřízené prvky je až do návrháře třídy.</span><span class="sxs-lookup"><span data-stu-id="44408-122">The schema defined for the child elements is up to the designer of the class.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="44408-123">Při použití <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> třídy nebo k poskytnutí řízení přístupu založeného na deklaracích ve vašem kódu, konfigurace identity, na kterou se odkazuje element, `<federationConfiguration>` konfiguruje správce autorizací deklarací identity a zásadu, která se používá k rozhodování o autorizaci.</span><span class="sxs-lookup"><span data-stu-id="44408-123">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="44408-124">To platí i ve scénářích, které nejsou pasivními webovými scénáři, například v aplikacích Windows Communication Foundation (WCF) nebo v aplikaci, která není založená na webu.</span><span class="sxs-lookup"><span data-stu-id="44408-124">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="44408-125">Pokud aplikace není pasivní webovou aplikací, použije se pro daný `<claimsAuthorizationManager>` prvek (a jeho podřízené prvky zásad, pokud jsou k dispozici) odkazovaná konfigurace identity pouze nastavení.</span><span class="sxs-lookup"><span data-stu-id="44408-125">If the application is not a passive Web application, the `<claimsAuthorizationManager>` element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="44408-126">Všechna ostatní nastavení se ignorují.</span><span class="sxs-lookup"><span data-stu-id="44408-126">All other settings are ignored.</span></span> <span data-ttu-id="44408-127">Další informace naleznete v tématu [\<federationConfiguration>](federationconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="44408-127">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="44408-128">Tento prvek nastaví <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="44408-128">This element sets the <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44408-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="44408-129">Example</span></span>  
 <span data-ttu-id="44408-130">Následující kód XML ukazuje konfiguraci pro Správce autorizací deklarací identity, která implementuje zásady složené z párů prostředků a akcí, každý z nich určuje logické kombinace deklarací identity, které musí žadatel provést k provedení akce na prostředku.</span><span class="sxs-lookup"><span data-stu-id="44408-130">The following XML shows the configuration for a claims authorization manager that implements policy composed of resource-action pairs each of which specifies boolean combinations of the claims that a requestor must possess to perform the action on the resource.</span></span> <span data-ttu-id="44408-131">Kód, který implementuje Správce autorizací deklarací identity, který je schopný použít tuto zásadu, najdete v `ClaimsBasedAuthorization` ukázce.</span><span class="sxs-lookup"><span data-stu-id="44408-131">The code that implements the claims authorization manager capable of using this policy can be found in the `ClaimsBasedAuthorization` sample.</span></span>  
  
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
