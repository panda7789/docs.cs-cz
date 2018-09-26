---
title: '&lt;audienceUris&gt;'
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: af138a4da49a48ed43e1bc8f2c2c81c56892feed
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082445"
---
# <a name="ltaudienceurisgt"></a><span data-ttu-id="e5cb2-102">&lt;audienceUris&gt;</span><span class="sxs-lookup"><span data-stu-id="e5cb2-102">&lt;audienceUris&gt;</span></span>
<span data-ttu-id="e5cb2-103">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="e5cb2-103">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="e5cb2-104">Tokeny nebudou přijímány, pokud jsou určená pro jeden z identifikátorů URI povolená cílová skupina.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-104">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="e5cb2-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e5cb2-105">\<system.identityModel></span></span>  
<span data-ttu-id="e5cb2-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e5cb2-106">\<identityConfiguration></span></span>  
<span data-ttu-id="e5cb2-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e5cb2-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e5cb2-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e5cb2-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="e5cb2-109">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="e5cb2-109">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cb2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5cb2-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5cb2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e5cb2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5cb2-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5cb2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e5cb2-113">Attributes</span></span>  
  
|<span data-ttu-id="e5cb2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="e5cb2-114">Attribute</span></span>|<span data-ttu-id="e5cb2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e5cb2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5cb2-116">režim</span><span class="sxs-lookup"><span data-stu-id="e5cb2-116">mode</span></span>|<span data-ttu-id="e5cb2-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnota, která určuje, zda má být použita omezení cílovou skupinu na příchozí token.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="e5cb2-118">Možné hodnoty jsou "Always", "Nikdy" a "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="e5cb2-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="e5cb2-119">Výchozí hodnota je "Always".</span><span class="sxs-lookup"><span data-stu-id="e5cb2-119">The default is "Always".</span></span> <span data-ttu-id="e5cb2-120">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5cb2-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e5cb2-121">Child Elements</span></span>  
  
|<span data-ttu-id="e5cb2-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5cb2-122">Element</span></span>|<span data-ttu-id="e5cb2-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e5cb2-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="e5cb2-124">Přidá určený identifikátor URI `value` atribut audienceUris kolekce.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="e5cb2-125">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-125">The `value` attribute is required.</span></span> <span data-ttu-id="e5cb2-126">Identifikátor URI je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="e5cb2-127">Vymaže kolekci audienceUris.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="e5cb2-128">Všechny identifikátory se odeberou z kolekce.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="e5cb2-129">Odstraní určený identifikátor URI `value` atribut z kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="e5cb2-130">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-130">The `value` attribute is required.</span></span> <span data-ttu-id="e5cb2-131">Identifikátor URI je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5cb2-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e5cb2-132">Parent Elements</span></span>  
  
|<span data-ttu-id="e5cb2-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5cb2-133">Element</span></span>|<span data-ttu-id="e5cb2-134">Popis</span><span class="sxs-lookup"><span data-stu-id="e5cb2-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5cb2-135">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e5cb2-135">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e5cb2-136">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5cb2-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5cb2-137">Remarks</span></span>  
 <span data-ttu-id="e5cb2-138">Ve výchozím nastavení je kolekce prázdná. použít `<add>`, `<clear>`, a `<remove>` prvků, které se změnit kolekci.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="e5cb2-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objektů použijte hodnoty v cílové skupině identifikátor URI kolekce ke konfiguraci libovolné povolené cílové skupiny omezení identifikátor URI v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekty.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="e5cb2-140">`<audienceUris>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="e5cb2-141">Je reprezentován jednotlivé identifikátor URI přidat do kolekce <xref:System.IdentityModel.Configuration.AudienceUriElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5cb2-142">Použití `<audienceUris>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e5cb2-143">Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5cb2-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5cb2-144">Example</span></span>  
 <span data-ttu-id="e5cb2-145">Následující kód XML ukazuje, jak nakonfigurovat přijatelné cílovou skupinu identifikátory URI pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="e5cb2-146">Tento příklad konfiguruje jednoho identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-146">This example configures a single URI.</span></span> <span data-ttu-id="e5cb2-147">Přijme tokeny oboru pro tento identifikátor URI, všechny ostatní budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="e5cb2-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
