---
title: <issuerMetadata>
ms.date: 03/30/2017
ms.assetid: e7eae2c0-cc17-4281-af59-e4eb8d54f92a
ms.openlocfilehash: a28223127f7987a80bdf12d2dcf42878f717a377
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397884"
---
# \<issuerMetadata>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="31ba2-101">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31ba2-101">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31ba2-102">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="31ba2-102">Attributes and Elements</span></span>  
 <span data-ttu-id="31ba2-103">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="31ba2-103">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31ba2-104">Atributy</span><span class="sxs-lookup"><span data-stu-id="31ba2-104">Attributes</span></span>  
  
|<span data-ttu-id="31ba2-105">Atribut</span><span class="sxs-lookup"><span data-stu-id="31ba2-105">Attribute</span></span>|<span data-ttu-id="31ba2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="31ba2-106">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31ba2-107">adresa</span><span class="sxs-lookup"><span data-stu-id="31ba2-107">address</span></span>|<span data-ttu-id="31ba2-108">Požadovaný `string` atribut.</span><span class="sxs-lookup"><span data-stu-id="31ba2-108">Required `string` attribute.</span></span><br /><br /> <span data-ttu-id="31ba2-109">Určuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="31ba2-109">Specifies the address of the endpoint.</span></span> <span data-ttu-id="31ba2-110">Adresa musí být absolutním identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="31ba2-110">The address must be an absolute URI.</span></span> <span data-ttu-id="31ba2-111">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="31ba2-111">The default value is an empty string.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31ba2-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="31ba2-112">Child Elements</span></span>  
  
|<span data-ttu-id="31ba2-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="31ba2-113">Element</span></span>|<span data-ttu-id="31ba2-114">Description</span><span class="sxs-lookup"><span data-stu-id="31ba2-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="31ba2-115">Kolekce hlaviček adres.</span><span class="sxs-lookup"><span data-stu-id="31ba2-115">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="31ba2-116">Identita, která umožňuje ověřování koncového bodu jinými koncovými body vyměňující zprávy.</span><span class="sxs-lookup"><span data-stu-id="31ba2-116">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="31ba2-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="31ba2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="31ba2-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="31ba2-118">Element</span></span>|<span data-ttu-id="31ba2-119">Description</span><span class="sxs-lookup"><span data-stu-id="31ba2-119">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="31ba2-120">Definuje nastavení pro zabezpečení na úrovni zprávy pro [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="31ba2-120">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31ba2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="31ba2-121">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.IssuerMetadata%2A>
- [<span data-ttu-id="31ba2-122">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="31ba2-122">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="31ba2-123">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="31ba2-123">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="31ba2-124">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="31ba2-124">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="31ba2-125">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="31ba2-125">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
