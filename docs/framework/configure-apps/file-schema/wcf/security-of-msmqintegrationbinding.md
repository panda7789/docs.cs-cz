---
title: <security> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 5b74c95ef2933fcf7e8d49aed89d95acbd288b80
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936697"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="59d6d-102">\<> zabezpečení > \<MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="59d6d-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="59d6d-103">Definuje nastavení zabezpečení přenosu pro integrační kanál služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="59d6d-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="59d6d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="59d6d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="59d6d-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="59d6d-105">\<bindings></span></span>  
<span data-ttu-id="59d6d-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="59d6d-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="59d6d-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="59d6d-107">\<binding></span></span>  
<span data-ttu-id="59d6d-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="59d6d-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d6d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59d6d-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>
  <binding>
    <security mode="None/Transport">
      <transport msmqAuthenticationMode="None/Windows/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
      <message algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               defaultProtectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</msmqIntegrationBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59d6d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59d6d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="59d6d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59d6d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59d6d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="59d6d-112">Attributes</span></span>  
  
|<span data-ttu-id="59d6d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="59d6d-113">Attribute</span></span>|<span data-ttu-id="59d6d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="59d6d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59d6d-115">režim</span><span class="sxs-lookup"><span data-stu-id="59d6d-115">mode</span></span>|<span data-ttu-id="59d6d-116">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování pomocí integračního kanálu služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="59d6d-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="59d6d-117">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="59d6d-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="59d6d-118">NTato Tím se zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59d6d-118">-   None: This disables security.</span></span><br /><span data-ttu-id="59d6d-119">Přepravu Přenos nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="59d6d-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="59d6d-120">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="59d6d-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="59d6d-121">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59d6d-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="59d6d-122">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59d6d-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="59d6d-123">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="59d6d-123">The default value is `Transport`.</span></span> <span data-ttu-id="59d6d-124">Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="59d6d-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59d6d-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59d6d-125">Child Elements</span></span>  
  
|<span data-ttu-id="59d6d-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="59d6d-126">Element</span></span>|<span data-ttu-id="59d6d-127">Popis</span><span class="sxs-lookup"><span data-stu-id="59d6d-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d6d-128">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="59d6d-128">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="59d6d-129">Definuje nastavení zabezpečení pro přenos Integration služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="59d6d-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="59d6d-130">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="59d6d-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59d6d-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59d6d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="59d6d-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="59d6d-132">Element</span></span>|<span data-ttu-id="59d6d-133">Popis</span><span class="sxs-lookup"><span data-stu-id="59d6d-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="59d6d-134">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="59d6d-134">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="59d6d-135">[ Prvek\<vazby > MsmqIntegrationBinding](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="59d6d-135">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59d6d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="59d6d-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="59d6d-137">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="59d6d-137">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="59d6d-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59d6d-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="59d6d-139">Vazby</span><span class="sxs-lookup"><span data-stu-id="59d6d-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59d6d-140">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="59d6d-140">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="59d6d-141">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59d6d-141">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="59d6d-142">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="59d6d-142">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="59d6d-143">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="59d6d-143">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
