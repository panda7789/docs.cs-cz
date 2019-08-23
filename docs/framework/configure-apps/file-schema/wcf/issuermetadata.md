---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: bf512c427637ca65a7271ec8300a373a38632108
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913521"
---
# <a name="issuermetadata"></a><span data-ttu-id="c5d27-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="c5d27-101">\<issuerMetadata></span></span>
<span data-ttu-id="c5d27-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c5d27-102">\<system.serviceModel></span></span>  
<span data-ttu-id="c5d27-103">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="c5d27-103">\<bindings></span></span>  
<span data-ttu-id="c5d27-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c5d27-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="c5d27-105">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c5d27-105">\<binding></span></span>  
<span data-ttu-id="c5d27-106">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c5d27-106">\<security></span></span>  
<span data-ttu-id="c5d27-107">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="c5d27-107">\<message></span></span>  
<span data-ttu-id="c5d27-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="c5d27-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5d27-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5d27-109">Syntax</span></span>  
  
```xml  
<issuerMetadata address="String">
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
</issuerMetadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5d27-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c5d27-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c5d27-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c5d27-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5d27-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c5d27-112">Attributes</span></span>  
  
|<span data-ttu-id="c5d27-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c5d27-113">Attribute</span></span>|<span data-ttu-id="c5d27-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c5d27-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5d27-115">adresa</span><span class="sxs-lookup"><span data-stu-id="c5d27-115">address</span></span>|<span data-ttu-id="c5d27-116">Požadovaný `string` atribut.</span><span class="sxs-lookup"><span data-stu-id="c5d27-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="c5d27-117">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="c5d27-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="c5d27-118">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="c5d27-118">The address must be an absolute URI.</span></span> <span data-ttu-id="c5d27-119">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c5d27-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5d27-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c5d27-120">Child Elements</span></span>  
  
|<span data-ttu-id="c5d27-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="c5d27-121">Element</span></span>|<span data-ttu-id="c5d27-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c5d27-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5d27-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="c5d27-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="c5d27-124">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="c5d27-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="c5d27-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="c5d27-125">\<identity></span></span>](identity.md)|<span data-ttu-id="c5d27-126">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="c5d27-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5d27-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c5d27-127">Parent Elements</span></span>  
  
|<span data-ttu-id="c5d27-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="c5d27-128">Element</span></span>|<span data-ttu-id="c5d27-129">Popis</span><span class="sxs-lookup"><span data-stu-id="c5d27-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5d27-130">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="c5d27-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c5d27-131">Definuje nastavení pro zabezpečení na úrovni zprávy pro [ \<element wsFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="c5d27-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5d27-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5d27-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="c5d27-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="c5d27-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="c5d27-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="c5d27-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="c5d27-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="c5d27-135">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="c5d27-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="c5d27-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
