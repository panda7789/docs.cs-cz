---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 003221ed4dc7f4ccf72d2e0d3a91265e13172813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941957"
---
# <a name="audienceuris"></a><span data-ttu-id="74046-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="74046-101">\<audienceUris></span></span>
<span data-ttu-id="74046-102">Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="74046-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="74046-103">Tokeny nebudou přijaty, pokud nejsou vymezeny pro některý z povolených identifikátorů URI cílové skupiny.</span><span class="sxs-lookup"><span data-stu-id="74046-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="74046-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="74046-104">\<system.identityModel></span></span>  
<span data-ttu-id="74046-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="74046-105">\<identityConfiguration></span></span>  
<span data-ttu-id="74046-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="74046-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="74046-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="74046-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="74046-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="74046-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74046-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74046-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="74046-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="74046-110">Attributes and Elements</span></span>  
 <span data-ttu-id="74046-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="74046-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="74046-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="74046-112">Attributes</span></span>  
  
|<span data-ttu-id="74046-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="74046-113">Attribute</span></span>|<span data-ttu-id="74046-114">Popis</span><span class="sxs-lookup"><span data-stu-id="74046-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="74046-115">režim</span><span class="sxs-lookup"><span data-stu-id="74046-115">mode</span></span>|<span data-ttu-id="74046-116"><xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnota, která určuje, jestli se má omezení cílové skupiny použít u příchozího tokenu.</span><span class="sxs-lookup"><span data-stu-id="74046-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="74046-117">Možné hodnoty jsou "Always", "Never" a "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="74046-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="74046-118">Výchozí hodnota je "Always".</span><span class="sxs-lookup"><span data-stu-id="74046-118">The default is "Always".</span></span> <span data-ttu-id="74046-119">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="74046-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="74046-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="74046-120">Child Elements</span></span>  
  
|<span data-ttu-id="74046-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="74046-121">Element</span></span>|<span data-ttu-id="74046-122">Popis</span><span class="sxs-lookup"><span data-stu-id="74046-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="74046-123">Přidá identifikátor URI určený `value` atributem do kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="74046-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="74046-124">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="74046-124">The `value` attribute is required.</span></span> <span data-ttu-id="74046-125">Identifikátor URI rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="74046-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="74046-126">Vymaže kolekci audienceUris.</span><span class="sxs-lookup"><span data-stu-id="74046-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="74046-127">Všechny identifikátory jsou z kolekce odebrané.</span><span class="sxs-lookup"><span data-stu-id="74046-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="74046-128">Odstraní identifikátor URI určený `value` atributem z kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="74046-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="74046-129">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="74046-129">The `value` attribute is required.</span></span> <span data-ttu-id="74046-130">Identifikátor URI rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="74046-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="74046-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="74046-131">Parent Elements</span></span>  
  
|<span data-ttu-id="74046-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="74046-132">Element</span></span>|<span data-ttu-id="74046-133">Popis</span><span class="sxs-lookup"><span data-stu-id="74046-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="74046-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="74046-134">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="74046-135">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="74046-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74046-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74046-136">Remarks</span></span>  
 <span data-ttu-id="74046-137">Ve výchozím nastavení je kolekce prázdná. pro `<add>`úpravu `<clear>`kolekce použijte `<remove>` prvky, a.</span><span class="sxs-lookup"><span data-stu-id="74046-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="74046-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>objekty <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a používají hodnoty v kolekci identifikátorů URI cílové skupiny ke konfiguraci libovolných povolených omezení <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> identifikátorů URI cílové skupiny v objektech.</span><span class="sxs-lookup"><span data-stu-id="74046-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="74046-139">Element je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection>třídou. `<audienceUris>`</span><span class="sxs-lookup"><span data-stu-id="74046-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="74046-140">Jednotlivé identifikátory URI přidané do kolekce jsou reprezentovány <xref:System.IdentityModel.Configuration.AudienceUriElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="74046-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74046-141">Použití `<audienceUris>` prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) bylo zastaralé, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="74046-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="74046-142">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.</span><span class="sxs-lookup"><span data-stu-id="74046-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74046-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="74046-143">Example</span></span>  
 <span data-ttu-id="74046-144">Následující kód XML ukazuje, jak nakonfigurovat přijatelné identifikátory URI cílové skupiny pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="74046-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="74046-145">Tento příklad nakonfiguruje jeden identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="74046-145">This example configures a single URI.</span></span> <span data-ttu-id="74046-146">Tokeny vymezené pro tento identifikátor URI budou přijaty, ostatní budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="74046-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
