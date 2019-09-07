---
title: <security> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: e4f10ab994429c6cbb690caef38114b8340e6839
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399870"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="4c78d-102">\<> zabezpečení > \<MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="4c78d-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="4c78d-103">Definuje nastavení zabezpečení přenosu pro integrační kanál služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="4c78d-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
<span data-ttu-id="4c78d-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4c78d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4c78d-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4c78d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4c78d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4c78d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="4c78d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<msmqIntegrationBinding >** ](msmqintegrationbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4c78d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)</span></span>\
<span data-ttu-id="4c78d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="4c78d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="4c78d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="4c78d-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c78d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c78d-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c78d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4c78d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4c78d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4c78d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c78d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4c78d-113">Attributes</span></span>  
  
|<span data-ttu-id="4c78d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="4c78d-114">Attribute</span></span>|<span data-ttu-id="4c78d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4c78d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c78d-116">režim</span><span class="sxs-lookup"><span data-stu-id="4c78d-116">mode</span></span>|<span data-ttu-id="4c78d-117">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování pomocí integračního kanálu služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="4c78d-117">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="4c78d-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="4c78d-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="4c78d-119">NTato Tím se zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4c78d-119">-   None: This disables security.</span></span><br /><span data-ttu-id="4c78d-120">Přepravu Přenos nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="4c78d-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="4c78d-121">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="4c78d-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="4c78d-122">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4c78d-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="4c78d-123">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4c78d-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="4c78d-124">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="4c78d-124">The default value is `Transport`.</span></span> <span data-ttu-id="4c78d-125">Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4c78d-125">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c78d-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4c78d-126">Child Elements</span></span>  
  
|<span data-ttu-id="4c78d-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c78d-127">Element</span></span>|<span data-ttu-id="4c78d-128">Popis</span><span class="sxs-lookup"><span data-stu-id="4c78d-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c78d-129">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="4c78d-129">\<transport></span></span>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="4c78d-130">Definuje nastavení zabezpečení pro přenos Integration služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="4c78d-130">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="4c78d-131">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="4c78d-131">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c78d-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4c78d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="4c78d-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c78d-133">Element</span></span>|<span data-ttu-id="4c78d-134">Popis</span><span class="sxs-lookup"><span data-stu-id="4c78d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c78d-135">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="4c78d-135">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="4c78d-136">[ Prvek\<vazby > MsmqIntegrationBinding](msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4c78d-136">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c78d-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c78d-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="4c78d-138">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="4c78d-138">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="4c78d-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4c78d-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4c78d-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="4c78d-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4c78d-141">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4c78d-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4c78d-142">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4c78d-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4c78d-143">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="4c78d-143">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="4c78d-144">\<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="4c78d-144">\<msmqIntegrationBinding></span></span>](msmqintegrationbinding.md)
