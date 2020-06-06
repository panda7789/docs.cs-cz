---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397919"
---
# \<issuer>
<span data-ttu-id="11d97-101">Určuje službu tokenů zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="11d97-101">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**  
  
## <a name="syntax"></a><span data-ttu-id="11d97-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="11d97-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11d97-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="11d97-103">Attributes and Elements</span></span>  
 <span data-ttu-id="11d97-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="11d97-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11d97-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="11d97-105">Attributes</span></span>  
  
|<span data-ttu-id="11d97-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="11d97-106">Attribute</span></span>|<span data-ttu-id="11d97-107">Popis</span><span class="sxs-lookup"><span data-stu-id="11d97-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="11d97-108">adresa</span><span class="sxs-lookup"><span data-stu-id="11d97-108">address</span></span>|<span data-ttu-id="11d97-109">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="11d97-109">Required string.</span></span> <span data-ttu-id="11d97-110">Adresa URL služby STS</span><span class="sxs-lookup"><span data-stu-id="11d97-110">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11d97-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="11d97-111">Child Elements</span></span>  
  
|<span data-ttu-id="11d97-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="11d97-112">Element</span></span>|<span data-ttu-id="11d97-113">Description</span><span class="sxs-lookup"><span data-stu-id="11d97-113">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers-element.md)|<span data-ttu-id="11d97-114">Kolekce záhlaví adres pro koncové body, které může tvůrce vytvořit.</span><span class="sxs-lookup"><span data-stu-id="11d97-114">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="11d97-115">Při použití vydaného tokenu aplikace určuje nastavení, které klientovi umožní Server ověřit.</span><span class="sxs-lookup"><span data-stu-id="11d97-115">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11d97-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="11d97-116">Parent Elements</span></span>  
  
|<span data-ttu-id="11d97-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="11d97-117">Element</span></span>|<span data-ttu-id="11d97-118">Description</span><span class="sxs-lookup"><span data-stu-id="11d97-118">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="11d97-119">Definuje nastavení pro zabezpečení na úrovni zprávy pro [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="11d97-119">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="11d97-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="11d97-120">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="11d97-121">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="11d97-121">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="11d97-122">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="11d97-122">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="11d97-123">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="11d97-123">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="11d97-124">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="11d97-124">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="11d97-125">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="11d97-125">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="11d97-126">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="11d97-126">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
