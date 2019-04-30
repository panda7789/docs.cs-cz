---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: e1b8acd48ee185b3c6c50f70321bb9ca66e8e02b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793858"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="baf9b-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="baf9b-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="baf9b-102">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="baf9b-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="baf9b-103">Reprezentována <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídy.</span><span class="sxs-lookup"><span data-stu-id="baf9b-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="baf9b-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="baf9b-104">\<system.identityModel></span></span>  
<span data-ttu-id="baf9b-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="baf9b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="baf9b-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="baf9b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="baf9b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="baf9b-107">\<add></span></span>  
<span data-ttu-id="baf9b-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="baf9b-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baf9b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baf9b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baf9b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="baf9b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="baf9b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="baf9b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baf9b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="baf9b-112">Attributes</span></span>  
  
|<span data-ttu-id="baf9b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="baf9b-113">Attribute</span></span>|<span data-ttu-id="baf9b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="baf9b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="baf9b-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="baf9b-115">mapToWindows</span></span>|<span data-ttu-id="baf9b-116">Určuje, zda obslužná rutina tokenů mělo mapovat ověřování tokenu účet Windows s použitím příchozí deklarace identity UPN.</span><span class="sxs-lookup"><span data-stu-id="baf9b-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="baf9b-117">Výchozí hodnota je "false".</span><span class="sxs-lookup"><span data-stu-id="baf9b-117">The default is "false".</span></span>|  
|<span data-ttu-id="baf9b-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="baf9b-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="baf9b-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="baf9b-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="baf9b-120">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="baf9b-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="baf9b-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="baf9b-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="baf9b-122"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který chcete použít pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="baf9b-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="baf9b-123">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="baf9b-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="baf9b-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="baf9b-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="baf9b-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="baf9b-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="baf9b-126">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="baf9b-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="baf9b-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="baf9b-127">issuerCertificateValidator</span></span>|<span data-ttu-id="baf9b-128">Vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="baf9b-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="baf9b-129">Pokud `issuerCertificateValidationMode` atribut je "Vlastní", instance tohoto typu se používá k ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="baf9b-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baf9b-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="baf9b-130">Child Elements</span></span>  
  
|<span data-ttu-id="baf9b-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="baf9b-131">Element</span></span>|<span data-ttu-id="baf9b-132">Popis</span><span class="sxs-lookup"><span data-stu-id="baf9b-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baf9b-133">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="baf9b-133">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="baf9b-134">Nastaví typ deklarace identity, která určuje, <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="baf9b-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="baf9b-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="baf9b-135">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="baf9b-136">Určuje typ deklarace identity, která definuje typ deklarace role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených podle <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metoda obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="baf9b-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="baf9b-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="baf9b-137">Parent Elements</span></span>  
  
|<span data-ttu-id="baf9b-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="baf9b-138">Element</span></span>|<span data-ttu-id="baf9b-139">Popis</span><span class="sxs-lookup"><span data-stu-id="baf9b-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baf9b-140">\<add></span><span class="sxs-lookup"><span data-stu-id="baf9b-140">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="baf9b-141">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="baf9b-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baf9b-142">Poznámky</span><span class="sxs-lookup"><span data-stu-id="baf9b-142">Remarks</span></span>  
 <span data-ttu-id="baf9b-143">`<samlSecurityTokenRequirement>` Element je reprezentována <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídy v objektovém modelu a slouží ke konfiguraci `SamlSecurityTokenRequirement` vlastnosti <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="baf9b-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baf9b-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="baf9b-144">Example</span></span>  
  
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
