---
title: <security> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 7877fd59aff581eee5b62a1ca224dbf51c956069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738679"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="b9d41-102">\<security> z \<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="b9d41-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="b9d41-103">Definuje nastavení zabezpečení pro vazbu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b9d41-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="b9d41-104">Určuje, zda je povoleno přenosu nebo zabezpečení SOAP, a pokud ano, jaký režim ověřování a úrovně ochrany se používají.</span><span class="sxs-lookup"><span data-stu-id="b9d41-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="b9d41-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9d41-105">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
             clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9d41-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b9d41-106">Attributes and Elements</span></span>  
 <span data-ttu-id="b9d41-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b9d41-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9d41-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="b9d41-108">Attributes</span></span>  
  
|<span data-ttu-id="b9d41-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="b9d41-109">Attribute</span></span>|<span data-ttu-id="b9d41-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b9d41-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9d41-111">režim</span><span class="sxs-lookup"><span data-stu-id="b9d41-111">mode</span></span>|<span data-ttu-id="b9d41-112">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování.</span><span class="sxs-lookup"><span data-stu-id="b9d41-112">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="b9d41-113">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="b9d41-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="b9d41-114">-None: zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b9d41-114">-   None: This disables security.</span></span><br /><span data-ttu-id="b9d41-115">-Transport: služba Transport nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="b9d41-115">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="b9d41-116">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="b9d41-116">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="b9d41-117">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b9d41-117">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="b9d41-118">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b9d41-118">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="b9d41-119">-Message: Určuje zabezpečení aplikace na konci.</span><span class="sxs-lookup"><span data-stu-id="b9d41-119">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="b9d41-120">V transportní vrstvě není nabízené žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b9d41-120">There is no security offered at the transport layer.</span></span> <span data-ttu-id="b9d41-121">To se podobá zabezpečení nabízené jinými standardními vazbami.</span><span class="sxs-lookup"><span data-stu-id="b9d41-121">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="b9d41-122">-Obojí: nabízí zabezpečení jak na úrovni přenosu, tak i ve vrstvě zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="b9d41-122">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="b9d41-123">Stejné přihlašovací údaje se vyžadují na obou úrovních.</span><span class="sxs-lookup"><span data-stu-id="b9d41-123">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="b9d41-124">Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="b9d41-124">The default value is Transport.</span></span> <span data-ttu-id="b9d41-125">Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="b9d41-125">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9d41-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b9d41-126">Child Elements</span></span>  
  
|<span data-ttu-id="b9d41-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9d41-127">Element</span></span>|<span data-ttu-id="b9d41-128">Description</span><span class="sxs-lookup"><span data-stu-id="b9d41-128">Description</span></span>|  
|-------------|-----------------|  
|[\<message>](message-of-netmsmqbinding.md)|<span data-ttu-id="b9d41-129">Definuje nastavení zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b9d41-129">Defines the SOAP message security settings.</span></span> <span data-ttu-id="b9d41-130">Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement> .</span><span class="sxs-lookup"><span data-stu-id="b9d41-130">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[\<transport>](transport-of-netmsmqbinding.md)|<span data-ttu-id="b9d41-131">Definuje nastavení zabezpečení pro přenos služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="b9d41-131">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="b9d41-132">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="b9d41-132">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9d41-133">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b9d41-133">Parent Elements</span></span>  
  
|<span data-ttu-id="b9d41-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="b9d41-134">Element</span></span>|<span data-ttu-id="b9d41-135">Description</span><span class="sxs-lookup"><span data-stu-id="b9d41-135">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9d41-136">vazba</span><span class="sxs-lookup"><span data-stu-id="b9d41-136">binding</span></span>|<span data-ttu-id="b9d41-137">Element Binding prvku[\<netMsmqBinding>](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b9d41-137">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b9d41-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9d41-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="b9d41-139">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b9d41-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b9d41-140">Vazby</span><span class="sxs-lookup"><span data-stu-id="b9d41-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b9d41-141">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b9d41-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b9d41-142">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b9d41-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- [<span data-ttu-id="b9d41-143">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="b9d41-143">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
