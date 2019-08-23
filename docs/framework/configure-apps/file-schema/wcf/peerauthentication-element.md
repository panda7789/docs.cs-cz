---
title: Element <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 09094c00b8faa28c37e202112251fee7cb4580be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934024"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="087bb-102">\<peerAuthentication – element ></span><span class="sxs-lookup"><span data-stu-id="087bb-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="087bb-103">Určuje možnosti ověřování pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="087bb-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="087bb-104">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="087bb-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="087bb-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="087bb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="087bb-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="087bb-106">\<behaviors></span></span>  
<span data-ttu-id="087bb-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="087bb-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="087bb-108">\<> chování</span><span class="sxs-lookup"><span data-stu-id="087bb-108">\<behavior></span></span>  
<span data-ttu-id="087bb-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="087bb-109">\<clientCredentials></span></span>  
<span data-ttu-id="087bb-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="087bb-110">\<peer></span></span>  
<span data-ttu-id="087bb-111">\<PeerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="087bb-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="087bb-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="087bb-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="087bb-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="087bb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="087bb-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="087bb-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="087bb-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="087bb-115">Attributes</span></span>  
  
|<span data-ttu-id="087bb-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="087bb-116">Attribute</span></span>|<span data-ttu-id="087bb-117">Popis</span><span class="sxs-lookup"><span data-stu-id="087bb-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="087bb-118">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="087bb-118">Optional string.</span></span> <span data-ttu-id="087bb-119">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="087bb-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="087bb-120">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="087bb-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="087bb-121">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="087bb-121">Optional enumeration.</span></span> <span data-ttu-id="087bb-122">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="087bb-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="087bb-123">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="087bb-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="087bb-124">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="087bb-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="087bb-125">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="087bb-125">Optional enumeration.</span></span> <span data-ttu-id="087bb-126">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="087bb-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="087bb-127">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="087bb-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="087bb-128">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="087bb-128">Optional enumeration.</span></span> <span data-ttu-id="087bb-129">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="087bb-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="087bb-130">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="087bb-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="087bb-131">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="087bb-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="087bb-132">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="087bb-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="087bb-133">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="087bb-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="087bb-134">Value</span><span class="sxs-lookup"><span data-stu-id="087bb-134">Value</span></span>|<span data-ttu-id="087bb-135">Popis</span><span class="sxs-lookup"><span data-stu-id="087bb-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="087bb-136">String</span><span class="sxs-lookup"><span data-stu-id="087bb-136">String</span></span>|<span data-ttu-id="087bb-137">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="087bb-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="087bb-138">Je vyžadován minimální obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="087bb-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="087bb-139">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="087bb-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="087bb-140">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="087bb-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="087bb-141">Value</span><span class="sxs-lookup"><span data-stu-id="087bb-141">Value</span></span>|<span data-ttu-id="087bb-142">Popis</span><span class="sxs-lookup"><span data-stu-id="087bb-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="087bb-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="087bb-143">Enumeration</span></span>|<span data-ttu-id="087bb-144">Jedna z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="087bb-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="087bb-145">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="087bb-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="087bb-146">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="087bb-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="087bb-147">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="087bb-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="087bb-148">Value</span><span class="sxs-lookup"><span data-stu-id="087bb-148">Value</span></span>|<span data-ttu-id="087bb-149">Popis</span><span class="sxs-lookup"><span data-stu-id="087bb-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="087bb-150">Výčet</span><span class="sxs-lookup"><span data-stu-id="087bb-150">Enumeration</span></span>|<span data-ttu-id="087bb-151">Jedna z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="087bb-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="087bb-152">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="087bb-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="087bb-153">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="087bb-153">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="087bb-154">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="087bb-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="087bb-155">Value</span><span class="sxs-lookup"><span data-stu-id="087bb-155">Value</span></span>|<span data-ttu-id="087bb-156">Popis</span><span class="sxs-lookup"><span data-stu-id="087bb-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="087bb-157">Výčet</span><span class="sxs-lookup"><span data-stu-id="087bb-157">Enumeration</span></span>|<span data-ttu-id="087bb-158">Jedna z následujících hodnot: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="087bb-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="087bb-159">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="087bb-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="087bb-160">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="087bb-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="087bb-161">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="087bb-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="087bb-162">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="087bb-162">Child Elements</span></span>  
 <span data-ttu-id="087bb-163">Žádné</span><span class="sxs-lookup"><span data-stu-id="087bb-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="087bb-164">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="087bb-164">Parent Elements</span></span>  
  
|<span data-ttu-id="087bb-165">Prvek</span><span class="sxs-lookup"><span data-stu-id="087bb-165">Element</span></span>|<span data-ttu-id="087bb-166">Popis</span><span class="sxs-lookup"><span data-stu-id="087bb-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="087bb-167">\<peer></span><span class="sxs-lookup"><span data-stu-id="087bb-167">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="087bb-168">Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.</span><span class="sxs-lookup"><span data-stu-id="087bb-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="087bb-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="087bb-169">Remarks</span></span>  
 <span data-ttu-id="087bb-170">`<authentication>` Prvek odpovídá<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídě.</span><span class="sxs-lookup"><span data-stu-id="087bb-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="087bb-171">Tento prvek určuje validátor, který je vyvolán při ověřování typu Neighbor-to-Neighbor v síti.</span><span class="sxs-lookup"><span data-stu-id="087bb-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="087bb-172">Když se nový partner pokusí vytvořit sousední připojení, předá partnerskému partnerovi své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="087bb-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="087bb-173">K ověření přihlašovacích údajů vzdálené strany se vyvolá validátor daného respondéru.</span><span class="sxs-lookup"><span data-stu-id="087bb-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="087bb-174">Pokaždé, když je v síti navázáno připojení typu peer, oba partneři se vzájemně ověřují, což znamená, že jsou vyvolány validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="087bb-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="087bb-175">Příklad</span><span class="sxs-lookup"><span data-stu-id="087bb-175">Example</span></span>  
 <span data-ttu-id="087bb-176">Následující kód nastaví režim ověřování certifikátu na `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="087bb-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="087bb-177">Viz také:</span><span class="sxs-lookup"><span data-stu-id="087bb-177">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="087bb-178">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="087bb-178">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="087bb-179">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="087bb-179">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="087bb-180">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="087bb-180">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="087bb-181">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="087bb-181">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="087bb-182">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="087bb-182">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
