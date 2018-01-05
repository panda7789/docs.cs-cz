---
title: '&lt;msmqTransportSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 0ece4395c574a4d6bc9399788ad3fb513cb86379
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltmsmqtransportsecuritygt"></a><span data-ttu-id="35170-102">&lt;msmqTransportSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="35170-102">&lt;msmqTransportSecurity&gt;</span></span>
<span data-ttu-id="35170-103">Určuje nastavení zabezpečení služby MSMQ přenos vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="35170-103">Specifies MSMQ transport security settings for a custom binding.</span></span>  
  
 <span data-ttu-id="35170-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="35170-104">\<system.serviceModel></span></span>  
<span data-ttu-id="35170-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="35170-105">\<bindings></span></span>  
<span data-ttu-id="35170-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35170-106">\<customBinding></span></span>  
<span data-ttu-id="35170-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="35170-107">\<binding></span></span>  
<span data-ttu-id="35170-108">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="35170-108">\<msmqIntegration></span></span>  
<span data-ttu-id="35170-109">\<msmqTransportSecurity ></span><span class="sxs-lookup"><span data-stu-id="35170-109">\<msmqTransportSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35170-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35170-110">Syntax</span></span>  
  
```xml  
<msmqTransportSecurity>  
   msmqAuthenticationMode="None/Windows/Certificate"  
   msmqEncryptionAlgorithm="RC4Stream/AES"  
   msmqProtectionLevel="None/Sign/EncryptAndSign"  
   msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</msmqTransportSecurity>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35170-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="35170-111">Attributes and Elements</span></span>  
 <span data-ttu-id="35170-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="35170-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35170-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="35170-113">Attributes</span></span>  
  
|<span data-ttu-id="35170-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="35170-114">Attribute</span></span>|<span data-ttu-id="35170-115">Popis</span><span class="sxs-lookup"><span data-stu-id="35170-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="35170-116">Určuje, jak ověřit zprávu přenos MSMQ.</span><span class="sxs-lookup"><span data-stu-id="35170-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="35170-117">Pokud je nastavena v `None`, hodnota `msmqProtectionLevel` musí být také nastaven `None`.</span><span class="sxs-lookup"><span data-stu-id="35170-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="35170-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="35170-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="35170-119">-None: Bez ověřování.</span><span class="sxs-lookup"><span data-stu-id="35170-119">-   None: No authentication.</span></span><br /><span data-ttu-id="35170-120">-Windows: Používá mechanismus ověřování služby Active Directory k získání certifikátu X.509 SID přidružené ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="35170-120">-   Windows: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="35170-121">Používá se potom zkontrolujte, že seznamu ACL fronty, aby uživatel má oprávnění k zápisu do fronty.</span><span class="sxs-lookup"><span data-stu-id="35170-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="35170-122">-Certifikát: Kanál získá certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="35170-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="35170-123">Výchozí hodnota je Windows.</span><span class="sxs-lookup"><span data-stu-id="35170-123">The default value is Windows.</span></span> <span data-ttu-id="35170-124">Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="35170-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="35170-125">Určuje algoritmus, který se má použít pro šifrování zpráv v drátové síti při přenosu zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="35170-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="35170-126">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="35170-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="35170-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="35170-127">-   RC4Stream</span></span><br /><span data-ttu-id="35170-128">-AES</span><span class="sxs-lookup"><span data-stu-id="35170-128">-   AES</span></span><br /><br /> <span data-ttu-id="35170-129">Výchozí hodnota je RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="35170-129">The default value is RC4Stream.</span></span> <span data-ttu-id="35170-130">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="35170-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="35170-131">Určuje, jak jsou zprávy zabezpečená na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="35170-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="35170-132">Šifrování zajistíte integritu zpráva při EncryptAndSign zajišťuje zpráva integrity a nepopiratelnosti; To znamená zpráva skutečně pochází z odesílatele a odesílatele je, kdo říká, že se.</span><span class="sxs-lookup"><span data-stu-id="35170-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span> <span data-ttu-id="35170-133">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="35170-133">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="35170-134">-None: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="35170-134">-   None: No protection.</span></span><br /><span data-ttu-id="35170-135">-Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="35170-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="35170-136">-EncryptAndSign: Zprávy jsou šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="35170-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="35170-137">Výchozí hodnota je přihlášení.</span><span class="sxs-lookup"><span data-stu-id="35170-137">The default value is Sign.</span></span> <span data-ttu-id="35170-138">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="35170-138">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="35170-139">Určuje algoritmus, který se má použít v oblasti výpočetních daný výtah jako součást podpisy.</span><span class="sxs-lookup"><span data-stu-id="35170-139">Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="35170-140">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="35170-140">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="35170-141">-MD5</span><span class="sxs-lookup"><span data-stu-id="35170-141">-   MD5</span></span><br /><span data-ttu-id="35170-142">-SHA1</span><span class="sxs-lookup"><span data-stu-id="35170-142">-   SHA1</span></span><br /><span data-ttu-id="35170-143">-SHA256</span><span class="sxs-lookup"><span data-stu-id="35170-143">-   SHA256</span></span><br /><span data-ttu-id="35170-144">-SHA512</span><span class="sxs-lookup"><span data-stu-id="35170-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="35170-145">Výchozí hodnota je SHA1.</span><span class="sxs-lookup"><span data-stu-id="35170-145">The default value is SHA1.</span></span> <span data-ttu-id="35170-146">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="35170-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35170-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="35170-147">Child Elements</span></span>  
 <span data-ttu-id="35170-148">Žádné</span><span class="sxs-lookup"><span data-stu-id="35170-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="35170-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="35170-149">Parent Elements</span></span>  
  
|<span data-ttu-id="35170-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="35170-150">Element</span></span>|<span data-ttu-id="35170-151">Popis</span><span class="sxs-lookup"><span data-stu-id="35170-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35170-152">\<msmqIntegration ></span><span class="sxs-lookup"><span data-stu-id="35170-152">\<msmqIntegration></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegration.md)|<span data-ttu-id="35170-153">Určuje nastavení pro interakci s služby Řízení front zpráv (MSMQ) odesílatele nebo příjemce.</span><span class="sxs-lookup"><span data-stu-id="35170-153">Specifies settings required for interaction with a Message Queuing (MSMQ) sender or receiver.</span></span>|  
|[<span data-ttu-id="35170-154">\<msmqTransport ></span><span class="sxs-lookup"><span data-stu-id="35170-154">\<msmqTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqtransport.md)|<span data-ttu-id="35170-155">Určuje vlastnosti komunikaci služby Řízení front služby Windows Communication Foundation (WCF), který používá protokol nativní služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="35170-155">Specifies the queuing communication properties for a Windows Communication Foundation (WCF) service that uses the native MSMQ protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35170-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35170-156">Remarks</span></span>  
 <span data-ttu-id="35170-157">Další informace o zabezpečení přenosu najdete v tématu [zabezpečení přenosu](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span><span class="sxs-lookup"><span data-stu-id="35170-157">For more information on transport security, see [Transport Security](../../../../../docs/framework/wcf/feature-details/transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35170-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="35170-158">See Also</span></span>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="35170-159">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="35170-159">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="35170-160">Přenosy</span><span class="sxs-lookup"><span data-stu-id="35170-160">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="35170-161">Volba přenosu</span><span class="sxs-lookup"><span data-stu-id="35170-161">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="35170-162">Vazby</span><span class="sxs-lookup"><span data-stu-id="35170-162">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="35170-163">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="35170-163">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="35170-164">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="35170-164">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="35170-165">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="35170-165">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="35170-166">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="35170-166">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
