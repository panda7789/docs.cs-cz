---
title: Element <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400082"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="ecc15-102">\<peerAuthentication – element ></span><span class="sxs-lookup"><span data-stu-id="ecc15-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="ecc15-103">Určuje možnosti ověřování pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="ecc15-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="ecc15-104">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="ecc15-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="ecc15-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ecc15-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ecc15-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ecc15-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ecc15-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ecc15-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ecc15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ecc15-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="ecc15-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ecc15-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="ecc15-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="ecc15-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="ecc15-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Partnerský >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="ecc15-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="ecc15-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<peerAuthentication >**</span><span class="sxs-lookup"><span data-stu-id="ecc15-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecc15-113">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecc15-113">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecc15-114">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ecc15-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ecc15-115">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ecc15-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecc15-116">Atributy</span><span class="sxs-lookup"><span data-stu-id="ecc15-116">Attributes</span></span>  
  
|<span data-ttu-id="ecc15-117">Atribut</span><span class="sxs-lookup"><span data-stu-id="ecc15-117">Attribute</span></span>|<span data-ttu-id="ecc15-118">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc15-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="ecc15-119">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ecc15-119">Optional string.</span></span> <span data-ttu-id="ecc15-120">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="ecc15-120">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="ecc15-121">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ecc15-121">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="ecc15-122">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="ecc15-122">Optional enumeration.</span></span> <span data-ttu-id="ecc15-123">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="ecc15-123">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="ecc15-124">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="ecc15-124">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="ecc15-125">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-125">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="ecc15-126">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="ecc15-126">Optional enumeration.</span></span> <span data-ttu-id="ecc15-127">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="ecc15-127">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="ecc15-128">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-128">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="ecc15-129">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="ecc15-129">Optional enumeration.</span></span> <span data-ttu-id="ecc15-130">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="ecc15-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="ecc15-131">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="ecc15-131">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="ecc15-132">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="ecc15-132">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="ecc15-133">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-133">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="ecc15-134">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="ecc15-134">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="ecc15-135">Value</span><span class="sxs-lookup"><span data-stu-id="ecc15-135">Value</span></span>|<span data-ttu-id="ecc15-136">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc15-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecc15-137">String</span><span class="sxs-lookup"><span data-stu-id="ecc15-137">String</span></span>|<span data-ttu-id="ecc15-138">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="ecc15-138">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="ecc15-139">Je vyžadován minimální obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="ecc15-139">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="ecc15-140">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="ecc15-140">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="ecc15-141">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="ecc15-141">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="ecc15-142">Value</span><span class="sxs-lookup"><span data-stu-id="ecc15-142">Value</span></span>|<span data-ttu-id="ecc15-143">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc15-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecc15-144">Výčet</span><span class="sxs-lookup"><span data-stu-id="ecc15-144">Enumeration</span></span>|<span data-ttu-id="ecc15-145">Jedna z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-145">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="ecc15-146">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-146">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="ecc15-147">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ecc15-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="ecc15-148">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="ecc15-148">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="ecc15-149">Value</span><span class="sxs-lookup"><span data-stu-id="ecc15-149">Value</span></span>|<span data-ttu-id="ecc15-150">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc15-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecc15-151">Výčet</span><span class="sxs-lookup"><span data-stu-id="ecc15-151">Enumeration</span></span>|<span data-ttu-id="ecc15-152">Jedna z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-152">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="ecc15-153">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-153">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="ecc15-154">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="ecc15-154">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="ecc15-155">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="ecc15-155">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="ecc15-156">Value</span><span class="sxs-lookup"><span data-stu-id="ecc15-156">Value</span></span>|<span data-ttu-id="ecc15-157">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc15-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ecc15-158">Výčet</span><span class="sxs-lookup"><span data-stu-id="ecc15-158">Enumeration</span></span>|<span data-ttu-id="ecc15-159">Jedna z následujících hodnot: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="ecc15-159">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="ecc15-160">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-160">The default is `CurrentUser`.</span></span> <span data-ttu-id="ecc15-161">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-161">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="ecc15-162">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-162">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecc15-163">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ecc15-163">Child Elements</span></span>  
 <span data-ttu-id="ecc15-164">Žádné</span><span class="sxs-lookup"><span data-stu-id="ecc15-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecc15-165">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ecc15-165">Parent Elements</span></span>  
  
|<span data-ttu-id="ecc15-166">Prvek</span><span class="sxs-lookup"><span data-stu-id="ecc15-166">Element</span></span>|<span data-ttu-id="ecc15-167">Popis</span><span class="sxs-lookup"><span data-stu-id="ecc15-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ecc15-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="ecc15-168">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="ecc15-169">Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.</span><span class="sxs-lookup"><span data-stu-id="ecc15-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ecc15-170">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecc15-170">Remarks</span></span>  
 <span data-ttu-id="ecc15-171">`<authentication>` Prvek odpovídá<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídě.</span><span class="sxs-lookup"><span data-stu-id="ecc15-171">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="ecc15-172">Tento prvek určuje validátor, který je vyvolán při ověřování typu Neighbor-to-Neighbor v síti.</span><span class="sxs-lookup"><span data-stu-id="ecc15-172">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="ecc15-173">Když se nový partner pokusí vytvořit sousední připojení, předá partnerskému partnerovi své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="ecc15-173">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="ecc15-174">K ověření přihlašovacích údajů vzdálené strany se vyvolá validátor daného respondéru.</span><span class="sxs-lookup"><span data-stu-id="ecc15-174">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="ecc15-175">Pokaždé, když je v síti navázáno připojení typu peer, oba partneři se vzájemně ověřují, což znamená, že jsou vyvolány validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="ecc15-175">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecc15-176">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecc15-176">Example</span></span>  
 <span data-ttu-id="ecc15-177">Následující kód nastaví režim ověřování certifikátu na `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="ecc15-177">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ecc15-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecc15-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="ecc15-179">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="ecc15-179">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="ecc15-180">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="ecc15-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="ecc15-181">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ecc15-181">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="ecc15-182">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="ecc15-182">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="ecc15-183">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="ecc15-183">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
