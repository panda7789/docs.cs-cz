---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251943"
---
# <a name="nameclaimtype"></a><span data-ttu-id="b39bb-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="b39bb-101">\<nameClaimType></span></span>
<span data-ttu-id="b39bb-102">Nastaví typ deklarace identity, který určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b39bb-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="b39bb-103">Typ deklarace identity se používá pro hledání <xref:System.Security.Claims.Claim> v <xref:System.Security.Claims.ClaimsIdentity> kolekci objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou této obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="b39bb-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="b39bb-104">Hodnota odpovídajícího deklarace identity se pak nastaví jako název <xref:System.Security.Principal.IIdentity> generovaný z této obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="b39bb-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
<span data-ttu-id="b39bb-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b39bb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b39bb-106">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="b39bb-106">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="b39bb-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b39bb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="b39bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="b39bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="b39bb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Přidat >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="b39bb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="b39bb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="b39bb-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="b39bb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameClaimType >**</span><span class="sxs-lookup"><span data-stu-id="b39bb-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b39bb-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b39bb-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b39bb-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b39bb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b39bb-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b39bb-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b39bb-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="b39bb-115">Attributes</span></span>  
  
|<span data-ttu-id="b39bb-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="b39bb-116">Attribute</span></span>|<span data-ttu-id="b39bb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b39bb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b39bb-118">value</span><span class="sxs-lookup"><span data-stu-id="b39bb-118">value</span></span>|<span data-ttu-id="b39bb-119">Řetězec určující identifikátor URI, který představuje typ deklarace identity, který má být použit pro <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b39bb-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="b39bb-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b39bb-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b39bb-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b39bb-121">Child Elements</span></span>  
 <span data-ttu-id="b39bb-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="b39bb-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b39bb-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b39bb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b39bb-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b39bb-124">Element</span></span>|<span data-ttu-id="b39bb-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b39bb-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b39bb-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="b39bb-126">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="b39bb-127">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="b39bb-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b39bb-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b39bb-128">Remarks</span></span>  
 <span data-ttu-id="b39bb-129">Element nastaví vlastnost, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> když <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> je objekt inicializován z konfigurace. `<nameClaimType>`</span><span class="sxs-lookup"><span data-stu-id="b39bb-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b39bb-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="b39bb-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b39bb-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b39bb-131">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
