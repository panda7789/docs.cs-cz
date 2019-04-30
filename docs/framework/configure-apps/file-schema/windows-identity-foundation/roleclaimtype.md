---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 8c7b7c9b42ac72b878aed4e12298dc3655f1e707
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793871"
---
# <a name="roleclaimtype"></a><span data-ttu-id="4f9b3-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="4f9b3-101">\<roleClaimType></span></span>
<span data-ttu-id="4f9b3-102">Určuje typ deklarace identity, která definuje typ deklarace role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených podle <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="4f9b3-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4f9b3-103">\<system.identityModel></span></span>  
<span data-ttu-id="4f9b3-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4f9b3-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4f9b3-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="4f9b3-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="4f9b3-106">\<add></span><span class="sxs-lookup"><span data-stu-id="4f9b3-106">\<add></span></span>  
<span data-ttu-id="4f9b3-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="4f9b3-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="4f9b3-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="4f9b3-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f9b3-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f9b3-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f9b3-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4f9b3-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4f9b3-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f9b3-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4f9b3-112">Attributes</span></span>  
  
|<span data-ttu-id="4f9b3-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4f9b3-113">Attribute</span></span>|<span data-ttu-id="4f9b3-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4f9b3-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f9b3-115">value</span><span class="sxs-lookup"><span data-stu-id="4f9b3-115">value</span></span>|<span data-ttu-id="4f9b3-116">Řetězec určující identifikátor URI, který představuje typ deklarace identity z deklarací identity pro deklarace typu role.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f9b3-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4f9b3-117">Child Elements</span></span>  
 <span data-ttu-id="4f9b3-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="4f9b3-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f9b3-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4f9b3-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4f9b3-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="4f9b3-120">Element</span></span>|<span data-ttu-id="4f9b3-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4f9b3-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f9b3-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="4f9b3-122">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="4f9b3-123">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f9b3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4f9b3-124">Remarks</span></span>  
 <span data-ttu-id="4f9b3-125">`<roleClaimType>` Nastaví element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> vlastnost při <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4f9b3-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f9b3-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f9b3-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f9b3-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f9b3-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
