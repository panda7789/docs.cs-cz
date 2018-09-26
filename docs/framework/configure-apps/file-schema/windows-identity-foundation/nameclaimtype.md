---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: bd4033b2edea7450b66c25f446669b3ded65e9af
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112215"
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="d668d-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="d668d-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="d668d-103">Nastaví typ deklarace identity, která určuje, <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d668d-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d668d-104">Typ deklarace identity se používá k hledání <xref:System.Security.Claims.Claim> v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených podle <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda této obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="d668d-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="d668d-105">Hodnota odpovídající deklarace identity je nastavili jako název <xref:System.Security.Principal.IIdentity> vygenerované z této obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="d668d-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="d668d-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d668d-106">\<system.identityModel></span></span>  
<span data-ttu-id="d668d-107">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d668d-107">\<identityConfiguration></span></span>  
<span data-ttu-id="d668d-108">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d668d-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d668d-109">\<add></span><span class="sxs-lookup"><span data-stu-id="d668d-109">\<add></span></span>  
<span data-ttu-id="d668d-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d668d-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="d668d-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="d668d-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d668d-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d668d-112">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d668d-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d668d-113">Attributes and Elements</span></span>  
 <span data-ttu-id="d668d-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d668d-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d668d-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="d668d-115">Attributes</span></span>  
  
|<span data-ttu-id="d668d-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="d668d-116">Attribute</span></span>|<span data-ttu-id="d668d-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d668d-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d668d-118">value</span><span class="sxs-lookup"><span data-stu-id="d668d-118">value</span></span>|<span data-ttu-id="d668d-119">Řetězec určující identifikátor URI, který představuje typ deklarace identity z deklarací identity pro <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d668d-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d668d-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d668d-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d668d-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d668d-121">Child Elements</span></span>  
 <span data-ttu-id="d668d-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="d668d-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d668d-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d668d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d668d-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d668d-124">Element</span></span>|<span data-ttu-id="d668d-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d668d-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d668d-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d668d-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="d668d-127">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="d668d-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d668d-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d668d-128">Remarks</span></span>  
 <span data-ttu-id="d668d-129">`<nameClaimType>` Nastaví element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> vlastnost při <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d668d-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d668d-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="d668d-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d668d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="d668d-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
