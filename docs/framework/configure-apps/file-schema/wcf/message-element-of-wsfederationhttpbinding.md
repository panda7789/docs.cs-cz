---
title: <message>prvek elementu<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: e26e1f94fb38e0654fd0bc9f06c6096a488bccfe
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400283"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="1f2cd-102">\<> prvku \<zprávy > WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1f2cd-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="1f2cd-103">Definuje nastavení pro zabezpečení [ \<](wsfederationhttpbinding.md)na úrovni zpráv > WSFederationHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
<span data-ttu-id="1f2cd-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1f2cd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1f2cd-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1f2cd-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1f2cd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="1f2cd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="1f2cd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsFederationHttpBinding >** ](wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1f2cd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1f2cd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="1f2cd-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="1f2cd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1f2cd-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)</span></span>\
<span data-ttu-id="1f2cd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zprávy**</span><span class="sxs-lookup"><span data-stu-id="1f2cd-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f2cd-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f2cd-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f2cd-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1f2cd-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1f2cd-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f2cd-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="1f2cd-114">Attributes</span></span>  
  
|<span data-ttu-id="1f2cd-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="1f2cd-115">Attribute</span></span>|<span data-ttu-id="1f2cd-116">Popis</span><span class="sxs-lookup"><span data-stu-id="1f2cd-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f2cd-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="1f2cd-117">algorithmSuite</span></span>|<span data-ttu-id="1f2cd-118">Nastaví šifrování zpráv a algoritmy pro zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="1f2cd-119">Platné hodnoty tohoto atributu najdete v tabulce atributu algorithmSuite.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-119">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="1f2cd-120">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-120">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="1f2cd-121">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-121">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="1f2cd-122">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="1f2cd-122">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="1f2cd-123">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="1f2cd-123">issuedKeyType</span></span>|<span data-ttu-id="1f2cd-124">Určuje typ klíče, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-124">Specifies the type of key to be issued.</span></span> <span data-ttu-id="1f2cd-125">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="1f2cd-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1f2cd-126">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="1f2cd-126">-   SymmetricKey</span></span><br /><span data-ttu-id="1f2cd-127">– PublicKey</span><span class="sxs-lookup"><span data-stu-id="1f2cd-127">-   PublicKey</span></span><br /><br /> <span data-ttu-id="1f2cd-128">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-128">The default is `SymmetricKey`.</span></span> <span data-ttu-id="1f2cd-129">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-129">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="1f2cd-130">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="1f2cd-130">issuedTokenType</span></span>|<span data-ttu-id="1f2cd-131">Řetězec obsahující identifikátor URI, který určuje typ tokenu, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-131">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="1f2cd-132">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-132">The default is `null`.</span></span>|  
|<span data-ttu-id="1f2cd-133">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="1f2cd-133">negotiateServiceCredential</span></span>|<span data-ttu-id="1f2cd-134">Logická hodnota určující, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-134">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="1f2cd-135">Výchozí hodnota je `true`, což znamená, že se pověření služby vyjednávat.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-135">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="1f2cd-136">algorithmSuite – atribut</span><span class="sxs-lookup"><span data-stu-id="1f2cd-136">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="1f2cd-137">Value</span><span class="sxs-lookup"><span data-stu-id="1f2cd-137">Value</span></span>|<span data-ttu-id="1f2cd-138">Popis</span><span class="sxs-lookup"><span data-stu-id="1f2cd-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1f2cd-139">Basic128</span><span class="sxs-lookup"><span data-stu-id="1f2cd-139">Basic128</span></span>|<span data-ttu-id="1f2cd-140">Pro zabalení klíče použijte šifrování Basic128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-140">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-141">Basic192</span><span class="sxs-lookup"><span data-stu-id="1f2cd-141">Basic192</span></span>|<span data-ttu-id="1f2cd-142">Pro zabalení klíče použijte šifrování Basic192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-142">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-143">Basic256</span><span class="sxs-lookup"><span data-stu-id="1f2cd-143">Basic256</span></span>|<span data-ttu-id="1f2cd-144">Pro zabalení klíče použijte šifrování Basic256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-144">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-145">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-145">Basic256Rsa15</span></span>|<span data-ttu-id="1f2cd-146">Použijte Basic256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-146">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-147">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-147">Basic192Rsa15</span></span>|<span data-ttu-id="1f2cd-148">Použijte Basic192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-148">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-149">TripleDes</span><span class="sxs-lookup"><span data-stu-id="1f2cd-149">TripleDes</span></span>|<span data-ttu-id="1f2cd-150">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-150">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-151">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-151">Basic128Rsa15</span></span>|<span data-ttu-id="1f2cd-152">Použijte Basic128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-152">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-153">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-153">TripleDesRsa15</span></span>|<span data-ttu-id="1f2cd-154">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-154">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-155">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="1f2cd-155">Basic128Sha256</span></span>|<span data-ttu-id="1f2cd-156">Pro zabalení klíče použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-156">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-157">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="1f2cd-157">Basic192Sha256</span></span>|<span data-ttu-id="1f2cd-158">Pro zabalení klíče použijte Basic192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-158">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-159">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="1f2cd-159">Basic256Sha256</span></span>|<span data-ttu-id="1f2cd-160">Pro zabalení klíče použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-160">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-161">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="1f2cd-161">TripleDesSha256</span></span>|<span data-ttu-id="1f2cd-162">Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-162">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-163">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-163">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="1f2cd-164">Použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-164">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-165">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-165">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="1f2cd-166">Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-166">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-167">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-167">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="1f2cd-168">Použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-168">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="1f2cd-169">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="1f2cd-169">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="1f2cd-170">Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-170">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f2cd-171">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1f2cd-171">Child Elements</span></span>  
  
