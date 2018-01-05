---
title: "Element &lt;message&gt; – &lt;wsFederationHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09e384311f50553585c0a7a14a51df20858fb439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltmessagegt-element-of-ltwsfederationhttpbindinggt"></a><span data-ttu-id="66824-102">Element &lt;message&gt; – &lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="66824-102">&lt;message&gt; element of &lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="66824-103">Definuje nastavení pro zprávy úroveň zabezpečení [ \<– wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="66824-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).</span></span>  
  
 <span data-ttu-id="66824-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="66824-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="66824-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="66824-105">\<bindings></span></span>  
<span data-ttu-id="66824-106">\<wsFederatedBinding ></span><span class="sxs-lookup"><span data-stu-id="66824-106">\<wsFederatedBinding></span></span>  
<span data-ttu-id="66824-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="66824-107">\<binding></span></span>  
<span data-ttu-id="66824-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="66824-108">\<security></span></span>  
<span data-ttu-id="66824-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="66824-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66824-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66824-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66824-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="66824-111">Attributes and Elements</span></span>  
 <span data-ttu-id="66824-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="66824-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66824-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="66824-113">Attributes</span></span>  
  
|<span data-ttu-id="66824-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="66824-114">Attribute</span></span>|<span data-ttu-id="66824-115">Popis</span><span class="sxs-lookup"><span data-stu-id="66824-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="66824-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="66824-116">algorithmSuite</span></span>|<span data-ttu-id="66824-117">Nastaví zprávu algoritmy šifrování a klíč wrap.</span><span class="sxs-lookup"><span data-stu-id="66824-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="66824-118">Najdete v tabulce "algorithmSuite atribut" platné hodnoty tohoto atributu.</span><span class="sxs-lookup"><span data-stu-id="66824-118">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="66824-119">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="66824-119">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="66824-120">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span><span class="sxs-lookup"><span data-stu-id="66824-120">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="66824-121">Tyto algoritmy mapovat platformám zadaným v specifikace jazyka zásady zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="66824-121">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="66824-122">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="66824-122">issuedKeyType</span></span>|<span data-ttu-id="66824-123">Určuje typ klíče pro vystavování.</span><span class="sxs-lookup"><span data-stu-id="66824-123">Specifies the type of key to be issued.</span></span> <span data-ttu-id="66824-124">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="66824-124">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="66824-125">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="66824-125">-   SymmetricKey</span></span><br /><span data-ttu-id="66824-126">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="66824-126">-   PublicKey</span></span><br /><br /> <span data-ttu-id="66824-127">Výchozí hodnota je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="66824-127">The default is `SymmetricKey`.</span></span> <span data-ttu-id="66824-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="66824-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="66824-129">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="66824-129">issuedTokenType</span></span>|<span data-ttu-id="66824-130">Řetězec, který obsahuje identifikátor URI, který určuje typ token, který má být vystavené.</span><span class="sxs-lookup"><span data-stu-id="66824-130">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="66824-131">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="66824-131">The default is `null`.</span></span>|  
|<span data-ttu-id="66824-132">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="66824-132">negotiateServiceCredential</span></span>|<span data-ttu-id="66824-133">Logická hodnota, která určuje, zda přihlašovací údaje služby by měl být v rámci vyjednávání vyměňují nebo je k dispozici vzdálené správy.</span><span class="sxs-lookup"><span data-stu-id="66824-133">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="66824-134">Výchozí hodnota je `true`, což znamená, že je vyjednal přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="66824-134">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="66824-135">algorithmSuite atribut</span><span class="sxs-lookup"><span data-stu-id="66824-135">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="66824-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="66824-136">Value</span></span>|<span data-ttu-id="66824-137">Popis</span><span class="sxs-lookup"><span data-stu-id="66824-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="66824-138">Basic128</span><span class="sxs-lookup"><span data-stu-id="66824-138">Basic128</span></span>|<span data-ttu-id="66824-139">Použijte šifrování Basic128, Sha1 pro hodnota hash a šifrování Rsa. oaep mgf1p zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-139">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-140">Basic192</span><span class="sxs-lookup"><span data-stu-id="66824-140">Basic192</span></span>|<span data-ttu-id="66824-141">Použijte šifrování pomocí Basic192, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-141">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-142">Basic256</span><span class="sxs-lookup"><span data-stu-id="66824-142">Basic256</span></span>|<span data-ttu-id="66824-143">Použijte šifrování pomocí Basic256, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-143">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-144">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="66824-144">Basic256Rsa15</span></span>|<span data-ttu-id="66824-145">Použijte Basic256 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-145">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="66824-146">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="66824-146">Basic192Rsa15</span></span>|<span data-ttu-id="66824-147">Použijte Basic192 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-147">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="66824-148">TripleDes</span><span class="sxs-lookup"><span data-stu-id="66824-148">TripleDes</span></span>|<span data-ttu-id="66824-149">Použití šifrování TripleDes, Sha1 pro hodnotu hash zpráv, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-149">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-150">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="66824-150">Basic128Rsa15</span></span>|<span data-ttu-id="66824-151">Použijte Basic128 pro šifrování zpráv, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-151">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="66824-152">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="66824-152">TripleDesRsa15</span></span>|<span data-ttu-id="66824-153">Použití šifrování TripleDes, Sha1 pro hodnota hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-153">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="66824-154">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="66824-154">Basic128Sha256</span></span>|<span data-ttu-id="66824-155">Použijte Basic128 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-155">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-156">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="66824-156">Basic192Sha256</span></span>|<span data-ttu-id="66824-157">Použijte Basic192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-157">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-158">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="66824-158">Basic256Sha256</span></span>|<span data-ttu-id="66824-159">Použijte Basic256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-159">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-160">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="66824-160">TripleDesSha256</span></span>|<span data-ttu-id="66824-161">Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="66824-162">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="66824-162">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="66824-163">Použijte Basic128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-163">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="66824-164">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="66824-164">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="66824-165">Použijte Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-165">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="66824-166">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="66824-166">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="66824-167">Použijte Basic256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-167">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="66824-168">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="66824-168">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="66824-169">Použití šifrování TripleDes pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="66824-169">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="66824-170">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="66824-170">Child Elements</span></span>  
  
|<span data-ttu-id="66824-171">Prvek</span><span class="sxs-lookup"><span data-stu-id="66824-171">Element</span></span>|<span data-ttu-id="66824-172">Popis</span><span class="sxs-lookup"><span data-stu-id="66824-172">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66824-173">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="66824-173">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="66824-174">Určuje kolekci typů deklarací identity pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="66824-174">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="66824-175">Každý element je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="66824-175">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="66824-176">issuer</span><span class="sxs-lookup"><span data-stu-id="66824-176">issuer</span></span>|<span data-ttu-id="66824-177">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="66824-177">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="66824-178">Tento element je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="66824-178">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="66824-179">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="66824-179">issuerMetadata</span></span>|<span data-ttu-id="66824-180">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="66824-180">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="66824-181">\<tokenRequestParameters ></span><span class="sxs-lookup"><span data-stu-id="66824-181">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="66824-182">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="66824-182">A collection of token request parameters.</span></span> <span data-ttu-id="66824-183">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="66824-183">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66824-184">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="66824-184">Parent Elements</span></span>  
  
|<span data-ttu-id="66824-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="66824-185">Element</span></span>|<span data-ttu-id="66824-186">Popis</span><span class="sxs-lookup"><span data-stu-id="66824-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66824-187">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="66824-187">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="66824-188">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="66824-188">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66824-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="66824-189">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="66824-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement`[Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="66824-190">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="66824-191">Vazby</span><span class="sxs-lookup"><span data-stu-id="66824-191">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="66824-192">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="66824-192">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="66824-193">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="66824-193">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="66824-194">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="66824-194">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
