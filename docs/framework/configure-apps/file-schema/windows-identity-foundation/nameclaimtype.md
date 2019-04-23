---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 5202e162a7eb5fc4e36d6a6c0a2c18af48872a69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130322"
---
# <a name="nameclaimtype"></a><span data-ttu-id="d9bcc-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="d9bcc-101">\<nameClaimType></span></span>
<span data-ttu-id="d9bcc-102">Nastaví typ deklarace identity, která určuje, <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d9bcc-103">Typ deklarace identity se používá k hledání <xref:System.Security.Claims.Claim> v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených podle <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda této obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="d9bcc-104">Hodnota odpovídající deklarace identity je nastavili jako název <xref:System.Security.Principal.IIdentity> vygenerované z této obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="d9bcc-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d9bcc-105">\<system.identityModel></span></span>  
<span data-ttu-id="d9bcc-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d9bcc-106">\<identityConfiguration></span></span>  
<span data-ttu-id="d9bcc-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d9bcc-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d9bcc-108">\<add></span><span class="sxs-lookup"><span data-stu-id="d9bcc-108">\<add></span></span>  
<span data-ttu-id="d9bcc-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d9bcc-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="d9bcc-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="d9bcc-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9bcc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9bcc-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9bcc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d9bcc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d9bcc-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9bcc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9bcc-114">Attributes</span></span>  
  
|<span data-ttu-id="d9bcc-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d9bcc-115">Attribute</span></span>|<span data-ttu-id="d9bcc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d9bcc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9bcc-117">value</span><span class="sxs-lookup"><span data-stu-id="d9bcc-117">value</span></span>|<span data-ttu-id="d9bcc-118">Řetězec určující identifikátor URI, který představuje typ deklarace identity z deklarací identity pro <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d9bcc-119">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9bcc-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d9bcc-120">Child Elements</span></span>  
 <span data-ttu-id="d9bcc-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="d9bcc-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9bcc-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d9bcc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d9bcc-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9bcc-123">Element</span></span>|<span data-ttu-id="d9bcc-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d9bcc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9bcc-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d9bcc-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="d9bcc-126">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9bcc-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9bcc-127">Remarks</span></span>  
 <span data-ttu-id="d9bcc-128">`<nameClaimType>` Nastaví element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> vlastnost při <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d9bcc-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9bcc-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9bcc-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9bcc-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9bcc-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
