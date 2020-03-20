---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152629"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="c97aa-101">\<> samlSecurityTokenRequirement</span><span class="sxs-lookup"><span data-stu-id="c97aa-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="c97aa-102">Poskytuje konfiguraci <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> pro <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu, třídu nebo odvozenou třídu jedné z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="c97aa-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="c97aa-103">Reprezentované třídou. <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="c97aa-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="c97aa-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c97aa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c97aa-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c97aa-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c97aa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c97aa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c97aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="c97aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="c97aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="c97aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="c97aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>samlSecurityTokenRequirement**</span><span class="sxs-lookup"><span data-stu-id="c97aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97aa-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c97aa-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c97aa-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c97aa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c97aa-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c97aa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c97aa-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c97aa-113">Attributes</span></span>  
  
|<span data-ttu-id="c97aa-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="c97aa-114">Attribute</span></span>|<span data-ttu-id="c97aa-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c97aa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c97aa-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="c97aa-116">mapToWindows</span></span>|<span data-ttu-id="c97aa-117">Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního název uživatele.</span><span class="sxs-lookup"><span data-stu-id="c97aa-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="c97aa-118">Výchozí hodnota je "false".</span><span class="sxs-lookup"><span data-stu-id="c97aa-118">The default is "false".</span></span>|  
|<span data-ttu-id="c97aa-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="c97aa-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="c97aa-120">Hodnota, <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> která určuje režim odvolání, který má být pro certifikát X.509 používán.</span><span class="sxs-lookup"><span data-stu-id="c97aa-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c97aa-121">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="c97aa-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="c97aa-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="c97aa-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="c97aa-123">Hodnota, <xref:System.ServiceModel.Security.X509CertificateValidationMode> která určuje režim ověření pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="c97aa-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="c97aa-124">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="c97aa-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="c97aa-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="c97aa-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="c97aa-126">Hodnota, <xref:System.Security.Cryptography.X509Certificates.StoreLocation> která určuje úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="c97aa-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="c97aa-127">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="c97aa-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="c97aa-128">emitentCertifikátValidator</span><span class="sxs-lookup"><span data-stu-id="c97aa-128">issuerCertificateValidator</span></span>|<span data-ttu-id="c97aa-129">Vlastní typ, který <xref:System.IdentityModel.Selectors.X509CertificateValidator>je odvozen od .</span><span class="sxs-lookup"><span data-stu-id="c97aa-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="c97aa-130">Pokud `issuerCertificateValidationMode` je atribut "Vlastní", instance tohoto typu se používá pro ověření certifikátu vystavitho.</span><span class="sxs-lookup"><span data-stu-id="c97aa-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c97aa-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c97aa-131">Child Elements</span></span>  
  
|<span data-ttu-id="c97aa-132">Element</span><span class="sxs-lookup"><span data-stu-id="c97aa-132">Element</span></span>|<span data-ttu-id="c97aa-133">Popis</span><span class="sxs-lookup"><span data-stu-id="c97aa-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c97aa-134">\<názevClaimType></span><span class="sxs-lookup"><span data-stu-id="c97aa-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="c97aa-135">Nastaví typ deklarace, <xref:System.Security.Principal.IIdentity.Name%2A> která určuje vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c97aa-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="c97aa-136">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="c97aa-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="c97aa-137">Určuje typ deklarace identity, který definuje deklarace typu role v kolekci objektů vrácených <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="c97aa-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c97aa-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c97aa-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c97aa-139">Element</span><span class="sxs-lookup"><span data-stu-id="c97aa-139">Element</span></span>|<span data-ttu-id="c97aa-140">Popis</span><span class="sxs-lookup"><span data-stu-id="c97aa-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c97aa-141">\<přidat></span><span class="sxs-lookup"><span data-stu-id="c97aa-141">\<add></span></span>](add.md)|<span data-ttu-id="c97aa-142">Přidá zadanou obslužnou rutinu tokenu do kolekce obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="c97aa-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c97aa-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c97aa-143">Remarks</span></span>  
 <span data-ttu-id="c97aa-144">Prvek `<samlSecurityTokenRequirement>` je reprezentován <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídou v objektovém modelu `SamlSecurityTokenRequirement` a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> slouží <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>ke konfiguraci vlastnosti na nebo .</span><span class="sxs-lookup"><span data-stu-id="c97aa-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c97aa-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="c97aa-145">Example</span></span>  
  
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
