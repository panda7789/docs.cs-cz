---
title: '&lt;transport&gt; – &lt;netMsmqBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: 513c8658760af1ba37f294281f046e1355c3a6ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lttransportgt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="a78ac-102">&lt;transport&gt; – &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a78ac-102">&lt;transport&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="a78ac-103">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="a78ac-103">Defines the transport security settings.</span></span>  
  
 <span data-ttu-id="a78ac-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a78ac-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a78ac-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a78ac-105">\<bindings></span></span>  
<span data-ttu-id="a78ac-106">\<– netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="a78ac-106">\<netMsmqBinding></span></span>  
<span data-ttu-id="a78ac-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a78ac-107">\<binding></span></span>  
<span data-ttu-id="a78ac-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="a78ac-108">\<security></span></span>  
<span data-ttu-id="a78ac-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="a78ac-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a78ac-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a78ac-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a78ac-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a78ac-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a78ac-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a78ac-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a78ac-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="a78ac-113">Attributes</span></span>  
  
|<span data-ttu-id="a78ac-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="a78ac-114">Attribute</span></span>|<span data-ttu-id="a78ac-115">Popis</span><span class="sxs-lookup"><span data-stu-id="a78ac-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a78ac-116">msmqAuthenticationMode</span><span class="sxs-lookup"><span data-stu-id="a78ac-116">msmqAuthenticationMode</span></span>|<span data-ttu-id="a78ac-117">Určuje, jak ověřit zprávu přenos MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a78ac-117">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="a78ac-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a78ac-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a78ac-119">-None: Bez ověřování.</span><span class="sxs-lookup"><span data-stu-id="a78ac-119">-   None: No authentication.</span></span><br /><span data-ttu-id="a78ac-120">-Třídy WindowsDomain: Ověřovací mechanismus používá služby Active Directory pro načtení certifikátu X.509 pro identifikátor zabezpečení spojený se zprávou.</span><span class="sxs-lookup"><span data-stu-id="a78ac-120">-   WindowsDomain: The authentication mechanism uses Active Directory to retrieve the X.509 certificate for the security identifier associated with the message.</span></span> <span data-ttu-id="a78ac-121">Používá se potom zkontrolujte, že seznamu ACL fronty, aby uživatel má oprávnění k zápisu pro frontu.</span><span class="sxs-lookup"><span data-stu-id="a78ac-121">This is then used to check the ACL of the queue to ensure the user has write permission for the queue.</span></span><br /><span data-ttu-id="a78ac-122">-Certifikát: Kanál načte příslušný certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="a78ac-122">-   Certificate: The channel retrieves the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="a78ac-123">Výchozí hodnota je `WindowsDomain`.</span><span class="sxs-lookup"><span data-stu-id="a78ac-123">The default is `WindowsDomain`.</span></span><br /><br /> <span data-ttu-id="a78ac-124">Pokud tento atribut je nastaven na `None`, `msmqProtectionLevel` musí být také nastaven `None`.</span><span class="sxs-lookup"><span data-stu-id="a78ac-124">If this attribute is set to `None`, the `msmqProtectionLevel` attribute must also be set to `None`.</span></span> <span data-ttu-id="a78ac-125">Tento atribut je typu<xref:System.ServiceModel.MsmqAuthenticationMode></span><span class="sxs-lookup"><span data-stu-id="a78ac-125">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode></span></span>|  
|<span data-ttu-id="a78ac-126">msmqEncryptionAlgorithm</span><span class="sxs-lookup"><span data-stu-id="a78ac-126">msmqEncryptionAlgorithm</span></span>|<span data-ttu-id="a78ac-127">Určuje algoritmus, který se má použít pro šifrování zpráv v drátové síti při přenosu zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="a78ac-127">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="a78ac-128">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a78ac-128">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a78ac-129">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="a78ac-129">-   RC4Stream</span></span><br /><span data-ttu-id="a78ac-130">-AES</span><span class="sxs-lookup"><span data-stu-id="a78ac-130">-   AES</span></span><br /><span data-ttu-id="a78ac-131">-Výchozí hodnota je `RC4Stream`.</span><span class="sxs-lookup"><span data-stu-id="a78ac-131">-   The default value is `RC4Stream`.</span></span> <span data-ttu-id="a78ac-132">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="a78ac-132">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|<span data-ttu-id="a78ac-133">msmqProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="a78ac-133">msmqProtectionLevel</span></span>|<span data-ttu-id="a78ac-134">Určuje, že zprávy způsob, jak jsou zabezpečené na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="a78ac-134">Specifies the way messages are secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="a78ac-135">Šifrování zajistí, že zajišťuje zpráva integrity, při přihlašování a šifrování zpráv integrity a nepopiratelnosti.</span><span class="sxs-lookup"><span data-stu-id="a78ac-135">Encryption ensures message integrity, while sign and encrypt ensures both message integrity and non-repudiation.</span></span> <span data-ttu-id="a78ac-136">To znamená zpráva skutečně pochází od odesílatele a odesílatele je, kdo říká, že se.</span><span class="sxs-lookup"><span data-stu-id="a78ac-136">That is, the message indeed came from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="a78ac-137">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a78ac-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a78ac-138">-None: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="a78ac-138">-   None: No protection.</span></span><br /><span data-ttu-id="a78ac-139">-Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="a78ac-139">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="a78ac-140">-EncryptAndSign: Zprávy jsou šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="a78ac-140">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><span data-ttu-id="a78ac-141">-Výchozí hodnota je `Sign`.</span><span class="sxs-lookup"><span data-stu-id="a78ac-141">-   The default is `Sign`.</span></span>|  
|<span data-ttu-id="a78ac-142">msmqSecureHashAlgorithm</span><span class="sxs-lookup"><span data-stu-id="a78ac-142">msmqSecureHashAlgorithm</span></span>|<span data-ttu-id="a78ac-143">Určuje algoritmus hash, který se má použít pro výpočty hodnota hash.</span><span class="sxs-lookup"><span data-stu-id="a78ac-143">Specifies the hash algorithm to be used for computing the message digest.</span></span> <span data-ttu-id="a78ac-144">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a78ac-144">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a78ac-145">-   MD5</span><span class="sxs-lookup"><span data-stu-id="a78ac-145">-   MD5</span></span><br /><span data-ttu-id="a78ac-146">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="a78ac-146">-   SHA1</span></span><br /><span data-ttu-id="a78ac-147">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="a78ac-147">-   SHA256</span></span><br /><span data-ttu-id="a78ac-148">-SHA512</span><span class="sxs-lookup"><span data-stu-id="a78ac-148">-   SHA512</span></span><br /><br /> <span data-ttu-id="a78ac-149">Výchozí hodnota je `SHA1`.</span><span class="sxs-lookup"><span data-stu-id="a78ac-149">The default is `SHA1`.</span></span> <span data-ttu-id="a78ac-150">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="a78ac-150">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a78ac-151">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a78ac-151">Child Elements</span></span>  
 <span data-ttu-id="a78ac-152">Žádné</span><span class="sxs-lookup"><span data-stu-id="a78ac-152">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a78ac-153">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a78ac-153">Parent Elements</span></span>  
  
|<span data-ttu-id="a78ac-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="a78ac-154">Element</span></span>|<span data-ttu-id="a78ac-155">Popis</span><span class="sxs-lookup"><span data-stu-id="a78ac-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a78ac-156">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="a78ac-156">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netmsmqbinding.md)|<span data-ttu-id="a78ac-157">Definuje nastavení zabezpečení přenosu pro přenosy ve frontě.</span><span class="sxs-lookup"><span data-stu-id="a78ac-157">Defines the transport security settings for queued transports.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a78ac-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="a78ac-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="a78ac-159">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="a78ac-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="a78ac-160">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="a78ac-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a78ac-161">Vazby</span><span class="sxs-lookup"><span data-stu-id="a78ac-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a78ac-162">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="a78ac-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a78ac-163">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="a78ac-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a78ac-164">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="a78ac-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
