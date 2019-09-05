---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: cab7572518a7a6dc26f8bbcf67cd424fa1c01085
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251893"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="c0b94-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="c0b94-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="c0b94-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="c0b94-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="c0b94-103">Reprezentované <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídou.</span><span class="sxs-lookup"><span data-stu-id="c0b94-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="c0b94-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0b94-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0b94-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0b94-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c0b94-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c0b94-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c0b94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="c0b94-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="c0b94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Přidat >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="c0b94-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="c0b94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<samlSecurityTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="c0b94-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b94-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0b94-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0b94-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c0b94-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c0b94-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c0b94-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0b94-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c0b94-113">Attributes</span></span>  
  
|<span data-ttu-id="c0b94-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="c0b94-114">Attribute</span></span>|<span data-ttu-id="c0b94-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b94-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0b94-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="c0b94-116">mapToWindows</span></span>|<span data-ttu-id="c0b94-117">Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního názvu uživatele (UPN).</span><span class="sxs-lookup"><span data-stu-id="c0b94-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="c0b94-118">Výchozí hodnota je false (NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="c0b94-118">The default is "false".</span></span>|  
|<span data-ttu-id="c0b94-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="c0b94-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="c0b94-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="c0b94-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c0b94-121">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="c0b94-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="c0b94-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="c0b94-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="c0b94-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="c0b94-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c0b94-124">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="c0b94-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="c0b94-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="c0b94-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="c0b94-126"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="c0b94-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="c0b94-127">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="c0b94-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="c0b94-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="c0b94-128">issuerCertificateValidator</span></span>|<span data-ttu-id="c0b94-129">Vlastní typ, který je odvozen z <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c0b94-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c0b94-130">Pokud je `issuerCertificateValidationMode` atribut "Custom", instance tohoto typu se používá pro ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="c0b94-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0b94-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c0b94-131">Child Elements</span></span>  
  
|<span data-ttu-id="c0b94-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0b94-132">Element</span></span>|<span data-ttu-id="c0b94-133">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b94-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0b94-134">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="c0b94-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="c0b94-135">Nastaví typ deklarace identity, který určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c0b94-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="c0b94-136">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="c0b94-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="c0b94-137">Určuje typ deklarace identity, který definuje deklarace typu role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="c0b94-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0b94-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c0b94-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c0b94-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="c0b94-139">Element</span></span>|<span data-ttu-id="c0b94-140">Popis</span><span class="sxs-lookup"><span data-stu-id="c0b94-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0b94-141">\<add></span><span class="sxs-lookup"><span data-stu-id="c0b94-141">\<add></span></span>](add.md)|<span data-ttu-id="c0b94-142">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c0b94-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0b94-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0b94-143">Remarks</span></span>  
 <span data-ttu-id="c0b94-144"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Element je reprezentován třídou v objektovém modelu a slouží ke konfiguraci vlastnosti v nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>. `<samlSecurityTokenRequirement>`</span><span class="sxs-lookup"><span data-stu-id="c0b94-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0b94-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0b94-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
