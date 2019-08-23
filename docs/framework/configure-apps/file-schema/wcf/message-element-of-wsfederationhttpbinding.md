---
title: <message>prvek elementu<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 4730d7e573eefdfcd5704621d0a7ccaa15f76d3a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931581"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="2a212-102">\<> prvku \<zprávy > WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2a212-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="2a212-103">Definuje nastavení pro zabezpečení [ \<](wsfederationhttpbinding.md)na úrovni zpráv > WSFederationHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="2a212-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="2a212-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a212-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a212-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="2a212-105">\<bindings></span></span>  
<span data-ttu-id="2a212-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="2a212-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="2a212-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="2a212-107">\<binding></span></span>  
<span data-ttu-id="2a212-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2a212-108">\<security></span></span>  
<span data-ttu-id="2a212-109">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="2a212-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a212-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a212-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>
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
</wsFederationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a212-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2a212-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2a212-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2a212-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a212-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="2a212-113">Attributes</span></span>  
  
|<span data-ttu-id="2a212-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="2a212-114">Attribute</span></span>|<span data-ttu-id="2a212-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2a212-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a212-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="2a212-116">algorithmSuite</span></span>|<span data-ttu-id="2a212-117">Nastaví šifrování zpráv a algoritmy pro zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="2a212-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="2a212-118">Platné hodnoty tohoto atributu najdete v tabulce atributu algorithmSuite.</span><span class="sxs-lookup"><span data-stu-id="2a212-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="2a212-119">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="2a212-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="2a212-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="2a212-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="2a212-121">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="2a212-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="2a212-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="2a212-122">issuedKeyType</span></span>|<span data-ttu-id="2a212-123">Určuje typ klíče, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="2a212-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="2a212-124">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="2a212-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2a212-125">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="2a212-125">-   SymmetricKey</span></span><br /><span data-ttu-id="2a212-126">– PublicKey</span><span class="sxs-lookup"><span data-stu-id="2a212-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="2a212-127">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="2a212-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="2a212-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="2a212-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="2a212-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="2a212-129">issuedTokenType</span></span>|<span data-ttu-id="2a212-130">Řetězec obsahující identifikátor URI, který určuje typ tokenu, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="2a212-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="2a212-131">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="2a212-131">The default is `null`.</span></span>|  
|<span data-ttu-id="2a212-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="2a212-132">negotiateServiceCredential</span></span>|<span data-ttu-id="2a212-133">Logická hodnota určující, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="2a212-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="2a212-134">Výchozí hodnota je `true`, což znamená, že se pověření služby vyjednávat.</span><span class="sxs-lookup"><span data-stu-id="2a212-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="2a212-135">algorithmSuite – atribut</span><span class="sxs-lookup"><span data-stu-id="2a212-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="2a212-136">Value</span><span class="sxs-lookup"><span data-stu-id="2a212-136">Value</span></span>|<span data-ttu-id="2a212-137">Popis</span><span class="sxs-lookup"><span data-stu-id="2a212-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a212-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="2a212-138">Basic128</span></span>|<span data-ttu-id="2a212-139">Pro zabalení klíče použijte šifrování Basic128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="2a212-140">Basic192</span></span>|<span data-ttu-id="2a212-141">Pro zabalení klíče použijte šifrování Basic192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="2a212-142">Basic256</span></span>|<span data-ttu-id="2a212-143">Pro zabalení klíče použijte šifrování Basic256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-144">Basic256Rsa15</span></span>|<span data-ttu-id="2a212-145">Použijte Basic256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2a212-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2a212-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-146">Basic192Rsa15</span></span>|<span data-ttu-id="2a212-147">Použijte Basic192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2a212-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2a212-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="2a212-148">TripleDes</span></span>|<span data-ttu-id="2a212-149">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-150">Basic128Rsa15</span></span>|<span data-ttu-id="2a212-151">Použijte Basic128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2a212-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2a212-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-152">TripleDesRsa15</span></span>|<span data-ttu-id="2a212-153">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="2a212-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2a212-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="2a212-154">Basic128Sha256</span></span>|<span data-ttu-id="2a212-155">Pro zabalení klíče použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="2a212-156">Basic192Sha256</span></span>|<span data-ttu-id="2a212-157">Pro zabalení klíče použijte Basic192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="2a212-158">Basic256Sha256</span></span>|<span data-ttu-id="2a212-159">Pro zabalení klíče použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="2a212-160">TripleDesSha256</span></span>|<span data-ttu-id="2a212-161">Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2a212-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2a212-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="2a212-163">Použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2a212-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2a212-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="2a212-165">Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2a212-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2a212-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="2a212-167">Použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2a212-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2a212-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2a212-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="2a212-169">Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="2a212-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a212-170">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2a212-170">Child Elements</span></span>  
  
|<span data-ttu-id="2a212-171">Prvek</span><span class="sxs-lookup"><span data-stu-id="2a212-171">Element</span></span>|<span data-ttu-id="2a212-172">Popis</span><span class="sxs-lookup"><span data-stu-id="2a212-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a212-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2a212-173">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="2a212-174">Určuje kolekci typů deklarací pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="2a212-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="2a212-175">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="2a212-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="2a212-176">issuer</span><span class="sxs-lookup"><span data-stu-id="2a212-176">issuer</span></span>|<span data-ttu-id="2a212-177">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2a212-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="2a212-178">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="2a212-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="2a212-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="2a212-179">issuerMetadata</span></span>|<span data-ttu-id="2a212-180">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="2a212-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="2a212-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="2a212-181">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="2a212-182">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="2a212-182">A collection of token request parameters.</span></span> <span data-ttu-id="2a212-183">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="2a212-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a212-184">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2a212-184">Parent Elements</span></span>  
  
|<span data-ttu-id="2a212-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="2a212-185">Element</span></span>|<span data-ttu-id="2a212-186">Popis</span><span class="sxs-lookup"><span data-stu-id="2a212-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a212-187">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2a212-187">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="2a212-188">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="2a212-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a212-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a212-189">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="2a212-190">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2a212-190">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2a212-191">Vazby</span><span class="sxs-lookup"><span data-stu-id="2a212-191">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2a212-192">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2a212-192">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2a212-193">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2a212-193">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2a212-194">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="2a212-194">\<binding></span></span>](../../../misc/binding.md)
