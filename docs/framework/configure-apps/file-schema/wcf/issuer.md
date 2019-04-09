---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 37d935287fa7dfba640c39071295fd660f4db7c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160820"
---
# <a name="issuer"></a><span data-ttu-id="1ea19-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="1ea19-101">\<issuer></span></span>
<span data-ttu-id="1ea19-102">Určuje Token služba zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1ea19-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
 <span data-ttu-id="1ea19-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1ea19-103">\<system.serviceModel></span></span>  
<span data-ttu-id="1ea19-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="1ea19-104">\<bindings></span></span>  
<span data-ttu-id="1ea19-105">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1ea19-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="1ea19-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="1ea19-106">\<binding></span></span>  
<span data-ttu-id="1ea19-107">\<security></span><span class="sxs-lookup"><span data-stu-id="1ea19-107">\<security></span></span>  
<span data-ttu-id="1ea19-108">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="1ea19-108">\<message></span></span>  
<span data-ttu-id="1ea19-109">\<issuer></span><span class="sxs-lookup"><span data-stu-id="1ea19-109">\<issuer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ea19-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ea19-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ea19-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ea19-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1ea19-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ea19-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ea19-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ea19-113">Attributes</span></span>  
  
|<span data-ttu-id="1ea19-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1ea19-114">Attribute</span></span>|<span data-ttu-id="1ea19-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1ea19-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ea19-116">adresa</span><span class="sxs-lookup"><span data-stu-id="1ea19-116">address</span></span>|<span data-ttu-id="1ea19-117">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="1ea19-117">Required string.</span></span> <span data-ttu-id="1ea19-118">Adresa URL služby STS.</span><span class="sxs-lookup"><span data-stu-id="1ea19-118">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ea19-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ea19-119">Child Elements</span></span>  
  
|<span data-ttu-id="1ea19-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ea19-120">Element</span></span>|<span data-ttu-id="1ea19-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1ea19-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ea19-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="1ea19-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="1ea19-123">Kolekce záhlaví adres pro koncové body, které můžete vytvořit tvůrce.</span><span class="sxs-lookup"><span data-stu-id="1ea19-123">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="1ea19-124">\<identity></span><span class="sxs-lookup"><span data-stu-id="1ea19-124">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="1ea19-125">Při použití vydaný token, určuje nastavení, které povoluje klient k ověření tohoto serveru.</span><span class="sxs-lookup"><span data-stu-id="1ea19-125">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ea19-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ea19-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1ea19-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ea19-127">Element</span></span>|<span data-ttu-id="1ea19-128">Popis</span><span class="sxs-lookup"><span data-stu-id="1ea19-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ea19-129">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="1ea19-129">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="1ea19-130">Definuje nastavení založená na úrovni zpráv zabezpečení pro [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="1ea19-130">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1ea19-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ea19-131">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="1ea19-132">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="1ea19-132">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1ea19-133">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="1ea19-133">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1ea19-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="1ea19-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="1ea19-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="1ea19-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="1ea19-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="1ea19-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="1ea19-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="1ea19-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
