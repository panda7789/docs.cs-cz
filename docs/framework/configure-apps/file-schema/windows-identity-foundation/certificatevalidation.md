---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: af4dc459da49b46d70276d3f4bcd5f94d2a91ffe
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="95d59-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="95d59-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="95d59-103">Určuje nastavení, které tokenu obslužné rutiny používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="95d59-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="95d59-104">Tato nastavení jsou přepsat, pokud obslužná rutina specifická nakonfigurovaný s vlastním validátoru.</span><span class="sxs-lookup"><span data-stu-id="95d59-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="95d59-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="95d59-105">\<system.identityModel></span></span>  
<span data-ttu-id="95d59-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="95d59-106">\<identityConfiguration></span></span>  
<span data-ttu-id="95d59-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="95d59-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95d59-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95d59-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95d59-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="95d59-109">Attributes and Elements</span></span>  
 <span data-ttu-id="95d59-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="95d59-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95d59-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="95d59-111">Attributes</span></span>  
  
|<span data-ttu-id="95d59-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="95d59-112">Attribute</span></span>|<span data-ttu-id="95d59-113">Popis</span><span class="sxs-lookup"><span data-stu-id="95d59-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95d59-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="95d59-114">certificateValidationMode</span></span>|<span data-ttu-id="95d59-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnotu, která určuje režim ověřování pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="95d59-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="95d59-116">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="95d59-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="95d59-117">Chcete-li zadat vlastní validátor, nastavte tento atribut na hodnotu "Vlastní" a zadejte validátor pomocí [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span><span class="sxs-lookup"><span data-stu-id="95d59-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="95d59-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="95d59-118">Optional.</span></span>|  
|<span data-ttu-id="95d59-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="95d59-119">revocationMode</span></span>|<span data-ttu-id="95d59-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnotu, která určuje režim odvolaných certifikátů pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="95d59-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="95d59-121">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="95d59-121">The default value is "Online".</span></span> <span data-ttu-id="95d59-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="95d59-122">Optional.</span></span>|  
|<span data-ttu-id="95d59-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="95d59-123">trustedStoreLocation</span></span>|<span data-ttu-id="95d59-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnotu, která určuje úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="95d59-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="95d59-125">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="95d59-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="95d59-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="95d59-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95d59-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="95d59-127">Child Elements</span></span>  
  
|<span data-ttu-id="95d59-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="95d59-128">Element</span></span>|<span data-ttu-id="95d59-129">Popis</span><span class="sxs-lookup"><span data-stu-id="95d59-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d59-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="95d59-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="95d59-131">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="95d59-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="95d59-132">Tento typ se používá pouze v případě `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element je nastaven na hodnotu "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="95d59-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95d59-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="95d59-133">Parent Elements</span></span>  
  
|<span data-ttu-id="95d59-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="95d59-134">Element</span></span>|<span data-ttu-id="95d59-135">Popis</span><span class="sxs-lookup"><span data-stu-id="95d59-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95d59-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="95d59-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="95d59-137">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="95d59-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="95d59-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="95d59-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="95d59-139">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="95d59-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95d59-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="95d59-140">Remarks</span></span>  
 <span data-ttu-id="95d59-141">A `<certificateValidation>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="95d59-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="95d59-142">Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="95d59-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="95d59-143">Některé tokenu obslužné rutiny umožňují určit nastavení ověření certifikátu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="95d59-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="95d59-144">Nastavení na jednotlivých tokenu obslužné rutiny přepsat tyto zadané na úrovni služby i na kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="95d59-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95d59-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="95d59-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
