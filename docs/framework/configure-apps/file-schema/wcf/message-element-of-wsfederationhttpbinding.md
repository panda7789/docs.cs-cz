---
title: Element &lt;message&gt; – &lt;wsFederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 820ee7015a51ecc5510889516faef20292cfbc07
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184712"
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="0a75a-102">Element &lt;message&gt; – &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="0a75a-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="0a75a-103">Definuje nastavení založená na úrovni zpráv zabezpečení pro [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0a75a-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="0a75a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0a75a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0a75a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0a75a-105">\<bindings></span></span>  
<span data-ttu-id="0a75a-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="0a75a-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="0a75a-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0a75a-107">\<binding></span></span>  
<span data-ttu-id="0a75a-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="0a75a-108">\<security></span></span>  
<span data-ttu-id="0a75a-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="0a75a-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a75a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a75a-110">Syntax</span></span>  
  
```xml  
<wsFederationBinding>  
     <binding >  
         <security>  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
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
                              <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a75a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a75a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0a75a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0a75a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a75a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a75a-113">Attributes</span></span>  
  
|<span data-ttu-id="0a75a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a75a-114">Attribute</span></span>|<span data-ttu-id="0a75a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0a75a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a75a-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="0a75a-116">algorithmSuite</span></span>|<span data-ttu-id="0a75a-117">Nastaví zprávu algoritmy šifrování a klíč zalamování řádků.</span><span class="sxs-lookup"><span data-stu-id="0a75a-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="0a75a-118">V tabulce "algorithmSuite atribut" platné hodnoty tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="0a75a-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="0a75a-119">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="0a75a-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="0a75a-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="0a75a-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="0a75a-121">Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="0a75a-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="0a75a-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="0a75a-122">issuedKeyType</span></span>|<span data-ttu-id="0a75a-123">Určuje typ klíče vystavování.</span><span class="sxs-lookup"><span data-stu-id="0a75a-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="0a75a-124">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="0a75a-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0a75a-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="0a75a-125">-   SymmetricKey</span></span><br /><span data-ttu-id="0a75a-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="0a75a-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="0a75a-127">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="0a75a-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="0a75a-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="0a75a-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="0a75a-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="0a75a-129">issuedTokenType</span></span>|<span data-ttu-id="0a75a-130">Řetězec, který obsahuje identifikátor URI, který určuje typ tokenu je nutno spustit.</span><span class="sxs-lookup"><span data-stu-id="0a75a-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="0a75a-131">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="0a75a-131">The default is `null`.</span></span>|  
|<span data-ttu-id="0a75a-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="0a75a-132">negotiateServiceCredential</span></span>|<span data-ttu-id="0a75a-133">Logická hodnota určující, zda by měl být vyměňují v rámci vyjednávání přihlašovacích údajů služby, nebo je k dispozici mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="0a75a-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="0a75a-134">Výchozí hodnota je `true`, což znamená, že se vyjedná přihlašovacích údajů pro služby.</span><span class="sxs-lookup"><span data-stu-id="0a75a-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="0a75a-135">algorithmSuite atribut</span><span class="sxs-lookup"><span data-stu-id="0a75a-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="0a75a-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0a75a-136">Value</span></span>|<span data-ttu-id="0a75a-137">Popis</span><span class="sxs-lookup"><span data-stu-id="0a75a-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a75a-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="0a75a-138">Basic128</span></span>|<span data-ttu-id="0a75a-139">Zabalení klíče použijte Basic128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.</span><span class="sxs-lookup"><span data-stu-id="0a75a-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="0a75a-140">Basic192</span></span>|<span data-ttu-id="0a75a-141">Použijte šifrování Basic192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="0a75a-142">Basic256</span></span>|<span data-ttu-id="0a75a-143">Použijte šifrování Basic256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-144">Basic256Rsa15</span></span>|<span data-ttu-id="0a75a-145">Použití Basic256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-146">Basic192Rsa15</span></span>|<span data-ttu-id="0a75a-147">Použití Basic192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="0a75a-148">TripleDes</span></span>|<span data-ttu-id="0a75a-149">Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-150">Basic128Rsa15</span></span>|<span data-ttu-id="0a75a-151">Použití Basic128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-152">TripleDesRsa15</span></span>|<span data-ttu-id="0a75a-153">Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="0a75a-154">Basic128Sha256</span></span>|<span data-ttu-id="0a75a-155">Použití Basic128 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="0a75a-156">Basic192Sha256</span></span>|<span data-ttu-id="0a75a-157">Použití Basic192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="0a75a-158">Basic256Sha256</span></span>|<span data-ttu-id="0a75a-159">Použití Basic256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="0a75a-160">TripleDesSha256</span></span>|<span data-ttu-id="0a75a-161">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="0a75a-163">Použití Basic128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="0a75a-165">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="0a75a-167">Použití Basic256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="0a75a-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="0a75a-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="0a75a-169">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="0a75a-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a75a-170">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a75a-170">Child Elements</span></span>  
  
|<span data-ttu-id="0a75a-171">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a75a-171">Element</span></span>|<span data-ttu-id="0a75a-172">Popis</span><span class="sxs-lookup"><span data-stu-id="0a75a-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a75a-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="0a75a-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="0a75a-174">Určuje kolekci typů deklarací identity pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="0a75a-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="0a75a-175">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="0a75a-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="0a75a-176">issuer</span><span class="sxs-lookup"><span data-stu-id="0a75a-176">issuer</span></span>|<span data-ttu-id="0a75a-177">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0a75a-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="0a75a-178">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="0a75a-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="0a75a-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="0a75a-179">issuerMetadata</span></span>|<span data-ttu-id="0a75a-180">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="0a75a-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="0a75a-181">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="0a75a-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="0a75a-182">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="0a75a-182">A collection of token request parameters.</span></span> <span data-ttu-id="0a75a-183">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="0a75a-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a75a-184">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a75a-184">Parent Elements</span></span>  
  
|<span data-ttu-id="0a75a-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a75a-185">Element</span></span>|<span data-ttu-id="0a75a-186">Popis</span><span class="sxs-lookup"><span data-stu-id="0a75a-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a75a-187">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="0a75a-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="0a75a-188">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="0a75a-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0a75a-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a75a-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="0a75a-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="0a75a-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="0a75a-191">Vazby</span><span class="sxs-lookup"><span data-stu-id="0a75a-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0a75a-192">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="0a75a-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0a75a-193">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="0a75a-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="0a75a-194">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0a75a-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
