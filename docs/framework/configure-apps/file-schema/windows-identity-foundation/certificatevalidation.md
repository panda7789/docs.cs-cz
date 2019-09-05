---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252135"
---
# <a name="certificatevalidation"></a><span data-ttu-id="837c7-101">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="837c7-101">\<certificateValidation></span></span>
<span data-ttu-id="837c7-102">Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="837c7-102">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="837c7-103">Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru.</span><span class="sxs-lookup"><span data-stu-id="837c7-103">These settings are overridden if a specific handler is configured with its own validator.</span></span>  
  
<span data-ttu-id="837c7-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="837c7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="837c7-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="837c7-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="837c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="837c7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="837c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<certificateValidation >**</span><span class="sxs-lookup"><span data-stu-id="837c7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="837c7-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="837c7-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="837c7-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="837c7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="837c7-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="837c7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="837c7-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="837c7-111">Attributes</span></span>  
  
|<span data-ttu-id="837c7-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="837c7-112">Attribute</span></span>|<span data-ttu-id="837c7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="837c7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="837c7-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="837c7-114">certificateValidationMode</span></span>|<span data-ttu-id="837c7-115"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="837c7-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="837c7-116">Výchozí hodnota je "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="837c7-116">The default value is "PeerOrChainTrust".</span></span> <span data-ttu-id="837c7-117">Chcete-li určit vlastní validátor, nastavte tento atribut na "Custom" a určete validátor pomocí [ \<> elementu certificateValidator](certificatevalidator.md) .</span><span class="sxs-lookup"><span data-stu-id="837c7-117">To specify a custom validator, set this attribute to "Custom" and specify the validator using the [\<certificateValidator>](certificatevalidator.md) element.</span></span> <span data-ttu-id="837c7-118">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="837c7-118">Optional.</span></span>|  
|<span data-ttu-id="837c7-119">revocationMode</span><span class="sxs-lookup"><span data-stu-id="837c7-119">revocationMode</span></span>|<span data-ttu-id="837c7-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="837c7-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="837c7-121">Výchozí hodnota je "online".</span><span class="sxs-lookup"><span data-stu-id="837c7-121">The default value is "Online".</span></span> <span data-ttu-id="837c7-122">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="837c7-122">Optional.</span></span>|  
|<span data-ttu-id="837c7-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="837c7-123">trustedStoreLocation</span></span>|<span data-ttu-id="837c7-124"><xref:System.Security.Cryptography.X509Certificates.StoreLocation> Hodnota, která určuje úložiště certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="837c7-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="837c7-125">Výchozí hodnota je "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="837c7-125">The default value is "LocalMachine".</span></span> <span data-ttu-id="837c7-126">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="837c7-126">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="837c7-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="837c7-127">Child Elements</span></span>  
  
|<span data-ttu-id="837c7-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="837c7-128">Element</span></span>|<span data-ttu-id="837c7-129">Popis</span><span class="sxs-lookup"><span data-stu-id="837c7-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="837c7-130">\<certificateValidator ></span><span class="sxs-lookup"><span data-stu-id="837c7-130">\<certificateValidator></span></span>](certificatevalidator.md)|<span data-ttu-id="837c7-131">Určuje vlastní typ pro ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="837c7-131">Specifies a custom type for certificate validation.</span></span> <span data-ttu-id="837c7-132">Tento typ se používá pouze v případě `certificateValidationMode` , že je atribut [ \<prvku certificateValidation >](certificatevalidation.md) nastaven na hodnotu "Custom".</span><span class="sxs-lookup"><span data-stu-id="837c7-132">This type is used only if the `certificateValidationMode` attribute of the [\<certificateValidation>](certificatevalidation.md) element is set to "Custom".</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="837c7-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="837c7-133">Parent Elements</span></span>  
  
|<span data-ttu-id="837c7-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="837c7-134">Element</span></span>|<span data-ttu-id="837c7-135">Popis</span><span class="sxs-lookup"><span data-stu-id="837c7-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="837c7-136">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="837c7-136">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="837c7-137">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="837c7-137">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="837c7-138">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="837c7-138">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="837c7-139">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="837c7-139">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="837c7-140">Poznámky</span><span class="sxs-lookup"><span data-stu-id="837c7-140">Remarks</span></span>  
 <span data-ttu-id="837c7-141">Element lze zadat na úrovni služby `<identityConfiguration>` pod prvkem nebo na úrovni kolekce `<securityTokenHandlerConfiguration>` obslužné rutiny tokenu zabezpečení pod prvkem. `<certificateValidation>`</span><span class="sxs-lookup"><span data-stu-id="837c7-141">A `<certificateValidation>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="837c7-142">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="837c7-142">Settings on a token handler collection override those specified on the service.</span></span> <span data-ttu-id="837c7-143">Některé obslužné rutiny tokenů umožňují zadat nastavení ověřování certifikátů v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="837c7-143">Some token handlers allow you to specify certificate validation settings in configuration.</span></span> <span data-ttu-id="837c7-144">Nastavení u jednotlivých obslužných rutin tokenů přepíší ty zadané na úrovni služby i v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="837c7-144">Settings on individual token handlers override those specified both at the service level and on the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="837c7-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="837c7-145">Example</span></span>  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
