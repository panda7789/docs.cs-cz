---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: bb83d2badad609394a66246fc14c19a6602399e0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45569135"
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="587c5-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="587c5-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="587c5-103">Určuje nastavení ověřování pro sdílené certifikát používaný službou partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="587c5-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="587c5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="587c5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="587c5-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="587c5-105">\<behaviors></span></span>  
<span data-ttu-id="587c5-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="587c5-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="587c5-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="587c5-107">\<behavior></span></span>  
<span data-ttu-id="587c5-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="587c5-108">\<serviceCredentials></span></span>  
<span data-ttu-id="587c5-109">\<sdílená ></span><span class="sxs-lookup"><span data-stu-id="587c5-109">\<peer></span></span>  
<span data-ttu-id="587c5-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="587c5-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587c5-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="587c5-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="587c5-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="587c5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="587c5-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="587c5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="587c5-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="587c5-114">Attributes</span></span>  
  
|<span data-ttu-id="587c5-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="587c5-115">Attribute</span></span>|<span data-ttu-id="587c5-116">Popis</span><span class="sxs-lookup"><span data-stu-id="587c5-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="587c5-117">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="587c5-117">Optional enumeration.</span></span> <span data-ttu-id="587c5-118">Určuje jeden ze tří režimů používaných pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="587c5-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="587c5-119">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="587c5-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="587c5-120">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="587c5-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="587c5-121">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="587c5-121">Optional string.</span></span> <span data-ttu-id="587c5-122">Určuje typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="587c5-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="587c5-123">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="587c5-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="587c5-124">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="587c5-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="587c5-125">Windows Communication Foundation (WCF) poskytuje sdílené výchozí validátor certifikátu, který ověřuje certifikát peer proti úložišti důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="587c5-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="587c5-126">Také ověřuje, že certifikát zřetězený platného kořenového.</span><span class="sxs-lookup"><span data-stu-id="587c5-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="587c5-127">Můžete implementovat vlastní validátor určit různá chování a používání tohoto atributu na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="587c5-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="587c5-128">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="587c5-128">Optional enumeration.</span></span> <span data-ttu-id="587c5-129">Určuje režim odvolání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="587c5-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="587c5-130">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="587c5-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="587c5-131">Systém ověří, že peer certifikát nebyl odvolaný ve vyhledávání v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="587c5-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="587c5-132">Tato kontrola lze provést tak, že zkontrolujete online nebo seznam odvolaných certifikátů uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="587c5-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="587c5-133">Kontrola odvolání můžete vypnout pomocí nastavení tohoto atributu na NoCheck.</span><span class="sxs-lookup"><span data-stu-id="587c5-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="587c5-134">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="587c5-134">Optional enumeration.</span></span> <span data-ttu-id="587c5-135">Určuje umístění úložiště pro důvěryhodného kde ověření certifikátu druhé strany systém zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="587c5-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="587c5-136">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="587c5-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="587c5-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="587c5-137">Child Elements</span></span>  
 <span data-ttu-id="587c5-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="587c5-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="587c5-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="587c5-139">Parent Elements</span></span>  
  
|<span data-ttu-id="587c5-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="587c5-140">Element</span></span>|<span data-ttu-id="587c5-141">Popis</span><span class="sxs-lookup"><span data-stu-id="587c5-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="587c5-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="587c5-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="587c5-143">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="587c5-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="587c5-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="587c5-144">Remarks</span></span>  
 <span data-ttu-id="587c5-145">`<authentication>` Odpovídá elementu <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="587c5-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="587c5-146">Tento prvek určuje ověřování, které se vyvolá při ověřování sousední souseda v mřížce.</span><span class="sxs-lookup"><span data-stu-id="587c5-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="587c5-147">Nový partnerský uzel pokusí navázat připojení k sousedovi, předá odpovídá peer své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="587c5-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="587c5-148">Validátor odpovídajícího objektu je vyvolán k ověření přihlašovacích údajů vzdálené strany.</span><span class="sxs-lookup"><span data-stu-id="587c5-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="587c5-149">Při každém navázání připojení partnera v mřížce, jak partnerské uzly jsou vzájemně se ověřují, jsou vyvolány význam validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="587c5-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="587c5-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="587c5-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="587c5-151">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="587c5-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="587c5-152">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="587c5-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="587c5-153">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="587c5-153">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="587c5-154">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="587c5-154">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="587c5-155">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="587c5-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
