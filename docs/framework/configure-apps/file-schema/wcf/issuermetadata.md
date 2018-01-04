---
title: '&lt;issuerMetadata&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28746481bd24eb0d80304456ea8f34f505a016b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="11fe7-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="11fe7-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="11fe7-103">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="11fe7-103">\<system.serviceModel></span></span>  
<span data-ttu-id="11fe7-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="11fe7-104">\<bindings></span></span>  
<span data-ttu-id="11fe7-105">\<– wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="11fe7-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="11fe7-106">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="11fe7-106">\<binding></span></span>  
<span data-ttu-id="11fe7-107">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="11fe7-107">\<security></span></span>  
<span data-ttu-id="11fe7-108">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="11fe7-108">\<message></span></span>  
<span data-ttu-id="11fe7-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="11fe7-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11fe7-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11fe7-110">Syntax</span></span>  
  
```xml  
<issuerMetadata address=String" >  
   <headers>  
      <add name="String"  
                 namespace="String" />  
   </headers>  
   <identity>  
           <certificate encodedValue="String"/>  
      <certificateReference findValue="String"   
         isChainIncluded="Boolean"  
         storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
         storeLocation="LocalMachine/CurrentUser"  
                  x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
      <dns value="String"/>  
      <rsa value="String"/>  
      <servicePrincipalName value="String"/>  
      <usePrincipalName value="String"/>  
   </identity>  
</issuerMetadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11fe7-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11fe7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="11fe7-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11fe7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11fe7-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="11fe7-113">Attributes</span></span>  
  
|<span data-ttu-id="11fe7-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="11fe7-114">Attribute</span></span>|<span data-ttu-id="11fe7-115">Popis</span><span class="sxs-lookup"><span data-stu-id="11fe7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11fe7-116">adresa</span><span class="sxs-lookup"><span data-stu-id="11fe7-116">address</span></span>|<span data-ttu-id="11fe7-117">Požadované `string` atribut.</span><span class="sxs-lookup"><span data-stu-id="11fe7-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="11fe7-118">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="11fe7-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="11fe7-119">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="11fe7-119">The address must be an absolute URI.</span></span> <span data-ttu-id="11fe7-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="11fe7-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11fe7-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11fe7-121">Child Elements</span></span>  
  
|<span data-ttu-id="11fe7-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="11fe7-122">Element</span></span>|<span data-ttu-id="11fe7-123">Popis</span><span class="sxs-lookup"><span data-stu-id="11fe7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11fe7-124">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="11fe7-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="11fe7-125">Kolekce hlavičky adresy.</span><span class="sxs-lookup"><span data-stu-id="11fe7-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="11fe7-126">\<identity ></span><span class="sxs-lookup"><span data-stu-id="11fe7-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="11fe7-127">Identita, která umožňuje ověření koncový bod pomocí dalších koncových bodů výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="11fe7-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11fe7-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11fe7-128">Parent Elements</span></span>  
  
|<span data-ttu-id="11fe7-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="11fe7-129">Element</span></span>|<span data-ttu-id="11fe7-130">Popis</span><span class="sxs-lookup"><span data-stu-id="11fe7-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="11fe7-131">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="11fe7-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="11fe7-132">Definuje nastavení pro zprávy úroveň zabezpečení [ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="11fe7-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11fe7-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="11fe7-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="11fe7-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="11fe7-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="11fe7-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="11fe7-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="11fe7-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="11fe7-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="11fe7-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="11fe7-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
