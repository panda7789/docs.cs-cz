---
title: <issuer>
ms.date: 03/30/2017
ms.assetid: 8c49c6ae-fa1a-4179-a84b-613c3216dcde
ms.openlocfilehash: 74f5f2fc1a0fa1ffbbb510e4e700c33a13d02ab3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397919"
---
# <a name="issuer"></a><span data-ttu-id="d5271-101">\<issuer></span><span class="sxs-lookup"><span data-stu-id="d5271-101">\<issuer></span></span>
<span data-ttu-id="d5271-102">Určuje službu tokenů zabezpečení (STS), která vydává tokeny zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d5271-102">Specifies the Security Token Service (STS) that issues security tokens.</span></span>  
  
<span data-ttu-id="d5271-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d5271-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d5271-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d5271-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d5271-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d5271-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d5271-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d5271-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d5271-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="d5271-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d5271-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d5271-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d5271-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zprávy**](message-element-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d5271-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<message>**](message-element-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="d5271-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vystavitele**</span><span class="sxs-lookup"><span data-stu-id="d5271-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5271-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5271-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5271-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d5271-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d5271-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d5271-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5271-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d5271-114">Attributes</span></span>  
  
|<span data-ttu-id="d5271-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d5271-115">Attribute</span></span>|<span data-ttu-id="d5271-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d5271-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d5271-117">adresa</span><span class="sxs-lookup"><span data-stu-id="d5271-117">address</span></span>|<span data-ttu-id="d5271-118">Povinný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d5271-118">Required string.</span></span> <span data-ttu-id="d5271-119">Adresa URL služby STS</span><span class="sxs-lookup"><span data-stu-id="d5271-119">The URL of the STS.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d5271-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d5271-120">Child Elements</span></span>  
  
|<span data-ttu-id="d5271-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="d5271-121">Element</span></span>|<span data-ttu-id="d5271-122">Popis</span><span class="sxs-lookup"><span data-stu-id="d5271-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5271-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="d5271-123">\<headers></span></span>](headers-element.md)|<span data-ttu-id="d5271-124">Kolekce záhlaví adres pro koncové body, které může tvůrce vytvořit.</span><span class="sxs-lookup"><span data-stu-id="d5271-124">A collection of address headers for the endpoints that the builder can create.</span></span>|  
|[<span data-ttu-id="d5271-125">\<identity></span><span class="sxs-lookup"><span data-stu-id="d5271-125">\<identity></span></span>](identity.md)|<span data-ttu-id="d5271-126">Při použití vydaného tokenu aplikace určuje nastavení, které klientovi umožní Server ověřit.</span><span class="sxs-lookup"><span data-stu-id="d5271-126">When using an issued token, specifies settings that enable the client to authenticate the server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5271-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d5271-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d5271-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="d5271-128">Element</span></span>|<span data-ttu-id="d5271-129">Popis</span><span class="sxs-lookup"><span data-stu-id="d5271-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d5271-130">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="d5271-130">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="d5271-131">Definuje nastavení pro zabezpečení na úrovni zprávy pro [ \<element wsFederationHttpBinding >](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="d5271-131">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5271-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5271-132">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.Issuer%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>
- [<span data-ttu-id="d5271-133">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d5271-133">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d5271-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d5271-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d5271-135">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="d5271-135">Service Identity and Authentication</span></span>](../../../wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d5271-136">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d5271-136">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="d5271-137">Možnosti zabezpečení u vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="d5271-137">Security Capabilities with Custom Bindings</span></span>](../../../wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [<span data-ttu-id="d5271-138">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="d5271-138">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
