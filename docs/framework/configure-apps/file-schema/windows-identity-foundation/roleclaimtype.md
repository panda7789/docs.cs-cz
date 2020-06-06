---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251914"
---
# \<roleClaimType>
<span data-ttu-id="0f6de-101">Určuje typ deklarace identity, který definuje deklarace typu role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="0f6de-101">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="0f6de-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f6de-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f6de-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0f6de-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0f6de-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0f6de-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f6de-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="0f6de-105">Attributes</span></span>  
  
|<span data-ttu-id="0f6de-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="0f6de-106">Attribute</span></span>|<span data-ttu-id="0f6de-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0f6de-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f6de-108">hodnota</span><span class="sxs-lookup"><span data-stu-id="0f6de-108">value</span></span>|<span data-ttu-id="0f6de-109">Řetězec určující identifikátor URI, který představuje typ deklarace identity, který se má použít pro typ deklarace role.</span><span class="sxs-lookup"><span data-stu-id="0f6de-109">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f6de-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0f6de-110">Child Elements</span></span>  
 <span data-ttu-id="0f6de-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="0f6de-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f6de-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0f6de-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0f6de-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="0f6de-113">Element</span></span>|<span data-ttu-id="0f6de-114">Description</span><span class="sxs-lookup"><span data-stu-id="0f6de-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="0f6de-115">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="0f6de-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f6de-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f6de-116">Remarks</span></span>  
 <span data-ttu-id="0f6de-117">`<roleClaimType>`Element nastaví vlastnost, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> Když <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> je objekt inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0f6de-117">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f6de-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f6de-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f6de-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0f6de-119">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
