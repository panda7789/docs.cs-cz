---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397884"
---
# <a name="issuermetadata"></a><span data-ttu-id="e5ab1-101">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="e5ab1-101">\<issuerMetadata></span></span>

<span data-ttu-id="e5ab1-102">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e5ab1-102">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e5ab1-103">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e5ab1-103">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e5ab1-104">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="e5ab1-104">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="e5ab1-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e5ab1-105">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e5ab1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="e5ab1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="e5ab1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e5ab1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e5ab1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zprávy**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="e5ab1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="e5ab1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerMetadata >**</span><span class="sxs-lookup"><span data-stu-id="e5ab1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5ab1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5ab1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5ab1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e5ab1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e5ab1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e5ab1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5ab1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e5ab1-113">Attributes</span></span>  
  
|<span data-ttu-id="e5ab1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="e5ab1-114">Attribute</span></span>|<span data-ttu-id="e5ab1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e5ab1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5ab1-116">adresa</span><span class="sxs-lookup"><span data-stu-id="e5ab1-116">address</span></span>|<span data-ttu-id="e5ab1-117">Požadovaný `string` atribut.</span><span class="sxs-lookup"><span data-stu-id="e5ab1-117">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="e5ab1-118">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e5ab1-118">Specifies the address of the endpoint.</span></span> <span data-ttu-id="e5ab1-119">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="e5ab1-119">The address must be an absolute URI.</span></span> <span data-ttu-id="e5ab1-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e5ab1-120">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5ab1-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e5ab1-121">Child Elements</span></span>  
  
|<span data-ttu-id="e5ab1-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5ab1-122">Element</span></span>|<span data-ttu-id="e5ab1-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e5ab1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5ab1-124">\<headers></span><span class="sxs-lookup"><span data-stu-id="e5ab1-124">\<headers></span></span>](headers-element.md)|<span data-ttu-id="e5ab1-125">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="e5ab1-125">A collection of address headers.</span></span>|  
|[<span data-ttu-id="e5ab1-126">\<identity></span><span class="sxs-lookup"><span data-stu-id="e5ab1-126">\<identity></span></span>](identity.md)|<span data-ttu-id="e5ab1-127">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="e5ab1-127">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5ab1-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e5ab1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="e5ab1-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="e5ab1-129">Element</span></span>|<span data-ttu-id="e5ab1-130">Popis</span><span class="sxs-lookup"><span data-stu-id="e5ab1-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5ab1-131">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="e5ab1-131">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="e5ab1-132">Definuje nastavení pro zabezpečení na úrovni zprávy pro [ \<element wsFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e5ab1-132">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5ab1-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5ab1-133">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="e5ab1-134">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e5ab1-134">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="e5ab1-135">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="e5ab1-135">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="e5ab1-136">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="e5ab1-136">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="e5ab1-137">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="e5ab1-137">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
