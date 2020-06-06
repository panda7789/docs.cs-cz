---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252135"
---
# \<certificateValidation>
<span data-ttu-id="086be-101">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="086be-101">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="086be-102">Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru.</span><span class="sxs-lookup"><span data-stu-id="086be-102">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
## <a name="syntax"></a><span data-ttu-id="086be-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="086be-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="086be-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="086be-104">Attributes and Elements</span></span>  
 <span data-ttu-id="086be-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="086be-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="086be-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="086be-106">Attributes</span></span>  
  
|<span data-ttu-id="086be-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="086be-107">Attribute</span></span>|<span data-ttu-id="086be-108">Popis</span><span class="sxs-lookup"><span data-stu-id="086be-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="086be-109">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="086be-109">certificateValidationMode</span></span>|<span data-ttu-id="086be-110"><xref:System.ServiceModel.Security.X509CertificateValidationMode>Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="086be-110">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="086be-111">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="086be-111">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="086be-112">Chcete-li určit vlastní validátor, nastavte tento atribut na hodnotu "Custom" a určete validátor pomocí [\<certificateValidator>](certificatevalidator.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="086be-112">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="086be-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="086be-113">Optional.</span></span>|  
|<span data-ttu-id="086be-114">revocationMode</span><span class="sxs-lookup"><span data-stu-id="086be-114">revocationMode</span></span>|<span data-ttu-id="086be-115"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="086be-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="086be-116">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="086be-116">The default value is "Online".</span></span> <span data-ttu-id="086be-117">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="086be-117">Optional.</span></span>|  
|<span data-ttu-id="086be-118">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="086be-118">trustedStoreLocation</span></span>|<span data-ttu-id="086be-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="086be-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="086be-120">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="086be-120">The default value is "LocalMachine".</span></span> <span data-ttu-id="086be-121">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="086be-121">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="086be-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="086be-122">Child Elements</span></span>  
  
|<span data-ttu-id="086be-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="086be-123">Element</span></span>|<span data-ttu-id="086be-124">Description</span><span class="sxs-lookup"><span data-stu-id="086be-124">Description</span></span>|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|<span data-ttu-id="086be-125">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="086be-125">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="086be-126">Tento typ se používá jenom v případě, že `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) je atribut elementu nastavený na Custom (vlastní).</span><span class="sxs-lookup"><span data-stu-id="086be-126">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="086be-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="086be-127">Parent Elements</span></span>  
  
|<span data-ttu-id="086be-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="086be-128">Element</span></span>|<span data-ttu-id="086be-129">Description</span><span class="sxs-lookup"><span data-stu-id="086be-129">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="086be-130">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="086be-130">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="086be-131">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="086be-131">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="086be-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="086be-132">Remarks</span></span>  
 <span data-ttu-id="086be-133">`<certificateValidation>`Element lze zadat na úrovni služby pod `<identityConfiguration>` prvkem nebo na úrovni kolekce obslužné rutiny tokenu zabezpečení pod `<securityTokenHandlerConfiguration>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="086be-133">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="086be-134">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="086be-134">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="086be-135">Některé obslužné rutiny tokenů umožňují zadat nastavení ověřování certifikátů v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="086be-135">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="086be-136">Nastavení u jednotlivých obslužných rutin tokenů přepíší ty zadané na úrovni služby i v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="086be-136">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="086be-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="086be-137">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
