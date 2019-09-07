---
title: <messageSenderAuthentication> – element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397779"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="2b8b4-102">\<messageSenderAuthentication – element ></span><span class="sxs-lookup"><span data-stu-id="2b8b4-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="2b8b4-103">Určuje možnosti ověřování pro odesílatele zpráv peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="2b8b4-104">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="2b8b4-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="2b8b4-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b8b4-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b8b4-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2b8b4-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2b8b4-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2b8b4-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="2b8b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2b8b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="2b8b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2b8b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="2b8b4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="2b8b4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="2b8b4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Partnerský >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b8b4-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="2b8b4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<messageSenderAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="2b8b4-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b8b4-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b8b4-113">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b8b4-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b8b4-114">Attributes and Elements</span></span>  
 <span data-ttu-id="2b8b4-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b8b4-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b8b4-116">Attributes</span></span>  
  
|<span data-ttu-id="2b8b4-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="2b8b4-117">Attribute</span></span>|<span data-ttu-id="2b8b4-118">Popis</span><span class="sxs-lookup"><span data-stu-id="2b8b4-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="2b8b4-119">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="2b8b4-120">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="2b8b4-121">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="2b8b4-122">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="2b8b4-122">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="2b8b4-123">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="2b8b4-123">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="2b8b4-124">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="2b8b4-124">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2b8b4-125">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-125">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="2b8b4-126">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-126">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="2b8b4-127">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="2b8b4-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="2b8b4-128">Value</span><span class="sxs-lookup"><span data-stu-id="2b8b4-128">Value</span></span>|<span data-ttu-id="2b8b4-129">Popis</span><span class="sxs-lookup"><span data-stu-id="2b8b4-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b8b4-130">String</span><span class="sxs-lookup"><span data-stu-id="2b8b4-130">String</span></span>|<span data-ttu-id="2b8b4-131">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-131">Optional.</span></span> <span data-ttu-id="2b8b4-132">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-132">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="2b8b4-133">Je vyžadován minimální obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-133">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="2b8b4-134">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-134">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="2b8b4-135">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="2b8b4-135">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="2b8b4-136">Value</span><span class="sxs-lookup"><span data-stu-id="2b8b4-136">Value</span></span>|<span data-ttu-id="2b8b4-137">Popis</span><span class="sxs-lookup"><span data-stu-id="2b8b4-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b8b4-138">Výčet</span><span class="sxs-lookup"><span data-stu-id="2b8b4-138">Enumeration</span></span>|<span data-ttu-id="2b8b4-139">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-139">Optional.</span></span> <span data-ttu-id="2b8b4-140">Jedna z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-140">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="2b8b4-141">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-141">The default is `ChainTrust`.</span></span> <span data-ttu-id="2b8b4-142">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-142">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="2b8b4-143">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2b8b4-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="2b8b4-144">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="2b8b4-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="2b8b4-145">Value</span><span class="sxs-lookup"><span data-stu-id="2b8b4-145">Value</span></span>|<span data-ttu-id="2b8b4-146">Popis</span><span class="sxs-lookup"><span data-stu-id="2b8b4-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b8b4-147">Výčet</span><span class="sxs-lookup"><span data-stu-id="2b8b4-147">Enumeration</span></span>|<span data-ttu-id="2b8b4-148">Jedna z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-148">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="2b8b4-149">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-149">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="2b8b4-150">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2b8b4-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="2b8b4-151">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="2b8b4-151">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="2b8b4-152">Value</span><span class="sxs-lookup"><span data-stu-id="2b8b4-152">Value</span></span>|<span data-ttu-id="2b8b4-153">Popis</span><span class="sxs-lookup"><span data-stu-id="2b8b4-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2b8b4-154">Výčet</span><span class="sxs-lookup"><span data-stu-id="2b8b4-154">Enumeration</span></span>|<span data-ttu-id="2b8b4-155">Jedna z následujících hodnot: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="2b8b4-155">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2b8b4-156">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-156">The default is `CurrentUser`.</span></span> <span data-ttu-id="2b8b4-157">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-157">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="2b8b4-158">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-158">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="2b8b4-159">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-159">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b8b4-160">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2b8b4-160">Child Elements</span></span>  
 <span data-ttu-id="2b8b4-161">Žádné</span><span class="sxs-lookup"><span data-stu-id="2b8b4-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b8b4-162">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2b8b4-162">Parent Elements</span></span>  
  
|<span data-ttu-id="2b8b4-163">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b8b4-163">Element</span></span>|<span data-ttu-id="2b8b4-164">Popis</span><span class="sxs-lookup"><span data-stu-id="2b8b4-164">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b8b4-165">\<peer></span><span class="sxs-lookup"><span data-stu-id="2b8b4-165">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="2b8b4-166">Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-166">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b8b4-167">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b8b4-167">Remarks</span></span>  
 <span data-ttu-id="2b8b4-168">Tento prvek musí být nakonfigurován, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-168">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="2b8b4-169">U výstupních kanálů se každá zpráva podepisuje pomocí certifikátu, který poskytuje [ \<> certifikátu](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="2b8b4-169">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="2b8b4-170">Všechny zprávy před doručením do aplikace jsou zkontrolovány proti pověření zprávy pomocí validátoru určeného `customCertificateValidatorType` atributem tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-170">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="2b8b4-171">Validátor může buď přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-171">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b8b4-172">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b8b4-172">Example</span></span>  
 <span data-ttu-id="2b8b4-173">Následující kód nastaví režim ověřování odesílatele zprávy na `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2b8b4-173">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="2b8b4-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b8b4-174">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="2b8b4-175">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="2b8b4-175">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2b8b4-176">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="2b8b4-176">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2b8b4-177">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2b8b4-177">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2b8b4-178">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2b8b4-178">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2b8b4-179">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="2b8b4-179">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
