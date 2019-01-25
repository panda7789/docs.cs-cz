---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 6114a95f3942c367849785ce981858f276c0b8fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54599943"
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="af93c-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="af93c-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="af93c-103">Určuje typ deklarace identity, která definuje typ deklarace role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených podle <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="af93c-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="af93c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="af93c-104">\<system.identityModel></span></span>  
<span data-ttu-id="af93c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="af93c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="af93c-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="af93c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="af93c-107">\<add></span><span class="sxs-lookup"><span data-stu-id="af93c-107">\<add></span></span>  
<span data-ttu-id="af93c-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="af93c-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="af93c-109">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="af93c-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af93c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af93c-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af93c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="af93c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="af93c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="af93c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af93c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="af93c-113">Attributes</span></span>  
  
|<span data-ttu-id="af93c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="af93c-114">Attribute</span></span>|<span data-ttu-id="af93c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="af93c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="af93c-116">value</span><span class="sxs-lookup"><span data-stu-id="af93c-116">value</span></span>|<span data-ttu-id="af93c-117">Řetězec určující identifikátor URI, který představuje typ deklarace identity z deklarací identity pro deklarace typu role.</span><span class="sxs-lookup"><span data-stu-id="af93c-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="af93c-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="af93c-118">Child Elements</span></span>  
 <span data-ttu-id="af93c-119">Žádná</span><span class="sxs-lookup"><span data-stu-id="af93c-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="af93c-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="af93c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="af93c-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="af93c-121">Element</span></span>|<span data-ttu-id="af93c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="af93c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af93c-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="af93c-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="af93c-124">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="af93c-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af93c-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af93c-125">Remarks</span></span>  
 <span data-ttu-id="af93c-126">`<roleClaimType>` Nastaví element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> vlastnost při <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="af93c-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af93c-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="af93c-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af93c-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af93c-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
