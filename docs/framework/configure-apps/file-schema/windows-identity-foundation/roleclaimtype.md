---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0ce2e06ee895d09de193bac1fe7038e71794dda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942545"
---
# <a name="roleclaimtype"></a><span data-ttu-id="d9e51-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="d9e51-101">\<roleClaimType></span></span>
<span data-ttu-id="d9e51-102">Určuje typ deklarace identity, který definuje deklarace typu role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="d9e51-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="d9e51-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d9e51-103">\<system.identityModel></span></span>  
<span data-ttu-id="d9e51-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d9e51-104">\<identityConfiguration></span></span>  
<span data-ttu-id="d9e51-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d9e51-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d9e51-106">\<add></span><span class="sxs-lookup"><span data-stu-id="d9e51-106">\<add></span></span>  
<span data-ttu-id="d9e51-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d9e51-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="d9e51-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="d9e51-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e51-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9e51-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9e51-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d9e51-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d9e51-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d9e51-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9e51-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9e51-112">Attributes</span></span>  
  
|<span data-ttu-id="d9e51-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d9e51-113">Attribute</span></span>|<span data-ttu-id="d9e51-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d9e51-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9e51-115">value</span><span class="sxs-lookup"><span data-stu-id="d9e51-115">value</span></span>|<span data-ttu-id="d9e51-116">Řetězec určující identifikátor URI, který představuje typ deklarace identity, který se má použít pro typ deklarace role.</span><span class="sxs-lookup"><span data-stu-id="d9e51-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9e51-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d9e51-117">Child Elements</span></span>  
 <span data-ttu-id="d9e51-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="d9e51-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9e51-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d9e51-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d9e51-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9e51-120">Element</span></span>|<span data-ttu-id="d9e51-121">Popis</span><span class="sxs-lookup"><span data-stu-id="d9e51-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9e51-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d9e51-122">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="d9e51-123">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="d9e51-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9e51-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9e51-124">Remarks</span></span>  
 <span data-ttu-id="d9e51-125">Element nastaví vlastnost, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> když <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> je objekt inicializován z konfigurace. `<roleClaimType>`</span><span class="sxs-lookup"><span data-stu-id="d9e51-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9e51-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9e51-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9e51-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9e51-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
