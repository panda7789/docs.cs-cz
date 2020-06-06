---
title: <transport> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152954"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="6fbe9-102">\<transport> z \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="6fbe9-102">\<transport> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="6fbe9-103">Definuje nastavení zabezpečení pro přenos Integration služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="6fbe9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fbe9-104">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fbe9-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6fbe9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6fbe9-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fbe9-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="6fbe9-107">Attributes</span></span>  
  
|<span data-ttu-id="6fbe9-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="6fbe9-108">Attribute</span></span>|<span data-ttu-id="6fbe9-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6fbe9-109">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="6fbe9-110">Určuje, jak musí být zpráva ověřena přenosem služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-110">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="6fbe9-111">Pokud je tento atribut nastaven na `None` hodnotu, `msmqProtectionLevel` musí být hodnota atributu také nastavena na `None` .</span><span class="sxs-lookup"><span data-stu-id="6fbe9-111">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="6fbe9-112">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6fbe9-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6fbe9-113">-None: žádné ověřování.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-113">-   None: No authentication.</span></span><br /><span data-ttu-id="6fbe9-114">-WindowsDomain: ověřovací mechanismus používá službu Active Directory k získání certifikátu X. 509 pro identifikátor SID přidružený ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-114">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="6fbe9-115">Pomocí této možnosti lze zkontrolovat seznam ACL fronty a zajistit tak, že uživatel má oprávnění k zápisu do fronty.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-115">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="6fbe9-116">-Certificate: kanál získá certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-116">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="6fbe9-117">Výchozí hodnota je WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-117">The default value is WindowsDomain.</span></span> <span data-ttu-id="6fbe9-118">Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode> .</span><span class="sxs-lookup"><span data-stu-id="6fbe9-118">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="6fbe9-119">Určuje algoritmus, který se má použít pro šifrování zpráv na lince při přenosu zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-119">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="6fbe9-120">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6fbe9-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6fbe9-121">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="6fbe9-121">-   RC4Stream</span></span><br /><span data-ttu-id="6fbe9-122">– AES</span><span class="sxs-lookup"><span data-stu-id="6fbe9-122">-   AES</span></span><br /><br /> <span data-ttu-id="6fbe9-123">Výchozí hodnota je RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-123">The default value is RC4Stream.</span></span> <span data-ttu-id="6fbe9-124">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="6fbe9-124">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="6fbe9-125">Určuje, jak je zpráva zabezpečena na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-125">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="6fbe9-126">Šifrování zajišťuje integritu zpráv i v době, kdy EncryptAndSign zajišťuje integritu zprávy i neneodvolatelnost; To znamená, že zpráva skutečně pochází od odesílatele a odesilatelem je, že k nim říká.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-126">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="6fbe9-127">-Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6fbe9-127">-   Valid values include the following:</span></span><br /><span data-ttu-id="6fbe9-128">-None: bez ochrany.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-128">-   None: No protection.</span></span><br /><span data-ttu-id="6fbe9-129">-Sign: zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-129">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="6fbe9-130">-EncryptAndSign: zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-130">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="6fbe9-131">Výchozí hodnota je Sign (podepsat).</span><span class="sxs-lookup"><span data-stu-id="6fbe9-131">The default value is Sign.</span></span> <span data-ttu-id="6fbe9-132">Tento atribut je typu ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-132">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="6fbe9-133">– Určuje algoritmus, který se má použít při výpočtu výtahu jako součásti signatur.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-133">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="6fbe9-134">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6fbe9-134">Valid values include the following:</span></span><br /><span data-ttu-id="6fbe9-135">– MD5</span><span class="sxs-lookup"><span data-stu-id="6fbe9-135">-   MD5</span></span><br /><span data-ttu-id="6fbe9-136">– SHA1</span><span class="sxs-lookup"><span data-stu-id="6fbe9-136">-   SHA1</span></span><br /><span data-ttu-id="6fbe9-137">– SHA256</span><span class="sxs-lookup"><span data-stu-id="6fbe9-137">-   SHA256</span></span><br /><span data-ttu-id="6fbe9-138">– SHA512</span><span class="sxs-lookup"><span data-stu-id="6fbe9-138">-   SHA512</span></span><br /><br /> <span data-ttu-id="6fbe9-139">Výchozí hodnota je SHA1.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-139">The default value is SHA1.</span></span> <span data-ttu-id="6fbe9-140">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="6fbe9-140">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="6fbe9-141">Microsoft doporučuje SHA256 nebo lepší z důvodu kolizí problémů s MD5 a SHA1.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-141">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fbe9-142">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6fbe9-142">Child Elements</span></span>  
 <span data-ttu-id="6fbe9-143">Žádné</span><span class="sxs-lookup"><span data-stu-id="6fbe9-143">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6fbe9-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6fbe9-144">Parent Elements</span></span>  
  
|<span data-ttu-id="6fbe9-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="6fbe9-145">Element</span></span>|<span data-ttu-id="6fbe9-146">Description</span><span class="sxs-lookup"><span data-stu-id="6fbe9-146">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="6fbe9-147">Definuje nastavení zabezpečení pro vazbu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-147">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fbe9-148">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fbe9-148">Remarks</span></span>  
 <span data-ttu-id="6fbe9-149">Tento prvek zapouzdřuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-149">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="6fbe9-150">Nastavení jsou stejná pro integraci služby Řízení front zpráv i pro přenos ve frontě.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-150">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="6fbe9-151">Umožňuje nastavit režim ověřování, šifrovací algoritmus, zabezpečený algoritmus hash a úroveň ochrany.</span><span class="sxs-lookup"><span data-stu-id="6fbe9-151">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fbe9-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="6fbe9-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="6fbe9-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6fbe9-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6fbe9-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="6fbe9-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6fbe9-155">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="6fbe9-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6fbe9-156">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6fbe9-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
