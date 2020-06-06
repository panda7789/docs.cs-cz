---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251943"
---
# \<nameClaimType>
<span data-ttu-id="945a9-101">Nastaví typ deklarace identity, který určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="945a9-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="945a9-102">Typ deklarace identity se používá pro hledání <xref:System.Security.Claims.Claim> v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou této obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="945a9-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="945a9-103">Hodnota odpovídajícího deklarace identity se pak nastaví jako název <xref:System.Security.Principal.IIdentity> generovaný z této obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="945a9-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="945a9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="945a9-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="945a9-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="945a9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="945a9-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="945a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="945a9-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="945a9-107">Attributes</span></span>  
  
|<span data-ttu-id="945a9-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="945a9-108">Attribute</span></span>|<span data-ttu-id="945a9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="945a9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="945a9-110">hodnota</span><span class="sxs-lookup"><span data-stu-id="945a9-110">value</span></span>|<span data-ttu-id="945a9-111">Řetězec určující identifikátor URI, který představuje typ deklarace identity, který má být použit pro <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="945a9-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="945a9-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="945a9-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="945a9-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="945a9-113">Child Elements</span></span>  
 <span data-ttu-id="945a9-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="945a9-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="945a9-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="945a9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="945a9-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="945a9-116">Element</span></span>|<span data-ttu-id="945a9-117">Description</span><span class="sxs-lookup"><span data-stu-id="945a9-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="945a9-118">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="945a9-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="945a9-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="945a9-119">Remarks</span></span>  
 <span data-ttu-id="945a9-120">`<nameClaimType>`Element nastaví vlastnost, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> Když <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> je objekt inicializován z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="945a9-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="945a9-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="945a9-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="945a9-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="945a9-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
