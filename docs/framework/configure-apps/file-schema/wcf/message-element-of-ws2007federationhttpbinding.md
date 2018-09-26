---
title: Element &lt;message&gt; – &lt;ws2007FederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 3f0dbc3128af812c7fd09eed5acd90ab43ec8351
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47207254"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="efba3-102">Element &lt;message&gt; – &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="efba3-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="efba3-103">Definuje nastavení pro zprávy úroveň zabezpečení pro [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="efba3-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="efba3-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="efba3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="efba3-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="efba3-105">\<bindings></span></span>  
<span data-ttu-id="efba3-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="efba3-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="efba3-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="efba3-107">\<binding></span></span>  
<span data-ttu-id="efba3-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="efba3-108">\<security></span></span>  
<span data-ttu-id="efba3-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="efba3-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efba3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efba3-110">Syntax</span></span>  
  
```xml  
<ws2007FederationBinding>  
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
</ws2007FederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efba3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="efba3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="efba3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="efba3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efba3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="efba3-113">Attributes</span></span>  
  
|<span data-ttu-id="efba3-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="efba3-114">Attribute</span></span>|<span data-ttu-id="efba3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="efba3-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="efba3-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="efba3-116">Optional.</span></span> <span data-ttu-id="efba3-117">Nastaví šifrování zpráv, podpisu a key-wrap algoritmy.</span><span class="sxs-lookup"><span data-stu-id="efba3-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="efba3-118">Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy.</span><span class="sxs-lookup"><span data-stu-id="efba3-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="efba3-119">Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="efba3-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="efba3-120">Najdete v následující tabulce možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="efba3-120">See the following table for possible values.</span></span> <span data-ttu-id="efba3-121">Výchozí hodnota je Basic256.</span><span class="sxs-lookup"><span data-stu-id="efba3-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="efba3-122">Určuje typ klíče vystavování.</span><span class="sxs-lookup"><span data-stu-id="efba3-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="efba3-123">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="efba3-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="efba3-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="efba3-124">-   SymmetricKey</span></span><br /><span data-ttu-id="efba3-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="efba3-125">-   PublicKey</span></span><br /><span data-ttu-id="efba3-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="efba3-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="efba3-127">Výchozí hodnota je SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="efba3-127">The default is SymmetricKey.</span></span> <span data-ttu-id="efba3-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="efba3-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="efba3-129">Identifikátor URI, který určuje typ tokenu je nutno spustit.</span><span class="sxs-lookup"><span data-stu-id="efba3-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="efba3-130">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="efba3-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="efba3-131">Hodnota, která určuje, zda by měl být vyměňují v rámci vyjednávání přihlašovacích údajů služby, nebo je k dispozici mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="efba3-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="efba3-132">Výchozí hodnota je `true`, což znamená, že se vyjedná přihlašovacích údajů pro služby.</span><span class="sxs-lookup"><span data-stu-id="efba3-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="efba3-133">algorithmSuite atribut</span><span class="sxs-lookup"><span data-stu-id="efba3-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="efba3-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="efba3-134">Value</span></span>|<span data-ttu-id="efba3-135">Popis</span><span class="sxs-lookup"><span data-stu-id="efba3-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="efba3-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="efba3-136">Basic128</span></span>|<span data-ttu-id="efba3-137">Zabalení klíče použijte Aes128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.</span><span class="sxs-lookup"><span data-stu-id="efba3-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="efba3-138">Basic192</span></span>|<span data-ttu-id="efba3-139">Použijte šifrování Aes192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="efba3-140">Basic256</span></span>|<span data-ttu-id="efba3-141">Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-142">Basic256Rsa15</span></span>|<span data-ttu-id="efba3-143">Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="efba3-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-144">Basic192Rsa15</span></span>|<span data-ttu-id="efba3-145">Použití Aes192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="efba3-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="efba3-146">TripleDes</span></span>|<span data-ttu-id="efba3-147">Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-148">Basic128Rsa15</span></span>|<span data-ttu-id="efba3-149">Použití Aes128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="efba3-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-150">TripleDesRsa15</span></span>|<span data-ttu-id="efba3-151">Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="efba3-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="efba3-152">Basic128Sha256</span></span>|<span data-ttu-id="efba3-153">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="efba3-154">Basic192Sha256</span></span>|<span data-ttu-id="efba3-155">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="efba3-156">Basic256Sha256</span></span>|<span data-ttu-id="efba3-157">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="efba3-158">TripleDesSha256</span></span>|<span data-ttu-id="efba3-159">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="efba3-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="efba3-161">Použití Aes128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="efba3-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="efba3-163">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="efba3-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="efba3-165">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="efba3-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="efba3-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="efba3-167">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="efba3-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efba3-168">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="efba3-168">Child Elements</span></span>  
  
|<span data-ttu-id="efba3-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="efba3-169">Element</span></span>|<span data-ttu-id="efba3-170">Popis</span><span class="sxs-lookup"><span data-stu-id="efba3-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efba3-171">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="efba3-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="efba3-172">Určuje kolekci typů deklarací identity pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="efba3-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="efba3-173">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="efba3-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="efba3-174">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="efba3-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="efba3-175">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="efba3-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="efba3-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="efba3-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="efba3-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="efba3-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="efba3-178">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="efba3-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="efba3-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="efba3-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="efba3-180">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="efba3-180">A collection of token request parameters.</span></span> <span data-ttu-id="efba3-181">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="efba3-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="efba3-182">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="efba3-182">Parent Elements</span></span>  
  
|<span data-ttu-id="efba3-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="efba3-183">Element</span></span>|<span data-ttu-id="efba3-184">Popis</span><span class="sxs-lookup"><span data-stu-id="efba3-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efba3-185">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="efba3-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="efba3-186">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="efba3-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efba3-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="efba3-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="efba3-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="efba3-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="efba3-189">Vazby</span><span class="sxs-lookup"><span data-stu-id="efba3-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="efba3-190">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="efba3-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="efba3-191">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="efba3-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="efba3-192">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="efba3-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
