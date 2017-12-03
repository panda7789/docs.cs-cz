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
ms.openlocfilehash: 235888aa97238489a51c2ea065efa0575e0d3724
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="0a447-102">&lt;Vystavitel&gt;</span><span class="sxs-lookup"><span data-stu-id="0a447-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="0a447-103">Určuje zabezpečení Token Service (Služba tokenů zabezpečení), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0a447-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="0a447-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0a447-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0a447-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0a447-105">\<bindings></span></span>  
<span data-ttu-id="0a447-106">\<– wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="0a447-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="0a447-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="0a447-107">\<binding></span></span>  
<span data-ttu-id="0a447-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="0a447-108">\<security></span></span>  
<span data-ttu-id="0a447-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="0a447-109">\<message></span></span>  
<span data-ttu-id="0a447-110">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="0a447-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a447-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a447-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a447-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a447-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0a447-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a447-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a447-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a447-114">Attributes</span></span>  
  
|<span data-ttu-id="0a447-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a447-115">Attribute</span></span>|<span data-ttu-id="0a447-116">Popis</span><span class="sxs-lookup"><span data-stu-id="0a447-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a447-117">adresa</span><span class="sxs-lookup"><span data-stu-id="0a447-117">address</span></span>|<span data-ttu-id="0a447-118">Požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="0a447-118">Required string.</span></span> <span data-ttu-id="0a447-119">Adresa URL Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0a447-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a447-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a447-120">Child Elements</span></span>  
  
|<span data-ttu-id="0a447-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a447-121">Element</span></span>|<span data-ttu-id="0a447-122">Popis</span><span class="sxs-lookup"><span data-stu-id="0a447-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a447-123">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="0a447-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="0a447-124">Kolekce hlavičky adresy pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="0a447-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="0a447-125">\<identity ></span><span class="sxs-lookup"><span data-stu-id="0a447-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="0a447-126">Při použití vydané token, určuje nastavení, které umožňují klienta k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="0a447-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a447-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a447-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0a447-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a447-128">Element</span></span>|<span data-ttu-id="0a447-129">Popis</span><span class="sxs-lookup"><span data-stu-id="0a447-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a447-130">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="0a447-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="0a447-131">Definuje nastavení pro zprávy úroveň zabezpečení [ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="0a447-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a447-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a447-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="0a447-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="0a447-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="0a447-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0a447-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="0a447-135">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="0a447-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="0a447-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0a447-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="0a447-137">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="0a447-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="0a447-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="0a447-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
