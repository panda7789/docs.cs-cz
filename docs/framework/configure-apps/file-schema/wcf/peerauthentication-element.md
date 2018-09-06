---
title: Element &lt;peerAuthentication&gt;
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4fb8cc4989313afa3ef16c90b54e0feae1ccb71d
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859013"
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="9f6d5-102">Element &lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="9f6d5-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="9f6d5-103">Určuje možnosti ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="9f6d5-104">Další informace o programování peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="9f6d5-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="9f6d5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f6d5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f6d5-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f6d5-106">\<behaviors></span></span>  
<span data-ttu-id="9f6d5-107">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="9f6d5-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="9f6d5-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f6d5-108">\<behavior></span></span>  
<span data-ttu-id="9f6d5-109">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="9f6d5-109">\<clientCredentials></span></span>  
<span data-ttu-id="9f6d5-110">\<sdílená ></span><span class="sxs-lookup"><span data-stu-id="9f6d5-110">\<peer></span></span>  
<span data-ttu-id="9f6d5-111">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="9f6d5-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f6d5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f6d5-112">Syntax</span></span>  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f6d5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f6d5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9f6d5-114">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f6d5-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f6d5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f6d5-115">Attributes</span></span>  
  
|<span data-ttu-id="9f6d5-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f6d5-116">Attribute</span></span>|<span data-ttu-id="9f6d5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9f6d5-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="9f6d5-118">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-118">Optional string.</span></span> <span data-ttu-id="9f6d5-119">Typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="9f6d5-120">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="9f6d5-121">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-121">Optional enumeration.</span></span> <span data-ttu-id="9f6d5-122">Určuje jeden ze tří režimů používaných pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="9f6d5-123">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="9f6d5-124">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="9f6d5-125">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-125">Optional enumeration.</span></span> <span data-ttu-id="9f6d5-126">Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="9f6d5-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="9f6d5-127">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="9f6d5-128">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-128">Optional enumeration.</span></span> <span data-ttu-id="9f6d5-129">Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="9f6d5-130">Tato hodnota se používá při certifikát služby se vyjedná do klienta.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="9f6d5-131">Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="9f6d5-132">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="9f6d5-133">customCertificateValidatorType atribut</span><span class="sxs-lookup"><span data-stu-id="9f6d5-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="9f6d5-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9f6d5-134">Value</span></span>|<span data-ttu-id="9f6d5-135">Popis</span><span class="sxs-lookup"><span data-stu-id="9f6d5-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f6d5-136">String</span><span class="sxs-lookup"><span data-stu-id="9f6d5-136">String</span></span>|<span data-ttu-id="9f6d5-137">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="9f6d5-138">Minimálně název oboru názvů a typ jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="9f6d5-139">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="9f6d5-140">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="9f6d5-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="9f6d5-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9f6d5-141">Value</span></span>|<span data-ttu-id="9f6d5-142">Popis</span><span class="sxs-lookup"><span data-stu-id="9f6d5-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f6d5-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="9f6d5-143">Enumeration</span></span>|<span data-ttu-id="9f6d5-144">Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="9f6d5-145">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="9f6d5-146">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9f6d5-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="9f6d5-147">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="9f6d5-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="9f6d5-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9f6d5-148">Value</span></span>|<span data-ttu-id="9f6d5-149">Popis</span><span class="sxs-lookup"><span data-stu-id="9f6d5-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f6d5-150">Výčet</span><span class="sxs-lookup"><span data-stu-id="9f6d5-150">Enumeration</span></span>|<span data-ttu-id="9f6d5-151">Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="9f6d5-152">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="9f6d5-153">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9f6d5-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="9f6d5-154">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="9f6d5-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="9f6d5-155">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9f6d5-155">Value</span></span>|<span data-ttu-id="9f6d5-156">Popis</span><span class="sxs-lookup"><span data-stu-id="9f6d5-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f6d5-157">Výčet</span><span class="sxs-lookup"><span data-stu-id="9f6d5-157">Enumeration</span></span>|<span data-ttu-id="9f6d5-158">Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="9f6d5-159">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="9f6d5-160">Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="9f6d5-161">Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f6d5-162">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f6d5-162">Child Elements</span></span>  
 <span data-ttu-id="9f6d5-163">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f6d5-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f6d5-164">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f6d5-164">Parent Elements</span></span>  
  
|<span data-ttu-id="9f6d5-165">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f6d5-165">Element</span></span>|<span data-ttu-id="9f6d5-166">Popis</span><span class="sxs-lookup"><span data-stu-id="9f6d5-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f6d5-167">\<peer></span><span class="sxs-lookup"><span data-stu-id="9f6d5-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="9f6d5-168">Určuje pověření pro ověření klienta ke službě partnera.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f6d5-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f6d5-169">Remarks</span></span>  
 <span data-ttu-id="9f6d5-170">`<authentication>` Odpovídá elementu <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="9f6d5-171">Tento prvek určuje ověřování, které se vyvolá při ověřování sousední souseda v mřížce.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="9f6d5-172">Nový partnerský uzel pokusí navázat připojení k sousedovi, předá odpovídá peer své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="9f6d5-173">Validátor odpovídajícího objektu je vyvolán k ověření přihlašovacích údajů vzdálené strany.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="9f6d5-174">Při každém navázání připojení partnera v mřížce, jak partnerské uzly jsou vzájemně se ověřují, jsou vyvolány význam validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f6d5-175">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f6d5-175">Example</span></span>  
 <span data-ttu-id="9f6d5-176">Následující kód nastaví režim ověřování certifikátu `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="9f6d5-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9f6d5-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f6d5-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="9f6d5-178">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="9f6d5-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="9f6d5-179">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="9f6d5-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="9f6d5-180">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="9f6d5-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="9f6d5-181">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="9f6d5-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="9f6d5-182">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="9f6d5-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
