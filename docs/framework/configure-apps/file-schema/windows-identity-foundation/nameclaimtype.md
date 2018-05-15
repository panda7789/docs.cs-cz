---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e403667f16e316004f766b8476e20eca9bd1c988
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="f6ff0-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="f6ff0-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="f6ff0-103">Nastaví typ deklarace identity, která určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="f6ff0-104">Typ deklarace identity se používá pro vyhledávání <xref:System.Security.Claims.Claim> v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácený <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda Tato obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="f6ff0-105">Hodnota odpovídající deklarace identity je pak nastavená na název <xref:System.Security.Principal.IIdentity> generované z této obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="f6ff0-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f6ff0-106">\<system.identityModel></span></span>  
<span data-ttu-id="f6ff0-107">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f6ff0-107">\<identityConfiguration></span></span>  
<span data-ttu-id="f6ff0-108">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="f6ff0-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f6ff0-109">\<add></span><span class="sxs-lookup"><span data-stu-id="f6ff0-109">\<add></span></span>  
<span data-ttu-id="f6ff0-110">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f6ff0-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="f6ff0-111">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="f6ff0-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6ff0-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6ff0-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6ff0-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f6ff0-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f6ff0-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6ff0-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f6ff0-115">Attributes</span></span>  
  
|<span data-ttu-id="f6ff0-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="f6ff0-116">Attribute</span></span>|<span data-ttu-id="f6ff0-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f6ff0-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f6ff0-118">value</span><span class="sxs-lookup"><span data-stu-id="f6ff0-118">value</span></span>|<span data-ttu-id="f6ff0-119">Řetězec, který určuje identifikátor URI, který představuje typ deklarace identity pro deklarace identity <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="f6ff0-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6ff0-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f6ff0-121">Child Elements</span></span>  
 <span data-ttu-id="f6ff0-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="f6ff0-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6ff0-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f6ff0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="f6ff0-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="f6ff0-124">Element</span></span>|<span data-ttu-id="f6ff0-125">Popis</span><span class="sxs-lookup"><span data-stu-id="f6ff0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f6ff0-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="f6ff0-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="f6ff0-127">Poskytuje konfigurace <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , nebo odvozená třída buď z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6ff0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6ff0-128">Remarks</span></span>  
 <span data-ttu-id="f6ff0-129">`<nameClaimType>` Nastaví element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> vlastnost při <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f6ff0-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6ff0-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6ff0-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6ff0-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6ff0-131">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
