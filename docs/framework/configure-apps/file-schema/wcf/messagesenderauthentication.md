---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c1d3662b2ceda83eb32abe99244e926332214698
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931327"
---
# <a name="messagesenderauthentication"></a><span data-ttu-id="a8c94-101">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="a8c94-101">\<messageSenderAuthentication></span></span>
<span data-ttu-id="a8c94-102">Určuje nastavení ověřování pro certifikát partnerských vztahů používaných odesílatelem zprávy.</span><span class="sxs-lookup"><span data-stu-id="a8c94-102">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="a8c94-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a8c94-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="a8c94-104">\<> chování</span><span class="sxs-lookup"><span data-stu-id="a8c94-104">\<behaviors></span></span>  
<span data-ttu-id="a8c94-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="a8c94-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="a8c94-106">\<> chování</span><span class="sxs-lookup"><span data-stu-id="a8c94-106">\<behavior></span></span>  
<span data-ttu-id="a8c94-107">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="a8c94-107">\<serviceCredentials></span></span>  
<span data-ttu-id="a8c94-108">\<peer></span><span class="sxs-lookup"><span data-stu-id="a8c94-108">\<peer></span></span>  
<span data-ttu-id="a8c94-109">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="a8c94-109">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8c94-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a8c94-110">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a8c94-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a8c94-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a8c94-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a8c94-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a8c94-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a8c94-113">Attributes</span></span>  
  
|<span data-ttu-id="a8c94-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a8c94-114">Attribute</span></span>|<span data-ttu-id="a8c94-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a8c94-115">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="a8c94-116">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="a8c94-116">Optional enumeration.</span></span> <span data-ttu-id="a8c94-117">Určuje jeden z pěti režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="a8c94-117">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="a8c94-118">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="a8c94-118">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="a8c94-119">Je-li `Custom`nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="a8c94-119">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="a8c94-120">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a8c94-120">Optional string.</span></span> <span data-ttu-id="a8c94-121">Určuje typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="a8c94-121">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a8c94-122">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a8c94-122">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="a8c94-123">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="a8c94-123">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="a8c94-124">Windows Communication Foundation (WCF) poskytuje výchozí validátor certifikátu peere, který ověřuje partnerský certifikát pro úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="a8c94-124">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="a8c94-125">Také ověří, že certifikát řetězí až k platnému kořenu.</span><span class="sxs-lookup"><span data-stu-id="a8c94-125">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="a8c94-126">Můžete implementovat vlastní validátor pro určení jiného chování a použít tento atribut k odkazování na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="a8c94-126">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="a8c94-127">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="a8c94-127">Optional enumeration.</span></span> <span data-ttu-id="a8c94-128">Určuje režim odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="a8c94-128">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="a8c94-129">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="a8c94-129">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="a8c94-130">Systém ověří, že se partnerský certifikát neodvolává tím, že ho vyhledá v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="a8c94-130">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="a8c94-131">Tuto kontrolu můžete provést buď kontrolou online, nebo se seznamem odvolaných certifikátů v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a8c94-131">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="a8c94-132">Kontrolu odvolání lze zapnout nastavením tohoto atributu na hodnotu Nekontrolovat.</span><span class="sxs-lookup"><span data-stu-id="a8c94-132">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="a8c94-133">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="a8c94-133">Optional enumeration.</span></span> <span data-ttu-id="a8c94-134">Určuje umístění důvěryhodného úložiště, ve kterém je certifikát partnerského vztahu ověřen systémem zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="a8c94-134">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="a8c94-135">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="a8c94-135">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a8c94-136">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a8c94-136">Child Elements</span></span>  
 <span data-ttu-id="a8c94-137">Žádné</span><span class="sxs-lookup"><span data-stu-id="a8c94-137">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a8c94-138">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a8c94-138">Parent Elements</span></span>  
  
|<span data-ttu-id="a8c94-139">Prvek</span><span class="sxs-lookup"><span data-stu-id="a8c94-139">Element</span></span>|<span data-ttu-id="a8c94-140">Popis</span><span class="sxs-lookup"><span data-stu-id="a8c94-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a8c94-141">\<peer></span><span class="sxs-lookup"><span data-stu-id="a8c94-141">\<peer></span></span>](peer-of-servicecredentials.md)|<span data-ttu-id="a8c94-142">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="a8c94-142">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8c94-143">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8c94-143">Remarks</span></span>  
 <span data-ttu-id="a8c94-144">Tento prvek musí být nakonfigurován, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="a8c94-144">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="a8c94-145">U výstupních kanálů se každá zpráva podepisuje pomocí certifikátu, který poskytuje [ \<> certifikátu](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="a8c94-145">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="a8c94-146">Všechny zprávy před doručením do aplikace jsou zkontrolovány proti pověření zprávy pomocí validátoru určeného `customCertificateValidatorType` atributem tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="a8c94-146">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="a8c94-147">Validátor může buď přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="a8c94-147">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8c94-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8c94-148">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="a8c94-149">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="a8c94-149">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a8c94-150">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="a8c94-150">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="a8c94-151">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a8c94-151">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="a8c94-152">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a8c94-152">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="a8c94-153">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="a8c94-153">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
