---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 118159617a7f4c27ecc5e8fe077c28cfefac8537
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397616"
---
# \<peerAuthentication>
<span data-ttu-id="72d97-101">Určuje nastavení ověřování pro partnerský certifikát používaný rovnocenným uzlem.</span><span class="sxs-lookup"><span data-stu-id="72d97-101">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="72d97-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72d97-102">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72d97-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="72d97-103">Attributes and Elements</span></span>  
 <span data-ttu-id="72d97-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="72d97-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72d97-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="72d97-105">Attributes</span></span>  
  
|<span data-ttu-id="72d97-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="72d97-106">Attribute</span></span>|<span data-ttu-id="72d97-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72d97-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="72d97-108">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="72d97-108">Optional enumeration.</span></span> <span data-ttu-id="72d97-109">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="72d97-109">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="72d97-110">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="72d97-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="72d97-111">Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také.</span><span class="sxs-lookup"><span data-stu-id="72d97-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="72d97-112">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="72d97-112">Optional string.</span></span> <span data-ttu-id="72d97-113">Určuje typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="72d97-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="72d97-114">Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .</span><span class="sxs-lookup"><span data-stu-id="72d97-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="72d97-115">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="72d97-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="72d97-116">Windows Communication Foundation (WCF) poskytuje výchozí validátor certifikátu peere, který ověřuje partnerský certifikát pro úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="72d97-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="72d97-117">Také ověří, že certifikát řetězí až k platnému kořenu.</span><span class="sxs-lookup"><span data-stu-id="72d97-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="72d97-118">Můžete implementovat vlastní validátor pro určení jiného chování a použít tento atribut k odkazování na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="72d97-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="72d97-119">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="72d97-119">Optional enumeration.</span></span> <span data-ttu-id="72d97-120">Určuje režim odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="72d97-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="72d97-121">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="72d97-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="72d97-122">Systém ověří, že se partnerský certifikát neodvolává tím, že ho vyhledá v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="72d97-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="72d97-123">Tuto kontrolu můžete provést buď kontrolou online, nebo se seznamem odvolaných certifikátů v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="72d97-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="72d97-124">Kontrolu odvolání lze zapnout nastavením tohoto atributu na hodnotu Nekontrolovat.</span><span class="sxs-lookup"><span data-stu-id="72d97-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="72d97-125">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="72d97-125">Optional enumeration.</span></span> <span data-ttu-id="72d97-126">Určuje umístění důvěryhodného úložiště, ve kterém je certifikát partnerského vztahu ověřen systémem zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="72d97-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="72d97-127">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="72d97-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72d97-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="72d97-128">Child Elements</span></span>  
 <span data-ttu-id="72d97-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="72d97-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72d97-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="72d97-130">Parent Elements</span></span>  
  
|<span data-ttu-id="72d97-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="72d97-131">Element</span></span>|<span data-ttu-id="72d97-132">Description</span><span class="sxs-lookup"><span data-stu-id="72d97-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="72d97-133">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="72d97-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72d97-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72d97-134">Remarks</span></span>  
 <span data-ttu-id="72d97-135">`<authentication>`Prvek odpovídá <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> třídě.</span><span class="sxs-lookup"><span data-stu-id="72d97-135">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="72d97-136">Tento prvek určuje validátor, který je vyvolán při ověřování typu Neighbor-to-Neighbor v síti.</span><span class="sxs-lookup"><span data-stu-id="72d97-136">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="72d97-137">Když se nový partner pokusí vytvořit sousední připojení, předá partnerskému partnerovi své vlastní přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="72d97-137">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="72d97-138">K ověření přihlašovacích údajů vzdálené strany se vyvolá validátor daného respondéru.</span><span class="sxs-lookup"><span data-stu-id="72d97-138">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="72d97-139">Pokaždé, když je v síti navázáno připojení typu peer, oba partneři se vzájemně ověřují, což znamená, že jsou vyvolány validátory na obou koncích.</span><span class="sxs-lookup"><span data-stu-id="72d97-139">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72d97-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="72d97-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="72d97-141">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="72d97-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="72d97-142">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="72d97-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="72d97-143">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="72d97-143">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="72d97-144">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="72d97-144">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="72d97-145">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="72d97-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
