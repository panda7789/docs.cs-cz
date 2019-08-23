---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: df259398beb242ea95efb248d6b5140b38ca3c45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942490"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="955de-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="955de-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="955de-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="955de-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="955de-103">Reprezentované <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídou.</span><span class="sxs-lookup"><span data-stu-id="955de-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="955de-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="955de-104">\<system.identityModel></span></span>  
<span data-ttu-id="955de-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="955de-105">\<identityConfiguration></span></span>  
<span data-ttu-id="955de-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="955de-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="955de-107">\<add></span><span class="sxs-lookup"><span data-stu-id="955de-107">\<add></span></span>  
<span data-ttu-id="955de-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="955de-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955de-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="955de-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="955de-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="955de-110">Attributes and Elements</span></span>  
 <span data-ttu-id="955de-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="955de-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="955de-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="955de-112">Attributes</span></span>  
  
|<span data-ttu-id="955de-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="955de-113">Attribute</span></span>|<span data-ttu-id="955de-114">Popis</span><span class="sxs-lookup"><span data-stu-id="955de-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="955de-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="955de-115">mapToWindows</span></span>|<span data-ttu-id="955de-116">Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního názvu uživatele (UPN).</span><span class="sxs-lookup"><span data-stu-id="955de-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="955de-117">Výchozí hodnota je false (NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="955de-117">The default is "false".</span></span>|  
|<span data-ttu-id="955de-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="955de-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="955de-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="955de-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="955de-120">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="955de-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="955de-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="955de-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="955de-122"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="955de-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="955de-123">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="955de-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="955de-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="955de-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="955de-125"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="955de-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="955de-126">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="955de-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="955de-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="955de-127">issuerCertificateValidator</span></span>|<span data-ttu-id="955de-128">Vlastní typ, který je odvozen z <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="955de-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="955de-129">Pokud je `issuerCertificateValidationMode` atribut "Custom", instance tohoto typu se používá pro ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="955de-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="955de-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="955de-130">Child Elements</span></span>  
  
|<span data-ttu-id="955de-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="955de-131">Element</span></span>|<span data-ttu-id="955de-132">Popis</span><span class="sxs-lookup"><span data-stu-id="955de-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="955de-133">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="955de-133">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="955de-134">Nastaví typ deklarace identity, který určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="955de-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="955de-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="955de-135">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="955de-136">Určuje typ deklarace identity, který definuje deklarace typu role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="955de-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="955de-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="955de-137">Parent Elements</span></span>  
  
|<span data-ttu-id="955de-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="955de-138">Element</span></span>|<span data-ttu-id="955de-139">Popis</span><span class="sxs-lookup"><span data-stu-id="955de-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="955de-140">\<add></span><span class="sxs-lookup"><span data-stu-id="955de-140">\<add></span></span>](add.md)|<span data-ttu-id="955de-141">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="955de-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="955de-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="955de-142">Remarks</span></span>  
 <span data-ttu-id="955de-143"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> Element je reprezentován třídou v objektovém modelu a slouží ke konfiguraci vlastnosti v nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>. `<samlSecurityTokenRequirement>`</span><span class="sxs-lookup"><span data-stu-id="955de-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="955de-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="955de-144">Example</span></span>  
  
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
