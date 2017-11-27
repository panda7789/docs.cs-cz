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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dcd85443a802db2b6f2e0b1823dd6cb60ed8f705
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuergt"></a><span data-ttu-id="2b4dc-102">&lt;Vystavitel&gt;</span><span class="sxs-lookup"><span data-stu-id="2b4dc-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="2b4dc-103">Určuje zabezpečení Token Service (Služba tokenů zabezpečení), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2b4dc-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="2b4dc-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2b4dc-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-105">\<bindings></span></span>  
<span data-ttu-id="2b4dc-106">\<– wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="2b4dc-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-107">\<binding></span></span>  
<span data-ttu-id="2b4dc-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-108">\<security></span></span>  
<span data-ttu-id="2b4dc-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-109">\<message></span></span>  
<span data-ttu-id="2b4dc-110">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b4dc-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b4dc-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b4dc-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b4dc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2b4dc-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b4dc-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b4dc-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b4dc-114">Attributes</span></span>  
  
|<span data-ttu-id="2b4dc-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="2b4dc-115">Attribute</span></span>|<span data-ttu-id="2b4dc-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2b4dc-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b4dc-117">adresa</span><span class="sxs-lookup"><span data-stu-id="2b4dc-117">address</span></span>|<span data-ttu-id="2b4dc-118">Požadovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2b4dc-118">Required string.</span></span> <span data-ttu-id="2b4dc-119">Adresa URL Služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2b4dc-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b4dc-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b4dc-120">Child Elements</span></span>  
  
|<span data-ttu-id="2b4dc-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b4dc-121">Element</span></span>|<span data-ttu-id="2b4dc-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2b4dc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b4dc-123">\<hlavičky ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="2b4dc-124">Kolekce hlavičky adresy pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="2b4dc-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="2b4dc-125">\<identity ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2b4dc-126">Při použití vydané token, určuje nastavení, které umožňují klienta k ověření serveru.</span><span class="sxs-lookup"><span data-stu-id="2b4dc-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2b4dc-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2b4dc-127">Parent Elements</span></span>  
  
|<span data-ttu-id="2b4dc-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b4dc-128">Element</span></span>|<span data-ttu-id="2b4dc-129">Popis</span><span class="sxs-lookup"><span data-stu-id="2b4dc-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b4dc-130">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="2b4dc-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="2b4dc-131">Definuje nastavení pro zprávy úroveň zabezpečení [ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="2b4dc-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b4dc-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b4dc-132">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>  
 [<span data-ttu-id="2b4dc-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="2b4dc-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2b4dc-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="2b4dc-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="2b4dc-135">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="2b4dc-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="2b4dc-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="2b4dc-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="2b4dc-137">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="2b4dc-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="2b4dc-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="2b4dc-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
