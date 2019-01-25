---
title: Element &lt;message&gt; – &lt;wsFederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 9614d973319e962655fd5e9c76f8703dab85c009
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740824"
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="2bc9c-102">Element &lt;message&gt; – &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="2bc9c-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="2bc9c-103">Definuje nastavení založená na úrovni zpráv zabezpečení pro [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2bc9c-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="2bc9c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2bc9c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2bc9c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="2bc9c-105">\<bindings></span></span>  
<span data-ttu-id="2bc9c-106">\<wsFederatedBinding></span><span class="sxs-lookup"><span data-stu-id="2bc9c-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="2bc9c-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2bc9c-107">\<binding></span></span>  
<span data-ttu-id="2bc9c-108">\<security></span><span class="sxs-lookup"><span data-stu-id="2bc9c-108">\<security></span></span>  
<span data-ttu-id="2bc9c-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="2bc9c-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc9c-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bc9c-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2bc9c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2bc9c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2bc9c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2bc9c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="2bc9c-113">Attributes</span></span>  
  
|<span data-ttu-id="2bc9c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="2bc9c-114">Attribute</span></span>|<span data-ttu-id="2bc9c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2bc9c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2bc9c-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="2bc9c-116">algorithmSuite</span></span>|<span data-ttu-id="2bc9c-117">Nastaví zprávu algoritmy šifrování a klíč zalamování řádků.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="2bc9c-118">V tabulce "algorithmSuite atribut" platné hodnoty tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="2bc9c-119">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="2bc9c-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="2bc9c-121">Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="2bc9c-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="2bc9c-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="2bc9c-122">issuedKeyType</span></span>|<span data-ttu-id="2bc9c-123">Určuje typ klíče vystavování.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="2bc9c-124">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="2bc9c-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2bc9c-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="2bc9c-125">-   SymmetricKey</span></span><br /><span data-ttu-id="2bc9c-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="2bc9c-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="2bc9c-127">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="2bc9c-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="2bc9c-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="2bc9c-129">issuedTokenType</span></span>|<span data-ttu-id="2bc9c-130">Řetězec, který obsahuje identifikátor URI, který určuje typ tokenu je nutno spustit.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="2bc9c-131">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-131">The default is `null`.</span></span>|  
|<span data-ttu-id="2bc9c-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="2bc9c-132">negotiateServiceCredential</span></span>|<span data-ttu-id="2bc9c-133">Logická hodnota určující, zda by měl být vyměňují v rámci vyjednávání přihlašovacích údajů služby, nebo je k dispozici mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="2bc9c-134">Výchozí hodnota je `true`, což znamená, že se vyjedná přihlašovacích údajů pro služby.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="2bc9c-135">algorithmSuite atribut</span><span class="sxs-lookup"><span data-stu-id="2bc9c-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="2bc9c-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2bc9c-136">Value</span></span>|<span data-ttu-id="2bc9c-137">Popis</span><span class="sxs-lookup"><span data-stu-id="2bc9c-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2bc9c-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="2bc9c-138">Basic128</span></span>|<span data-ttu-id="2bc9c-139">Zabalení klíče použijte Basic128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="2bc9c-140">Basic192</span></span>|<span data-ttu-id="2bc9c-141">Použijte šifrování Basic192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="2bc9c-142">Basic256</span></span>|<span data-ttu-id="2bc9c-143">Použijte šifrování Basic256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-144">Basic256Rsa15</span></span>|<span data-ttu-id="2bc9c-145">Použití Basic256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-146">Basic192Rsa15</span></span>|<span data-ttu-id="2bc9c-147">Použití Basic192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="2bc9c-148">TripleDes</span></span>|<span data-ttu-id="2bc9c-149">Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-150">Basic128Rsa15</span></span>|<span data-ttu-id="2bc9c-151">Použití Basic128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-152">TripleDesRsa15</span></span>|<span data-ttu-id="2bc9c-153">Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="2bc9c-154">Basic128Sha256</span></span>|<span data-ttu-id="2bc9c-155">Použití Basic128 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="2bc9c-156">Basic192Sha256</span></span>|<span data-ttu-id="2bc9c-157">Použití Basic192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="2bc9c-158">Basic256Sha256</span></span>|<span data-ttu-id="2bc9c-159">Použití Basic256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="2bc9c-160">TripleDesSha256</span></span>|<span data-ttu-id="2bc9c-161">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="2bc9c-163">Použití Basic128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="2bc9c-165">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="2bc9c-167">Použití Basic256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="2bc9c-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="2bc9c-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="2bc9c-169">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2bc9c-170">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2bc9c-170">Child Elements</span></span>  
  
|<span data-ttu-id="2bc9c-171">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bc9c-171">Element</span></span>|<span data-ttu-id="2bc9c-172">Popis</span><span class="sxs-lookup"><span data-stu-id="2bc9c-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bc9c-173">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="2bc9c-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="2bc9c-174">Určuje kolekci typů deklarací identity pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="2bc9c-175">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="2bc9c-176">issuer</span><span class="sxs-lookup"><span data-stu-id="2bc9c-176">issuer</span></span>|<span data-ttu-id="2bc9c-177">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="2bc9c-178">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="2bc9c-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="2bc9c-179">issuerMetadata</span></span>|<span data-ttu-id="2bc9c-180">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="2bc9c-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="2bc9c-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="2bc9c-182">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-182">A collection of token request parameters.</span></span> <span data-ttu-id="2bc9c-183">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2bc9c-184">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2bc9c-184">Parent Elements</span></span>  
  
|<span data-ttu-id="2bc9c-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="2bc9c-185">Element</span></span>|<span data-ttu-id="2bc9c-186">Popis</span><span class="sxs-lookup"><span data-stu-id="2bc9c-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2bc9c-187">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="2bc9c-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="2bc9c-188">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="2bc9c-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bc9c-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2bc9c-189">See also</span></span>
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
 `System.ServiceModel.Configuration.FederatedMessageSecurityElement`
- [<span data-ttu-id="2bc9c-190">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2bc9c-190">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2bc9c-191">Vazby</span><span class="sxs-lookup"><span data-stu-id="2bc9c-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="2bc9c-192">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2bc9c-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2bc9c-193">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2bc9c-193">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2bc9c-194">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="2bc9c-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
