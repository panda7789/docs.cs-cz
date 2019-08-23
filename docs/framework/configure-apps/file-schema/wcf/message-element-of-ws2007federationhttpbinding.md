---
title: <message>prvek elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 4340727026cb151f2efe813dfa005c1c5a1908be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931627"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="a8172-102">\<> prvku \<zprávy > WS2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="a8172-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="a8172-103">Definuje nastavení pro zabezpečení na úrovni zprávy pro [ \<element WS2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a8172-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="a8172-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a8172-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8172-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="a8172-105">\<bindings></span></span>  
<span data-ttu-id="a8172-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a8172-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="a8172-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a8172-107">\<binding></span></span>  
<span data-ttu-id="a8172-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a8172-108">\<security></span></span>  
<span data-ttu-id="a8172-109">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="a8172-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8172-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8172-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               issuedTokenType="string"
               issuedKeyType="SymmetricKey/PublicKey"
               negotiateServiceCredential="Boolean">
        <claimTypeRequirements>
          <add claimType="URI"
               isOptional="Boolean" />
        </claimTypeRequirements>
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
</ws2007FederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8172-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a8172-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a8172-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a8172-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8172-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a8172-113">Attributes</span></span>  
  
|<span data-ttu-id="a8172-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a8172-114">Attribute</span></span>|<span data-ttu-id="a8172-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a8172-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="a8172-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="a8172-116">Optional.</span></span> <span data-ttu-id="a8172-117">Nastaví algoritmy šifrování, podpisu a zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="a8172-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="a8172-118">Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou.</span><span class="sxs-lookup"><span data-stu-id="a8172-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="a8172-119">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="a8172-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="a8172-120">Možné hodnoty jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a8172-120">See the following table for possible values.</span></span> <span data-ttu-id="a8172-121">Výchozí hodnota je Basic256.</span><span class="sxs-lookup"><span data-stu-id="a8172-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="a8172-122">Určuje typ klíče, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="a8172-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="a8172-123">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a8172-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a8172-124">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="a8172-124">-   SymmetricKey</span></span><br /><span data-ttu-id="a8172-125">– PublicKey</span><span class="sxs-lookup"><span data-stu-id="a8172-125">-   PublicKey</span></span><br /><span data-ttu-id="a8172-126">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="a8172-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="a8172-127">Výchozí hodnota je SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="a8172-127">The default is SymmetricKey.</span></span> <span data-ttu-id="a8172-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="a8172-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="a8172-129">Identifikátor URI, který určuje typ tokenu, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="a8172-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="a8172-130">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="a8172-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="a8172-131">Hodnota, která určuje, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="a8172-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="a8172-132">Výchozí hodnota je `true`, což znamená, že se pověření služby vyjednávat.</span><span class="sxs-lookup"><span data-stu-id="a8172-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="a8172-133">algorithmSuite – atribut</span><span class="sxs-lookup"><span data-stu-id="a8172-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="a8172-134">Value</span><span class="sxs-lookup"><span data-stu-id="a8172-134">Value</span></span>|<span data-ttu-id="a8172-135">Popis</span><span class="sxs-lookup"><span data-stu-id="a8172-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a8172-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="a8172-136">Basic128</span></span>|<span data-ttu-id="a8172-137">Pro zabalení klíče použijte šifrování Aes128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="a8172-138">Basic192</span></span>|<span data-ttu-id="a8172-139">Pro zabalení klíče použijte šifrování Aes192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="a8172-140">Basic256</span></span>|<span data-ttu-id="a8172-141">Pro zabalení klíče použijte šifrování AES256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-142">Basic256Rsa15</span></span>|<span data-ttu-id="a8172-143">Použijte AES256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="a8172-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a8172-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-144">Basic192Rsa15</span></span>|<span data-ttu-id="a8172-145">Použijte Aes192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="a8172-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a8172-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="a8172-146">TripleDes</span></span>|<span data-ttu-id="a8172-147">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-148">Basic128Rsa15</span></span>|<span data-ttu-id="a8172-149">Použijte Aes128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="a8172-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a8172-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-150">TripleDesRsa15</span></span>|<span data-ttu-id="a8172-151">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="a8172-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a8172-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="a8172-152">Basic128Sha256</span></span>|<span data-ttu-id="a8172-153">Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="a8172-154">Basic192Sha256</span></span>|<span data-ttu-id="a8172-155">Pro zabalení klíče použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="a8172-156">Basic256Sha256</span></span>|<span data-ttu-id="a8172-157">Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="a8172-158">TripleDesSha256</span></span>|<span data-ttu-id="a8172-159">Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="a8172-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="a8172-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="a8172-161">Použijte Aes128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="a8172-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a8172-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="a8172-163">Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="a8172-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a8172-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="a8172-165">Použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="a8172-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="a8172-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="a8172-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="a8172-167">Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="a8172-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8172-168">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a8172-168">Child Elements</span></span>  
  
|<span data-ttu-id="a8172-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8172-169">Element</span></span>|<span data-ttu-id="a8172-170">Popis</span><span class="sxs-lookup"><span data-stu-id="a8172-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8172-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="a8172-171">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="a8172-172">Určuje kolekci typů deklarací pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="a8172-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="a8172-173">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="a8172-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="a8172-174">\<issuer></span><span class="sxs-lookup"><span data-stu-id="a8172-174">\<issuer></span></span>](issuer.md)|<span data-ttu-id="a8172-175">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a8172-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="a8172-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="a8172-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="a8172-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="a8172-177">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="a8172-178">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="a8172-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="a8172-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="a8172-179">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="a8172-180">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="a8172-180">A collection of token request parameters.</span></span> <span data-ttu-id="a8172-181">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="a8172-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a8172-182">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a8172-182">Parent Elements</span></span>  
  
|<span data-ttu-id="a8172-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8172-183">Element</span></span>|<span data-ttu-id="a8172-184">Popis</span><span class="sxs-lookup"><span data-stu-id="a8172-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8172-185">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a8172-185">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="a8172-186">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="a8172-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8172-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8172-187">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="a8172-188">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a8172-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a8172-189">Vazby</span><span class="sxs-lookup"><span data-stu-id="a8172-189">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a8172-190">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a8172-190">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a8172-191">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a8172-191">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a8172-192">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a8172-192">\<binding></span></span>](../../../misc/binding.md)
