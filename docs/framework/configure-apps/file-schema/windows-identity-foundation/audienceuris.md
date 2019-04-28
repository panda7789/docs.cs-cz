---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: 556c444d5e48e27036c4b49338f6e70de7ef5c5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61750745"
---
# <a name="audienceuris"></a><span data-ttu-id="999ff-101">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="999ff-101">\<audienceUris></span></span>
<span data-ttu-id="999ff-102">Určuje sadu identifikátorů URI, které jsou přípustné identifikátory předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="999ff-102">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="999ff-103">Tokeny nebudou přijímány, pokud jsou určená pro jeden z identifikátorů URI povolená cílová skupina.</span><span class="sxs-lookup"><span data-stu-id="999ff-103">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
 <span data-ttu-id="999ff-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="999ff-104">\<system.identityModel></span></span>  
<span data-ttu-id="999ff-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="999ff-105">\<identityConfiguration></span></span>  
<span data-ttu-id="999ff-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="999ff-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="999ff-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="999ff-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="999ff-108">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="999ff-108">\<audienceUris></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999ff-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="999ff-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="999ff-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="999ff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="999ff-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="999ff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="999ff-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="999ff-112">Attributes</span></span>  
  
|<span data-ttu-id="999ff-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="999ff-113">Attribute</span></span>|<span data-ttu-id="999ff-114">Popis</span><span class="sxs-lookup"><span data-stu-id="999ff-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="999ff-115">režim</span><span class="sxs-lookup"><span data-stu-id="999ff-115">mode</span></span>|<span data-ttu-id="999ff-116"><xref:System.IdentityModel.Selectors.AudienceUriMode> Hodnota, která určuje, zda má být použita omezení cílovou skupinu na příchozí token.</span><span class="sxs-lookup"><span data-stu-id="999ff-116">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="999ff-117">Možné hodnoty jsou "Always", "Nikdy" a "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="999ff-117">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="999ff-118">Výchozí hodnota je "Always".</span><span class="sxs-lookup"><span data-stu-id="999ff-118">The default is "Always".</span></span> <span data-ttu-id="999ff-119">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="999ff-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="999ff-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="999ff-120">Child Elements</span></span>  
  
|<span data-ttu-id="999ff-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="999ff-121">Element</span></span>|<span data-ttu-id="999ff-122">Popis</span><span class="sxs-lookup"><span data-stu-id="999ff-122">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="999ff-123">Přidá určený identifikátor URI `value` atribut audienceUris kolekce.</span><span class="sxs-lookup"><span data-stu-id="999ff-123">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="999ff-124">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="999ff-124">The `value` attribute is required.</span></span> <span data-ttu-id="999ff-125">Identifikátor URI je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="999ff-125">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="999ff-126">Vymaže kolekci audienceUris.</span><span class="sxs-lookup"><span data-stu-id="999ff-126">Clears the audienceUris collection.</span></span> <span data-ttu-id="999ff-127">Všechny identifikátory se odeberou z kolekce.</span><span class="sxs-lookup"><span data-stu-id="999ff-127">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="999ff-128">Odstraní určený identifikátor URI `value` atribut z kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="999ff-128">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="999ff-129">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="999ff-129">The `value` attribute is required.</span></span> <span data-ttu-id="999ff-130">Identifikátor URI je velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="999ff-130">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="999ff-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="999ff-131">Parent Elements</span></span>  
  
|<span data-ttu-id="999ff-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="999ff-132">Element</span></span>|<span data-ttu-id="999ff-133">Popis</span><span class="sxs-lookup"><span data-stu-id="999ff-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="999ff-134">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="999ff-134">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="999ff-135">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="999ff-135">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="999ff-136">Poznámky</span><span class="sxs-lookup"><span data-stu-id="999ff-136">Remarks</span></span>  
 <span data-ttu-id="999ff-137">Ve výchozím nastavení je kolekce prázdná. použít `<add>`, `<clear>`, a `<remove>` prvků, které se změnit kolekci.</span><span class="sxs-lookup"><span data-stu-id="999ff-137">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="999ff-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objektů použijte hodnoty v cílové skupině identifikátor URI kolekce ke konfiguraci libovolné povolené cílové skupiny omezení identifikátor URI v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekty.</span><span class="sxs-lookup"><span data-stu-id="999ff-138"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="999ff-139">`<audienceUris>` Prvek je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="999ff-139">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="999ff-140">Je reprezentován jednotlivé identifikátor URI přidat do kolekce <xref:System.IdentityModel.Configuration.AudienceUriElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="999ff-140">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="999ff-141">Použití `<audienceUris>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována.</span><span class="sxs-lookup"><span data-stu-id="999ff-141">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="999ff-142">Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="999ff-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="999ff-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="999ff-143">Example</span></span>  
 <span data-ttu-id="999ff-144">Následující kód XML ukazuje, jak nakonfigurovat přijatelné cílovou skupinu identifikátory URI pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="999ff-144">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="999ff-145">Tento příklad konfiguruje jednoho identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="999ff-145">This example configures a single URI.</span></span> <span data-ttu-id="999ff-146">Přijme tokeny oboru pro tento identifikátor URI, všechny ostatní budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="999ff-146">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
