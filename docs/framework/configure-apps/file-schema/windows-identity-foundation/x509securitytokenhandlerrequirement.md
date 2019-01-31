---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 6e8267f170dbb26381564be7b66df5f617156885
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271938"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="9c483-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="9c483-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="9c483-102">Poskytuje volitelné konfigurace pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="9c483-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="9c483-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9c483-103">\<system.identityModel></span></span>  
<span data-ttu-id="9c483-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9c483-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9c483-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="9c483-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="9c483-106">\<add></span><span class="sxs-lookup"><span data-stu-id="9c483-106">\<add></span></span>  
<span data-ttu-id="9c483-107">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="9c483-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c483-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c483-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c483-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9c483-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9c483-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9c483-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c483-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="9c483-111">Attributes</span></span>  
  
|<span data-ttu-id="9c483-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="9c483-112">Attribute</span></span>|<span data-ttu-id="9c483-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9c483-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c483-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="9c483-114">certificateValidationMode</span></span>|<span data-ttu-id="9c483-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který chcete použít pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="9c483-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9c483-116">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="9c483-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="9c483-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="9c483-117">mapToWindows</span></span>|<span data-ttu-id="9c483-118">Určuje, zda obslužná rutina tokenů mělo mapovat ověřování tokenu účet Windows s použitím příchozí deklarace identity UPN.</span><span class="sxs-lookup"><span data-stu-id="9c483-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="9c483-119">Výchozí hodnota je "false".</span><span class="sxs-lookup"><span data-stu-id="9c483-119">The default is "false".</span></span>|  
|<span data-ttu-id="9c483-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="9c483-120">revocationMode</span></span>|<span data-ttu-id="9c483-121"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="9c483-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9c483-122">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="9c483-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="9c483-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="9c483-123">trustedStoreLocation</span></span>|<span data-ttu-id="9c483-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="9c483-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="9c483-125">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="9c483-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="9c483-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="9c483-126">certificateValidator</span></span>|<span data-ttu-id="9c483-127">Vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="9c483-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="9c483-128">Pokud `certificateValidationMode` atribut je "Vlastní", instance tohoto typu se používá k ověření certifikátu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="9c483-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c483-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9c483-129">Child Elements</span></span>  
 <span data-ttu-id="9c483-130">Žádná</span><span class="sxs-lookup"><span data-stu-id="9c483-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c483-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9c483-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9c483-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="9c483-132">Element</span></span>|<span data-ttu-id="9c483-133">Popis</span><span class="sxs-lookup"><span data-stu-id="9c483-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c483-134">\<add></span><span class="sxs-lookup"><span data-stu-id="9c483-134">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="9c483-135">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="9c483-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9c483-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c483-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
