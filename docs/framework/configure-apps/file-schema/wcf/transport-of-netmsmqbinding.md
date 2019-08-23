---
title: <transport> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934683"
---
# <a name="transport-of-netmsmqbinding"></a><span data-ttu-id="a7173-102">\<> přenosu > \<NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="a7173-102">\<transport> of \<netMsmqBinding></span></span>
<span data-ttu-id="a7173-103">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="a7173-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="a7173-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a7173-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a7173-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="a7173-105">\<bindings></span></span>  
<span data-ttu-id="a7173-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="a7173-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="a7173-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a7173-107">\<binding></span></span>  
<span data-ttu-id="a7173-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a7173-108">\<security></span></span>  
<span data-ttu-id="a7173-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="a7173-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7173-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7173-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7173-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a7173-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a7173-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a7173-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7173-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a7173-113">Attributes</span></span>  
  
|<span data-ttu-id="a7173-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a7173-114">Attribute</span></span>|<span data-ttu-id="a7173-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a7173-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7173-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="a7173-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="a7173-117">Určuje, jak musí být zpráva ověřena přenosem služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a7173-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="a7173-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a7173-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7173-119">NTato Bez ověřování.</span><span class="sxs-lookup"><span data-stu-id="a7173-119">-   None: No authentication.</span></span><br /><span data-ttu-id="a7173-120">- WindowsDomain: Ověřovací mechanismus používá službu Active Directory k načtení certifikátu X. 509 pro identifikátor zabezpečení přidružený ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="a7173-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="a7173-121">Pomocí této možnosti lze zkontrolovat seznam ACL fronty a ověřit, zda má uživatel oprávnění k zápisu do fronty.</span><span class="sxs-lookup"><span data-stu-id="a7173-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="a7173-122">Certifikát Kanál načte certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="a7173-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="a7173-123">Výchozí hodnota je `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="a7173-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="a7173-124">Pokud je tento atribut nastaven na `None`hodnotu `msmqProtectionLevel` , musí být atribut také nastaven na `None`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a7173-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="a7173-125">Tento atribut je typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="a7173-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="a7173-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="a7173-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="a7173-127">Určuje algoritmus, který se má použít pro šifrování zpráv na lince při přenosu zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="a7173-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="a7173-128">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a7173-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7173-129">- RC4Stream</span><span class="sxs-lookup"><span data-stu-id="a7173-129">-   RC4Stream</span></span><br /><span data-ttu-id="a7173-130">– AES</span><span class="sxs-lookup"><span data-stu-id="a7173-130">-   AES</span></span><br /><span data-ttu-id="a7173-131">– Výchozí hodnota je `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="a7173-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="a7173-132">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="a7173-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="a7173-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="a7173-133">msmqProtectionLevel</span></span>|<span data-ttu-id="a7173-134">Určuje způsob, jakým jsou zprávy zabezpečeny na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a7173-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="a7173-135">Šifrování zajišťuje integritu zprávy, zatímco při podepisování a šifrování je zajištěna integrita zprávy i Neodmítnutí.</span><span class="sxs-lookup"><span data-stu-id="a7173-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="a7173-136">To znamená, že zpráva skutečně pochází od odesílatele a odesilatele se říká, že je.</span><span class="sxs-lookup"><span data-stu-id="a7173-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="a7173-137">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a7173-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7173-138">NTato Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="a7173-138">-   None: No protection.</span></span><br /><span data-ttu-id="a7173-139">Osobě Zprávy jsou podepsány.</span><span class="sxs-lookup"><span data-stu-id="a7173-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a7173-140">EncryptAndSign Zprávy jsou zašifrovány a podepsány.</span><span class="sxs-lookup"><span data-stu-id="a7173-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="a7173-141">– Výchozí hodnota je `Sign`.</span><span class="sxs-lookup"><span data-stu-id="a7173-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="a7173-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="a7173-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="a7173-143">Určuje algoritmus hash, který se má použít k výpočtu výtahu zprávy.</span><span class="sxs-lookup"><span data-stu-id="a7173-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="a7173-144">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="a7173-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a7173-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="a7173-145">-   MD5</span></span><br /><span data-ttu-id="a7173-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="a7173-146">-   SHA1</span></span><br /><span data-ttu-id="a7173-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="a7173-147">-   SHA256</span></span><br /><span data-ttu-id="a7173-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="a7173-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="a7173-149">Výchozí hodnota je `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="a7173-149">The default is `SHA1`.</span></span> <span data-ttu-id="a7173-150">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="a7173-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="a7173-151">Microsoft doporučuje SHA256 nebo lepší z důvodu kolizí problémů s MD5 a SHA1.</span><span class="sxs-lookup"><span data-stu-id="a7173-151">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7173-152">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a7173-152">Child Elements</span></span>  
 <span data-ttu-id="a7173-153">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7173-153">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7173-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a7173-154">Parent Elements</span></span>  
  
|<span data-ttu-id="a7173-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="a7173-155">Element</span></span>|<span data-ttu-id="a7173-156">Popis</span><span class="sxs-lookup"><span data-stu-id="a7173-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a7173-157">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a7173-157">\<security></span></span>](security-of-netmsmqbinding.md)|<span data-ttu-id="a7173-158">Definuje nastavení zabezpečení přenosu pro přenosy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="a7173-158">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a7173-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7173-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="a7173-160">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="a7173-160">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="a7173-161">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a7173-161">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a7173-162">Vazby</span><span class="sxs-lookup"><span data-stu-id="a7173-162">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a7173-163">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a7173-163">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a7173-164">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a7173-164">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a7173-165">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="a7173-165">\<binding></span></span>](../../../misc/binding.md)
