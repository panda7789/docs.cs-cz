---
title: <security> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 2268bf48a2b86c3b3b25db006e6f8f55ea33af73
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738692"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="002c5-102">> \<zabezpečení \<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="002c5-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="002c5-103">Definuje nastavení zabezpečení přenosu pro integrační kanál služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="002c5-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
<span data-ttu-id="002c5-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="002c5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="002c5-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="002c5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="002c5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="002c5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="002c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<msmqIntegrationBinding >** ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="002c5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="002c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="002c5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="002c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="002c5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="002c5-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="002c5-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="002c5-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="002c5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="002c5-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="002c5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="002c5-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="002c5-113">Attributes</span></span>  
  
|<span data-ttu-id="002c5-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="002c5-114">Attribute</span></span>|<span data-ttu-id="002c5-115">Popis</span><span class="sxs-lookup"><span data-stu-id="002c5-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="002c5-116">režim</span><span class="sxs-lookup"><span data-stu-id="002c5-116">mode</span></span>|<span data-ttu-id="002c5-117">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování pomocí integračního kanálu služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="002c5-117">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="002c5-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="002c5-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="002c5-119">-None: zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="002c5-119">-   None: This disables security.</span></span><br /><span data-ttu-id="002c5-120">-Transport: služba Transport nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="002c5-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="002c5-121">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="002c5-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="002c5-122">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="002c5-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="002c5-123">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="002c5-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="002c5-124">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="002c5-124">The default value is `Transport`.</span></span> <span data-ttu-id="002c5-125">Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="002c5-125">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="002c5-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="002c5-126">Child Elements</span></span>  
  
|<span data-ttu-id="002c5-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="002c5-127">Element</span></span>|<span data-ttu-id="002c5-128">Popis</span><span class="sxs-lookup"><span data-stu-id="002c5-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="002c5-129">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="002c5-129">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="002c5-130">Definuje nastavení zabezpečení pro přenos Integration služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="002c5-130">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="002c5-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="002c5-131">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="002c5-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="002c5-132">Parent Elements</span></span>  
  
|<span data-ttu-id="002c5-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="002c5-133">Element</span></span>|<span data-ttu-id="002c5-134">Popis</span><span class="sxs-lookup"><span data-stu-id="002c5-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="002c5-135">vazba \<</span><span class="sxs-lookup"><span data-stu-id="002c5-135">\<binding></span></span>](bindings.md)|<span data-ttu-id="002c5-136">Prvek vazby [\<msmqIntegrationBinding >](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="002c5-136">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="002c5-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="002c5-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="002c5-138">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="002c5-138">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="002c5-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="002c5-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="002c5-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="002c5-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="002c5-141">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="002c5-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="002c5-142">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="002c5-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="002c5-143">vazba \<</span><span class="sxs-lookup"><span data-stu-id="002c5-143">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="002c5-144">\<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="002c5-144">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
