---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 7b8823d792e3f15846a9483d670994be4b368980
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667350"
---
# <a name="certificatevalidation"></a><span data-ttu-id="d008c-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="d008c-101">\<certificateValidation></span></span>
<span data-ttu-id="d008c-102">Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="d008c-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="d008c-103">Tato nastavení jsou přepsány, pokud jsou nakonfigurované vlastní validátor konkrétní obslužnou rutinou.</span><span class="sxs-lookup"><span data-stu-id="d008c-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="d008c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d008c-104">\<system.identityModel></span></span>  
<span data-ttu-id="d008c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d008c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d008c-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="d008c-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d008c-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d008c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d008c-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d008c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d008c-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d008c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d008c-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d008c-110">Attributes</span></span>  
  
|<span data-ttu-id="d008c-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d008c-111">Attribute</span></span>|<span data-ttu-id="d008c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d008c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d008c-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="d008c-113">certificateValidationMode</span></span>|<span data-ttu-id="d008c-114"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který chcete použít pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="d008c-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d008c-115">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="d008c-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="d008c-116">Pokud chcete zadat vlastní validátor, tento atribut nastaven na "Vlastní" a zadejte validátor pomocí [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d008c-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) element.</span></span> <span data-ttu-id="d008c-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d008c-117">Optional.</span></span>|  
|<span data-ttu-id="d008c-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="d008c-118">revocationMode</span></span>|<span data-ttu-id="d008c-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání pro certifikát X.509.</span><span class="sxs-lookup"><span data-stu-id="d008c-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d008c-120">Výchozí hodnota je "Online".</span><span class="sxs-lookup"><span data-stu-id="d008c-120">The default value is "Online".</span></span> <span data-ttu-id="d008c-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d008c-121">Optional.</span></span>|  
|<span data-ttu-id="d008c-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d008c-122">trustedStoreLocation</span></span>|<span data-ttu-id="d008c-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje úložiště certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="d008c-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d008c-124">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="d008c-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="d008c-125">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d008c-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d008c-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d008c-126">Child Elements</span></span>  
  
|<span data-ttu-id="d008c-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="d008c-127">Element</span></span>|<span data-ttu-id="d008c-128">Popis</span><span class="sxs-lookup"><span data-stu-id="d008c-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d008c-129">\<certificateValidator></span><span class="sxs-lookup"><span data-stu-id="d008c-129">\<certificateValidator></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|<span data-ttu-id="d008c-130">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d008c-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="d008c-131">Tento typ se používá jenom v případě, `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvek je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="d008c-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d008c-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d008c-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d008c-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="d008c-133">Element</span></span>|<span data-ttu-id="d008c-134">Popis</span><span class="sxs-lookup"><span data-stu-id="d008c-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d008c-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d008c-135">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="d008c-136">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="d008c-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="d008c-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d008c-137">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="d008c-138">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="d008c-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d008c-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d008c-139">Remarks</span></span>  
 <span data-ttu-id="d008c-140">A `<certificateValidation>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d008c-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="d008c-141">Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="d008c-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="d008c-142">Některé obslužné rutiny tokenů vám umožňují určit nastavení ověření certifikátu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d008c-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="d008c-143">Nastavení na jednotlivých obslužné rutiny tokenů přepsat zadaný na úrovni služby a na kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d008c-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d008c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="d008c-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
