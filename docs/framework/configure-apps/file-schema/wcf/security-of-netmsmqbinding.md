---
title: <security> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: 1bbc3a460ce707e71b72a469af2e03acd8dc79e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936688"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="561fe-102">\<> zabezpečení > \<NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="561fe-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="561fe-103">Definuje nastavení zabezpečení pro vazbu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="561fe-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="561fe-104">Určuje, zda je povoleno přenosu nebo zabezpečení SOAP, a pokud ano, jaký režim ověřování a úrovně ochrany se používají.</span><span class="sxs-lookup"><span data-stu-id="561fe-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="561fe-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="561fe-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="561fe-106">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="561fe-106">\<bindings></span></span>  
<span data-ttu-id="561fe-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="561fe-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="561fe-108">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="561fe-108">\<binding></span></span>  
<span data-ttu-id="561fe-109">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="561fe-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="561fe-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="561fe-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="561fe-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="561fe-111">Attributes and Elements</span></span>  
 <span data-ttu-id="561fe-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="561fe-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="561fe-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="561fe-113">Attributes</span></span>  
  
|<span data-ttu-id="561fe-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="561fe-114">Attribute</span></span>|<span data-ttu-id="561fe-115">Popis</span><span class="sxs-lookup"><span data-stu-id="561fe-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="561fe-116">režim</span><span class="sxs-lookup"><span data-stu-id="561fe-116">mode</span></span>|<span data-ttu-id="561fe-117">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování.</span><span class="sxs-lookup"><span data-stu-id="561fe-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="561fe-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="561fe-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="561fe-119">NTato Tím se zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="561fe-119">-   None: This disables security.</span></span><br /><span data-ttu-id="561fe-120">Přepravu Přenos nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="561fe-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="561fe-121">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="561fe-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="561fe-122">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="561fe-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="561fe-123">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="561fe-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="561fe-124">Zpráva Určuje zabezpečení aplikací koncového konce.</span><span class="sxs-lookup"><span data-stu-id="561fe-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="561fe-125">V transportní vrstvě není nabízené žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="561fe-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="561fe-126">To se podobá zabezpečení nabízené jinými standardními vazbami.</span><span class="sxs-lookup"><span data-stu-id="561fe-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="561fe-127">Protokoly Nabízí zabezpečení jak na úrovni přenosu, tak i ve vrstvě zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="561fe-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="561fe-128">Stejné přihlašovací údaje se vyžadují na obou úrovních.</span><span class="sxs-lookup"><span data-stu-id="561fe-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="561fe-129">Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="561fe-129">The default value is Transport.</span></span> <span data-ttu-id="561fe-130">Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="561fe-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="561fe-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="561fe-131">Child Elements</span></span>  
  
|<span data-ttu-id="561fe-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="561fe-132">Element</span></span>|<span data-ttu-id="561fe-133">Popis</span><span class="sxs-lookup"><span data-stu-id="561fe-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="561fe-134">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="561fe-134">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="561fe-135">Definuje nastavení zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="561fe-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="561fe-136">Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="561fe-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="561fe-137">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="561fe-137">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="561fe-138">Definuje nastavení zabezpečení pro přenos služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="561fe-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="561fe-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="561fe-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="561fe-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="561fe-140">Parent Elements</span></span>  
  
|<span data-ttu-id="561fe-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="561fe-141">Element</span></span>|<span data-ttu-id="561fe-142">Popis</span><span class="sxs-lookup"><span data-stu-id="561fe-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="561fe-143">vazba</span><span class="sxs-lookup"><span data-stu-id="561fe-143">binding</span></span>|<span data-ttu-id="561fe-144">Prvek vazby [> \<NetMsmqBinding](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="561fe-144">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="561fe-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="561fe-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="561fe-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="561fe-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="561fe-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="561fe-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="561fe-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="561fe-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="561fe-149">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="561fe-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="561fe-150">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="561fe-150">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="561fe-151">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="561fe-151">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
