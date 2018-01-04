---
title: '&lt;audienceUris&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 69c96698b309a789b4527c76e1fe8b8b99811a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="53e41-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="53e41-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="53e41-103">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="53e41-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="53e41-104">Tokeny nebudou přijímány, pokud jsou určené pro jednu z povolená cílová skupina identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="53e41-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="53e41-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="53e41-105">\<system.identityModel></span></span>  
<span data-ttu-id="53e41-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="53e41-106">\<identityConfiguration></span></span>  
<span data-ttu-id="53e41-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="53e41-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="53e41-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="53e41-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="53e41-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="53e41-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e41-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53e41-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53e41-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53e41-111">Attributes and Elements</span></span>  
 <span data-ttu-id="53e41-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53e41-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53e41-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="53e41-113">Attributes</span></span>  
  
|<span data-ttu-id="53e41-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="53e41-114">Attribute</span></span>|<span data-ttu-id="53e41-115">Popis</span><span class="sxs-lookup"><span data-stu-id="53e41-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53e41-116">režim</span><span class="sxs-lookup"><span data-stu-id="53e41-116">mode</span></span>|<span data-ttu-id="53e41-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnotu, která určuje, zda má být použita omezení cílovou skupinu do příchozího tokenu.</span><span class="sxs-lookup"><span data-stu-id="53e41-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="53e41-118">Možné hodnoty jsou "Vždy", "Nikdy" a "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="53e41-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="53e41-119">Výchozí hodnota je "Vždy".</span><span class="sxs-lookup"><span data-stu-id="53e41-119">The default is "Always".</span></span> <span data-ttu-id="53e41-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="53e41-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53e41-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53e41-121">Child Elements</span></span>  
  
|<span data-ttu-id="53e41-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="53e41-122">Element</span></span>|<span data-ttu-id="53e41-123">Popis</span><span class="sxs-lookup"><span data-stu-id="53e41-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="53e41-124">Přidá identifikátor URI určeného `value` atribut audienceUris kolekce.</span><span class="sxs-lookup"><span data-stu-id="53e41-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="53e41-125">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="53e41-125">The `value` attribute is required.</span></span> <span data-ttu-id="53e41-126">Identifikátor URI je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="53e41-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="53e41-127">Vymaže kolekci audienceUris.</span><span class="sxs-lookup"><span data-stu-id="53e41-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="53e41-128">Všechny identifikátory se odeberou z kolekce.</span><span class="sxs-lookup"><span data-stu-id="53e41-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="53e41-129">Odebere identifikátor URI určeného `value` atribut z kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="53e41-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="53e41-130">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="53e41-130">The `value` attribute is required.</span></span> <span data-ttu-id="53e41-131">Identifikátor URI je malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="53e41-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53e41-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53e41-132">Parent Elements</span></span>  
  
|<span data-ttu-id="53e41-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="53e41-133">Element</span></span>|<span data-ttu-id="53e41-134">Popis</span><span class="sxs-lookup"><span data-stu-id="53e41-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53e41-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="53e41-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="53e41-136">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="53e41-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e41-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53e41-137">Remarks</span></span>  
 <span data-ttu-id="53e41-138">Ve výchozím nastavení je kolekce prázdná. použít `<add>`, `<clear>`, a `<remove>` elementy upravit kolekci.</span><span class="sxs-lookup"><span data-stu-id="53e41-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="53e41-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objekty použijte hodnoty v cílové skupině URI kolekce ke konfiguraci libovolné povolené cílové skupiny omezení URI v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekty.</span><span class="sxs-lookup"><span data-stu-id="53e41-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="53e41-140">`<audienceUris>` Element je reprezentována <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="53e41-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="53e41-141">Identifikátor jednotlivých URI přidaných do kolekce je reprezentována <xref:System.IdentityModel.Configuration.AudienceUriElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="53e41-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53e41-142">Použití `<audienceUris>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="53e41-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="53e41-143">Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="53e41-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53e41-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="53e41-144">Example</span></span>  
 <span data-ttu-id="53e41-145">Následující kód XML ukazuje, jak nakonfigurovat přijatelné cílovou skupinu identifikátory URI, pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="53e41-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="53e41-146">Tento příklad konfiguruje jeden identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="53e41-146">This example configures a single URI.</span></span> <span data-ttu-id="53e41-147">Přijme tokeny, které jsou určené pro tento identifikátor URI, všechny ostatní budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="53e41-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
