---
title: <security> z <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 6c07d1ca18837f66548411262b84b9a326f5ec4a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399735"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="49152-102">\<security> of \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="49152-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="49152-103">Definuje nastavení [ \<zabezpečení WSFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="49152-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="49152-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="49152-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="49152-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="49152-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="49152-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="49152-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="49152-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="49152-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="49152-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="49152-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="49152-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="49152-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49152-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49152-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49152-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="49152-111">Attributes and Elements</span></span>  
 <span data-ttu-id="49152-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="49152-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49152-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="49152-113">Attributes</span></span>  
  
|<span data-ttu-id="49152-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="49152-114">Attribute</span></span>|<span data-ttu-id="49152-115">Popis</span><span class="sxs-lookup"><span data-stu-id="49152-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49152-116">Režim</span><span class="sxs-lookup"><span data-stu-id="49152-116">Mode</span></span>|<span data-ttu-id="49152-117">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="49152-117">Optional.</span></span> <span data-ttu-id="49152-118">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="49152-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="49152-119">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="49152-119">The default value is `Message`.</span></span> <span data-ttu-id="49152-120">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="49152-120">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="49152-121">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="49152-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="49152-122">Value</span><span class="sxs-lookup"><span data-stu-id="49152-122">Value</span></span>|<span data-ttu-id="49152-123">Popis</span><span class="sxs-lookup"><span data-stu-id="49152-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49152-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="49152-124">None</span></span>|<span data-ttu-id="49152-125">Zpráva SOAP není během přenosu zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="49152-125">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="49152-126">Message</span><span class="sxs-lookup"><span data-stu-id="49152-126">Message</span></span>|<span data-ttu-id="49152-127">Integrita, důvěrnost, ověřování serveru a ověřování klientů jsou k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="49152-127">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="49152-128">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="49152-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="49152-129">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="49152-129">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="49152-130">Ověřování klientů vychází z tokenu vystaveného klientovi tokenem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="49152-130">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="49152-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="49152-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="49152-132">Integrita, důvěrnost a ověřování serveru poskytuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="49152-132">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="49152-133">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="49152-133">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="49152-134">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP a je založeno na tokenu vydanému klientovi pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="49152-134">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49152-135">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="49152-135">Child Elements</span></span>  
  
|<span data-ttu-id="49152-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="49152-136">Element</span></span>|<span data-ttu-id="49152-137">Popis</span><span class="sxs-lookup"><span data-stu-id="49152-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49152-138">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="49152-138">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="49152-139">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="49152-139">Defines the settings for the message-level security.</span></span> <span data-ttu-id="49152-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="49152-140">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49152-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="49152-141">Parent Elements</span></span>  
  
|<span data-ttu-id="49152-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="49152-142">Element</span></span>|<span data-ttu-id="49152-143">Popis</span><span class="sxs-lookup"><span data-stu-id="49152-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49152-144">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="49152-144">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="49152-145">Definuje všechny schopnosti [ \<vazby wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="49152-145">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49152-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49152-146">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="49152-147">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="49152-147">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="49152-148">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="49152-148">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="49152-149">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="49152-149">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="49152-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="49152-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="49152-151">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="49152-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="49152-152">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="49152-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="49152-153">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="49152-153">\<binding></span></span>](../../../misc/binding.md)
