---
title: '&lt;transport&gt; – &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 7eac5c7a0da71e2d06929322ac5c702d83a1ea65
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597434"
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="31fcf-102">&lt;transport&gt; – &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="31fcf-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="31fcf-103">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="31fcf-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="31fcf-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="31fcf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="31fcf-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="31fcf-105">\<bindings></span></span>  
<span data-ttu-id="31fcf-106">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="31fcf-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="31fcf-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="31fcf-107">\<binding></span></span>  
<span data-ttu-id="31fcf-108">\<security></span><span class="sxs-lookup"><span data-stu-id="31fcf-108">\<security></span></span>  
<span data-ttu-id="31fcf-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="31fcf-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31fcf-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31fcf-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31fcf-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="31fcf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="31fcf-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="31fcf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31fcf-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="31fcf-113">Attributes</span></span>  
  
|<span data-ttu-id="31fcf-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="31fcf-114">Attribute</span></span>|<span data-ttu-id="31fcf-115">Popis</span><span class="sxs-lookup"><span data-stu-id="31fcf-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31fcf-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="31fcf-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="31fcf-117">Určuje, jak ověření zprávy dopravou služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="31fcf-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="31fcf-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="31fcf-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="31fcf-119">-Žádný: Bez ověřování.</span><span class="sxs-lookup"><span data-stu-id="31fcf-119">-   None: No authentication.</span></span><br /><span data-ttu-id="31fcf-120">– Třída: Mechanismus ověřování služby Active Directory používá k načtení certifikátu X.509 pro identifikátor zabezpečení spojený se zprávou.</span><span class="sxs-lookup"><span data-stu-id="31fcf-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="31fcf-121">Potom se používá ke kontrole, že seznam ACL fronty, aby uživatel má oprávnění k zápisu pro danou frontu.</span><span class="sxs-lookup"><span data-stu-id="31fcf-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="31fcf-122">-Certifikátu: Kanál načte příslušný certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="31fcf-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="31fcf-123">Výchozí hodnota je `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="31fcf-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="31fcf-124">Pokud tento atribut je nastaven na `None`, `msmqProtectionLevel` atribut musí být také nastaven na `None`.</span><span class="sxs-lookup"><span data-stu-id="31fcf-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="31fcf-125">Tento atribut je typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="31fcf-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="31fcf-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="31fcf-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="31fcf-127">Určuje algoritmus se má použít pro šifrování zpráv na lince, přenos zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="31fcf-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="31fcf-128">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="31fcf-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="31fcf-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="31fcf-129">-   RC4Stream</span></span><br /><span data-ttu-id="31fcf-130">-   AES</span><span class="sxs-lookup"><span data-stu-id="31fcf-130">-   AES</span></span><br /><span data-ttu-id="31fcf-131">– Výchozí hodnota je `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="31fcf-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="31fcf-132">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="31fcf-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="31fcf-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="31fcf-133">msmqProtectionLevel</span></span>|<span data-ttu-id="31fcf-134">Určuje že způsob, jak zprávy jsou zabezpečená na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="31fcf-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="31fcf-135">Šifrování zajišťuje, že zajišťuje zprávu integrity, při přihlašování a šifrování zpráv integrity a nepopiratelnosti.</span><span class="sxs-lookup"><span data-stu-id="31fcf-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="31fcf-136">To znamená že zpráva pochází skutečně od odesílatele a odesílatel je, který říká, že je.</span><span class="sxs-lookup"><span data-stu-id="31fcf-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="31fcf-137">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="31fcf-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="31fcf-138">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="31fcf-138">-   None: No protection.</span></span><br /><span data-ttu-id="31fcf-139">– Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="31fcf-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="31fcf-140">-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="31fcf-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="31fcf-141">– Výchozí hodnota je `Sign`.</span><span class="sxs-lookup"><span data-stu-id="31fcf-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="31fcf-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="31fcf-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="31fcf-143">Určuje algoritmus hash, který má být použit pro výpočet výběru zprávy.</span><span class="sxs-lookup"><span data-stu-id="31fcf-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="31fcf-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="31fcf-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="31fcf-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="31fcf-145">-   MD5</span></span><br /><span data-ttu-id="31fcf-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="31fcf-146">-   SHA1</span></span><br /><span data-ttu-id="31fcf-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="31fcf-147">-   SHA256</span></span><br /><span data-ttu-id="31fcf-148">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="31fcf-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="31fcf-149">Výchozí hodnota je `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="31fcf-149">The default is `SHA1`.</span></span> <span data-ttu-id="31fcf-150">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="31fcf-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31fcf-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="31fcf-151">Child Elements</span></span>  
 <span data-ttu-id="31fcf-152">Žádná</span><span class="sxs-lookup"><span data-stu-id="31fcf-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31fcf-153">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="31fcf-153">Parent Elements</span></span>  
  
|<span data-ttu-id="31fcf-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="31fcf-154">Element</span></span>|<span data-ttu-id="31fcf-155">Popis</span><span class="sxs-lookup"><span data-stu-id="31fcf-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="31fcf-156">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="31fcf-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="31fcf-157">Definuje nastavení zabezpečení přenosu pro přenosy tohoto zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="31fcf-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31fcf-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31fcf-158">See also</span></span>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="31fcf-159">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="31fcf-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="31fcf-160">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="31fcf-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="31fcf-161">Vazby</span><span class="sxs-lookup"><span data-stu-id="31fcf-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="31fcf-162">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="31fcf-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="31fcf-163">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="31fcf-163">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="31fcf-164">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="31fcf-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
