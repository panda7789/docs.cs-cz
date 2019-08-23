---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 08fda249b526961ff711f439cf729a18e15b412b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929365"
---
# <a name="issuer"></a><span data-ttu-id="3003d-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="3003d-101">\<issuer></span></span>
<span data-ttu-id="3003d-102">Určuje službu tokenů zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3003d-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="3003d-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3003d-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3003d-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="3003d-104">\<bindings></span></span>  
<span data-ttu-id="3003d-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3003d-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="3003d-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="3003d-106">\<binding></span></span>  
<span data-ttu-id="3003d-107">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3003d-107">\<security></span></span>  
<span data-ttu-id="3003d-108">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="3003d-108">\<message></span></span>  
<span data-ttu-id="3003d-109">\<issuer></span><span class="sxs-lookup"><span data-stu-id="3003d-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3003d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3003d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3003d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3003d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3003d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3003d-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3003d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3003d-113">Attributes</span></span>  
  
|<span data-ttu-id="3003d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3003d-114">Attribute</span></span>|<span data-ttu-id="3003d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3003d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3003d-116">adresa</span><span class="sxs-lookup"><span data-stu-id="3003d-116">address</span></span>|<span data-ttu-id="3003d-117">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3003d-117">Required string.</span></span> <span data-ttu-id="3003d-118">Adresa URL služby STS</span><span class="sxs-lookup"><span data-stu-id="3003d-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3003d-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3003d-119">Child Elements</span></span>  
  
|<span data-ttu-id="3003d-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="3003d-120">Element</span></span>|<span data-ttu-id="3003d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="3003d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3003d-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="3003d-122">\<headers></span></span>](headers-element.md)|<span data-ttu-id="3003d-123">Kolekce záhlaví adres pro koncové body, které může tvůrce vytvořit.</span><span class="sxs-lookup"><span data-stu-id="3003d-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="3003d-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="3003d-124">\<identity></span></span>](identity.md)|<span data-ttu-id="3003d-125">Při použití vydaného tokenu aplikace určuje nastavení, které klientovi umožní Server ověřit.</span><span class="sxs-lookup"><span data-stu-id="3003d-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3003d-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3003d-126">Parent Elements</span></span>  
  
|<span data-ttu-id="3003d-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="3003d-127">Element</span></span>|<span data-ttu-id="3003d-128">Popis</span><span class="sxs-lookup"><span data-stu-id="3003d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3003d-129">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="3003d-129">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="3003d-130">Definuje nastavení pro zabezpečení na úrovni zprávy pro [ \<element wsFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3003d-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3003d-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3003d-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="3003d-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="3003d-132">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3003d-133">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="3003d-133">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3003d-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="3003d-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="3003d-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="3003d-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="3003d-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="3003d-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="3003d-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="3003d-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
