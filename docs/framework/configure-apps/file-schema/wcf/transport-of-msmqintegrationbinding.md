---
title: "&lt;transport&gt; – &lt;msmqIntegrationBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2dc4f3cb08436f0f1af2e559c924446faa7b870c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="f8b9a-102">&lt;transport&gt; – &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f8b9a-102">&lt;transport&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="f8b9a-103">Definuje nastavení zabezpečení pro transport integrace služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-103">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
 <span data-ttu-id="f8b9a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f8b9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f8b9a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f8b9a-105">\<bindings></span></span>  
<span data-ttu-id="f8b9a-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="f8b9a-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="f8b9a-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f8b9a-107">\<binding></span></span>  
<span data-ttu-id="f8b9a-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="f8b9a-108">\<security></span></span>  
<span data-ttu-id="f8b9a-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="f8b9a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8b9a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8b9a-110">Syntax</span></span>  
  
```xml  
<security>  
    <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
        msmqEncryptionAlgorithm="RC4Stream/AES"  
        msmqProtectionLevel="None/Sign/EncryptAndSign"  
        msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8b9a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f8b9a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f8b9a-112">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8b9a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8b9a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="f8b9a-113">Attributes</span></span>  
  
|<span data-ttu-id="f8b9a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="f8b9a-114">Attribute</span></span>|<span data-ttu-id="f8b9a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="f8b9a-115">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="f8b9a-116">Určuje, jak ověřit zprávu přenos MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-116">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="f8b9a-117">Pokud je nastavena v `None`, hodnota `msmqProtectionLevel` musí být také nastaven `None`.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-117">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="f8b9a-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="f8b9a-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f8b9a-119">-None: Bez ověřování.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-119">-   None: No authentication.</span></span><br /><span data-ttu-id="f8b9a-120">-Třídy WindowsDomain: Ověřovací mechanismus používá služby Active Directory k získání certifikátu X.509 SID přidružené ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-120">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="f8b9a-121">Používá se potom zkontrolujte, že seznamu ACL fronty, aby uživatel má oprávnění k zápisu do fronty.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-121">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="f8b9a-122">-Certifikát: Kanál získá certifikát z úložiště certifikátů.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-122">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="f8b9a-123">Výchozí hodnota je třídy WindowsDomain.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-123">The default value is WindowsDomain.</span></span> <span data-ttu-id="f8b9a-124">Tento atribut je typu <xref:System.ServiceModel.MsmqAuthenticationMode>.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-124">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="f8b9a-125">Určuje algoritmus, který se má použít pro šifrování zpráv v drátové síti při přenosu zpráv mezi správci fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-125">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="f8b9a-126">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="f8b9a-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f8b9a-127">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="f8b9a-127">-   RC4Stream</span></span><br /><span data-ttu-id="f8b9a-128">-AES</span><span class="sxs-lookup"><span data-stu-id="f8b9a-128">-   AES</span></span><br /><br /> <span data-ttu-id="f8b9a-129">Výchozí hodnota je RC4Stream.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-129">The default value is RC4Stream.</span></span> <span data-ttu-id="f8b9a-130">Tento atribut je typu <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-130">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="f8b9a-131">Určuje, jak jsou zprávy zabezpečená na úrovni přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-131">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="f8b9a-132">Šifrování zajistíte integritu zpráva při EncryptAndSign zajišťuje zpráva integrity a nepopiratelnosti; To znamená zpráva skutečně pochází z odesílatele a odesílatele je, kdo říká, že se.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-132">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who he says he is.</span></span><br /><br /> <span data-ttu-id="f8b9a-133">-Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="f8b9a-133">-   Valid values include the following:</span></span><br /><span data-ttu-id="f8b9a-134">-None: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-134">-   None: No protection.</span></span><br /><span data-ttu-id="f8b9a-135">-Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-135">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="f8b9a-136">-EncryptAndSign: Zprávy jsou šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-136">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="f8b9a-137">Výchozí hodnota je přihlášení.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-137">The default value is Sign.</span></span> <span data-ttu-id="f8b9a-138">Tento atribut je typu ProtectionLevel.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-138">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="f8b9a-139">-Určuje algoritmus, který se má použít v oblasti výpočetních daný výtah jako součást podpisy.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-139">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="f8b9a-140">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="f8b9a-140">Valid values include the following:</span></span><br /><span data-ttu-id="f8b9a-141">-   MD5</span><span class="sxs-lookup"><span data-stu-id="f8b9a-141">-   MD5</span></span><br /><span data-ttu-id="f8b9a-142">-   SHA1</span><span class="sxs-lookup"><span data-stu-id="f8b9a-142">-   SHA1</span></span><br /><span data-ttu-id="f8b9a-143">-   SHA256</span><span class="sxs-lookup"><span data-stu-id="f8b9a-143">-   SHA256</span></span><br /><span data-ttu-id="f8b9a-144">-   SHA512</span><span class="sxs-lookup"><span data-stu-id="f8b9a-144">-   SHA512</span></span><br /><br /> <span data-ttu-id="f8b9a-145">Výchozí hodnota je SHA1.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-145">The default value is SHA1.</span></span> <span data-ttu-id="f8b9a-146">Tento atribut je typu <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-146">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8b9a-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8b9a-147">Child Elements</span></span>  
 <span data-ttu-id="f8b9a-148">Žádné</span><span class="sxs-lookup"><span data-stu-id="f8b9a-148">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f8b9a-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f8b9a-149">Parent Elements</span></span>  
  
|<span data-ttu-id="f8b9a-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8b9a-150">Element</span></span>|<span data-ttu-id="f8b9a-151">Popis</span><span class="sxs-lookup"><span data-stu-id="f8b9a-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8b9a-152">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="f8b9a-152">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="f8b9a-153">Definuje nastavení zabezpečení pro vazby služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-153">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8b9a-154">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8b9a-154">Remarks</span></span>  
 <span data-ttu-id="f8b9a-155">Tento element zapouzdří nastavení zabezpečení pro transport integrace služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-155">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="f8b9a-156">Nastavení jsou stejné pro integraci služby Řízení front zpráv a ve frontě přenosů.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-156">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="f8b9a-157">Umožňuje nastavit režim ověřování, algoritmus šifrování, algoritmus Secure Hash Algorithm a úroveň ochrany.</span><span class="sxs-lookup"><span data-stu-id="f8b9a-157">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b9a-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8b9a-158">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.MsmqTransportSecurity>  
 [<span data-ttu-id="f8b9a-159">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f8b9a-159">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f8b9a-160">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f8b9a-160">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f8b9a-161">Vazby</span><span class="sxs-lookup"><span data-stu-id="f8b9a-161">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f8b9a-162">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f8b9a-162">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f8b9a-163">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="f8b9a-163">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f8b9a-164">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f8b9a-164">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
