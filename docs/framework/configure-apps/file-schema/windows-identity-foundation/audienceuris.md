---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7415cb3f1792d2de566161ae6c348ef591b4a0c3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755991"
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="60ba8-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="60ba8-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="60ba8-103">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="60ba8-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="60ba8-104">Tokeny nebudou přijímány, pokud jsou určené pro jednu z povolená cílová skupina identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="60ba8-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="60ba8-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="60ba8-105">\<system.identityModel></span></span>  
<span data-ttu-id="60ba8-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60ba8-106">\<identityConfiguration></span></span>  
<span data-ttu-id="60ba8-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="60ba8-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="60ba8-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60ba8-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="60ba8-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="60ba8-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60ba8-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60ba8-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60ba8-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60ba8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="60ba8-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60ba8-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60ba8-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="60ba8-113">Attributes</span></span>  
  
|<span data-ttu-id="60ba8-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="60ba8-114">Attribute</span></span>|<span data-ttu-id="60ba8-115">Popis</span><span class="sxs-lookup"><span data-stu-id="60ba8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60ba8-116">režim</span><span class="sxs-lookup"><span data-stu-id="60ba8-116">mode</span></span>|<span data-ttu-id="60ba8-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnotu, která určuje, zda má být použita omezení cílovou skupinu do příchozího tokenu.</span><span class="sxs-lookup"><span data-stu-id="60ba8-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="60ba8-118">Možné hodnoty jsou "Vždy", "Nikdy" a "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="60ba8-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="60ba8-119">Výchozí hodnota je "Vždy".</span><span class="sxs-lookup"><span data-stu-id="60ba8-119">The default is "Always".</span></span> <span data-ttu-id="60ba8-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="60ba8-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60ba8-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60ba8-121">Child Elements</span></span>  
  
|<span data-ttu-id="60ba8-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="60ba8-122">Element</span></span>|<span data-ttu-id="60ba8-123">Popis</span><span class="sxs-lookup"><span data-stu-id="60ba8-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="60ba8-124">Přidá identifikátor URI určeného `value` atribut audienceUris kolekce.</span><span class="sxs-lookup"><span data-stu-id="60ba8-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="60ba8-125">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="60ba8-125">The `value` attribute is required.</span></span> <span data-ttu-id="60ba8-126">Identifikátor URI je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="60ba8-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="60ba8-127">Vymaže kolekci audienceUris.</span><span class="sxs-lookup"><span data-stu-id="60ba8-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="60ba8-128">Všechny identifikátory se odeberou z kolekce.</span><span class="sxs-lookup"><span data-stu-id="60ba8-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="60ba8-129">Odebere identifikátor URI určeného `value` atribut z kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="60ba8-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="60ba8-130">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="60ba8-130">The `value` attribute is required.</span></span> <span data-ttu-id="60ba8-131">Identifikátor URI je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="60ba8-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60ba8-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60ba8-132">Parent Elements</span></span>  
  
|<span data-ttu-id="60ba8-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="60ba8-133">Element</span></span>|<span data-ttu-id="60ba8-134">Popis</span><span class="sxs-lookup"><span data-stu-id="60ba8-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60ba8-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60ba8-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="60ba8-136">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="60ba8-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60ba8-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60ba8-137">Remarks</span></span>  
 <span data-ttu-id="60ba8-138">Ve výchozím nastavení je kolekce prázdná. použít `<add>`, `<clear>`, a `<remove>` elementy upravit kolekci.</span><span class="sxs-lookup"><span data-stu-id="60ba8-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="60ba8-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objekty použijte hodnoty v cílové skupině URI kolekce ke konfiguraci libovolné povolené cílové skupiny omezení URI v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekty.</span><span class="sxs-lookup"><span data-stu-id="60ba8-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="60ba8-140">`<audienceUris>` Element je reprezentována <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="60ba8-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="60ba8-141">Identifikátor jednotlivých URI přidaných do kolekce je reprezentována <xref:System.IdentityModel.Configuration.AudienceUriElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="60ba8-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60ba8-142">Použití `<audienceUris>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="60ba8-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="60ba8-143">Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="60ba8-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60ba8-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="60ba8-144">Example</span></span>  
 <span data-ttu-id="60ba8-145">Následující kód XML ukazuje, jak nakonfigurovat přijatelné cílovou skupinu identifikátory URI, pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="60ba8-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="60ba8-146">Tento příklad konfiguruje jeden identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="60ba8-146">This example configures a single URI.</span></span> <span data-ttu-id="60ba8-147">Přijme tokeny, které jsou určené pro tento identifikátor URI, všechny ostatní budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="60ba8-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
