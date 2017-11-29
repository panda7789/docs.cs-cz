---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e0d8d467c2636f5ce95cf5fed189ae00c3ca75fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="60cf1-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="60cf1-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="60cf1-103">Poskytuje konfigurace <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , nebo odvozená třída buď z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="60cf1-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="60cf1-104">Reprezentována <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídy.</span><span class="sxs-lookup"><span data-stu-id="60cf1-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="60cf1-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="60cf1-105">\<system.identityModel></span></span>  
<span data-ttu-id="60cf1-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="60cf1-106">\<identityConfiguration></span></span>  
<span data-ttu-id="60cf1-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="60cf1-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="60cf1-108">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="60cf1-108">\<add></span></span>  
<span data-ttu-id="60cf1-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="60cf1-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60cf1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60cf1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60cf1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="60cf1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="60cf1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="60cf1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60cf1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="60cf1-113">Attributes</span></span>  
  
|<span data-ttu-id="60cf1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="60cf1-114">Attribute</span></span>|<span data-ttu-id="60cf1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="60cf1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="60cf1-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="60cf1-116">mapToWindows</span></span>|<span data-ttu-id="60cf1-117">Určuje, zda obslužná rutina tokenu by měl mapovat ověřování tokenu účet systému Windows pomocí příchozí deklarace identity UPN.</span><span class="sxs-lookup"><span data-stu-id="60cf1-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="60cf1-118">Výchozí hodnota je "false".</span><span class="sxs-lookup"><span data-stu-id="60cf1-118">The default is "false".</span></span>|  
|<span data-ttu-id="60cf1-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="60cf1-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="60cf1-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnotu, která určuje režim odvolaných certifikátů pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="60cf1-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="60cf1-121">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="60cf1-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="60cf1-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="60cf1-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="60cf1-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnotu, která určuje režim ověřování pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="60cf1-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="60cf1-124">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="60cf1-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="60cf1-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="60cf1-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="60cf1-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="60cf1-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="60cf1-127">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="60cf1-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="60cf1-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="60cf1-128">issuerCertificateValidator</span></span>|<span data-ttu-id="60cf1-129">Vlastního typu, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="60cf1-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="60cf1-130">Pokud `issuerCertificateValidationMode` atribut je "Vlastní", instance tohoto typu se používá k ověření vystavitele certifikátu.</span><span class="sxs-lookup"><span data-stu-id="60cf1-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60cf1-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="60cf1-131">Child Elements</span></span>  
  
|<span data-ttu-id="60cf1-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="60cf1-132">Element</span></span>|<span data-ttu-id="60cf1-133">Popis</span><span class="sxs-lookup"><span data-stu-id="60cf1-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60cf1-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="60cf1-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="60cf1-135">Nastaví typ deklarace identity, která určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="60cf1-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="60cf1-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="60cf1-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="60cf1-137">Určuje typ deklarace identity, která definuje typ deklarace role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácený <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="60cf1-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="60cf1-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="60cf1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="60cf1-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="60cf1-139">Element</span></span>|<span data-ttu-id="60cf1-140">Popis</span><span class="sxs-lookup"><span data-stu-id="60cf1-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60cf1-141">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="60cf1-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="60cf1-142">Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="60cf1-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="60cf1-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60cf1-143">Remarks</span></span>  
 <span data-ttu-id="60cf1-144">`<samlSecurityTokenRequirement>` Element je reprezentována <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídy v objektovém modelu a slouží ke konfiguraci `SamlSecurityTokenRequirement` vlastnost <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="60cf1-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60cf1-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="60cf1-145">Example</span></span>  
  
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
