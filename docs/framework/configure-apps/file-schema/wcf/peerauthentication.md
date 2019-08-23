---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 7facf3eb54637445d1ae20297effc92605c81a61
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933993"
---
# <a name="peerauthentication"></a><span data-ttu-id="1c880-101">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="1c880-101">\<peerAuthentication></span></span>
<span data-ttu-id="1c880-102">Určuje nastavení ověřování pro partnerský certifikát používaný rovnocenným uzlem.</span><span class="sxs-lookup"><span data-stu-id="1c880-102">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="1c880-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1c880-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1c880-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="1c880-104">\<behaviors></span></span>  
<span data-ttu-id="1c880-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1c880-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="1c880-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="1c880-106">\<behavior></span></span>  
<span data-ttu-id="1c880-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="1c880-107">\<serviceCredentials></span></span>  
<span data-ttu-id="1c880-108">\<peer></span><span class="sxs-lookup"><span data-stu-id="1c880-108">\<peer></span></span>  
<span data-ttu-id="1c880-109">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="1c880-109">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c880-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c880-110">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c880-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c880-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1c880-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c880-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c880-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c880-113">Attributes</span></span>  
  
|<span data-ttu-id="1c880-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1c880-114">Attribute</span></span>|<span data-ttu-id="1c880-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1c880-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="1c880-116">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="1c880-116">Optional enumeration.</span></span> <span data-ttu-id="1c880-117">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="1c880-117">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="1c880-118">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="1c880-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="1c880-119">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="1c880-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="1c880-120">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="1c880-120">Optional string.</span></span> <span data-ttu-id="1c880-121">Určuje typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="1c880-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="1c880-122">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c880-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="1c880-123">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="1c880-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="1c880-124">Windows Communication Foundation (WCF) poskytuje výchozí validátor certifikátu peere, který ověřuje partnerský certifikát pro úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="1c880-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="1c880-125">Také ověří, že certifikát řetězí až k platnému kořenu.</span><span class="sxs-lookup"><span data-stu-id="1c880-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="1c880-126">Můžete implementovat vlastní validátor pro určení jiného chování a použít tento atribut k odkazování na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="1c880-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="1c880-127">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="1c880-127">Optional enumeration.</span></span> <span data-ttu-id="1c880-128">Určuje režim odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1c880-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="1c880-129">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="1c880-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="1c880-130">Systém ověří, že se partnerský certifikát neodvolává tím, že ho vyhledá v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="1c880-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="1c880-131">Tuto kontrolu můžete provést buď kontrolou online, nebo se seznamem odvolaných certifikátů v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1c880-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="1c880-132">Kontrolu odvolání lze zapnout nastavením tohoto atributu na hodnotu Nekontrolovat.</span><span class="sxs-lookup"><span data-stu-id="1c880-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="1c880-133">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="1c880-133">Optional enumeration.</span></span> <span data-ttu-id="1c880-134">Určuje umístění důvěryhodného úložiště, ve kterém je certifikát partnerského vztahu ověřen systémem zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="1c880-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="1c880-135">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="1c880-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c880-136">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c880-136">Child Elements</span></span>  
 <span data-ttu-id="1c880-137">Žádné</span><span class="sxs-lookup"><span data-stu-id="1c880-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c880-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c880-138">Parent Elements</span></span>  
  
|<span data-ttu-id="1c880-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c880-139">Element</span></span>|<span data-ttu-id="1c880-140">Popis</span><span class="sxs-lookup"><span data-stu-id="1c880-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c880-141">\<peer></span><span class="sxs-lookup"><span data-stu-id="1c880-141">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="1c880-142">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="1c880-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c880-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c880-143">Remarks</span></span>  
 <span data-ttu-id="1c880-144">`<authentication>` Prvek odpovídá<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídě.</span><span class="sxs-lookup"><span data-stu-id="1c880-144">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="1c880-145">Tento prvek určuje validátor, který je vyvolán při ověřování typu Neighbor-to-Neighbor v síti.</span><span class="sxs-lookup"><span data-stu-id="1c880-145">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="1c880-146">Když se nový partner pokusí vytvořit sousední připojení, předá partnerskému partnerovi své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="1c880-146">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="1c880-147">K ověření přihlašovacích údajů vzdálené strany se vyvolá validátor daného respondéru.</span><span class="sxs-lookup"><span data-stu-id="1c880-147">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="1c880-148">Pokaždé, když je v síti navázáno připojení typu peer, oba partneři se vzájemně ověřují, což znamená, že jsou vyvolány validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="1c880-148">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c880-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c880-149">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="1c880-150">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="1c880-150">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1c880-151">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="1c880-151">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="1c880-152">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1c880-152">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1c880-153">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1c880-153">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1c880-154">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="1c880-154">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
