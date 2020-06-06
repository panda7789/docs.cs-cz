---
title: Element <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400082"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="92322-102">Element \<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="92322-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="92322-103">Určuje možnosti ověřování pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="92322-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="92322-104">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="92322-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="92322-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92322-105">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92322-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="92322-106">Attributes and Elements</span></span>  
 <span data-ttu-id="92322-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="92322-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92322-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="92322-108">Attributes</span></span>  
  
|<span data-ttu-id="92322-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="92322-109">Attribute</span></span>|<span data-ttu-id="92322-110">Popis</span><span class="sxs-lookup"><span data-stu-id="92322-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="92322-111">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="92322-111">Optional string.</span></span> <span data-ttu-id="92322-112">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="92322-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="92322-113">Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .</span><span class="sxs-lookup"><span data-stu-id="92322-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="92322-114">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="92322-114">Optional enumeration.</span></span> <span data-ttu-id="92322-115">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="92322-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="92322-116">Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také.</span><span class="sxs-lookup"><span data-stu-id="92322-116">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="92322-117">Výchozí formát je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="92322-117">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="92322-118">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="92322-118">Optional enumeration.</span></span> <span data-ttu-id="92322-119">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="92322-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="92322-120">Výchozí formát je `Online`.</span><span class="sxs-lookup"><span data-stu-id="92322-120">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="92322-121">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="92322-121">Optional enumeration.</span></span> <span data-ttu-id="92322-122">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="92322-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="92322-123">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="92322-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="92322-124">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="92322-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="92322-125">Výchozí formát je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="92322-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="92322-126">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="92322-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="92322-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="92322-127">Value</span></span>|<span data-ttu-id="92322-128">Description</span><span class="sxs-lookup"><span data-stu-id="92322-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92322-129">Řetězec</span><span class="sxs-lookup"><span data-stu-id="92322-129">String</span></span>|<span data-ttu-id="92322-130">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="92322-130">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="92322-131">Je vyžadován minimální obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="92322-131">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="92322-132">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="92322-132">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="92322-133">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="92322-133">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="92322-134">Hodnota</span><span class="sxs-lookup"><span data-stu-id="92322-134">Value</span></span>|<span data-ttu-id="92322-135">Description</span><span class="sxs-lookup"><span data-stu-id="92322-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92322-136">Výčet</span><span class="sxs-lookup"><span data-stu-id="92322-136">Enumeration</span></span>|<span data-ttu-id="92322-137">Jedna z následujících hodnot: `None` , `PeerTrust` , `ChainTrust` , `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="92322-137">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="92322-138">Výchozí formát je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="92322-138">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="92322-139">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="92322-139">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="92322-140">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="92322-140">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="92322-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="92322-141">Value</span></span>|<span data-ttu-id="92322-142">Description</span><span class="sxs-lookup"><span data-stu-id="92322-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92322-143">Výčet</span><span class="sxs-lookup"><span data-stu-id="92322-143">Enumeration</span></span>|<span data-ttu-id="92322-144">Jedna z následujících hodnot: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="92322-144">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="92322-145">Výchozí formát je `Online`.</span><span class="sxs-lookup"><span data-stu-id="92322-145">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="92322-146">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="92322-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="92322-147">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="92322-147">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="92322-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="92322-148">Value</span></span>|<span data-ttu-id="92322-149">Description</span><span class="sxs-lookup"><span data-stu-id="92322-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92322-150">Výčet</span><span class="sxs-lookup"><span data-stu-id="92322-150">Enumeration</span></span>|<span data-ttu-id="92322-151">Jedna z následujících hodnot: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="92322-151">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="92322-152">Výchozí formát je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="92322-152">The default is `CurrentUser`.</span></span> <span data-ttu-id="92322-153">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="92322-153">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="92322-154">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="92322-154">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92322-155">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="92322-155">Child Elements</span></span>  
 <span data-ttu-id="92322-156">Žádné</span><span class="sxs-lookup"><span data-stu-id="92322-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92322-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="92322-157">Parent Elements</span></span>  
  
|<span data-ttu-id="92322-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="92322-158">Element</span></span>|<span data-ttu-id="92322-159">Description</span><span class="sxs-lookup"><span data-stu-id="92322-159">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="92322-160">Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.</span><span class="sxs-lookup"><span data-stu-id="92322-160">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92322-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92322-161">Remarks</span></span>  
 <span data-ttu-id="92322-162">`<authentication>`Prvek odpovídá <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídě.</span><span class="sxs-lookup"><span data-stu-id="92322-162">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="92322-163">Tento prvek určuje validátor, který je vyvolán při ověřování typu Neighbor-to-Neighbor v síti.</span><span class="sxs-lookup"><span data-stu-id="92322-163">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="92322-164">Když se nový partner pokusí vytvořit sousední připojení, předá partnerskému partnerovi své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="92322-164">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="92322-165">K ověření přihlašovacích údajů vzdálené strany se vyvolá validátor daného respondéru.</span><span class="sxs-lookup"><span data-stu-id="92322-165">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="92322-166">Pokaždé, když je v síti navázáno připojení typu peer, oba partneři se vzájemně ověřují, což znamená, že jsou vyvolány validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="92322-166">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92322-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="92322-167">Example</span></span>  
 <span data-ttu-id="92322-168">Následující kód nastaví režim ověřování certifikátu na `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="92322-168">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92322-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="92322-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="92322-170">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="92322-170">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="92322-171">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="92322-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="92322-172">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="92322-172">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="92322-173">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="92322-173">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="92322-174">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="92322-174">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
