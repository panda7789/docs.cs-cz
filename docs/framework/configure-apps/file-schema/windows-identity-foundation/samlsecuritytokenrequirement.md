---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152629"
---
# \<samlSecurityTokenRequirement>
<span data-ttu-id="1e760-101">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="1e760-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="1e760-102">Reprezentované <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídou.</span><span class="sxs-lookup"><span data-stu-id="1e760-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="1e760-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e760-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e760-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1e760-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1e760-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1e760-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e760-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="1e760-106">Attributes</span></span>  
  
|<span data-ttu-id="1e760-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="1e760-107">Attribute</span></span>|<span data-ttu-id="1e760-108">Popis</span><span class="sxs-lookup"><span data-stu-id="1e760-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1e760-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="1e760-109">mapToWindows</span></span>|<span data-ttu-id="1e760-110">Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního názvu uživatele (UPN).</span><span class="sxs-lookup"><span data-stu-id="1e760-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="1e760-111">Výchozí hodnota je false (NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="1e760-111">The default is "false".</span></span>|  
|<span data-ttu-id="1e760-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="1e760-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="1e760-113"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="1e760-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1e760-114">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="1e760-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="1e760-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1e760-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="1e760-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="1e760-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1e760-117">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="1e760-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="1e760-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1e760-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="1e760-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="1e760-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="1e760-120">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="1e760-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="1e760-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="1e760-121">issuerCertificateValidator</span></span>|<span data-ttu-id="1e760-122">Vlastní typ, který je odvozen z <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="1e760-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="1e760-123">Pokud `issuerCertificateValidationMode` je atribut "Custom", instance tohoto typu se používá pro ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="1e760-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e760-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1e760-124">Child Elements</span></span>  
  
|<span data-ttu-id="1e760-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="1e760-125">Element</span></span>|<span data-ttu-id="1e760-126">Description</span><span class="sxs-lookup"><span data-stu-id="1e760-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="1e760-127">Nastaví typ deklarace identity, který určuje <xref:System.Security.Principal.IIdentity.Name%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1e760-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="1e760-128">Určuje typ deklarace identity, který definuje deklarace typu role v kolekci <xref:System.Security.Claims.ClaimsIdentity> objektů vrácených <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> metodou obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="1e760-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e760-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1e760-129">Parent Elements</span></span>  
  
|<span data-ttu-id="1e760-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="1e760-130">Element</span></span>|<span data-ttu-id="1e760-131">Description</span><span class="sxs-lookup"><span data-stu-id="1e760-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="1e760-132">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1e760-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e760-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e760-133">Remarks</span></span>  
 <span data-ttu-id="1e760-134">`<samlSecurityTokenRequirement>`Element je reprezentován <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> třídou v objektovém modelu a slouží ke konfiguraci `SamlSecurityTokenRequirement` vlastnosti v <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> nebo <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="1e760-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e760-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e760-135">Example</span></span>  
  
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
