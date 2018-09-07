---
title: Element &lt;message&gt; – &lt;ws2007FederationHttpBinding&gt;
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: 3f0dbc3128af812c7fd09eed5acd90ab43ec8351
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063479"
---
# <a name="ltmessagegt-element-of-ltws2007federationhttpbindinggt"></a><span data-ttu-id="49714-102">Element &lt;message&gt; – &lt;ws2007FederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="49714-102">&lt;message&gt; element of &lt;ws2007FederationHttpBinding&gt;</span></span>
<span data-ttu-id="49714-103">Definuje nastavení pro zprávy úroveň zabezpečení pro [ \<ws2007FederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="49714-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) element.</span></span>  
  
 <span data-ttu-id="49714-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="49714-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="49714-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="49714-105">\<bindings></span></span>  
<span data-ttu-id="49714-106">\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="49714-106">\<ws2007FederationHttpBinding></span></span>  
<span data-ttu-id="49714-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="49714-107">\<binding></span></span>  
<span data-ttu-id="49714-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="49714-108">\<security></span></span>  
<span data-ttu-id="49714-109">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="49714-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49714-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49714-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49714-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="49714-111">Attributes and Elements</span></span>  
 <span data-ttu-id="49714-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="49714-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49714-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="49714-113">Attributes</span></span>  
  
|<span data-ttu-id="49714-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="49714-114">Attribute</span></span>|<span data-ttu-id="49714-115">Popis</span><span class="sxs-lookup"><span data-stu-id="49714-115">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="49714-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="49714-116">Optional.</span></span> <span data-ttu-id="49714-117">Nastaví šifrování zpráv, podpisu a key-wrap algoritmy.</span><span class="sxs-lookup"><span data-stu-id="49714-117">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="49714-118">Algoritmy a velikosti klíče jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídy.</span><span class="sxs-lookup"><span data-stu-id="49714-118">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="49714-119">Tyto algoritmy namapovat na uvedené ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="49714-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="49714-120">Najdete v následující tabulce možných hodnot.</span><span class="sxs-lookup"><span data-stu-id="49714-120">See the following table for possible values.</span></span> <span data-ttu-id="49714-121">Výchozí hodnota je Basic256.</span><span class="sxs-lookup"><span data-stu-id="49714-121">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="49714-122">Určuje typ klíče vystavování.</span><span class="sxs-lookup"><span data-stu-id="49714-122">Specifies the type of key to be issued.</span></span> <span data-ttu-id="49714-123">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="49714-123">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="49714-124">-SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="49714-124">-   SymmetricKey</span></span><br /><span data-ttu-id="49714-125">-PublicKey</span><span class="sxs-lookup"><span data-stu-id="49714-125">-   PublicKey</span></span><br /><span data-ttu-id="49714-126">-BearerKey</span><span class="sxs-lookup"><span data-stu-id="49714-126">-   BearerKey</span></span><br /><br /> <span data-ttu-id="49714-127">Výchozí hodnota je SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="49714-127">The default is SymmetricKey.</span></span> <span data-ttu-id="49714-128">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span><span class="sxs-lookup"><span data-stu-id="49714-128">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="49714-129">Identifikátor URI, který určuje typ tokenu je nutno spustit.</span><span class="sxs-lookup"><span data-stu-id="49714-129">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="49714-130">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="49714-130">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="49714-131">Hodnota, která určuje, zda by měl být vyměňují v rámci vyjednávání přihlašovacích údajů služby, nebo je k dispozici mimo pásmo.</span><span class="sxs-lookup"><span data-stu-id="49714-131">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="49714-132">Výchozí hodnota je `true`, což znamená, že se vyjedná přihlašovacích údajů pro služby.</span><span class="sxs-lookup"><span data-stu-id="49714-132">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="49714-133">algorithmSuite atribut</span><span class="sxs-lookup"><span data-stu-id="49714-133">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="49714-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="49714-134">Value</span></span>|<span data-ttu-id="49714-135">Popis</span><span class="sxs-lookup"><span data-stu-id="49714-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="49714-136">Basic128</span><span class="sxs-lookup"><span data-stu-id="49714-136">Basic128</span></span>|<span data-ttu-id="49714-137">Zabalení klíče použijte Aes128 šifrování, algoritmus pro hash Sha1 a Rsa. oaep mgf1p.</span><span class="sxs-lookup"><span data-stu-id="49714-137">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-138">Basic192</span><span class="sxs-lookup"><span data-stu-id="49714-138">Basic192</span></span>|<span data-ttu-id="49714-139">Použijte šifrování Aes192, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-139">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-140">Basic256</span><span class="sxs-lookup"><span data-stu-id="49714-140">Basic256</span></span>|<span data-ttu-id="49714-141">Použijte šifrování pomocí Aes256, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-141">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-142">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="49714-142">Basic256Rsa15</span></span>|<span data-ttu-id="49714-143">Pomocí Aes256 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-143">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="49714-144">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="49714-144">Basic192Rsa15</span></span>|<span data-ttu-id="49714-145">Použití Aes192 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-145">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="49714-146">TripleDes</span><span class="sxs-lookup"><span data-stu-id="49714-146">TripleDes</span></span>|<span data-ttu-id="49714-147">Použití šifrování TripleDes, Sha1 pro hodnotu hash, oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-147">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-148">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="49714-148">Basic128Rsa15</span></span>|<span data-ttu-id="49714-149">Použití Aes128 pro šifrování zpráv, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-149">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="49714-150">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="49714-150">TripleDesRsa15</span></span>|<span data-ttu-id="49714-151">Použití šifrování TripleDes, Sha1 pro hodnotu hash a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-151">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="49714-152">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="49714-152">Basic128Sha256</span></span>|<span data-ttu-id="49714-153">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-153">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-154">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="49714-154">Basic192Sha256</span></span>|<span data-ttu-id="49714-155">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-155">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-156">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="49714-156">Basic256Sha256</span></span>|<span data-ttu-id="49714-157">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-157">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-158">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="49714-158">TripleDesSha256</span></span>|<span data-ttu-id="49714-159">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a oaep mgf1p Rsa pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-159">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="49714-160">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="49714-160">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="49714-161">Použití Aes128 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-161">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="49714-162">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="49714-162">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="49714-163">Použití Aes192 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-163">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="49714-164">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="49714-164">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="49714-165">Pomocí Aes256 pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-165">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="49714-166">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="49714-166">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="49714-167">TripleDes použijte pro šifrování zpráv pro hodnota hash Sha256 a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="49714-167">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49714-168">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="49714-168">Child Elements</span></span>  
  
|<span data-ttu-id="49714-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="49714-169">Element</span></span>|<span data-ttu-id="49714-170">Popis</span><span class="sxs-lookup"><span data-stu-id="49714-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49714-171">\<claimTypeRequirements ></span><span class="sxs-lookup"><span data-stu-id="49714-171">\<claimTypeRequirements></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-element.md)|<span data-ttu-id="49714-172">Určuje kolekci typů deklarací identity pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="49714-172">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="49714-173">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span><span class="sxs-lookup"><span data-stu-id="49714-173">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[<span data-ttu-id="49714-174">\<Issuer ></span><span class="sxs-lookup"><span data-stu-id="49714-174">\<issuer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuer.md)|<span data-ttu-id="49714-175">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="49714-175">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="49714-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span><span class="sxs-lookup"><span data-stu-id="49714-176">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[<span data-ttu-id="49714-177">\<issuerMetadata></span><span class="sxs-lookup"><span data-stu-id="49714-177">\<issuerMetadata></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuermetadata.md)|<span data-ttu-id="49714-178">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="49714-178">Specifies the endpoint address of the issuer.</span></span>|  
|[<span data-ttu-id="49714-179">\<tokenRequestParameters></span><span class="sxs-lookup"><span data-stu-id="49714-179">\<tokenRequestParameters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tokenrequestparameters.md)|<span data-ttu-id="49714-180">Kolekce parametrů žádosti o token.</span><span class="sxs-lookup"><span data-stu-id="49714-180">A collection of token request parameters.</span></span> <span data-ttu-id="49714-181">Každý parametr je platný element XML.</span><span class="sxs-lookup"><span data-stu-id="49714-181">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49714-182">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="49714-182">Parent Elements</span></span>  
  
|<span data-ttu-id="49714-183">Prvek</span><span class="sxs-lookup"><span data-stu-id="49714-183">Element</span></span>|<span data-ttu-id="49714-184">Popis</span><span class="sxs-lookup"><span data-stu-id="49714-184">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49714-185">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="49714-185">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="49714-186">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="49714-186">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49714-187">Viz také</span><span class="sxs-lookup"><span data-stu-id="49714-187">See Also</span></span>  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>  
 <span data-ttu-id="49714-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span><span class="sxs-lookup"><span data-stu-id="49714-188">`System.ServiceModel.Configuration.FederatedMessageSecurityElement` [Securing Services and Clients](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)</span></span>  
 [<span data-ttu-id="49714-189">Vazby</span><span class="sxs-lookup"><span data-stu-id="49714-189">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="49714-190">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="49714-190">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="49714-191">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="49714-191">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="49714-192">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="49714-192">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
