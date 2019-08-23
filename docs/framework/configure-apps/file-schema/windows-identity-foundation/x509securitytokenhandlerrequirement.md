---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 2851820460a34d62175929b48ad57914df557059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945182"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="2ea37-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="2ea37-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="2ea37-102">Poskytuje volitelnou konfiguraci pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="2ea37-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="2ea37-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2ea37-103">\<system.identityModel></span></span>  
<span data-ttu-id="2ea37-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2ea37-104">\<identityConfiguration></span></span>  
<span data-ttu-id="2ea37-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2ea37-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2ea37-106">\<add></span><span class="sxs-lookup"><span data-stu-id="2ea37-106">\<add></span></span>  
<span data-ttu-id="2ea37-107">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="2ea37-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea37-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ea37-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ea37-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ea37-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ea37-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ea37-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ea37-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ea37-111">Attributes</span></span>  
  
|<span data-ttu-id="2ea37-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ea37-112">Attribute</span></span>|<span data-ttu-id="2ea37-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2ea37-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2ea37-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="2ea37-114">certificateValidationMode</span></span>|<span data-ttu-id="2ea37-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="2ea37-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2ea37-116">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="2ea37-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="2ea37-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="2ea37-117">mapToWindows</span></span>|<span data-ttu-id="2ea37-118">Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního názvu uživatele (UPN).</span><span class="sxs-lookup"><span data-stu-id="2ea37-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="2ea37-119">Výchozí hodnota je false (NEPRAVDA).</span><span class="sxs-lookup"><span data-stu-id="2ea37-119">The default is "false".</span></span>|  
|<span data-ttu-id="2ea37-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="2ea37-120">revocationMode</span></span>|<span data-ttu-id="2ea37-121"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="2ea37-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="2ea37-122">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="2ea37-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="2ea37-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="2ea37-123">trustedStoreLocation</span></span>|<span data-ttu-id="2ea37-124"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="2ea37-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="2ea37-125">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="2ea37-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="2ea37-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="2ea37-126">certificateValidator</span></span>|<span data-ttu-id="2ea37-127">Vlastní typ, který je odvozen z <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="2ea37-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="2ea37-128">Pokud je `certificateValidationMode` atribut "Custom", instance tohoto typu se používá pro ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="2ea37-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ea37-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ea37-129">Child Elements</span></span>  
 <span data-ttu-id="2ea37-130">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ea37-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ea37-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ea37-131">Parent Elements</span></span>  
  
|<span data-ttu-id="2ea37-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ea37-132">Element</span></span>|<span data-ttu-id="2ea37-133">Popis</span><span class="sxs-lookup"><span data-stu-id="2ea37-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ea37-134">\<add></span><span class="sxs-lookup"><span data-stu-id="2ea37-134">\<add></span></span>](add.md)|<span data-ttu-id="2ea37-135">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2ea37-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2ea37-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ea37-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
