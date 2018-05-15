---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 909df1bd6054d9737f91c30c3c6b2d68b932281c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="feb49-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="feb49-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="feb49-103">Určuje typ deklarace identity, která definuje typ deklarace role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácený <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="feb49-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="feb49-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="feb49-104">\<system.identityModel></span></span>  
<span data-ttu-id="feb49-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="feb49-105">\<identityConfiguration></span></span>  
<span data-ttu-id="feb49-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="feb49-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="feb49-107">\<add></span><span class="sxs-lookup"><span data-stu-id="feb49-107">\<add></span></span>  
<span data-ttu-id="feb49-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="feb49-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="feb49-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="feb49-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="feb49-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feb49-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="feb49-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="feb49-111">Attributes and Elements</span></span>  
 <span data-ttu-id="feb49-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="feb49-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="feb49-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="feb49-113">Attributes</span></span>  
  
|<span data-ttu-id="feb49-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="feb49-114">Attribute</span></span>|<span data-ttu-id="feb49-115">Popis</span><span class="sxs-lookup"><span data-stu-id="feb49-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="feb49-116">value</span><span class="sxs-lookup"><span data-stu-id="feb49-116">value</span></span>|<span data-ttu-id="feb49-117">Řetězec, který určuje identifikátor URI, který představuje typ deklarace identity deklarací identity pro typ deklarace role.</span><span class="sxs-lookup"><span data-stu-id="feb49-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="feb49-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="feb49-118">Child Elements</span></span>  
 <span data-ttu-id="feb49-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="feb49-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="feb49-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="feb49-120">Parent Elements</span></span>  
  
|<span data-ttu-id="feb49-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="feb49-121">Element</span></span>|<span data-ttu-id="feb49-122">Popis</span><span class="sxs-lookup"><span data-stu-id="feb49-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="feb49-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="feb49-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="feb49-124">Poskytuje konfigurace <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , nebo odvozená třída buď z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="feb49-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feb49-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="feb49-125">Remarks</span></span>  
 <span data-ttu-id="feb49-126">`<roleClaimType>` Nastaví element <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> vlastnost při <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> objekt je inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="feb49-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feb49-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="feb49-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="feb49-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="feb49-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
