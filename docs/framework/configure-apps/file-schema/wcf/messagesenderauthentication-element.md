---
title: <messageSenderAuthentication> – element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 1e63b6fa93e1abfa87c83da4b5d46f492c59b9bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931378"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="a4a8f-102">\<messageSenderAuthentication – element ></span><span class="sxs-lookup"><span data-stu-id="a4a8f-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="a4a8f-103">Určuje možnosti ověřování pro odesílatele zpráv peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="a4a8f-104">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="a4a8f-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="a4a8f-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a4a8f-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a4a8f-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="a4a8f-106">\<behaviors></span></span>  
<span data-ttu-id="a4a8f-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a4a8f-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="a4a8f-108">\<> chování</span><span class="sxs-lookup"><span data-stu-id="a4a8f-108">\<behavior></span></span>  
<span data-ttu-id="a4a8f-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a4a8f-109">\<clientCredentials></span></span>  
<span data-ttu-id="a4a8f-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="a4a8f-110">\<peer></span></span>  
<span data-ttu-id="a4a8f-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="a4a8f-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a8f-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a8f-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4a8f-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a4a8f-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a4a8f-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4a8f-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="a4a8f-115">Attributes</span></span>  
  
|<span data-ttu-id="a4a8f-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="a4a8f-116">Attribute</span></span>|<span data-ttu-id="a4a8f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a8f-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="a4a8f-118">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a4a8f-119">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="a4a8f-120">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a4a8f-121">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="a4a8f-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="a4a8f-122">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="a4a8f-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="a4a8f-123">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="a4a8f-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a4a8f-124">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="a4a8f-125">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="a4a8f-126">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="a4a8f-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="a4a8f-127">Value</span><span class="sxs-lookup"><span data-stu-id="a4a8f-127">Value</span></span>|<span data-ttu-id="a4a8f-128">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a8f-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a8f-129">String</span><span class="sxs-lookup"><span data-stu-id="a4a8f-129">String</span></span>|<span data-ttu-id="a4a8f-130">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-130">Optional.</span></span> <span data-ttu-id="a4a8f-131">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="a4a8f-132">Je vyžadován minimální obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="a4a8f-133">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="a4a8f-134">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="a4a8f-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="a4a8f-135">Value</span><span class="sxs-lookup"><span data-stu-id="a4a8f-135">Value</span></span>|<span data-ttu-id="a4a8f-136">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a8f-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a8f-137">Výčet</span><span class="sxs-lookup"><span data-stu-id="a4a8f-137">Enumeration</span></span>|<span data-ttu-id="a4a8f-138">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-138">Optional.</span></span> <span data-ttu-id="a4a8f-139">Jedna z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="a4a8f-140">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="a4a8f-141">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="a4a8f-142">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a4a8f-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="a4a8f-143">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="a4a8f-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="a4a8f-144">Value</span><span class="sxs-lookup"><span data-stu-id="a4a8f-144">Value</span></span>|<span data-ttu-id="a4a8f-145">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a8f-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a8f-146">Výčet</span><span class="sxs-lookup"><span data-stu-id="a4a8f-146">Enumeration</span></span>|<span data-ttu-id="a4a8f-147">Jedna z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="a4a8f-148">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="a4a8f-149">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a4a8f-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="a4a8f-150">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="a4a8f-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="a4a8f-151">Value</span><span class="sxs-lookup"><span data-stu-id="a4a8f-151">Value</span></span>|<span data-ttu-id="a4a8f-152">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a8f-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a4a8f-153">Výčet</span><span class="sxs-lookup"><span data-stu-id="a4a8f-153">Enumeration</span></span>|<span data-ttu-id="a4a8f-154">Jedna z následujících hodnot: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="a4a8f-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a4a8f-155">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="a4a8f-156">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="a4a8f-157">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="a4a8f-158">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4a8f-159">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a4a8f-159">Child Elements</span></span>  
 <span data-ttu-id="a4a8f-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="a4a8f-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a4a8f-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a4a8f-161">Parent Elements</span></span>  
  
|<span data-ttu-id="a4a8f-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="a4a8f-162">Element</span></span>|<span data-ttu-id="a4a8f-163">Popis</span><span class="sxs-lookup"><span data-stu-id="a4a8f-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a4a8f-164">\<peer></span><span class="sxs-lookup"><span data-stu-id="a4a8f-164">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="a4a8f-165">Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4a8f-166">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4a8f-166">Remarks</span></span>  
 <span data-ttu-id="a4a8f-167">Tento prvek musí být nakonfigurován, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="a4a8f-168">U výstupních kanálů se každá zpráva podepisuje pomocí certifikátu, který poskytuje [ \<> certifikátu](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="a4a8f-168">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="a4a8f-169">Všechny zprávy před doručením do aplikace jsou zkontrolovány proti pověření zprávy pomocí validátoru určeného `customCertificateValidatorType` atributem tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="a4a8f-170">Validátor může buď přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4a8f-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a8f-171">Example</span></span>  
 <span data-ttu-id="a4a8f-172">Následující kód nastaví režim ověřování odesílatele zprávy na `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a4a8f-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a4a8f-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4a8f-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="a4a8f-174">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="a4a8f-174">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a4a8f-175">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="a4a8f-175">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="a4a8f-176">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a4a8f-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="a4a8f-177">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a4a8f-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="a4a8f-178">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="a4a8f-178">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
