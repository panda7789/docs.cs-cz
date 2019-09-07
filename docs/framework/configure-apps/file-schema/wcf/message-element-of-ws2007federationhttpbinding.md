---
title: <message>prvek elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: b1128bda6068a1fe3d8f5bb5ac29cc349f023b5b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397853"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="65376-102">\<> prvku \<zprávy > WS2007FederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="65376-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="65376-103">Definuje nastavení pro zabezpečení na úrovni zprávy pro [ \<element WS2007FederationHttpBinding >](ws2007federationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="65376-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
<span data-ttu-id="65376-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="65376-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="65376-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="65376-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="65376-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="65376-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="65376-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007FederationHttpBinding >** ](ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="65376-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="65376-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="65376-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="65376-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-element-of-ws2007federationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="65376-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)</span></span>\
<span data-ttu-id="65376-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zprávy**</span><span class="sxs-lookup"><span data-stu-id="65376-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65376-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65376-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65376-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="65376-112">Attributes and Elements</span></span>  
 <span data-ttu-id="65376-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="65376-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65376-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="65376-114">Attributes</span></span>  
  
|<span data-ttu-id="65376-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="65376-115">Attribute</span></span>|<span data-ttu-id="65376-116">Popis</span><span class="sxs-lookup"><span data-stu-id="65376-116">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="65376-117">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="65376-117">Optional.</span></span> <span data-ttu-id="65376-118">Nastaví algoritmy šifrování, podpisu a zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="65376-118">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="65376-119">Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou.</span><span class="sxs-lookup"><span data-stu-id="65376-119">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="65376-120">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="65376-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="65376-121">Možné hodnoty jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="65376-121">See the following table for possible values.</span></span> <span data-ttu-id="65376-122">Výchozí hodnota je Basic256.</span><span class="sxs-lookup"><span data-stu-id="65376-122">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="65376-123">Určuje typ klíče, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="65376-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="65376-124">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="65376-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="65376-125">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="65376-125">-   SymmetricKey</span></span><br /><span data-ttu-id="65376-126">– PublicKey</span><span class="sxs-lookup"><span data-stu-id="65376-126">-   PublicKey</span></span><br /><span data-ttu-id="65376-127">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="65376-127">-   BearerKey</span></span><br /><br /> <span data-ttu-id="65376-128">Výchozí hodnota je SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="65376-128">The default is SymmetricKey.</span></span> <span data-ttu-id="65376-129">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="65376-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="65376-130">Identifikátor URI, který určuje typ tokenu, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="65376-130">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="65376-131">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="65376-131">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="65376-132">Hodnota, která určuje, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="65376-132">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="65376-133">Výchozí hodnota je `true`, což znamená, že se pověření služby vyjednávat.</span><span class="sxs-lookup"><span data-stu-id="65376-133">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="65376-134">algorithmSuite – atribut</span><span class="sxs-lookup"><span data-stu-id="65376-134">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="65376-135">Value</span><span class="sxs-lookup"><span data-stu-id="65376-135">Value</span></span>|<span data-ttu-id="65376-136">Popis</span><span class="sxs-lookup"><span data-stu-id="65376-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="65376-137">Basic128</span><span class="sxs-lookup"><span data-stu-id="65376-137">Basic128</span></span>|<span data-ttu-id="65376-138">Pro zabalení klíče použijte šifrování Aes128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-138">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-139">Basic192</span><span class="sxs-lookup"><span data-stu-id="65376-139">Basic192</span></span>|<span data-ttu-id="65376-140">Pro zabalení klíče použijte šifrování Aes192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-140">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-141">Basic256</span><span class="sxs-lookup"><span data-stu-id="65376-141">Basic256</span></span>|<span data-ttu-id="65376-142">Pro zabalení klíče použijte šifrování AES256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-142">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-143">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="65376-143">Basic256Rsa15</span></span>|<span data-ttu-id="65376-144">Použijte AES256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="65376-144">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="65376-145">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="65376-145">Basic192Rsa15</span></span>|<span data-ttu-id="65376-146">Použijte Aes192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="65376-146">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="65376-147">TripleDes</span><span class="sxs-lookup"><span data-stu-id="65376-147">TripleDes</span></span>|<span data-ttu-id="65376-148">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-148">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-149">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="65376-149">Basic128Rsa15</span></span>|<span data-ttu-id="65376-150">Použijte Aes128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="65376-150">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="65376-151">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="65376-151">TripleDesRsa15</span></span>|<span data-ttu-id="65376-152">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="65376-152">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="65376-153">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="65376-153">Basic128Sha256</span></span>|<span data-ttu-id="65376-154">Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-154">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-155">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="65376-155">Basic192Sha256</span></span>|<span data-ttu-id="65376-156">Pro zabalení klíče použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-156">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-157">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="65376-157">Basic256Sha256</span></span>|<span data-ttu-id="65376-158">Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-158">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-159">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="65376-159">TripleDesSha256</span></span>|<span data-ttu-id="65376-160">Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="65376-160">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="65376-161">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="65376-161">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="65376-162">Použijte Aes128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="65376-162">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="65376-163">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="65376-163">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="65376-164">Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="65376-164">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="65376-165">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="65376-165">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="65376-166">Použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="65376-166">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="65376-167">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="65376-167">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="65376-168">Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="65376-168">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65376-169">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="65376-169">Child Elements</span></span>  
  
|<span data-ttu-id="65376-170">Prvek</span><span class="sxs-lookup"><span data-stu-id="65376-170">Element</span></span>|<span data-ttu-id="65376-171">Popis</span><span class="sxs-lookup"><span data-stu-id="65376-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65376-172">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="65376-172">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="65376-173">Určuje kolekci typů deklarací pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="65376-173">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="65376-174">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="65376-174">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="65376-175">\<issuer></span><span class="sxs-lookup"><span data-stu-id="65376-175">\<issuer></span></span>](issuer.md)|<span data-ttu-id="65376-176">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="65376-176">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="65376-177">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="65376-177">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="65376-178">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="65376-178">\<issuerMetadata></span></span>](issuermetadata.md)|<span data-ttu-id="65376-179">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="65376-179">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="65376-180">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="65376-180">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="65376-181">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="65376-181">A collection of token request parameters.</span></span> <span data-ttu-id="65376-182">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="65376-182">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65376-183">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="65376-183">Parent Elements</span></span>  
  
|<span data-ttu-id="65376-184">Prvek</span><span class="sxs-lookup"><span data-stu-id="65376-184">Element</span></span>|<span data-ttu-id="65376-185">Popis</span><span class="sxs-lookup"><span data-stu-id="65376-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65376-186">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="65376-186">\<security></span></span>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="65376-187">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="65376-187">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65376-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65376-188">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="65376-189">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="65376-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="65376-190">Vazby</span><span class="sxs-lookup"><span data-stu-id="65376-190">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="65376-191">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="65376-191">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="65376-192">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="65376-192">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="65376-193">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="65376-193">\<binding></span></span>](../../../misc/binding.md)
