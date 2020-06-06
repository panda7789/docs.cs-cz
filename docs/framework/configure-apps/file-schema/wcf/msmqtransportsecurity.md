---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153006"
---
# \<msmqTransportSecurity>
<span data-ttu-id="57525-101">Určuje nastavení zabezpečení přenosu služby MSMQ pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="57525-101">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegration>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<msmqTransportSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="57525-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57525-102">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57525-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57525-103">Attributes and Elements</span></span>  
 <span data-ttu-id="57525-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57525-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57525-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="57525-105">Attributes</span></span>  
  
|<span data-ttu-id="57525-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="57525-106">Attribute</span></span>|<span data-ttu-id="57525-107">Popis</span><span class="sxs-lookup"><span data-stu-id="57525-107">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="57525-108">Určuje, jak musí být zpráva ověřena přenosem služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="57525-108">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="57525-109">Pokud je tento atribut nastaven na `None` hodnotu, `msmqProtectionLevel` musí být hodnota atributu také nastavena na `None` .</span><span class="sxs-lookup"><span data-stu-id="57525-109">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="57525-110">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="57525-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57525-111">-None: žádné ověřování.</span><span class="sxs-lookup"><span data-stu-id="57525-111">-   None: No authentication.</span></span><br /><span data-ttu-id="57525-112">-Windows: ověřovací mechanismus používá službu Active Directory k získání certifikátu X. 509 pro identifikátor SID přidružený ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="57525-112">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="57525-113">Pomocí této možnosti lze zkontrolovat seznam ACL fronty a zajistit tak, že uživatel má oprávnění k zápisu do fronty.</span><span class="sxs-lookup"><span data-stu-id="57525-113">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="57525-114">-Certificate: kanál získá certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="57525-114">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="57525-115">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="57525-115">The default value is Windows.</span></span> <span data-ttu-id="57525-116">Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="57525-116">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="57525-117">Určuje algoritmus, který se má použít pro šifrování zpráv na lince při přenosu zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="57525-117">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="57525-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="57525-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57525-119">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="57525-119">-   RC4Stream</span></span><br /><span data-ttu-id="57525-120">– AES</span><span class="sxs-lookup"><span data-stu-id="57525-120">-   AES</span></span><br /><br /> <span data-ttu-id="57525-121">Výchozí hodnota je RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="57525-121">The default value is RC4Stream.</span></span> <span data-ttu-id="57525-122">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="57525-122">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="57525-123">Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="57525-123">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="57525-124">Šifrování zajišťuje integritu zpráv i v době, kdy EncryptAndSign zajišťuje integritu zprávy i neneodvolatelnost; To znamená, že zpráva skutečně pochází od odesílatele a odesilatelem je, že k nim říká.</span><span class="sxs-lookup"><span data-stu-id="57525-124">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="57525-125">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="57525-125">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57525-126">-None: bez ochrany.</span><span class="sxs-lookup"><span data-stu-id="57525-126">-   None: No protection.</span></span><br /><span data-ttu-id="57525-127">-Sign: zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="57525-127">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="57525-128">-EncryptAndSign: zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="57525-128">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="57525-129">Výchozí hodnota je Sign (podepsat).</span><span class="sxs-lookup"><span data-stu-id="57525-129">The default value is Sign.</span></span> <span data-ttu-id="57525-130">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="57525-130">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="57525-131">Určuje algoritmus, který se má použít při výpočtu výtahu jako součásti signatur.</span><span class="sxs-lookup"><span data-stu-id="57525-131">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="57525-132">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="57525-132">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="57525-133">– MD5</span><span class="sxs-lookup"><span data-stu-id="57525-133">-   MD5</span></span><br /><span data-ttu-id="57525-134">– SHA1</span><span class="sxs-lookup"><span data-stu-id="57525-134">-   SHA1</span></span><br /><span data-ttu-id="57525-135">– SHA256</span><span class="sxs-lookup"><span data-stu-id="57525-135">-   SHA256</span></span><br /><span data-ttu-id="57525-136">– SHA512</span><span class="sxs-lookup"><span data-stu-id="57525-136">-   SHA512</span></span><br /><br /> <span data-ttu-id="57525-137">Výchozí hodnota je SHA1.</span><span class="sxs-lookup"><span data-stu-id="57525-137">The default value is SHA1.</span></span> <span data-ttu-id="57525-138">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="57525-138">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="57525-139">Microsoft doporučuje SHA256 nebo lepší z důvodu kolizí problémů s MD5 a SHA1.</span><span class="sxs-lookup"><span data-stu-id="57525-139">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57525-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57525-140">Child Elements</span></span>  
 <span data-ttu-id="57525-141">Žádné</span><span class="sxs-lookup"><span data-stu-id="57525-141">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57525-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57525-142">Parent Elements</span></span>  
  
|<span data-ttu-id="57525-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="57525-143">Element</span></span>|<span data-ttu-id="57525-144">Description</span><span class="sxs-lookup"><span data-stu-id="57525-144">Description</span></span>|  
|-------------|-----------------|  
|[\<msmqIntegration>](msmqintegration.md)|<span data-ttu-id="57525-145">Určuje nastavení vyžadované pro interakci s odesílatelem nebo příjemcem služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="57525-145">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[\<msmqTransport>](msmqtransport.md)|<span data-ttu-id="57525-146">Určuje vlastnosti komunikace služby Řízení front pro službu Windows Communication Foundation (WCF), která používá nativní protokol MSMQ.</span><span class="sxs-lookup"><span data-stu-id="57525-146">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57525-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57525-147">Remarks</span></span>  
 <span data-ttu-id="57525-148">Další informace o zabezpečení přenosu najdete v tématu [zabezpečení přenosu](../../../wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="57525-148">For more information on transport security, see [Transport Security](../../../wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57525-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="57525-149">See also</span></span>

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="57525-150">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="57525-150">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="57525-151">Přenosy</span><span class="sxs-lookup"><span data-stu-id="57525-151">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="57525-152">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="57525-152">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="57525-153">Vazby</span><span class="sxs-lookup"><span data-stu-id="57525-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="57525-154">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="57525-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="57525-155">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="57525-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="57525-156">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="57525-156">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
