---
title: <message> Element <ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 9150b6f1ab821f7d062f389c3dbd7fa9119fd0db
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289702"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="7b971-102">\<Zpráva > prvek \<ws2007FederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="7b971-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="7b971-103">Definuje nastavení pro zprávy úroveň zabezpečení pro [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7b971-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="7b971-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b971-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b971-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7b971-105">\<bindings></span></span>  
<span data-ttu-id="7b971-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="7b971-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="7b971-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="7b971-107">\<binding></span></span>  
<span data-ttu-id="7b971-108">\<security></span><span class="sxs-lookup"><span data-stu-id="7b971-108">\<security></span></span>  
<span data-ttu-id="7b971-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="7b971-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b971-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b971-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b971-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b971-111">Attributes and Elements</span></span>  
 <span data-ttu-id="7b971-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b971-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b971-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b971-113">Attributes</span></span>  
  
|<span data-ttu-id="7b971-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b971-114">Attribute</span></span>|<span data-ttu-id="7b971-115">Popis</span><span class="sxs-lookup"><span data-stu-id="7b971-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="7b971-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="7b971-116">Optional.</span></span> <span data-ttu-id="7b971-117">Nastaví šifrování zpráv, podpisu a key-wrap algoritmy.</span><span class="sxs-lookup"><span data-stu-id="7b971-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="7b971-118">Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy.</span><span class="sxs-lookup"><span data-stu-id="7b971-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="7b971-119">Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="7b971-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="7b971-120">Najdete v následující tabulce možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="7b971-120">See the following table for possible values.</span></span> <span data-ttu-id="7b971-121">Výchozí hodnota je Basic256.</span><span class="sxs-lookup"><span data-stu-id="7b971-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="7b971-122">Určuje typ klíče vystavování.</span><span class="sxs-lookup"><span data-stu-id="7b971-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="7b971-123">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="7b971-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7b971-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="7b971-124">-   SymmetricKey</span></span><br /><span data-ttu-id="7b971-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="7b971-125">-   PublicKey</span></span><br /><span data-ttu-id="7b971-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="7b971-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="7b971-127">Výchozí hodnota je SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="7b971-127">The default is SymmetricKey.</span></span> <span data-ttu-id="7b971-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="7b971-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="7b971-129">Identifikátor URI, který určuje typ tokenu je nutno spustit.</span><span class="sxs-lookup"><span data-stu-id="7b971-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="7b971-130">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="7b971-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="7b971-131">Hodnota, která určuje, zda by měl být vyměňují v rámci vyjednávání přihlašovacích údajů služby, nebo je k dispozici mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="7b971-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="7b971-132">Výchozí hodnota je `true`, což znamená, že se vyjedná přihlašovacích údajů pro služby.</span><span class="sxs-lookup"><span data-stu-id="7b971-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="7b971-133">algorithmSuite atribut</span><span class="sxs-lookup"><span data-stu-id="7b971-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="7b971-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="7b971-134">Value</span></span>|<span data-ttu-id="7b971-135">Popis</span><span class="sxs-lookup"><span data-stu-id="7b971-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7b971-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="7b971-136">Basic128</span></span>|<span data-ttu-id="7b971-137">Zabalení klíče použijte Aes128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.</span><span class="sxs-lookup"><span data-stu-id="7b971-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="7b971-138">Basic192</span></span>|<span data-ttu-id="7b971-139">Použijte šifrování Aes192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="7b971-140">Basic256</span></span>|<span data-ttu-id="7b971-141">Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-142">Basic256Rsa15</span></span>|<span data-ttu-id="7b971-143">Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7b971-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-144">Basic192Rsa15</span></span>|<span data-ttu-id="7b971-145">Použití Aes192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7b971-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="7b971-146">TripleDes</span></span>|<span data-ttu-id="7b971-147">Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-148">Basic128Rsa15</span></span>|<span data-ttu-id="7b971-149">Použití Aes128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7b971-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-150">TripleDesRsa15</span></span>|<span data-ttu-id="7b971-151">Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7b971-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="7b971-152">Basic128Sha256</span></span>|<span data-ttu-id="7b971-153">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="7b971-154">Basic192Sha256</span></span>|<span data-ttu-id="7b971-155">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="7b971-156">Basic256Sha256</span></span>|<span data-ttu-id="7b971-157">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="7b971-158">TripleDesSha256</span></span>|<span data-ttu-id="7b971-159">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="7b971-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="7b971-161">Použití Aes128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7b971-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="7b971-163">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7b971-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="7b971-165">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="7b971-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="7b971-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="7b971-167">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="7b971-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b971-168">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b971-168">Child Elements</span></span>  
  
|<span data-ttu-id="7b971-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b971-169">Element</span></span>|<span data-ttu-id="7b971-170">Popis</span><span class="sxs-lookup"><span data-stu-id="7b971-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b971-171">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="7b971-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="7b971-172">Určuje kolekci typů deklarací identity pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="7b971-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="7b971-173">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="7b971-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="7b971-174">\<issuer></span><span class="sxs-lookup"><span data-stu-id="7b971-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="7b971-175">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b971-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="7b971-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="7b971-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="7b971-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="7b971-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="7b971-178">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="7b971-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="7b971-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="7b971-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="7b971-180">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="7b971-180">A collection of token request parameters.</span></span> <span data-ttu-id="7b971-181">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="7b971-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b971-182">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b971-182">Parent Elements</span></span>  
  
|<span data-ttu-id="7b971-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b971-183">Element</span></span>|<span data-ttu-id="7b971-184">Popis</span><span class="sxs-lookup"><span data-stu-id="7b971-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b971-185">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="7b971-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="7b971-186">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7b971-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b971-187">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b971-187">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement` 
- [<span data-ttu-id="7b971-188">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7b971-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7b971-189">Vazby</span><span class="sxs-lookup"><span data-stu-id="7b971-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="7b971-190">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7b971-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7b971-191">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7b971-191">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="7b971-192">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="7b971-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
