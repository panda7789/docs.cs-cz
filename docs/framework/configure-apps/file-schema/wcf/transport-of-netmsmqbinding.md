---
title: <transport> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152928"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="8f0b7-102">\<transport> z \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="8f0b7-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="8f0b7-103">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-103">Defines the transport security settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="8f0b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f0b7-104">Syntax</span></span>  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f0b7-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8f0b7-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8f0b7-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f0b7-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8f0b7-107">Attributes</span></span>  
  
|<span data-ttu-id="8f0b7-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8f0b7-108">Attribute</span></span>|<span data-ttu-id="8f0b7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8f0b7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8f0b7-110">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="8f0b7-110">msmqAuthenticationMode</span></span>|<span data-ttu-id="8f0b7-111">Určuje, jak musí být zpráva ověřena přenosem služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="8f0b7-112">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8f0b7-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8f0b7-113">-None: žádné ověřování.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-113">-   None: No authentication.</span></span><br /><span data-ttu-id="8f0b7-114">-WindowsDomain: ověřovací mechanismus používá službu Active Directory k načtení certifikátu X. 509 pro identifikátor zabezpečení přidružený ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-114">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="8f0b7-115">Pomocí této možnosti lze zkontrolovat seznam ACL fronty a ověřit, zda má uživatel oprávnění k zápisu do fronty.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-115">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="8f0b7-116">-Certificate: kanál načte certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-116">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="8f0b7-117">Výchozí formát je `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-117">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="8f0b7-118">Pokud je tento atribut nastaven na hodnotu `None` , `msmqProtectionLevel` musí být atribut také nastaven na hodnotu `None` .</span><span class="sxs-lookup"><span data-stu-id="8f0b7-118">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="8f0b7-119">Tento atribut je typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="8f0b7-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="8f0b7-120">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="8f0b7-120">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="8f0b7-121">Určuje algoritmus, který se má použít pro šifrování zpráv na lince při přenosu zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-121">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="8f0b7-122">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8f0b7-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8f0b7-123">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="8f0b7-123">-   RC4Stream</span></span><br /><span data-ttu-id="8f0b7-124">– AES</span><span class="sxs-lookup"><span data-stu-id="8f0b7-124">-   AES</span></span><br /><span data-ttu-id="8f0b7-125">– Výchozí hodnota je `RC4Stream` .</span><span class="sxs-lookup"><span data-stu-id="8f0b7-125">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="8f0b7-126">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="8f0b7-126">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="8f0b7-127">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="8f0b7-127">msmqProtectionLevel</span></span>|<span data-ttu-id="8f0b7-128">Určuje způsob, jakým jsou zprávy zabezpečeny na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-128">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="8f0b7-129">Šifrování zajišťuje integritu zprávy, zatímco při podepisování a šifrování je zajištěna integrita zprávy i Neodmítnutí.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-129">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="8f0b7-130">To znamená, že zpráva skutečně pochází od odesílatele a odesilatele, kterou říkají.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-130">That is, the message indeed came from the sender and the sender is who they say they are.</span></span> <span data-ttu-id="8f0b7-131">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8f0b7-131">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8f0b7-132">-None: bez ochrany.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-132">-   None: No protection.</span></span><br /><span data-ttu-id="8f0b7-133">-Sign: zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-133">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="8f0b7-134">-EncryptAndSign: zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-134">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="8f0b7-135">– Výchozí hodnota je `Sign` .</span><span class="sxs-lookup"><span data-stu-id="8f0b7-135">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="8f0b7-136">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="8f0b7-136">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="8f0b7-137">Určuje algoritmus hash, který se má použít k výpočtu výtahu zprávy.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-137">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="8f0b7-138">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8f0b7-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8f0b7-139">– MD5</span><span class="sxs-lookup"><span data-stu-id="8f0b7-139">-   MD5</span></span><br /><span data-ttu-id="8f0b7-140">– SHA1</span><span class="sxs-lookup"><span data-stu-id="8f0b7-140">-   SHA1</span></span><br /><span data-ttu-id="8f0b7-141">– SHA256</span><span class="sxs-lookup"><span data-stu-id="8f0b7-141">-   SHA256</span></span><br /><span data-ttu-id="8f0b7-142">– SHA512</span><span class="sxs-lookup"><span data-stu-id="8f0b7-142">-   SHA512</span></span><br /><br /> <span data-ttu-id="8f0b7-143">Výchozí formát je `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-143">The default is `SHA1`.</span></span> <span data-ttu-id="8f0b7-144">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm> .</span><span class="sxs-lookup"><span data-stu-id="8f0b7-144">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="8f0b7-145">Microsoft doporučuje SHA256 nebo lepší z důvodu kolizí problémů s MD5 a SHA1.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-145">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f0b7-146">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8f0b7-146">Child Elements</span></span>  
 <span data-ttu-id="8f0b7-147">Žádné</span><span class="sxs-lookup"><span data-stu-id="8f0b7-147">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f0b7-148">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8f0b7-148">Parent Elements</span></span>  
  
|<span data-ttu-id="8f0b7-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="8f0b7-149">Element</span></span>|<span data-ttu-id="8f0b7-150">Description</span><span class="sxs-lookup"><span data-stu-id="8f0b7-150">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|<span data-ttu-id="8f0b7-151">Definuje nastavení zabezpečení přenosu pro přenosy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="8f0b7-151">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f0b7-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f0b7-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="8f0b7-153">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="8f0b7-153">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="8f0b7-154">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8f0b7-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8f0b7-155">Vazby</span><span class="sxs-lookup"><span data-stu-id="8f0b7-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8f0b7-156">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="8f0b7-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8f0b7-157">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8f0b7-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
