---
title: <message> element <wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738984"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="976ae-102">\<> elementu \<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="976ae-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="976ae-103">Definuje nastavení pro zabezpečení na úrovni zpráv [\<WSFederationHttpBinding](wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="976ae-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="976ae-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="976ae-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="976ae-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="976ae-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="976ae-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="976ae-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="976ae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="976ae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="976ae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="976ae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="976ae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="976ae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="976ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zpráva >**</span><span class="sxs-lookup"><span data-stu-id="976ae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="976ae-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="976ae-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="976ae-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="976ae-112">Attributes and Elements</span></span>  
 <span data-ttu-id="976ae-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="976ae-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="976ae-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="976ae-114">Attributes</span></span>  
  
|<span data-ttu-id="976ae-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="976ae-115">Attribute</span></span>|<span data-ttu-id="976ae-116">Popis</span><span class="sxs-lookup"><span data-stu-id="976ae-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="976ae-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="976ae-117">algorithmSuite</span></span>|<span data-ttu-id="976ae-118">Nastaví šifrování zpráv a algoritmy pro zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="976ae-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="976ae-119">Platné hodnoty tohoto atributu najdete v tabulce atributu algorithmSuite.</span><span class="sxs-lookup"><span data-stu-id="976ae-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="976ae-120">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="976ae-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="976ae-121">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="976ae-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="976ae-122">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="976ae-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="976ae-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="976ae-123">issuedKeyType</span></span>|<span data-ttu-id="976ae-124">Určuje typ klíče, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="976ae-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="976ae-125">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="976ae-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="976ae-126">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="976ae-126">-   SymmetricKey</span></span><br /><span data-ttu-id="976ae-127">– PublicKey</span><span class="sxs-lookup"><span data-stu-id="976ae-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="976ae-128">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="976ae-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="976ae-129">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="976ae-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="976ae-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="976ae-130">issuedTokenType</span></span>|<span data-ttu-id="976ae-131">Řetězec obsahující identifikátor URI, který určuje typ tokenu, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="976ae-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="976ae-132">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="976ae-132">The default is `null`.</span></span>|  
|<span data-ttu-id="976ae-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="976ae-133">negotiateServiceCredential</span></span>|<span data-ttu-id="976ae-134">Logická hodnota určující, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="976ae-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="976ae-135">Výchozí hodnota je `true`, což znamená, že se pověření služby vyjednávat.</span><span class="sxs-lookup"><span data-stu-id="976ae-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="976ae-136">algorithmSuite – atribut</span><span class="sxs-lookup"><span data-stu-id="976ae-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="976ae-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="976ae-137">Value</span></span>|<span data-ttu-id="976ae-138">Popis</span><span class="sxs-lookup"><span data-stu-id="976ae-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="976ae-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="976ae-139">Basic128</span></span>|<span data-ttu-id="976ae-140">Pro zabalení klíče použijte šifrování Basic128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="976ae-141">Basic192</span></span>|<span data-ttu-id="976ae-142">Pro zabalení klíče použijte šifrování Basic192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="976ae-143">Basic256</span></span>|<span data-ttu-id="976ae-144">Pro zabalení klíče použijte šifrování Basic256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-145">Basic256Rsa15</span></span>|<span data-ttu-id="976ae-146">Použijte Basic256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="976ae-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="976ae-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-147">Basic192Rsa15</span></span>|<span data-ttu-id="976ae-148">Použijte Basic192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="976ae-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="976ae-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="976ae-149">TripleDes</span></span>|<span data-ttu-id="976ae-150">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-151">Basic128Rsa15</span></span>|<span data-ttu-id="976ae-152">Použijte Basic128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="976ae-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="976ae-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-153">TripleDesRsa15</span></span>|<span data-ttu-id="976ae-154">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="976ae-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="976ae-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="976ae-155">Basic128Sha256</span></span>|<span data-ttu-id="976ae-156">Pro zabalení klíče použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="976ae-157">Basic192Sha256</span></span>|<span data-ttu-id="976ae-158">Pro zabalení klíče použijte Basic192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="976ae-159">Basic256Sha256</span></span>|<span data-ttu-id="976ae-160">Pro zabalení klíče použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="976ae-161">TripleDesSha256</span></span>|<span data-ttu-id="976ae-162">Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="976ae-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="976ae-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="976ae-164">Použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="976ae-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="976ae-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="976ae-166">Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="976ae-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="976ae-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="976ae-168">Použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="976ae-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="976ae-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="976ae-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="976ae-170">Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="976ae-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="976ae-171">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="976ae-171">Child Elements</span></span>  
  
|<span data-ttu-id="976ae-172">Prvek</span><span class="sxs-lookup"><span data-stu-id="976ae-172">Element</span></span>|<span data-ttu-id="976ae-173">Popis</span><span class="sxs-lookup"><span data-stu-id="976ae-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="976ae-174">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="976ae-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="976ae-175">Určuje kolekci typů deklarací pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="976ae-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="976ae-176">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="976ae-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="976ae-177">issuer</span><span class="sxs-lookup"><span data-stu-id="976ae-177">issuer</span></span>|<span data-ttu-id="976ae-178">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="976ae-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="976ae-179">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="976ae-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="976ae-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="976ae-180">issuerMetadata</span></span>|<span data-ttu-id="976ae-181">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="976ae-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="976ae-182">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="976ae-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="976ae-183">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="976ae-183">A collection of token request parameters.</span></span> <span data-ttu-id="976ae-184">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="976ae-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="976ae-185">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="976ae-185">Parent Elements</span></span>  
  
|<span data-ttu-id="976ae-186">Prvek</span><span class="sxs-lookup"><span data-stu-id="976ae-186">Element</span></span>|<span data-ttu-id="976ae-187">Popis</span><span class="sxs-lookup"><span data-stu-id="976ae-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="976ae-188">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="976ae-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="976ae-189">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="976ae-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="976ae-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="976ae-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="976ae-191">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="976ae-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="976ae-192">Vazby</span><span class="sxs-lookup"><span data-stu-id="976ae-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="976ae-193">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="976ae-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="976ae-194">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="976ae-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="976ae-195">vazba \<</span><span class="sxs-lookup"><span data-stu-id="976ae-195">\<binding></span></span>](bindings.md)
