---
title: <message>prvek elementu<wsFederationHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9d710389-d9d8-4454-9bf2-da4ccda31cec
ms.openlocfilehash: 8e0903dd1313e68e2de65730e129079199ebe2f2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738984"
---
# <a name="message-element-of-wsfederationhttpbinding"></a><span data-ttu-id="b1893-102">\<message>prvek elementu\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="b1893-102">\<message> element of \<wsFederationHttpBinding></span></span>
<span data-ttu-id="b1893-103">Definuje nastavení pro zabezpečení na úrovni zprávy pro [\<wsFederationHttpBinding>](wsfederationhttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b1893-103">Defines the settings for the message-level security for the [\<wsFederationHttpBinding>](wsfederationhttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsFederationHttpBinding>**](wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-wsfederationhttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="b1893-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1893-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1893-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1893-105">Attributes and Elements</span></span>  
 <span data-ttu-id="b1893-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1893-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1893-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1893-107">Attributes</span></span>  
  
|<span data-ttu-id="b1893-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1893-108">Attribute</span></span>|<span data-ttu-id="b1893-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b1893-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1893-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="b1893-110">algorithmSuite</span></span>|<span data-ttu-id="b1893-111">Nastaví šifrování zpráv a algoritmy pro zabalení klíčů.</span><span class="sxs-lookup"><span data-stu-id="b1893-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="b1893-112">Platné hodnoty tohoto atributu najdete v tabulce atributu algorithmSuite.</span><span class="sxs-lookup"><span data-stu-id="b1893-112">See the "algorithmSuite attribute" table for valid values of this attribute.</span></span> <span data-ttu-id="b1893-113">Výchozí hodnota je `Basic256`.</span><span class="sxs-lookup"><span data-stu-id="b1893-113">The default value is `Basic256`.</span></span><br /><br /> <span data-ttu-id="b1893-114">Tento atribut je typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .</span><span class="sxs-lookup"><span data-stu-id="b1893-114">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.</span></span> <span data-ttu-id="b1893-115">Tyto algoritmy jsou mapovány na ty, které jsou zadány ve specifikaci jazyka zásad zabezpečení (WS-SecurityPolicy).</span><span class="sxs-lookup"><span data-stu-id="b1893-115">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span>|  
|<span data-ttu-id="b1893-116">issuedKeyType</span><span class="sxs-lookup"><span data-stu-id="b1893-116">issuedKeyType</span></span>|<span data-ttu-id="b1893-117">Určuje typ klíče, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="b1893-117">Specifies the type of key to be issued.</span></span> <span data-ttu-id="b1893-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="b1893-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b1893-119">- SymmetricKey</span><span class="sxs-lookup"><span data-stu-id="b1893-119">-   SymmetricKey</span></span><br /><span data-ttu-id="b1893-120">– PublicKey</span><span class="sxs-lookup"><span data-stu-id="b1893-120">-   PublicKey</span></span><br /><br /> <span data-ttu-id="b1893-121">Výchozí formát je `SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="b1893-121">The default is `SymmetricKey`.</span></span> <span data-ttu-id="b1893-122">Tento atribut je typu <xref:System.IdentityModel.Tokens.SecurityKeyType> .</span><span class="sxs-lookup"><span data-stu-id="b1893-122">This attribute is of type <xref:System.IdentityModel.Tokens.SecurityKeyType>.</span></span>|  
|<span data-ttu-id="b1893-123">issuedTokenType</span><span class="sxs-lookup"><span data-stu-id="b1893-123">issuedTokenType</span></span>|<span data-ttu-id="b1893-124">Řetězec obsahující identifikátor URI, který určuje typ tokenu, který se má vystavit.</span><span class="sxs-lookup"><span data-stu-id="b1893-124">A string that contains a URI that specifies the type of token to be issued.</span></span> <span data-ttu-id="b1893-125">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="b1893-125">The default is `null`.</span></span>|  
|<span data-ttu-id="b1893-126">negotiateServiceCredential</span><span class="sxs-lookup"><span data-stu-id="b1893-126">negotiateServiceCredential</span></span>|<span data-ttu-id="b1893-127">Logická hodnota určující, zda má být pověření služby vyměněno jako součást vyjednávání nebo je k dispozici mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="b1893-127">A Boolean value that specifies whether the service credential should be exchanged as part of negotiation or is available out of band.</span></span> <span data-ttu-id="b1893-128">Výchozí hodnota je `true` , což znamená, že se pověření služby vyjednávat.</span><span class="sxs-lookup"><span data-stu-id="b1893-128">The default is `true`, which means that the service credential is negotiated.</span></span>|  
  
## <a name="algorithmsuite-attribute"></a><span data-ttu-id="b1893-129">algorithmSuite – atribut</span><span class="sxs-lookup"><span data-stu-id="b1893-129">algorithmSuite Attribute</span></span>  
  
|<span data-ttu-id="b1893-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b1893-130">Value</span></span>|<span data-ttu-id="b1893-131">Description</span><span class="sxs-lookup"><span data-stu-id="b1893-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1893-132">Basic128</span><span class="sxs-lookup"><span data-stu-id="b1893-132">Basic128</span></span>|<span data-ttu-id="b1893-133">Pro zabalení klíče použijte šifrování Basic128, SHA1 pro Digest zpráv a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-133">Use Basic128 encryption, Sha1 for message digest, and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-134">Basic192</span><span class="sxs-lookup"><span data-stu-id="b1893-134">Basic192</span></span>|<span data-ttu-id="b1893-135">Pro zabalení klíče použijte šifrování Basic192, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-135">Use Basic192 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-136">Basic256</span><span class="sxs-lookup"><span data-stu-id="b1893-136">Basic256</span></span>|<span data-ttu-id="b1893-137">Pro zabalení klíče použijte šifrování Basic256, SHA1 pro Digest zpráv, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-137">Use Basic256 encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-138">Basic256Rsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-138">Basic256Rsa15</span></span>|<span data-ttu-id="b1893-139">Použijte Basic256 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="b1893-139">Use Basic256 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="b1893-140">Basic192Rsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-140">Basic192Rsa15</span></span>|<span data-ttu-id="b1893-141">Použijte Basic192 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="b1893-141">Use Basic192 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="b1893-142">TripleDes</span><span class="sxs-lookup"><span data-stu-id="b1893-142">TripleDes</span></span>|<span data-ttu-id="b1893-143">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Digest zprávy, RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-143">Use TripleDes encryption, Sha1 for message digest, Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-144">Basic128Rsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-144">Basic128Rsa15</span></span>|<span data-ttu-id="b1893-145">Použijte Basic128 pro šifrování zpráv, SHA1 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="b1893-145">Use Basic128 for message encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="b1893-146">TripleDesRsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-146">TripleDesRsa15</span></span>|<span data-ttu-id="b1893-147">Pro zabalení klíče použijte šifrování TripleDes, SHA1 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="b1893-147">Use TripleDes encryption, Sha1 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="b1893-148">Basic128Sha256</span><span class="sxs-lookup"><span data-stu-id="b1893-148">Basic128Sha256</span></span>|<span data-ttu-id="b1893-149">Pro zabalení klíče použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-149">Use Basic128 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-150">Basic192Sha256</span><span class="sxs-lookup"><span data-stu-id="b1893-150">Basic192Sha256</span></span>|<span data-ttu-id="b1893-151">Pro zabalení klíče použijte Basic192 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-151">Use Basic192 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-152">Basic256Sha256</span><span class="sxs-lookup"><span data-stu-id="b1893-152">Basic256Sha256</span></span>|<span data-ttu-id="b1893-153">Pro zabalení klíče použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-153">Use Basic256 for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-154">TripleDesSha256</span><span class="sxs-lookup"><span data-stu-id="b1893-154">TripleDesSha256</span></span>|<span data-ttu-id="b1893-155">Pro zabalení klíče použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a RSA-výplně OAEP-mgf1p.</span><span class="sxs-lookup"><span data-stu-id="b1893-155">Use TripleDes for message encryption, Sha256 for message digest and Rsa-oaep-mgf1p for key wrap.</span></span>|  
|<span data-ttu-id="b1893-156">Basic128Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-156">Basic128Sha256Rsa15</span></span>|<span data-ttu-id="b1893-157">Použijte Basic128 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="b1893-157">Use Basic128 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="b1893-158">Basic192Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-158">Basic192Sha256Rsa15</span></span>|<span data-ttu-id="b1893-159">Použijte Aes192 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="b1893-159">Use Aes192 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="b1893-160">Basic256Sha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-160">Basic256Sha256Rsa15</span></span>|<span data-ttu-id="b1893-161">Použijte Basic256 pro šifrování zpráv, SHA256 pro Message Digest a Rsa15 pro zabalení klíče.</span><span class="sxs-lookup"><span data-stu-id="b1893-161">Use Basic256 for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
|<span data-ttu-id="b1893-162">TripleDesSha256Rsa15</span><span class="sxs-lookup"><span data-stu-id="b1893-162">TripleDesSha256Rsa15</span></span>|<span data-ttu-id="b1893-163">Pro zabalení zprávy použijte TripleDes pro šifrování zpráv, SHA256 pro Message Digest a Rsa15.</span><span class="sxs-lookup"><span data-stu-id="b1893-163">Use TripleDes for message encryption, Sha256 for message digest and Rsa15 for key wrap.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1893-164">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1893-164">Child Elements</span></span>  
  
|<span data-ttu-id="b1893-165">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1893-165">Element</span></span>|<span data-ttu-id="b1893-166">Description</span><span class="sxs-lookup"><span data-stu-id="b1893-166">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequirements>](claimtyperequirements-element.md)|<span data-ttu-id="b1893-167">Určuje kolekci typů deklarací pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1893-167">Specifies a collection of claim types for this binding.</span></span> <span data-ttu-id="b1893-168">Každý prvek je typu <xref:System.ServiceModel.Configuration.ClaimTypeElement> .</span><span class="sxs-lookup"><span data-stu-id="b1893-168">Each element is of type <xref:System.ServiceModel.Configuration.ClaimTypeElement>.</span></span>|  
|<span data-ttu-id="b1893-169">issuer</span><span class="sxs-lookup"><span data-stu-id="b1893-169">issuer</span></span>|<span data-ttu-id="b1893-170">Určuje koncový bod, který vydá token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b1893-170">Specifies an endpoint that issues a security token.</span></span> <span data-ttu-id="b1893-171">Tento prvek je typu <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement> .</span><span class="sxs-lookup"><span data-stu-id="b1893-171">This element is of type <xref:System.ServiceModel.Configuration.IssuedTokenParametersEndpointAddressElement>.</span></span>|  
|<span data-ttu-id="b1893-172">issuerMetadata</span><span class="sxs-lookup"><span data-stu-id="b1893-172">issuerMetadata</span></span>|<span data-ttu-id="b1893-173">Určuje adresu koncového bodu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="b1893-173">Specifies the endpoint address of the issuer.</span></span>|  
|[\<tokenRequestParameters>](tokenrequestparameters.md)|<span data-ttu-id="b1893-174">Kolekce parametrů požadavku tokenu</span><span class="sxs-lookup"><span data-stu-id="b1893-174">A collection of token request parameters.</span></span> <span data-ttu-id="b1893-175">Každý parametr je XML element.</span><span class="sxs-lookup"><span data-stu-id="b1893-175">Each parameter is an XML element.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1893-176">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1893-176">Parent Elements</span></span>  
  
|<span data-ttu-id="b1893-177">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1893-177">Element</span></span>|<span data-ttu-id="b1893-178">Description</span><span class="sxs-lookup"><span data-stu-id="b1893-178">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-wsfederationhttpbinding.md)|<span data-ttu-id="b1893-179">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1893-179">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b1893-180">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1893-180">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp>
- <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSFederationHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement>
- [<span data-ttu-id="b1893-181">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b1893-181">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b1893-182">Vazby</span><span class="sxs-lookup"><span data-stu-id="b1893-182">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b1893-183">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b1893-183">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b1893-184">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b1893-184">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
