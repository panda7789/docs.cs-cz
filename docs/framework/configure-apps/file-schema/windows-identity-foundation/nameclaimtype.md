---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 47366c5bb2bd9228268fce3ae6e1fb5ad457dab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942624"
---
# <a name="nameclaimtype"></a><span data-ttu-id="ae1de-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="ae1de-101">\<nameClaimType></span></span>
<span data-ttu-id="ae1de-102">Nastaví typ deklarace identity, který určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae1de-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="ae1de-103">Typ deklarace identity se používá pro hledání <xref:System.Security.Claims.Claim> v <xref:System.Security.Claims.ClaimsIdentity> kolekci objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou této obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="ae1de-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="ae1de-104">Hodnota odpovídajícího deklarace identity se pak nastaví jako název <xref:System.Security.Principal.IIdentity> generovaný z této obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="ae1de-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="ae1de-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ae1de-105">\<system.identityModel></span></span>  
<span data-ttu-id="ae1de-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ae1de-106">\<identityConfiguration></span></span>  
<span data-ttu-id="ae1de-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ae1de-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ae1de-108">\<add></span><span class="sxs-lookup"><span data-stu-id="ae1de-108">\<add></span></span>  
<span data-ttu-id="ae1de-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ae1de-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="ae1de-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="ae1de-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae1de-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ae1de-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae1de-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ae1de-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ae1de-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ae1de-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae1de-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="ae1de-114">Attributes</span></span>  
  
|<span data-ttu-id="ae1de-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="ae1de-115">Attribute</span></span>|<span data-ttu-id="ae1de-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ae1de-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae1de-117">value</span><span class="sxs-lookup"><span data-stu-id="ae1de-117">value</span></span>|<span data-ttu-id="ae1de-118">Řetězec určující identifikátor URI, který představuje typ deklarace identity, který má být použit pro <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ae1de-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="ae1de-119">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="ae1de-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae1de-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ae1de-120">Child Elements</span></span>  
 <span data-ttu-id="ae1de-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="ae1de-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae1de-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ae1de-122">Parent Elements</span></span>  
  
|<span data-ttu-id="ae1de-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="ae1de-123">Element</span></span>|<span data-ttu-id="ae1de-124">Popis</span><span class="sxs-lookup"><span data-stu-id="ae1de-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae1de-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ae1de-125">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="ae1de-126">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="ae1de-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae1de-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ae1de-127">Remarks</span></span>  
 <span data-ttu-id="ae1de-128">Element nastaví vlastnost, <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> když <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> je objekt inicializován z konfigurace. `<nameClaimType>`</span><span class="sxs-lookup"><span data-stu-id="ae1de-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae1de-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae1de-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae1de-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae1de-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
