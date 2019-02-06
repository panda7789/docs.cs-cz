---
title: Element <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 7607f5bab6083c190303fd0a9121ffab55c620c3
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759441"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="f18d6-102">\<peerAuthentication > – Element</span><span class="sxs-lookup"><span data-stu-id="f18d6-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="f18d6-103">Určuje možnosti ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="f18d6-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="f18d6-104">Další informace o programování peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="f18d6-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="f18d6-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f18d6-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="f18d6-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f18d6-106">\<behaviors></span></span>  
<span data-ttu-id="f18d6-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="f18d6-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="f18d6-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f18d6-108">\<behavior></span></span>  
<span data-ttu-id="f18d6-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="f18d6-109">\<clientCredentials></span></span>  
<span data-ttu-id="f18d6-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="f18d6-110">\<peer></span></span>  
<span data-ttu-id="f18d6-111">\<PeerAuthentication></span><span class="sxs-lookup"><span data-stu-id="f18d6-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f18d6-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f18d6-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f18d6-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f18d6-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f18d6-114">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f18d6-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f18d6-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f18d6-115">Attributes</span></span>  
  
|<span data-ttu-id="f18d6-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="f18d6-116">Attribute</span></span>|<span data-ttu-id="f18d6-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f18d6-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="f18d6-118">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f18d6-118">Optional string.</span></span> <span data-ttu-id="f18d6-119">Typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="f18d6-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f18d6-120">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="f18d6-121">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="f18d6-121">Optional enumeration.</span></span> <span data-ttu-id="f18d6-122">Určuje jeden ze tří režimů používaných pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="f18d6-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f18d6-123">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="f18d6-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="f18d6-124">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="f18d6-125">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="f18d6-125">Optional enumeration.</span></span> <span data-ttu-id="f18d6-126">Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="f18d6-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="f18d6-127">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f18d6-128">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="f18d6-128">Optional enumeration.</span></span> <span data-ttu-id="f18d6-129">Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f18d6-130">Tato hodnota se používá při certifikát služby se vyjedná do klienta.</span><span class="sxs-lookup"><span data-stu-id="f18d6-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="f18d6-131">Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště.</span><span class="sxs-lookup"><span data-stu-id="f18d6-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="f18d6-132">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="f18d6-133">customCertificateValidatorType Attribute</span><span class="sxs-lookup"><span data-stu-id="f18d6-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="f18d6-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f18d6-134">Value</span></span>|<span data-ttu-id="f18d6-135">Popis</span><span class="sxs-lookup"><span data-stu-id="f18d6-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f18d6-136">String</span><span class="sxs-lookup"><span data-stu-id="f18d6-136">String</span></span>|<span data-ttu-id="f18d6-137">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="f18d6-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="f18d6-138">Minimálně název oboru názvů a typ jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="f18d6-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="f18d6-139">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="f18d6-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="f18d6-140">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="f18d6-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="f18d6-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f18d6-141">Value</span></span>|<span data-ttu-id="f18d6-142">Popis</span><span class="sxs-lookup"><span data-stu-id="f18d6-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f18d6-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="f18d6-143">Enumeration</span></span>|<span data-ttu-id="f18d6-144">Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="f18d6-145">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="f18d6-146">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f18d6-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="f18d6-147">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="f18d6-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="f18d6-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f18d6-148">Value</span></span>|<span data-ttu-id="f18d6-149">Popis</span><span class="sxs-lookup"><span data-stu-id="f18d6-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f18d6-150">Výčet</span><span class="sxs-lookup"><span data-stu-id="f18d6-150">Enumeration</span></span>|<span data-ttu-id="f18d6-151">Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="f18d6-152">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="f18d6-153">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="f18d6-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="f18d6-154">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="f18d6-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="f18d6-155">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f18d6-155">Value</span></span>|<span data-ttu-id="f18d6-156">Popis</span><span class="sxs-lookup"><span data-stu-id="f18d6-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f18d6-157">Výčet</span><span class="sxs-lookup"><span data-stu-id="f18d6-157">Enumeration</span></span>|<span data-ttu-id="f18d6-158">Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="f18d6-159">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="f18d6-160">Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="f18d6-161">Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f18d6-162">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f18d6-162">Child Elements</span></span>  
 <span data-ttu-id="f18d6-163">Žádné</span><span class="sxs-lookup"><span data-stu-id="f18d6-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f18d6-164">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f18d6-164">Parent Elements</span></span>  
  
|<span data-ttu-id="f18d6-165">Prvek</span><span class="sxs-lookup"><span data-stu-id="f18d6-165">Element</span></span>|<span data-ttu-id="f18d6-166">Popis</span><span class="sxs-lookup"><span data-stu-id="f18d6-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f18d6-167">\<peer></span><span class="sxs-lookup"><span data-stu-id="f18d6-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="f18d6-168">Určuje pověření pro ověření klienta ke službě partnera.</span><span class="sxs-lookup"><span data-stu-id="f18d6-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f18d6-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f18d6-169">Remarks</span></span>  
 <span data-ttu-id="f18d6-170">`<authentication>` Odpovídá elementu <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="f18d6-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="f18d6-171">Tento prvek určuje ověřování, které se vyvolá při ověřování sousední souseda v mřížce.</span><span class="sxs-lookup"><span data-stu-id="f18d6-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="f18d6-172">Nový partnerský uzel pokusí navázat připojení k sousedovi, předá odpovídá peer své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="f18d6-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="f18d6-173">Validátor odpovídajícího objektu je vyvolán k ověření přihlašovacích údajů vzdálené strany.</span><span class="sxs-lookup"><span data-stu-id="f18d6-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="f18d6-174">Při každém navázání připojení partnera v mřížce, jak partnerské uzly jsou vzájemně se ověřují, jsou vyvolány význam validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="f18d6-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f18d6-175">Příklad</span><span class="sxs-lookup"><span data-stu-id="f18d6-175">Example</span></span>  
 <span data-ttu-id="f18d6-176">Následující kód nastaví režim ověřování certifikátu `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="f18d6-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f18d6-177">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f18d6-177">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="f18d6-178">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="f18d6-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f18d6-179">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="f18d6-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f18d6-180">[Ověřování zpráv protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f18d6-180">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f18d6-181">[Vlastní ověřování protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f18d6-181">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f18d6-182">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="f18d6-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
