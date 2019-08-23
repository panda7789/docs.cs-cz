---
title: <security> z <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: a8e5e854-b8dc-4921-843d-34b6a4a6a8ba
ms.openlocfilehash: 875ce7d548d59f32465da817e9e956217f346f60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936539"
---
# <a name="security-of-wsfederationhttpbinding"></a><span data-ttu-id="c131f-102">\<security> of \<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="c131f-102">\<security> of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="c131f-103">Definuje nastavení [ \<zabezpečení WSFederationHttpBinding >](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c131f-103">Defines the security settings of the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="c131f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c131f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c131f-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="c131f-105">\<bindings></span></span>  
<span data-ttu-id="c131f-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="c131f-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="c131f-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c131f-107">\<binding></span></span>  
<span data-ttu-id="c131f-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c131f-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c131f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c131f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c131f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c131f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c131f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c131f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c131f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c131f-112">Attributes</span></span>  
  
|<span data-ttu-id="c131f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="c131f-113">Attribute</span></span>|<span data-ttu-id="c131f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="c131f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c131f-115">Režim</span><span class="sxs-lookup"><span data-stu-id="c131f-115">Mode</span></span>|<span data-ttu-id="c131f-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="c131f-116">Optional.</span></span> <span data-ttu-id="c131f-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="c131f-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="c131f-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="c131f-118">The default value is `Message`.</span></span> <span data-ttu-id="c131f-119">Tento atribut je typu <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="c131f-119">This attribute is of type <xref:System.ServiceModel.WSFederationHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c131f-120">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="c131f-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="c131f-121">Value</span><span class="sxs-lookup"><span data-stu-id="c131f-121">Value</span></span>|<span data-ttu-id="c131f-122">Popis</span><span class="sxs-lookup"><span data-stu-id="c131f-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c131f-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="c131f-123">None</span></span>|<span data-ttu-id="c131f-124">Zpráva SOAP není během přenosu zabezpečená.</span><span class="sxs-lookup"><span data-stu-id="c131f-124">The SOAP message is not secure during transfer.</span></span>|  
|<span data-ttu-id="c131f-125">Message</span><span class="sxs-lookup"><span data-stu-id="c131f-125">Message</span></span>|<span data-ttu-id="c131f-126">Integrita, důvěrnost, ověřování serveru a ověřování klientů jsou k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="c131f-126">Integrity, confidentiality, server authentication and client authentication are provided using SOAP message security.</span></span> <span data-ttu-id="c131f-127">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="c131f-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="c131f-128">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="c131f-128">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="c131f-129">Ověřování klientů vychází z tokenu vystaveného klientovi tokenem zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c131f-129">Client authentication is based on the token issued to the client by a security token service</span></span>|  
|<span data-ttu-id="c131f-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c131f-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="c131f-131">Integrita, důvěrnost a ověřování serveru poskytuje protokol HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c131f-131">Integrity, confidentiality and server authentication are provided by HTTPS.</span></span> <span data-ttu-id="c131f-132">Služba musí být nakonfigurovaná s certifikátem.</span><span class="sxs-lookup"><span data-stu-id="c131f-132">The service needs to be configured with a certificate.</span></span> <span data-ttu-id="c131f-133">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP a je založeno na tokenu vydanému klientovi pomocí služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c131f-133">Client authentication is provided by means of SOAP message security and is based on the token issued to the client by a security token service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c131f-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c131f-134">Child Elements</span></span>  
  
|<span data-ttu-id="c131f-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="c131f-135">Element</span></span>|<span data-ttu-id="c131f-136">Popis</span><span class="sxs-lookup"><span data-stu-id="c131f-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c131f-137">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="c131f-137">\<message></span></span>](message-element-of-wsfederationhttpbinding.md)|<span data-ttu-id="c131f-138">Definuje nastavení pro zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="c131f-138">Defines the settings for the message-level security.</span></span> <span data-ttu-id="c131f-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="c131f-139">This element is of type <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c131f-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c131f-140">Parent Elements</span></span>  
  
|<span data-ttu-id="c131f-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="c131f-141">Element</span></span>|<span data-ttu-id="c131f-142">Popis</span><span class="sxs-lookup"><span data-stu-id="c131f-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c131f-143">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c131f-143">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="c131f-144">Definuje všechny schopnosti [ \<vazby wsDualHttpBinding >](wsdualhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c131f-144">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c131f-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c131f-145">See also</span></span>

- <xref:System.ServiceModel.WSFederationHttpSecurity>
- <xref:System.ServiceModel.WSFederationHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>
- [<span data-ttu-id="c131f-146">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c131f-146">How to: Create a WSFederationHttpBinding</span></span>](../../../wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [<span data-ttu-id="c131f-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c131f-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c131f-148">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="c131f-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="c131f-149">Vazby</span><span class="sxs-lookup"><span data-stu-id="c131f-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c131f-150">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="c131f-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c131f-151">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="c131f-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c131f-152">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="c131f-152">\<binding></span></span>](../../../misc/binding.md)
