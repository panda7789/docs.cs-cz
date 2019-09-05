---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252173"
---
# <a name="audienceuris"></a><span data-ttu-id="fcca0-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="fcca0-101">\<audienceUris></span></span>
<span data-ttu-id="fcca0-102">Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="fcca0-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="fcca0-103">Tokeny nebudou přijaty, pokud nejsou vymezeny pro některý z povolených identifikátorů URI cílové skupiny.</span><span class="sxs-lookup"><span data-stu-id="fcca0-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
<span data-ttu-id="fcca0-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fcca0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fcca0-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="fcca0-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="fcca0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="fcca0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="fcca0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="fcca0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="fcca0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="fcca0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="fcca0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<audienceUris >**</span><span class="sxs-lookup"><span data-stu-id="fcca0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcca0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fcca0-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fcca0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fcca0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fcca0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fcca0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fcca0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="fcca0-113">Attributes</span></span>  
  
|<span data-ttu-id="fcca0-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="fcca0-114">Attribute</span></span>|<span data-ttu-id="fcca0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="fcca0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fcca0-116">režim</span><span class="sxs-lookup"><span data-stu-id="fcca0-116">mode</span></span>|<span data-ttu-id="fcca0-117"><xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnota, která určuje, jestli se má omezení cílové skupiny použít u příchozího tokenu.</span><span class="sxs-lookup"><span data-stu-id="fcca0-117">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="fcca0-118">Možné hodnoty jsou "Always", "Never" a "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="fcca0-118">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="fcca0-119">Výchozí hodnota je "Always".</span><span class="sxs-lookup"><span data-stu-id="fcca0-119">The default is "Always".</span></span> <span data-ttu-id="fcca0-120">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="fcca0-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fcca0-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fcca0-121">Child Elements</span></span>  
  
|<span data-ttu-id="fcca0-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="fcca0-122">Element</span></span>|<span data-ttu-id="fcca0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="fcca0-123">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="fcca0-124">Přidá identifikátor URI určený `value` atributem do kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="fcca0-124">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="fcca0-125">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="fcca0-125">The `value` attribute is required.</span></span> <span data-ttu-id="fcca0-126">Identifikátor URI rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="fcca0-126">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="fcca0-127">Vymaže kolekci audienceUris.</span><span class="sxs-lookup"><span data-stu-id="fcca0-127">Clears the audienceUris collection.</span></span> <span data-ttu-id="fcca0-128">Všechny identifikátory jsou z kolekce odebrané.</span><span class="sxs-lookup"><span data-stu-id="fcca0-128">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="fcca0-129">Odstraní identifikátor URI určený `value` atributem z kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="fcca0-129">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="fcca0-130">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="fcca0-130">The `value` attribute is required.</span></span> <span data-ttu-id="fcca0-131">Identifikátor URI rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="fcca0-131">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fcca0-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fcca0-132">Parent Elements</span></span>  
  
|<span data-ttu-id="fcca0-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="fcca0-133">Element</span></span>|<span data-ttu-id="fcca0-134">Popis</span><span class="sxs-lookup"><span data-stu-id="fcca0-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fcca0-135">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="fcca0-135">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="fcca0-136">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fcca0-136">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcca0-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fcca0-137">Remarks</span></span>  
 <span data-ttu-id="fcca0-138">Ve výchozím nastavení je kolekce prázdná. pro `<add>`úpravu `<clear>`kolekce použijte `<remove>` prvky, a.</span><span class="sxs-lookup"><span data-stu-id="fcca0-138">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="fcca0-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>objekty <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a používají hodnoty v kolekci identifikátorů URI cílové skupiny ke konfiguraci libovolných povolených omezení <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> identifikátorů URI cílové skupiny v objektech.</span><span class="sxs-lookup"><span data-stu-id="fcca0-139"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="fcca0-140">Element je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection>třídou. `<audienceUris>`</span><span class="sxs-lookup"><span data-stu-id="fcca0-140">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="fcca0-141">Jednotlivé identifikátory URI přidané do kolekce jsou reprezentovány <xref:System.IdentityModel.Configuration.AudienceUriElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="fcca0-141">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fcca0-142">Použití `<audienceUris>` prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) bylo zastaralé, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="fcca0-142">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="fcca0-143">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.</span><span class="sxs-lookup"><span data-stu-id="fcca0-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcca0-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="fcca0-144">Example</span></span>  
 <span data-ttu-id="fcca0-145">Následující kód XML ukazuje, jak nakonfigurovat přijatelné identifikátory URI cílové skupiny pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fcca0-145">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="fcca0-146">Tento příklad nakonfiguruje jeden identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="fcca0-146">This example configures a single URI.</span></span> <span data-ttu-id="fcca0-147">Tokeny vymezené pro tento identifikátor URI budou přijaty, ostatní budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="fcca0-147">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
