---
title: <security> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 7877fd59aff581eee5b62a1ca224dbf51c956069
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738679"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="5bdfe-102">> \<zabezpečení \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="5bdfe-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="5bdfe-103">Definuje nastavení zabezpečení pro vazbu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="5bdfe-104">Určuje, zda je povoleno přenosu nebo zabezpečení SOAP, a pokud ano, jaký režim ověřování a úrovně ochrany se používají.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
<span data-ttu-id="5bdfe-105">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5bdfe-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5bdfe-106">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="5bdfe-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5bdfe-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5bdfe-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5bdfe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5bdfe-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="5bdfe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="5bdfe-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5bdfe-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="5bdfe-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bdfe-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bdfe-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bdfe-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5bdfe-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5bdfe-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bdfe-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5bdfe-114">Attributes</span></span>  
  
|<span data-ttu-id="5bdfe-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="5bdfe-115">Attribute</span></span>|<span data-ttu-id="5bdfe-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5bdfe-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bdfe-117">režim</span><span class="sxs-lookup"><span data-stu-id="5bdfe-117">mode</span></span>|<span data-ttu-id="5bdfe-118">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-118">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="5bdfe-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="5bdfe-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5bdfe-120">-None: zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-120">-   None: This disables security.</span></span><br /><span data-ttu-id="5bdfe-121">-Transport: služba Transport nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-121">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="5bdfe-122">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-122">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="5bdfe-123">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-123">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="5bdfe-124">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-124">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="5bdfe-125">-Message: Určuje zabezpečení aplikace na konci.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-125">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="5bdfe-126">V transportní vrstvě není nabízené žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-126">There is no security offered at the transport layer.</span></span> <span data-ttu-id="5bdfe-127">To se podobá zabezpečení nabízené jinými standardními vazbami.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-127">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="5bdfe-128">-Obojí: nabízí zabezpečení jak na úrovni přenosu, tak i ve vrstvě zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-128">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="5bdfe-129">Stejné přihlašovací údaje se vyžadují na obou úrovních.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-129">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="5bdfe-130">Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-130">The default value is Transport.</span></span> <span data-ttu-id="5bdfe-131">Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-131">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bdfe-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5bdfe-132">Child Elements</span></span>  
  
|<span data-ttu-id="5bdfe-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="5bdfe-133">Element</span></span>|<span data-ttu-id="5bdfe-134">Popis</span><span class="sxs-lookup"><span data-stu-id="5bdfe-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5bdfe-135">> \<zprávy</span><span class="sxs-lookup"><span data-stu-id="5bdfe-135">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="5bdfe-136">Definuje nastavení zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-136">Defines the SOAP message security settings.</span></span> <span data-ttu-id="5bdfe-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-137">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="5bdfe-138">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="5bdfe-138">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="5bdfe-139">Definuje nastavení zabezpečení pro přenos služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-139">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="5bdfe-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5bdfe-140">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5bdfe-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5bdfe-141">Parent Elements</span></span>  
  
|<span data-ttu-id="5bdfe-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="5bdfe-142">Element</span></span>|<span data-ttu-id="5bdfe-143">Popis</span><span class="sxs-lookup"><span data-stu-id="5bdfe-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5bdfe-144">vazba</span><span class="sxs-lookup"><span data-stu-id="5bdfe-144">binding</span></span>|<span data-ttu-id="5bdfe-145">Prvek vazby [\<netMsmqBinding >](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5bdfe-145">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5bdfe-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5bdfe-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="5bdfe-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5bdfe-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5bdfe-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="5bdfe-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5bdfe-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5bdfe-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5bdfe-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5bdfe-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5bdfe-151">vazba \<</span><span class="sxs-lookup"><span data-stu-id="5bdfe-151">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="5bdfe-152">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="5bdfe-152">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
