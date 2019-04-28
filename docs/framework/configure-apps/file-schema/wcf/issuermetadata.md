---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: 0dffad6a17720dd0506acbcd60efe4aafe24ed28
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761673"
---
# <a name="issuermetadata"></a><span data-ttu-id="76ee5-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="76ee5-101">\<issuerMetadata></span></span>
<span data-ttu-id="76ee5-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="76ee5-102">\<system.serviceModel></span></span>  
<span data-ttu-id="76ee5-103">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="76ee5-103">\<bindings></span></span>  
<span data-ttu-id="76ee5-104">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="76ee5-104">\<wsFederationHttpBinding></span></span>  
<span data-ttu-id="76ee5-105">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="76ee5-105">\<binding></span></span>  
<span data-ttu-id="76ee5-106">\<security></span><span class="sxs-lookup"><span data-stu-id="76ee5-106">\<security></span></span>  
<span data-ttu-id="76ee5-107">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="76ee5-107">\<message></span></span>  
<span data-ttu-id="76ee5-108">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="76ee5-108">\<issuerMetadata></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76ee5-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76ee5-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76ee5-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="76ee5-110">Attributes and Elements</span></span>  
 <span data-ttu-id="76ee5-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="76ee5-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76ee5-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="76ee5-112">Attributes</span></span>  
  
|<span data-ttu-id="76ee5-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="76ee5-113">Attribute</span></span>|<span data-ttu-id="76ee5-114">Popis</span><span class="sxs-lookup"><span data-stu-id="76ee5-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76ee5-115">adresa</span><span class="sxs-lookup"><span data-stu-id="76ee5-115">address</span></span>|<span data-ttu-id="76ee5-116">Vyžaduje `string` atribut.</span><span class="sxs-lookup"><span data-stu-id="76ee5-116">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="76ee5-117">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="76ee5-117">Specifies the address of the endpoint.</span></span> <span data-ttu-id="76ee5-118">Tato adresa musí být absolutní identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="76ee5-118">The address must be an absolute URI.</span></span> <span data-ttu-id="76ee5-119">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="76ee5-119">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76ee5-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="76ee5-120">Child Elements</span></span>  
  
|<span data-ttu-id="76ee5-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="76ee5-121">Element</span></span>|<span data-ttu-id="76ee5-122">Popis</span><span class="sxs-lookup"><span data-stu-id="76ee5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76ee5-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="76ee5-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="76ee5-124">Kolekce záhlaví adres.</span><span class="sxs-lookup"><span data-stu-id="76ee5-124">A collection of address headers.</span></span>|  
|[<span data-ttu-id="76ee5-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="76ee5-125">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="76ee5-126">Identita, která umožňuje ověřování z koncového bodu jiné koncové body výměna zpráv s ním.</span><span class="sxs-lookup"><span data-stu-id="76ee5-126">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="76ee5-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="76ee5-127">Parent Elements</span></span>  
  
|<span data-ttu-id="76ee5-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="76ee5-128">Element</span></span>|<span data-ttu-id="76ee5-129">Popis</span><span class="sxs-lookup"><span data-stu-id="76ee5-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="76ee5-130">\<message></span><span class="sxs-lookup"><span data-stu-id="76ee5-130">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="76ee5-131">Definuje nastavení založená na úrovni zpráv zabezpečení pro [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="76ee5-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76ee5-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76ee5-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="76ee5-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="76ee5-133">Service Identity and Authentication</span></span>](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="76ee5-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="76ee5-134">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="76ee5-135">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="76ee5-135">Security Capabilities with Custom Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="76ee5-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="76ee5-136">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
