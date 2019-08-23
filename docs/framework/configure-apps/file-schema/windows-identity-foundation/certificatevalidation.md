---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941910"
---
# <a name="certificatevalidation"></a><span data-ttu-id="b08a6-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="b08a6-101">\<certificateValidation></span></span>
<span data-ttu-id="b08a6-102">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="b08a6-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="b08a6-103">Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru.</span><span class="sxs-lookup"><span data-stu-id="b08a6-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
 <span data-ttu-id="b08a6-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="b08a6-104">\<system.identityModel></span></span>  
<span data-ttu-id="b08a6-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b08a6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="b08a6-106">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="b08a6-106">\<certificateValidation></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b08a6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b08a6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b08a6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b08a6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b08a6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b08a6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b08a6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b08a6-110">Attributes</span></span>  
  
|<span data-ttu-id="b08a6-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b08a6-111">Attribute</span></span>|<span data-ttu-id="b08a6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b08a6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b08a6-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b08a6-113">certificateValidationMode</span></span>|<span data-ttu-id="b08a6-114"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="b08a6-114">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b08a6-115">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="b08a6-115">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="b08a6-116">Chcete-li určit vlastní validátor, nastavte tento atribut na "Custom" a určete validátor pomocí [ \<> elementu certificateValidator](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="b08a6-116">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="b08a6-117">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b08a6-117">Optional.</span></span>|  
|<span data-ttu-id="b08a6-118">revocationMode</span><span class="sxs-lookup"><span data-stu-id="b08a6-118">revocationMode</span></span>|<span data-ttu-id="b08a6-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="b08a6-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b08a6-120">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="b08a6-120">The default value is "Online".</span></span> <span data-ttu-id="b08a6-121">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b08a6-121">Optional.</span></span>|  
|<span data-ttu-id="b08a6-122">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b08a6-122">trustedStoreLocation</span></span>|<span data-ttu-id="b08a6-123"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="b08a6-123">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="b08a6-124">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="b08a6-124">The default value is "LocalMachine".</span></span> <span data-ttu-id="b08a6-125">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="b08a6-125">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b08a6-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b08a6-126">Child Elements</span></span>  
  
|<span data-ttu-id="b08a6-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="b08a6-127">Element</span></span>|<span data-ttu-id="b08a6-128">Popis</span><span class="sxs-lookup"><span data-stu-id="b08a6-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b08a6-129">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="b08a6-129">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="b08a6-130">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="b08a6-130">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="b08a6-131">Tento typ se používá pouze v případě `certificateValidationMode` , že je atribut [ \<prvku certificateValidation >](certificatevalidation.md) nastaven na hodnotu "Custom".</span><span class="sxs-lookup"><span data-stu-id="b08a6-131">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b08a6-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b08a6-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b08a6-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="b08a6-133">Element</span></span>|<span data-ttu-id="b08a6-134">Popis</span><span class="sxs-lookup"><span data-stu-id="b08a6-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b08a6-135">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="b08a6-135">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="b08a6-136">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="b08a6-136">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="b08a6-137">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b08a6-137">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="b08a6-138">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b08a6-138">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b08a6-139">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b08a6-139">Remarks</span></span>  
 <span data-ttu-id="b08a6-140">Element lze zadat na úrovni služby `<identityConfiguration>` pod prvkem nebo na úrovni kolekce `<securityTokenHandlerConfiguration>` obslužné rutiny tokenu zabezpečení pod prvkem. `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="b08a6-140">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="b08a6-141">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="b08a6-141">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="b08a6-142">Některé obslužné rutiny tokenů umožňují zadat nastavení ověřování certifikátů v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b08a6-142">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="b08a6-143">Nastavení u jednotlivých obslužných rutin tokenů přepíší ty zadané na úrovni služby i v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b08a6-143">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b08a6-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="b08a6-144">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
