---
title: '&lt;issuerMetadata&gt;'
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 38fa373212464a7dc919c2f364524a391db17d43
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149355"
---
# <a name="ltissuermetadatagt"></a><span data-ttu-id="a67f0-102">&lt;issuerMetadata&gt;</span><span class="sxs-lookup"><span data-stu-id="a67f0-102">&lt;issuerMetadata&gt;</span></span>
<span data-ttu-id="a67f0-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a67f0-103">\<system.serviceModel></span></span>  
<span data-ttu-id="a67f0-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a67f0-104">\<bindings></span></span>  
<span data-ttu-id="a67f0-105">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="a67f0-105">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="a67f0-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a67f0-106">\<binding></span></span>  
<span data-ttu-id="a67f0-107">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="a67f0-107">\<security></span></span>  
<span data-ttu-id="a67f0-108">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="a67f0-108">\<message></span></span>  
<span data-ttu-id="a67f0-109">\<issuerMetadata ></span><span class="sxs-lookup"><span data-stu-id="a67f0-109">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a67f0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a67f0-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a67f0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a67f0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a67f0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a67f0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a67f0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a67f0-113">Attributes</span></span>  
  
|<span data-ttu-id="a67f0-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a67f0-114">Attribute</span></span>|<span data-ttu-id="a67f0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a67f0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a67f0-116">adresa</span><span class="sxs-lookup"><span data-stu-id="a67f0-116">address</span></span>|<span data-ttu-id="a67f0-117">Vyžaduje `string` atribut.</span><span class="sxs-lookup"><span data-stu-id="a67f0-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="a67f0-118">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a67f0-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="a67f0-119">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="a67f0-119">The address must be an absolute URI.</span></span> <span data-ttu-id="a67f0-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a67f0-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a67f0-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a67f0-121">Child Elements</span></span>  
  
|<span data-ttu-id="a67f0-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="a67f0-122">Element</span></span>|<span data-ttu-id="a67f0-123">Popis</span><span class="sxs-lookup"><span data-stu-id="a67f0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a67f0-124">\<záhlaví ></span><span class="sxs-lookup"><span data-stu-id="a67f0-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="a67f0-125">Kolekce záhlaví adres.</span><span class="sxs-lookup"><span data-stu-id="a67f0-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="a67f0-126">\<identity ></span><span class="sxs-lookup"><span data-stu-id="a67f0-126">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="a67f0-127">Identita, která umožňuje ověřování z koncového bodu jiné koncové body výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="a67f0-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a67f0-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a67f0-128">Parent Elements</span></span>  
  
|<span data-ttu-id="a67f0-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="a67f0-129">Element</span></span>|<span data-ttu-id="a67f0-130">Popis</span><span class="sxs-lookup"><span data-stu-id="a67f0-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a67f0-131">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="a67f0-131">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="a67f0-132">Definuje nastavení založená na úrovni zpráv zabezpečení pro [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="a67f0-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a67f0-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="a67f0-133">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>  
 [<span data-ttu-id="a67f0-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="a67f0-134">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="a67f0-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a67f0-135">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="a67f0-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="a67f0-136">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [<span data-ttu-id="a67f0-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="a67f0-137">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
