---
title: '&lt;Vystavitel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e034b3ed0813d621ed86c2c3e86bb901ab39e40b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="90c2a-102">&lt;Vystavitel&gt;</span><span class="sxs-lookup"><span data-stu-id="90c2a-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="90c2a-103">Určuje zabezpečení Token Service (Služba tokenů zabezpečení), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="90c2a-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="90c2a-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="90c2a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="90c2a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="90c2a-105">\<bindings></span></span>  
<span data-ttu-id="90c2a-106">\<– wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="90c2a-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="90c2a-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="90c2a-107">\<binding></span></span>  
<span data-ttu-id="90c2a-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="90c2a-108">\<security></span></span>  
<span data-ttu-id="90c2a-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="90c2a-109">\<message></span></span>  
<span data-ttu-id="90c2a-110">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="90c2a-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90c2a-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90c2a-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri" >  
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
</issuer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90c2a-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="90c2a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="90c2a-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90c2a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90c2a-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="90c2a-114">Attributes</span></span>  
  
|<span data-ttu-id="90c2a-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="90c2a-115">Attribute</span></span>|<span data-ttu-id="90c2a-116">Popis</span><span class="sxs-lookup"><span data-stu-id="90c2a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90c2a-117">adresa</span><span class="sxs-lookup"><span data-stu-id="90c2a-117">address</span></span>|<span data-ttu-id="90c2a-118">Požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="90c2a-118">Required string.</span></span> <span data-ttu-id="90c2a-119">Adresa URL Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="90c2a-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90c2a-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="90c2a-120">Child Elements</span></span>  
  
|<span data-ttu-id="90c2a-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="90c2a-121">Element</span></span>|<span data-ttu-id="90c2a-122">Popis</span><span class="sxs-lookup"><span data-stu-id="90c2a-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90c2a-123">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="90c2a-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="90c2a-124">Kolekce hlavičky adresy pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="90c2a-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="90c2a-125">\<identity ></span><span class="sxs-lookup"><span data-stu-id="90c2a-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="90c2a-126">Při použití vydané token, určuje nastavení, které umožňují klienta k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="90c2a-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90c2a-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="90c2a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="90c2a-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="90c2a-128">Element</span></span>|<span data-ttu-id="90c2a-129">Popis</span><span class="sxs-lookup"><span data-stu-id="90c2a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90c2a-130">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="90c2a-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="90c2a-131">Definuje nastavení pro zprávy úroveň zabezpečení [ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="90c2a-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90c2a-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="90c2a-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="90c2a-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="90c2a-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="90c2a-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="90c2a-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="90c2a-135">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="90c2a-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="90c2a-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="90c2a-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="90c2a-137">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="90c2a-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="90c2a-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="90c2a-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
