---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 8a3beb42d1064e6c6629014369628248b4cd5c8d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416011"
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="d0226-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="d0226-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="d0226-103">Určuje nastavení ověřování pro sdílené certifikát používaný službou odesílatele zprávy.</span><span class="sxs-lookup"><span data-stu-id="d0226-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="d0226-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0226-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0226-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d0226-105">\<behaviors></span></span>  
<span data-ttu-id="d0226-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d0226-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d0226-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="d0226-107">\<behavior></span></span>  
<span data-ttu-id="d0226-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="d0226-108">\<serviceCredentials></span></span>  
<span data-ttu-id="d0226-109">\<sdílená ></span><span class="sxs-lookup"><span data-stu-id="d0226-109">\<peer></span></span>  
<span data-ttu-id="d0226-110">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="d0226-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0226-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0226-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0226-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d0226-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d0226-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d0226-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0226-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d0226-114">Attributes</span></span>  
  
|<span data-ttu-id="d0226-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d0226-115">Attribute</span></span>|<span data-ttu-id="d0226-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d0226-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="d0226-117">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="d0226-117">Optional enumeration.</span></span> <span data-ttu-id="d0226-118">Určuje jeden z pěti režimů pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="d0226-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="d0226-119">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="d0226-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="d0226-120">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="d0226-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="d0226-121">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="d0226-121">Optional string.</span></span> <span data-ttu-id="d0226-122">Určuje typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="d0226-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="d0226-123">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="d0226-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="d0226-124">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="d0226-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d0226-125">Windows Communication Foundation (WCF) poskytuje sdílené výchozí validátor certifikátu, který ověřuje certifikát peer proti úložišti důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="d0226-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="d0226-126">Také ověřuje, že certifikát zřetězený platného kořenového.</span><span class="sxs-lookup"><span data-stu-id="d0226-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="d0226-127">Můžete implementovat vlastní validátor určit různá chování a používání tohoto atributu na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="d0226-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="d0226-128">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="d0226-128">Optional enumeration.</span></span> <span data-ttu-id="d0226-129">Určuje režim odvolání certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d0226-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="d0226-130">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="d0226-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="d0226-131">Systém ověří, že peer certifikát nebyl odvolaný ve vyhledávání v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="d0226-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="d0226-132">Tato kontrola lze provést tak, že zkontrolujete online nebo seznam odvolaných certifikátů uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d0226-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="d0226-133">Kontrola odvolání můžete vypnout pomocí nastavení tohoto atributu na NoCheck.</span><span class="sxs-lookup"><span data-stu-id="d0226-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="d0226-134">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="d0226-134">Optional enumeration.</span></span> <span data-ttu-id="d0226-135">Určuje umístění úložiště pro důvěryhodného kde ověření certifikátu druhé strany systém zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="d0226-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="d0226-136">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="d0226-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0226-137">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d0226-137">Child Elements</span></span>  
 <span data-ttu-id="d0226-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="d0226-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0226-139">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d0226-139">Parent Elements</span></span>  
  
|<span data-ttu-id="d0226-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="d0226-140">Element</span></span>|<span data-ttu-id="d0226-141">Popis</span><span class="sxs-lookup"><span data-stu-id="d0226-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0226-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="d0226-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="d0226-143">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="d0226-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0226-144">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0226-144">Remarks</span></span>  
 <span data-ttu-id="d0226-145">Tento element musí být nakonfigurované, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="d0226-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="d0226-146">Pro výstup kanály, každá zpráva je podepsaná pomocí certifikátu poskytnutého [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="d0226-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="d0226-147">Všechny zprávy, předtím, než se doručí do aplikace, jsou porovnávána s přihlašovacími údaji zprávy pomocí validátor určené `customCertificateValidatorType` atribut tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="d0226-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="d0226-148">Validátor můžete přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d0226-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0226-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0226-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="d0226-150">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="d0226-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="d0226-151">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="d0226-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="d0226-152">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="d0226-152">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="d0226-153">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="d0226-153">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="d0226-154">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="d0226-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
