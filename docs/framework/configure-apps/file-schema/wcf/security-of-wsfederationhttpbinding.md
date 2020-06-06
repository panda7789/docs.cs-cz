---
title: <security> z <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: ea029444cee331a235c7a2fc140b4321d7530063
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736325"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="b6301-102">\<security> z \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b6301-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="b6301-103">Definuje nastavení zabezpečení [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b6301-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="b6301-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6301-104">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
  <binding>
    <security mode="None/Message/TransportWithMessageCredential">
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
        <issuer address="Uri" >
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
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuer>
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
                                  X509FindType="System.Security.Cryptography.X509certificates.X509findtype" />
            <dns value="String" />
            <rsa value="String" />
            <servicePrincipalName value="String" />
            <usePrincipalName value="String" />
          </identity>
        </issuerMetadata>
        <tokenRequestParameters>
          <xmlElement>
          </xmlElement>
        </tokenRequestParameters>
      </message>
    </security>
  </binding>
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6301-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b6301-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b6301-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b6301-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6301-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b6301-107">Attributes</span></span>  
  
|<span data-ttu-id="b6301-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b6301-108">Attribute</span></span>|<span data-ttu-id="b6301-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b6301-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6301-110">Mode</span><span class="sxs-lookup"><span data-stu-id="b6301-110">Mode</span></span>|<span data-ttu-id="b6301-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b6301-111">Optional.</span></span> <span data-ttu-id="b6301-112">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="b6301-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="b6301-113">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="b6301-113">The default value is `Message`.</span></span> <span data-ttu-id="b6301-114">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="b6301-114">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b6301-115">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="b6301-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="b6301-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b6301-116">Value</span></span>|<span data-ttu-id="b6301-117">Description</span><span class="sxs-lookup"><span data-stu-id="b6301-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b6301-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="b6301-118">None</span></span>|<span data-ttu-id="b6301-119">Zpráva SOAP není během přenosu zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="b6301-119">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="b6301-120">Zpráva</span><span class="sxs-lookup"><span data-stu-id="b6301-120">Message</span></span>|<span data-ttu-id="b6301-121">Integrita, důvěrnost, ověřování serveru a ověřování klientů jsou k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="b6301-121">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="b6301-122">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="b6301-122">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="b6301-123">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="b6301-123">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="b6301-124">Ověřování klientů vychází z tokenu vystaveného klientovi tokenem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b6301-124">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="b6301-125">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b6301-125">TransportWithMessageCredential</span></span>|<span data-ttu-id="b6301-126">Integrita, důvěrnost a ověřování serveru poskytuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b6301-126">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="b6301-127">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="b6301-127">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="b6301-128">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP a je založeno na tokenu vydanému klientovi pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b6301-128">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6301-129">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b6301-129">Child Elements</span></span>  
  
|<span data-ttu-id="b6301-130">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6301-130">Element</span></span>|<span data-ttu-id="b6301-131">Description</span><span class="sxs-lookup"><span data-stu-id="b6301-131">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="b6301-132">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="b6301-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="b6301-133">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement> .</span><span class="sxs-lookup"><span data-stu-id="b6301-133">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6301-134">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b6301-134">Parent Elements</span></span>  
  
|<span data-ttu-id="b6301-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6301-135">Element</span></span>|<span data-ttu-id="b6301-136">Description</span><span class="sxs-lookup"><span data-stu-id="b6301-136">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="b6301-137">Definuje všechny schopnosti vazby pro [\<wsDualHttpBinding>](wsdualhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b6301-137">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6301-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6301-138">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="b6301-139">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="b6301-139">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="b6301-140">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b6301-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b6301-141">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="b6301-141">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b6301-142">Vazby</span><span class="sxs-lookup"><span data-stu-id="b6301-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b6301-143">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b6301-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b6301-144">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b6301-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
