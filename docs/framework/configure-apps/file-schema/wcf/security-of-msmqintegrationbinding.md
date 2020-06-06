---
title: <security> z <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
ms.openlocfilehash: 2268bf48a2b86c3b3b25db006e6f8f55ea33af73
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738692"
---
# <a name="security-of-msmqintegrationbinding"></a><span data-ttu-id="59ab4-102">\<security> z \<msmqIntegrationBinding></span><span class="sxs-lookup"><span data-stu-id="59ab4-102">\<security> of \<msmqIntegrationBinding></span></span>
<span data-ttu-id="59ab4-103">Definuje nastavení zabezpečení přenosu pro integrační kanál služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="59ab4-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="59ab4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59ab4-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59ab4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59ab4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="59ab4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59ab4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59ab4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="59ab4-107">Attributes</span></span>  
  
|<span data-ttu-id="59ab4-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="59ab4-108">Attribute</span></span>|<span data-ttu-id="59ab4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="59ab4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="59ab4-110">režim</span><span class="sxs-lookup"><span data-stu-id="59ab4-110">mode</span></span>|<span data-ttu-id="59ab4-111">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování pomocí integračního kanálu služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="59ab4-111">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="59ab4-112">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="59ab4-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="59ab4-113">-None: zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59ab4-113">-   None: This disables security.</span></span><br /><span data-ttu-id="59ab4-114">-Transport: služba Transport nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="59ab4-114">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="59ab4-115">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="59ab4-115">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="59ab4-116">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59ab4-116">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="59ab4-117">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59ab4-117">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="59ab4-118">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="59ab4-118">The default value is `Transport`.</span></span> <span data-ttu-id="59ab4-119">Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="59ab4-119">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59ab4-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59ab4-120">Child Elements</span></span>  
  
|<span data-ttu-id="59ab4-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="59ab4-121">Element</span></span>|<span data-ttu-id="59ab4-122">Description</span><span class="sxs-lookup"><span data-stu-id="59ab4-122">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-msmqintegrationbinding.md)|<span data-ttu-id="59ab4-123">Definuje nastavení zabezpečení pro přenos Integration služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="59ab4-123">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="59ab4-124">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="59ab4-124">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="59ab4-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59ab4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="59ab4-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="59ab4-126">Element</span></span>|<span data-ttu-id="59ab4-127">Description</span><span class="sxs-lookup"><span data-stu-id="59ab4-127">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="59ab4-128">Prvek vazby prvku [\<msmqIntegrationBinding>](msmqintegrationbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="59ab4-128">The binding element of the [\<msmqIntegrationBinding>](msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="59ab4-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="59ab4-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- [<span data-ttu-id="59ab4-130">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="59ab4-130">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
- [<span data-ttu-id="59ab4-131">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59ab4-131">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="59ab4-132">Vazby</span><span class="sxs-lookup"><span data-stu-id="59ab4-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59ab4-133">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="59ab4-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="59ab4-134">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="59ab4-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [\<msmqIntegrationBinding>](msmqintegrationbinding.md)