|<span data-ttu-id="1f2cd-172">Prvek</span><span class="sxs-lookup"><span data-stu-id="1f2cd-172">Element</span></span>|<span data-ttu-id="1f2cd-173">Popis</span><span class="sxs-lookup"><span data-stu-id="1f2cd-173">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f2cd-174">\<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="1f2cd-174">\<claimTypeRequirements></span></span>](claimtyperequirements-element.md)|<span data-ttu-id="1f2cd-175">Určuje kolekci typů deklarací pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-175">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="1f2cd-176">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-176">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="1f2cd-177">issuer</span><span class="sxs-lookup"><span data-stu-id="1f2cd-177">issuer</span></span>|<span data-ttu-id="1f2cd-178">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-178">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="1f2cd-179">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-179">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="1f2cd-180">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="1f2cd-180">issuerMetadata</span></span>|<span data-ttu-id="1f2cd-181">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-181">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="1f2cd-182">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="1f2cd-182">\<tokenRequestParameters></span></span>](tokenrequestparameters.md)|<span data-ttu-id="1f2cd-183">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="1f2cd-183">A collection of token request parameters.</span></span> <span data-ttu-id="1f2cd-184">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-184">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f2cd-185">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1f2cd-185">Parent Elements</span></span>  
  
|<span data-ttu-id="1f2cd-186">Prvek</span><span class="sxs-lookup"><span data-stu-id="1f2cd-186">Element</span></span>|<span data-ttu-id="1f2cd-187">Popis</span><span class="sxs-lookup"><span data-stu-id="1f2cd-187">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f2cd-188">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1f2cd-188">\<security></span></span>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="1f2cd-189">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="1f2cd-189">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f2cd-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f2cd-190">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="1f2cd-191">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1f2cd-191">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1f2cd-192">Vazby</span><span class="sxs-lookup"><span data-stu-id="1f2cd-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1f2cd-193">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="1f2cd-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1f2cd-194">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1f2cd-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1f2cd-195">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1f2cd-195">\<binding></span></span>](../../../misc/binding.md)
