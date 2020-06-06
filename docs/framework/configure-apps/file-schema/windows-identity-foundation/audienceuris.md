---
title: <audienceUris>
ms.date: 03/30/2017
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
author: BrucePerlerMS
ms.openlocfilehash: bd04e4ebdf5c58adaeea0ff0ca5993d7d9ce38f1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252173"
---
# \<audienceUris>
<span data-ttu-id="81612-101">Určuje sadu identifikátorů URI, které jsou přijatelné identifikátory předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="81612-101">Specifies the set of URIs that are acceptable identifiers of the relying party (RP).</span></span> <span data-ttu-id="81612-102">Tokeny nebudou přijaty, pokud nejsou vymezeny pro některý z povolených identifikátorů URI cílové skupiny.</span><span class="sxs-lookup"><span data-stu-id="81612-102">Tokens will not be accepted unless they are scoped for one of the allowed audience URIs.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<audienceUris>**  
  
## <a name="syntax"></a><span data-ttu-id="81612-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81612-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81612-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="81612-104">Attributes and Elements</span></span>  
 <span data-ttu-id="81612-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="81612-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81612-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="81612-106">Attributes</span></span>  
  
|<span data-ttu-id="81612-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="81612-107">Attribute</span></span>|<span data-ttu-id="81612-108">Popis</span><span class="sxs-lookup"><span data-stu-id="81612-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81612-109">režim</span><span class="sxs-lookup"><span data-stu-id="81612-109">mode</span></span>|<span data-ttu-id="81612-110"><xref:System.IdentityModel.Selectors.AudienceUriMode>Hodnota, která určuje, jestli se má omezení cílové skupiny použít u příchozího tokenu.</span><span class="sxs-lookup"><span data-stu-id="81612-110">An <xref:System.IdentityModel.Selectors.AudienceUriMode> value that specifies whether the audience restriction should be applied to an incoming token.</span></span> <span data-ttu-id="81612-111">Možné hodnoty jsou "Always", "Never" a "BearerKeyOnly".</span><span class="sxs-lookup"><span data-stu-id="81612-111">The possible values are "Always", "Never", and "BearerKeyOnly".</span></span> <span data-ttu-id="81612-112">Výchozí hodnota je "Always".</span><span class="sxs-lookup"><span data-stu-id="81612-112">The default is "Always".</span></span> <span data-ttu-id="81612-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="81612-113">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81612-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="81612-114">Child Elements</span></span>  
  
|<span data-ttu-id="81612-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="81612-115">Element</span></span>|<span data-ttu-id="81612-116">Description</span><span class="sxs-lookup"><span data-stu-id="81612-116">Description</span></span>|  
|-------------|-----------------|  
|`<add value=xs:string>`|<span data-ttu-id="81612-117">Přidá identifikátor URI určený `value` atributem do kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="81612-117">Adds the URI specified by the `value` attribute to the audienceUris collection.</span></span> <span data-ttu-id="81612-118">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="81612-118">The `value` attribute is required.</span></span> <span data-ttu-id="81612-119">Identifikátor URI rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="81612-119">The URI is case-sensitive.</span></span>|  
|`<clear>`|<span data-ttu-id="81612-120">Vymaže kolekci audienceUris.</span><span class="sxs-lookup"><span data-stu-id="81612-120">Clears the audienceUris collection.</span></span> <span data-ttu-id="81612-121">Všechny identifikátory jsou z kolekce odebrané.</span><span class="sxs-lookup"><span data-stu-id="81612-121">All identifiers are removed from the collection.</span></span>|  
|`<remove value=xs:string>`|<span data-ttu-id="81612-122">Odstraní identifikátor URI určený `value` atributem z kolekce audienceUris.</span><span class="sxs-lookup"><span data-stu-id="81612-122">Removes the URI specified by the `value` attribute from the audienceUris collection.</span></span> <span data-ttu-id="81612-123">`value` Atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="81612-123">The `value` attribute is required.</span></span> <span data-ttu-id="81612-124">Identifikátor URI rozlišuje velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="81612-124">The URI is case-sensitive.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="81612-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="81612-125">Parent Elements</span></span>  
  
|<span data-ttu-id="81612-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="81612-126">Element</span></span>|<span data-ttu-id="81612-127">Description</span><span class="sxs-lookup"><span data-stu-id="81612-127">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="81612-128">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="81612-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81612-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81612-129">Remarks</span></span>  
 <span data-ttu-id="81612-130">Ve výchozím nastavení je kolekce prázdná. `<add>` `<clear>` `<remove>` pro úpravu kolekce použijte prvky, a.</span><span class="sxs-lookup"><span data-stu-id="81612-130">By default, the collection is empty; use `<add>`, `<clear>`, and `<remove>` elements to modify the collection.</span></span> <span data-ttu-id="81612-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler><xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>objekty a používají hodnoty v kolekci identifikátorů URI cílové skupiny ke konfiguraci libovolných povolených omezení identifikátorů URI cílové skupiny v <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objektech.</span><span class="sxs-lookup"><span data-stu-id="81612-131"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> and <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> objects use the values in the audience URI collection to configure any allowed audience URI restrictions in <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objects.</span></span>  
  
 <span data-ttu-id="81612-132">`<audienceUris>`Element je reprezentován <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> třídou.</span><span class="sxs-lookup"><span data-stu-id="81612-132">The `<audienceUris>` element is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElementCollection> class.</span></span> <span data-ttu-id="81612-133">Jednotlivé identifikátory URI přidané do kolekce jsou reprezentovány <xref:System.IdentityModel.Configuration.AudienceUriElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="81612-133">An individual URI added to the collection is represented by the <xref:System.IdentityModel.Configuration.AudienceUriElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81612-134">Použití `<audienceUris>` prvku jako podřízeného prvku [\<identityConfiguration>](identityconfiguration.md) elementu je zastaralé, ale je stále podporováno z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="81612-134">The use of the `<audienceUris>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="81612-135">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="81612-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81612-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="81612-136">Example</span></span>  
 <span data-ttu-id="81612-137">Následující kód XML ukazuje, jak nakonfigurovat přijatelné identifikátory URI cílové skupiny pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="81612-137">The following XML shows how to configure the acceptable audience URIs for an application.</span></span> <span data-ttu-id="81612-138">Tento příklad nakonfiguruje jeden identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="81612-138">This example configures a single URI.</span></span> <span data-ttu-id="81612-139">Tokeny vymezené pro tento identifikátor URI budou přijaty, ostatní budou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="81612-139">Tokens scoped for this URI will be accepted, all others will be rejected.</span></span>  
  
```xml  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```
