---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152447"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="1f740-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="1f740-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="1f740-102">Poskytuje volitelnou <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> konfiguraci pro třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="1f740-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="1f740-103">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f740-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f740-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="1f740-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="1f740-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="1f740-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="1f740-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="1f740-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="1f740-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="1f740-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="1f740-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509je>**</span><span class="sxs-lookup"><span data-stu-id="1f740-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f740-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f740-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f740-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1f740-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1f740-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1f740-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f740-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f740-112">Attributes</span></span>  
  
|<span data-ttu-id="1f740-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1f740-113">Attribute</span></span>|<span data-ttu-id="1f740-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1f740-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f740-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1f740-115">certificateValidationMode</span></span>|<span data-ttu-id="1f740-116">Hodnota, <xref:System.ServiceModel.Security.X509CertificateValidationMode> která určuje režim ověření pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="1f740-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1f740-117">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="1f740-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="1f740-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="1f740-118">mapToWindows</span></span>|<span data-ttu-id="1f740-119">Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního název uživatele.</span><span class="sxs-lookup"><span data-stu-id="1f740-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="1f740-120">Výchozí hodnota je "false".</span><span class="sxs-lookup"><span data-stu-id="1f740-120">The default is "false".</span></span>|  
|<span data-ttu-id="1f740-121">režim odvolání</span><span class="sxs-lookup"><span data-stu-id="1f740-121">revocationMode</span></span>|<span data-ttu-id="1f740-122">Hodnota, <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> která určuje režim odvolání, který má být pro certifikát X.509 používán.</span><span class="sxs-lookup"><span data-stu-id="1f740-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1f740-123">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="1f740-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="1f740-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1f740-124">trustedStoreLocation</span></span>|<span data-ttu-id="1f740-125">Hodnota, <xref:System.Security.Cryptography.X509Certificates.StoreLocation> která určuje úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="1f740-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="1f740-126">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="1f740-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="1f740-127">certifikátValidator</span><span class="sxs-lookup"><span data-stu-id="1f740-127">certificateValidator</span></span>|<span data-ttu-id="1f740-128">Vlastní typ, který <xref:System.IdentityModel.Selectors.X509CertificateValidator>je odvozen od .</span><span class="sxs-lookup"><span data-stu-id="1f740-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="1f740-129">Pokud `certificateValidationMode` je atribut "Vlastní", instance tohoto typu se používá pro ověření certifikátu vystavitho.</span><span class="sxs-lookup"><span data-stu-id="1f740-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f740-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1f740-130">Child Elements</span></span>  
 <span data-ttu-id="1f740-131">Žádný</span><span class="sxs-lookup"><span data-stu-id="1f740-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f740-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1f740-132">Parent Elements</span></span>  
  
|<span data-ttu-id="1f740-133">Element</span><span class="sxs-lookup"><span data-stu-id="1f740-133">Element</span></span>|<span data-ttu-id="1f740-134">Popis</span><span class="sxs-lookup"><span data-stu-id="1f740-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f740-135">\<přidat></span><span class="sxs-lookup"><span data-stu-id="1f740-135">\<add></span></span>](add.md)|<span data-ttu-id="1f740-136">Přidá zadanou obslužnou rutinu tokenu do kolekce obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="1f740-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f740-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f740-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
