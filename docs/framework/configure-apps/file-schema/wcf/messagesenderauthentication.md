---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c6183a8d27d56c7199b815ccb31b06f983a51b33
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398392"
---
# \<messageSenderAuthentication>
<span data-ttu-id="7b395-101">Určuje nastavení ověřování pro certifikát partnerských vztahů používaných odesílatelem zprávy.</span><span class="sxs-lookup"><span data-stu-id="7b395-101">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="7b395-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b395-102">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b395-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b395-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7b395-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b395-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b395-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b395-105">Attributes</span></span>  
  
|<span data-ttu-id="7b395-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b395-106">Attribute</span></span>|<span data-ttu-id="7b395-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7b395-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="7b395-108">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="7b395-108">Optional enumeration.</span></span> <span data-ttu-id="7b395-109">Určuje jeden z pěti režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="7b395-109">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="7b395-110">Tento atribut je typu <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="7b395-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="7b395-111">Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také.</span><span class="sxs-lookup"><span data-stu-id="7b395-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="7b395-112">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="7b395-112">Optional string.</span></span> <span data-ttu-id="7b395-113">Určuje typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="7b395-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="7b395-114">Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .</span><span class="sxs-lookup"><span data-stu-id="7b395-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="7b395-115">Tento atribut je typu <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="7b395-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="7b395-116">Windows Communication Foundation (WCF) poskytuje výchozí validátor certifikátu peere, který ověřuje partnerský certifikát pro úložiště důvěryhodných osob.</span><span class="sxs-lookup"><span data-stu-id="7b395-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="7b395-117">Také ověří, že certifikát řetězí až k platnému kořenu.</span><span class="sxs-lookup"><span data-stu-id="7b395-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="7b395-118">Můžete implementovat vlastní validátor pro určení jiného chování a použít tento atribut k odkazování na vlastní validátor.</span><span class="sxs-lookup"><span data-stu-id="7b395-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="7b395-119">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="7b395-119">Optional enumeration.</span></span> <span data-ttu-id="7b395-120">Určuje režim odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b395-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="7b395-121">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="7b395-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="7b395-122">Systém ověří, že se partnerský certifikát neodvolává tím, že ho vyhledá v seznamu odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7b395-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="7b395-123">Tuto kontrolu můžete provést buď kontrolou online, nebo se seznamem odvolaných certifikátů v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="7b395-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="7b395-124">Kontrolu odvolání lze zapnout nastavením tohoto atributu na hodnotu Nekontrolovat.</span><span class="sxs-lookup"><span data-stu-id="7b395-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="7b395-125">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="7b395-125">Optional enumeration.</span></span> <span data-ttu-id="7b395-126">Určuje umístění důvěryhodného úložiště, ve kterém je certifikát partnerského vztahu ověřen systémem zabezpečení WCF.</span><span class="sxs-lookup"><span data-stu-id="7b395-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="7b395-127">Tento atribut je typu <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="7b395-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b395-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b395-128">Child Elements</span></span>  
 <span data-ttu-id="7b395-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="7b395-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b395-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b395-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7b395-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b395-131">Element</span></span>|<span data-ttu-id="7b395-132">Description</span><span class="sxs-lookup"><span data-stu-id="7b395-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="7b395-133">Určuje aktuální pověření pro partnerský uzel.</span><span class="sxs-lookup"><span data-stu-id="7b395-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b395-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b395-134">Remarks</span></span>  
 <span data-ttu-id="7b395-135">Tento prvek musí být nakonfigurován, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="7b395-135">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="7b395-136">U výstupních kanálů se každá zpráva podepisuje pomocí certifikátu, který poskytuje [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="7b395-136">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="7b395-137">Všechny zprávy před doručením do aplikace jsou zkontrolovány proti pověření zprávy pomocí validátoru určeného `customCertificateValidatorType` atributem tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="7b395-137">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="7b395-138">Validátor může buď přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="7b395-138">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b395-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b395-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="7b395-140">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="7b395-140">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7b395-141">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="7b395-141">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="7b395-142">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7b395-142">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="7b395-143">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7b395-143">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="7b395-144">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="7b395-144">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
