---
title: <message>prvek elementu<ws2007FederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 52cd941d-e230-4c82-8b29-333a7d20eca8
ms.openlocfilehash: dde763687dbc62d6fb342a21a4c614208f28d7e8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738994"
---
# <a name="message-element-of-ws2007federationhttpbinding"></a><span data-ttu-id="22b1b-102">\<message>prvek elementu\<ws2007FederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="22b1b-102">\<message> element of \<ws2007FederationHttpBinding></span></span>
<span data-ttu-id="22b1b-103">Definuje nastavení pro zabezpečení na úrovni zprávy pro [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="22b1b-103">Defines settings for the message-level security for the [\<ws2007FederationHttpBinding>](ws2007federationhttpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007FederationHttpBinding>**](ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-element-of-ws2007federationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="22b1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22b1b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22b1b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22b1b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="22b1b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22b1b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22b1b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="22b1b-107">Attributes</span></span>  
  
|<span data-ttu-id="22b1b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="22b1b-108">Attribute</span></span>|<span data-ttu-id="22b1b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="22b1b-109">Description</span></span>|  
|---------------|-----------------|  
|`algorithmSuite`|<span data-ttu-id="22b1b-110">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="22b1b-110">Optional.</span></span> <span data-ttu-id="22b1b-111">Nastaví algoritmy šifrování, podpisu a zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="22b1b-111">Sets the message encryption, signature, and key-wrap algorithms.</span></span> <span data-ttu-id="22b1b-112">Algoritmy a velikosti klíčů jsou určeny <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> třídou.</span><span class="sxs-lookup"><span data-stu-id="22b1b-112">The algorithms and the key sizes are determined by the <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> class.</span></span> <span data-ttu-id="22b1b-113">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="22b1b-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="22b1b-114">Možné hodnoty jsou uvedené v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="22b1b-114">See the following table for possible values.</span></span> <span data-ttu-id="22b1b-115">Výchozí hodnota je Basic256.</span><span class="sxs-lookup"><span data-stu-id="22b1b-115">The default value is Basic256.</span></span>|  
|`issuedKeyType`|<span data-ttu-id="22b1b-116">Určuje typ klíče, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="22b1b-116">Specifies the type of key to be issued.</span></span> <span data-ttu-id="22b1b-117">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="22b1b-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22b1b-118">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="22b1b-118">-   SymmetricKey</span></span><br /><span data-ttu-id="22b1b-119">– PublicKey</span><span class="sxs-lookup"><span data-stu-id="22b1b-119">-   PublicKey</span></span><br /><span data-ttu-id="22b1b-120">- BearerKey</span><span class="sxs-lookup"><span data-stu-id="22b1b-120">-   BearerKey</span></span><br /><br /> <span data-ttu-id="22b1b-121">Výchozí hodnota je SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="22b1b-121">The default is SymmetricKey.</span></span> <span data-ttu-id="22b1b-122">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="22b1b-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|`issuedTokenType`|<span data-ttu-id="22b1b-123">Identifikátor URI, který určuje typ tokenu, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="22b1b-123">A URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="22b1b-124">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="22b1b-124">The default is `null`.</span></span>|  
|`negotiateServiceCredential`|<span data-ttu-id="22b1b-125">Hodnota, která určuje, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="22b1b-125">A value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="22b1b-126">Výchozí hodnota je `true` , což znamená, že se pověření služby vyjednávat.</span><span class="sxs-lookup"><span data-stu-id="22b1b-126">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="22b1b-127">algorithmSuite – atribut</span><span class="sxs-lookup"><span data-stu-id="22b1b-127">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="22b1b-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="22b1b-128">Value</span></span>|<span data-ttu-id="22b1b-129">Description</span><span class="sxs-lookup"><span data-stu-id="22b1b-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="22b1b-130">Basic128</span><span class="sxs-lookup"><span data-stu-id="22b1b-130">Basic128</span></span>|<span data-ttu-id="22b1b-131">Pro zabalení klíče použijte šifrování Aes128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-131">Use Aes128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-132">Basic192</span><span class="sxs-lookup"><span data-stu-id="22b1b-132">Basic192</span></span>|<span data-ttu-id="22b1b-133">Pro zabalení klíče použijte šifrování Aes192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-133">Use Aes192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-134">Basic256</span><span class="sxs-lookup"><span data-stu-id="22b1b-134">Basic256</span></span>|<span data-ttu-id="22b1b-135">Pro zabalení klíče použijte šifrování AES256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-135">Use Aes256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-136">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-136">Basic256Rsa15</span></span>|<span data-ttu-id="22b1b-137">Použijte AES256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="22b1b-137">Use Aes256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-138">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-138">Basic192Rsa15</span></span>|<span data-ttu-id="22b1b-139">Použijte Aes192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="22b1b-139">Use Aes192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-140">TripleDes</span><span class="sxs-lookup"><span data-stu-id="22b1b-140">TripleDes</span></span>|<span data-ttu-id="22b1b-141">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-141">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-142">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-142">Basic128Rsa15</span></span>|<span data-ttu-id="22b1b-143">Použijte Aes128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="22b1b-143">Use Aes128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-144">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-144">TripleDesRsa15</span></span>|<span data-ttu-id="22b1b-145">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="22b1b-145">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-146">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="22b1b-146">Basic128Sha256</span></span>|<span data-ttu-id="22b1b-147">Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-147">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-148">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="22b1b-148">Basic192Sha256</span></span>|<span data-ttu-id="22b1b-149">Pro zabalení klíče použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-149">Use Aes192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-150">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="22b1b-150">Basic256Sha256</span></span>|<span data-ttu-id="22b1b-151">Pro zabalení klíče použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-151">Use Aes256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-152">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="22b1b-152">TripleDesSha256</span></span>|<span data-ttu-id="22b1b-153">Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="22b1b-153">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-154">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-154">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="22b1b-155">Použijte Aes128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="22b1b-155">Use Aes128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-156">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-156">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="22b1b-157">Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="22b1b-157">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-158">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-158">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="22b1b-159">Použijte AES256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="22b1b-159">Use Aes256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="22b1b-160">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="22b1b-160">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="22b1b-161">Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="22b1b-161">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22b1b-162">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22b1b-162">Child Elements</span></span>  
  
|<span data-ttu-id="22b1b-163">Prvek</span><span class="sxs-lookup"><span data-stu-id="22b1b-163">Element</span></span>|<span data-ttu-id="22b1b-164">Description</span><span class="sxs-lookup"><span data-stu-id="22b1b-164">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="22b1b-165">Určuje kolekci typů deklarací pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="22b1b-165">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="22b1b-166">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="22b1b-166">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|[\<issuer>](issuer.md)|<span data-ttu-id="22b1b-167">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="22b1b-167">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="22b1b-168">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="22b1b-168">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|[\<issuerMetadata>](issuermetadata.md)|<span data-ttu-id="22b1b-169">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="22b1b-169">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="22b1b-170">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="22b1b-170">A collection of token request parameters.</span></span> <span data-ttu-id="22b1b-171">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="22b1b-171">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22b1b-172">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22b1b-172">Parent Elements</span></span>  
  
|<span data-ttu-id="22b1b-173">Prvek</span><span class="sxs-lookup"><span data-stu-id="22b1b-173">Element</span></span>|<span data-ttu-id="22b1b-174">Description</span><span class="sxs-lookup"><span data-stu-id="22b1b-174">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-element-of-ws2007federationhttpbinding.md)|<span data-ttu-id="22b1b-175">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="22b1b-175">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22b1b-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="22b1b-176">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="22b1b-177">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="22b1b-177">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="22b1b-178">Vazby</span><span class="sxs-lookup"><span data-stu-id="22b1b-178">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="22b1b-179">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="22b1b-179">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="22b1b-180">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="22b1b-180">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
