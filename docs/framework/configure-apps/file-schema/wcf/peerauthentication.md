---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: b627105dc4aae49557b0a6684569719622e13f08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180593"
---
# <a name="peerauthentication"></a><span data-ttu-id="6a430-101">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="6a430-101">\<peerAuthentication></span></span>
<span data-ttu-id="6a430-102">Určuje nastavení ověřování pro sdílené certifikát používaný službou partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="6a430-102">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="6a430-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a430-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a430-104">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6a430-104">\<behaviors></span></span>  
<span data-ttu-id="6a430-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6a430-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="6a430-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6a430-106">\<behavior></span></span>  
<span data-ttu-id="6a430-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6a430-107">\<serviceCredentials></span></span>  
<span data-ttu-id="6a430-108">\<peer></span><span class="sxs-lookup"><span data-stu-id="6a430-108">\<peer></span></span>  
<span data-ttu-id="6a430-109">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="6a430-109">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a430-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a430-110">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a430-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6a430-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6a430-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6a430-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a430-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6a430-113">Attributes</span></span>  
  
|<span data-ttu-id="6a430-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="6a430-114">Attribute</span></span>|<span data-ttu-id="6a430-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6a430-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="6a430-116">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="6a430-116">Optional enumeration.</span></span> <span data-ttu-id="6a430-117">Určuje jeden ze tří režimů používaných pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="6a430-117">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="6a430-118">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="6a430-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="6a430-119">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="6a430-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="6a430-120">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="6a430-120">Optional string.</span></span> <span data-ttu-id="6a430-121">Určuje typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="6a430-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="6a430-122">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="6a430-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="6a430-123">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="6a430-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="6a430-124">Windows Communication Foundation (WCF) poskytuje sdílené výchozí validátor certifikátu, který ověřuje certifikát peer proti úložišti důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="6a430-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="6a430-125">Také ověřuje, že certifikát zřetězený platného kořenového.</span><span class="sxs-lookup"><span data-stu-id="6a430-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="6a430-126">Můžete implementovat vlastní validátor určit různá chování a používání tohoto atributu na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="6a430-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="6a430-127">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="6a430-127">Optional enumeration.</span></span> <span data-ttu-id="6a430-128">Určuje režim odvolání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="6a430-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="6a430-129">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="6a430-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="6a430-130">Systém ověří, že peer certifikát nebyl odvolaný ve vyhledávání v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="6a430-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="6a430-131">Tato kontrola lze provést tak, že zkontrolujete online nebo seznam odvolaných certifikátů uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6a430-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="6a430-132">Kontrola odvolání můžete vypnout pomocí nastavení tohoto atributu na NoCheck.</span><span class="sxs-lookup"><span data-stu-id="6a430-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="6a430-133">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="6a430-133">Optional enumeration.</span></span> <span data-ttu-id="6a430-134">Určuje umístění úložiště pro důvěryhodného kde ověření certifikátu druhé strany systém zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="6a430-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="6a430-135">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="6a430-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a430-136">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6a430-136">Child Elements</span></span>  
 <span data-ttu-id="6a430-137">Žádné</span><span class="sxs-lookup"><span data-stu-id="6a430-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a430-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6a430-138">Parent Elements</span></span>  
  
|<span data-ttu-id="6a430-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="6a430-139">Element</span></span>|<span data-ttu-id="6a430-140">Popis</span><span class="sxs-lookup"><span data-stu-id="6a430-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a430-141">\<peer></span><span class="sxs-lookup"><span data-stu-id="6a430-141">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="6a430-142">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="6a430-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a430-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a430-143">Remarks</span></span>  
 <span data-ttu-id="6a430-144">`<authentication>` Odpovídá elementu <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="6a430-144">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="6a430-145">Tento prvek určuje ověřování, které se vyvolá při ověřování sousední souseda v mřížce.</span><span class="sxs-lookup"><span data-stu-id="6a430-145">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="6a430-146">Nový partnerský uzel pokusí navázat připojení k sousedovi, předá odpovídá peer své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="6a430-146">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="6a430-147">Validátor odpovídajícího objektu je vyvolán k ověření přihlašovacích údajů vzdálené strany.</span><span class="sxs-lookup"><span data-stu-id="6a430-147">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="6a430-148">Při každém navázání připojení partnera v mřížce, jak partnerské uzly jsou vzájemně se ověřují, jsou vyvolány význam validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="6a430-148">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a430-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a430-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="6a430-150">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="6a430-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6a430-151">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="6a430-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="6a430-152">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="6a430-152">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="6a430-153">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="6a430-153">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="6a430-154">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="6a430-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
