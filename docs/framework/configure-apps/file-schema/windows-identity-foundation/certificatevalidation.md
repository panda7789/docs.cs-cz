---
title: '&lt;certificateValidation&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7a5d31bce5f71e644b40b3aa7e7c0c1c8790cab6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="9a307-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="9a307-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="9a307-103">Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9a307-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="9a307-104">Tato nastavení jsou přepsat, pokud obslužná rutina specifická nakonfigurovaný s vlastním validátoru.</span><span class="sxs-lookup"><span data-stu-id="9a307-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="9a307-105">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="9a307-105">\<system.identityModel></span></span>  
<span data-ttu-id="9a307-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9a307-106">\<identityConfiguration></span></span>  
<span data-ttu-id="9a307-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="9a307-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a307-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a307-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a307-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9a307-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9a307-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9a307-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9a307-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="9a307-111">Attributes</span></span>  
  
|<span data-ttu-id="9a307-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="9a307-112">Attribute</span></span>|<span data-ttu-id="9a307-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9a307-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9a307-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="9a307-114">certificateValidationMode</span></span>|<span data-ttu-id="9a307-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnotu, která určuje režim ověřování pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="9a307-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9a307-116">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="9a307-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="9a307-117">Chcete-li zadat vlastní validátor, nastavte tento atribut na hodnotu "Vlastní" a zadejte validátor pomocí [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span><span class="sxs-lookup"><span data-stu-id="9a307-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="9a307-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9a307-118">Optional.</span></span>|  
|<span data-ttu-id="9a307-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="9a307-119">revocationMode</span></span>|<span data-ttu-id="9a307-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnotu, která určuje režim odvolaných certifikátů pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="9a307-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="9a307-121">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="9a307-121">The default value is "Online".</span></span> <span data-ttu-id="9a307-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9a307-122">Optional.</span></span>|  
|<span data-ttu-id="9a307-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="9a307-123">trustedStoreLocation</span></span>|<span data-ttu-id="9a307-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="9a307-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="9a307-125">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="9a307-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="9a307-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="9a307-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9a307-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9a307-127">Child Elements</span></span>  
  
|<span data-ttu-id="9a307-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="9a307-128">Element</span></span>|<span data-ttu-id="9a307-129">Popis</span><span class="sxs-lookup"><span data-stu-id="9a307-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a307-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="9a307-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="9a307-131">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="9a307-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="9a307-132">Tento typ se používá pouze v případě `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element je nastaven na hodnotu "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="9a307-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9a307-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9a307-133">Parent Elements</span></span>  
  
|<span data-ttu-id="9a307-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="9a307-134">Element</span></span>|<span data-ttu-id="9a307-135">Popis</span><span class="sxs-lookup"><span data-stu-id="9a307-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9a307-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9a307-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="9a307-137">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="9a307-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="9a307-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9a307-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="9a307-139">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="9a307-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a307-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a307-140">Remarks</span></span>  
 <span data-ttu-id="9a307-141">A `<certificateValidation>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9a307-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="9a307-142">Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="9a307-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="9a307-143">Některé tokenu obslužné rutiny umožňují určit nastavení ověření certifikátu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="9a307-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="9a307-144">Nastavení na jednotlivých tokenu obslužné rutiny přepsat tyto zadané na úrovni služby i na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="9a307-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a307-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a307-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
