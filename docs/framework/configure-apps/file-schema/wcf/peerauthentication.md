---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1de8b8ceaf56931dfd3f09e5cc21ac939c49b4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="c5e36-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="c5e36-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="c5e36-103">Určuje nastavení ověřování pro certifikát sdílené používá sdílené uzel.</span><span class="sxs-lookup"><span data-stu-id="c5e36-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="c5e36-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c5e36-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c5e36-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c5e36-105">\<behaviors></span></span>  
<span data-ttu-id="c5e36-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c5e36-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="c5e36-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c5e36-107">\<behavior></span></span>  
<span data-ttu-id="c5e36-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="c5e36-108">\<serviceCredentials></span></span>  
<span data-ttu-id="c5e36-109">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="c5e36-109">\<peer></span></span>  
<span data-ttu-id="c5e36-110">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="c5e36-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e36-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5e36-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5e36-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c5e36-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c5e36-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c5e36-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5e36-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="c5e36-114">Attributes</span></span>  
  
|<span data-ttu-id="c5e36-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="c5e36-115">Attribute</span></span>|<span data-ttu-id="c5e36-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c5e36-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="c5e36-117">Volitelné výčtu.</span><span class="sxs-lookup"><span data-stu-id="c5e36-117">Optional enumeration.</span></span> <span data-ttu-id="c5e36-118">Určuje jeden ze tří režimů slouží k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="c5e36-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="c5e36-119">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="c5e36-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="c5e36-120">Pokud nastavena na `Custom`, pak `customCertificateValidator` musí být uveden také.</span><span class="sxs-lookup"><span data-stu-id="c5e36-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="c5e36-121">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="c5e36-121">Optional string.</span></span> <span data-ttu-id="c5e36-122">Určuje typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="c5e36-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c5e36-123">Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="c5e36-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="c5e36-124">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="c5e36-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="c5e36-125">poskytuje sdílené výchozí validátor certifikátu, který ověřuje certifikátu partnerského proti úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="c5e36-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="c5e36-126">Také ověřuje, že certifikát řetězí platný kořenový.</span><span class="sxs-lookup"><span data-stu-id="c5e36-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="c5e36-127">Můžete implementovat vlastní validátor zadejte odlišné chování a používat tento atribut tak, aby odkazovalo na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="c5e36-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="c5e36-128">Volitelné výčtu.</span><span class="sxs-lookup"><span data-stu-id="c5e36-128">Optional enumeration.</span></span> <span data-ttu-id="c5e36-129">Určuje režim odvolání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c5e36-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="c5e36-130">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="c5e36-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="c5e36-131">Systém ověří, že sdílené certifikát nebyl odvolaný podle vyhledá v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="c5e36-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="c5e36-132">Tato kontrola může provést kontrolou online nebo seznam odvolaných certifikátů uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c5e36-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="c5e36-133">Kontrola odvolání může být vypnuto nastavením tohoto atributu na hodnotu NoCheck.</span><span class="sxs-lookup"><span data-stu-id="c5e36-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c5e36-134">Volitelné výčtu.</span><span class="sxs-lookup"><span data-stu-id="c5e36-134">Optional enumeration.</span></span> <span data-ttu-id="c5e36-135">Určuje umístění důvěryhodného úložiště, kde je ověřen certifikátu partnerského [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zabezpečení systému.</span><span class="sxs-lookup"><span data-stu-id="c5e36-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="c5e36-136">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="c5e36-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5e36-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c5e36-137">Child Elements</span></span>  
 <span data-ttu-id="c5e36-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="c5e36-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c5e36-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c5e36-139">Parent Elements</span></span>  
  
|<span data-ttu-id="c5e36-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="c5e36-140">Element</span></span>|<span data-ttu-id="c5e36-141">Popis</span><span class="sxs-lookup"><span data-stu-id="c5e36-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c5e36-142">\<sdílené ></span><span class="sxs-lookup"><span data-stu-id="c5e36-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="c5e36-143">Určuje, že aktuální přihlašovací údaje pro uzel sdílené.</span><span class="sxs-lookup"><span data-stu-id="c5e36-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5e36-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5e36-144">Remarks</span></span>  
 <span data-ttu-id="c5e36-145">`<authentication>` Element odpovídá <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="c5e36-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="c5e36-146">Tento element určuje validátor, která se vyvolá při ověřování sousedním sousedním v mřížce.</span><span class="sxs-lookup"><span data-stu-id="c5e36-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="c5e36-147">Když se nové sdílené pokusí navázat připojení sousedním, předá vlastní pověření na odpovídá partnera.</span><span class="sxs-lookup"><span data-stu-id="c5e36-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="c5e36-148">Validátor odpovídající partner je vyvolána k ověření pověření vzdálené strany.</span><span class="sxs-lookup"><span data-stu-id="c5e36-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="c5e36-149">Při každém navázání připojení sdílené v mřížce, oba partneři jsou vzájemně ověřeni, jsou vyvolány význam validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="c5e36-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5e36-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5e36-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="c5e36-151">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="c5e36-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="c5e36-152">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="c5e36-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="c5e36-153">Ověřování zpráv rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="c5e36-153">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="c5e36-154">Vlastní ověřování rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="c5e36-154">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="c5e36-155">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="c5e36-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
