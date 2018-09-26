---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 29881be43f02d275ad135efd97dc8b25a7409beb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074785"
---
# <a name="ltcertificatevalidationgt"></a><span data-ttu-id="1cab6-102">&lt;certificateValidation&gt;</span><span class="sxs-lookup"><span data-stu-id="1cab6-102">&lt;certificateValidation&gt;</span></span>
<span data-ttu-id="1cab6-103">Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1cab6-103">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="1cab6-104">Tato nastavení jsou přepsány, pokud jsou nakonfigurované vlastní validátor konkrétní obslužnou rutinou.</span><span class="sxs-lookup"><span data-stu-id="1cab6-104">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="1cab6-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1cab6-105">\<system.identityModel></span></span>  
<span data-ttu-id="1cab6-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1cab6-106">\<identityConfiguration></span></span>  
<span data-ttu-id="1cab6-107">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="1cab6-107">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cab6-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1cab6-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cab6-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1cab6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1cab6-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1cab6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cab6-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1cab6-111">Attributes</span></span>  
  
|<span data-ttu-id="1cab6-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1cab6-112">Attribute</span></span>|<span data-ttu-id="1cab6-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1cab6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1cab6-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1cab6-114">certificateValidationMode</span></span>|<span data-ttu-id="1cab6-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který chcete použít pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="1cab6-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1cab6-116">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="1cab6-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="1cab6-117">Pokud chcete zadat vlastní validátor, tento atribut nastaven na "Vlastní" a zadejte validátor pomocí [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1cab6-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="1cab6-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1cab6-118">Optional.</span></span>|  
|<span data-ttu-id="1cab6-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="1cab6-119">revocationMode</span></span>|<span data-ttu-id="1cab6-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="1cab6-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="1cab6-121">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="1cab6-121">The default value is "Online".</span></span> <span data-ttu-id="1cab6-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1cab6-122">Optional.</span></span>|  
|<span data-ttu-id="1cab6-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1cab6-123">trustedStoreLocation</span></span>|<span data-ttu-id="1cab6-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="1cab6-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="1cab6-125">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="1cab6-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="1cab6-126">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1cab6-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1cab6-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1cab6-127">Child Elements</span></span>  
  
|<span data-ttu-id="1cab6-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="1cab6-128">Element</span></span>|<span data-ttu-id="1cab6-129">Popis</span><span class="sxs-lookup"><span data-stu-id="1cab6-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cab6-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="1cab6-130">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="1cab6-131">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="1cab6-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="1cab6-132">Tento typ se používá jenom v případě, `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvek je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="1cab6-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1cab6-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1cab6-133">Parent Elements</span></span>  
  
|<span data-ttu-id="1cab6-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="1cab6-134">Element</span></span>|<span data-ttu-id="1cab6-135">Popis</span><span class="sxs-lookup"><span data-stu-id="1cab6-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cab6-136">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1cab6-136">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="1cab6-137">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="1cab6-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="1cab6-138">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1cab6-138">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="1cab6-139">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="1cab6-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cab6-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1cab6-140">Remarks</span></span>  
 <span data-ttu-id="1cab6-141">A `<certificateValidation>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1cab6-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="1cab6-142">Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="1cab6-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="1cab6-143">Některé obslužné rutiny tokenů vám umožňují určit nastavení ověření certifikátu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1cab6-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="1cab6-144">Nastavení na jednotlivých obslužné rutiny tokenů přepsat zadaný na úrovni služby a na kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1cab6-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cab6-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="1cab6-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
