---
title: '&lt;issuer&gt;'
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 8313d7e361356e5159d1f2d531a6dd34ae7ff4d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612174"
---
# <a name="ltissuergt"></a><span data-ttu-id="7599d-102">&lt;issuer&gt;</span><span class="sxs-lookup"><span data-stu-id="7599d-102">&lt;issuer&gt;</span></span>
<span data-ttu-id="7599d-103">Určuje Token služba zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7599d-103">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="7599d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7599d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="7599d-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7599d-105">\<bindings></span></span>  
<span data-ttu-id="7599d-106">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7599d-106">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="7599d-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="7599d-107">\<binding></span></span>  
<span data-ttu-id="7599d-108">\<security></span><span class="sxs-lookup"><span data-stu-id="7599d-108">\<security></span></span>  
<span data-ttu-id="7599d-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="7599d-109">\<message></span></span>  
<span data-ttu-id="7599d-110">\<issuer></span><span class="sxs-lookup"><span data-stu-id="7599d-110">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7599d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7599d-111">Syntax</span></span>  
  
```xml  
<issuer address="Uri">
  <headers>
    <add name="String"
         namespace="String" />
  </headers>
  <identity>
    <certificate encodedValue="String" />
    <certificateReference findValue="String"
                          isChainIncluded="Boolean"
                          storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                          storeLocation="LocalMachine/CurrentUser"
                          x509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
    <dns value="String" />
    <rsa value="String" />
    <servicePrincipalName value="String" />
    <usePrincipalName value="String" />
  </identity>
</issuer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7599d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7599d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7599d-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7599d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7599d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7599d-114">Attributes</span></span>  
  
|<span data-ttu-id="7599d-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="7599d-115">Attribute</span></span>|<span data-ttu-id="7599d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7599d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7599d-117">adresa</span><span class="sxs-lookup"><span data-stu-id="7599d-117">address</span></span>|<span data-ttu-id="7599d-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="7599d-118">Required string.</span></span> <span data-ttu-id="7599d-119">Adresa URL služby STS.</span><span class="sxs-lookup"><span data-stu-id="7599d-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7599d-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7599d-120">Child Elements</span></span>  
  
|<span data-ttu-id="7599d-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="7599d-121">Element</span></span>|<span data-ttu-id="7599d-122">Popis</span><span class="sxs-lookup"><span data-stu-id="7599d-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7599d-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="7599d-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="7599d-124">Kolekce záhlaví adres pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="7599d-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="7599d-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="7599d-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="7599d-126">Při použití vydaný token, určuje nastavení, které povoluje klient k ověření tohoto serveru.</span><span class="sxs-lookup"><span data-stu-id="7599d-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7599d-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7599d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7599d-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="7599d-128">Element</span></span>|<span data-ttu-id="7599d-129">Popis</span><span class="sxs-lookup"><span data-stu-id="7599d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7599d-130">\<message></span><span class="sxs-lookup"><span data-stu-id="7599d-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="7599d-131">Definuje nastavení založená na úrovni zpráv zabezpečení pro [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7599d-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7599d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7599d-132">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="7599d-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="7599d-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7599d-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="7599d-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7599d-135">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="7599d-135">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="7599d-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="7599d-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="7599d-137">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="7599d-137">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="7599d-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="7599d-138">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
