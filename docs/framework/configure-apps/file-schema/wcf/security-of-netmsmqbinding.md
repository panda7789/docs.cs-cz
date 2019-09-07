---
title: <security> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: c780b157d0d566e24c6826c253401a51fbfab69d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399844"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="ea6e8-102">\<> zabezpečení > \<NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="ea6e8-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="ea6e8-103">Definuje nastavení zabezpečení pro vazbu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="ea6e8-104">Určuje, zda je povoleno přenosu nebo zabezpečení SOAP, a pokud ano, jaký režim ověřování a úrovně ochrany se používají.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
<span data-ttu-id="ea6e8-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ea6e8-106">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ea6e8-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="ea6e8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)</span></span>\
<span data-ttu-id="ea6e8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="ea6e8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="ea6e8-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea6e8-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea6e8-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea6e8-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ea6e8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ea6e8-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea6e8-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="ea6e8-114">Attributes</span></span>  
  
|<span data-ttu-id="ea6e8-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="ea6e8-115">Attribute</span></span>|<span data-ttu-id="ea6e8-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ea6e8-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea6e8-117">režim</span><span class="sxs-lookup"><span data-stu-id="ea6e8-117">mode</span></span>|<span data-ttu-id="ea6e8-118">Určuje typ zabezpečení, který řídí integritu, důvěrnost a ověřování.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-118">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="ea6e8-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="ea6e8-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="ea6e8-120">NTato Tím se zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-120">-   None: This disables security.</span></span><br /><span data-ttu-id="ea6e8-121">Přepravu Přenos nabízí ochranu a ověřování.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-121">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="ea6e8-122">To platí pro zabezpečení zpráv mezi dvěma správci fronty.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-122">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="ea6e8-123">Mezi aplikací a správcem front se nenabízí žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-123">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="ea6e8-124">Stávající aplikace služby MSMQ jsou funkčně ekvivalentní s tímto typem režimu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-124">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="ea6e8-125">Zpráva Určuje zabezpečení aplikací koncového konce.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-125">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="ea6e8-126">V transportní vrstvě není nabízené žádné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-126">There is no security offered at the transport layer.</span></span> <span data-ttu-id="ea6e8-127">To se podobá zabezpečení nabízené jinými standardními vazbami.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-127">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="ea6e8-128">Protokoly Nabízí zabezpečení jak na úrovni přenosu, tak i ve vrstvě zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-128">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="ea6e8-129">Stejné přihlašovací údaje se vyžadují na obou úrovních.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-129">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="ea6e8-130">Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-130">The default value is Transport.</span></span> <span data-ttu-id="ea6e8-131">Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-131">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ea6e8-132">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ea6e8-132">Child Elements</span></span>  
  
|<span data-ttu-id="ea6e8-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="ea6e8-133">Element</span></span>|<span data-ttu-id="ea6e8-134">Popis</span><span class="sxs-lookup"><span data-stu-id="ea6e8-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea6e8-135">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="ea6e8-135">\<message></span></span>](message-of-netmsmqbinding.md)|<span data-ttu-id="ea6e8-136">Definuje nastavení zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-136">Defines the SOAP message security settings.</span></span> <span data-ttu-id="ea6e8-137">Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-137">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="ea6e8-138">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="ea6e8-138">\<transport></span></span>](transport-of-netmsmqbinding.md)|<span data-ttu-id="ea6e8-139">Definuje nastavení zabezpečení pro přenos služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-139">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="ea6e8-140">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ea6e8-140">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea6e8-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ea6e8-141">Parent Elements</span></span>  
  
|<span data-ttu-id="ea6e8-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="ea6e8-142">Element</span></span>|<span data-ttu-id="ea6e8-143">Popis</span><span class="sxs-lookup"><span data-stu-id="ea6e8-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ea6e8-144">vazba</span><span class="sxs-lookup"><span data-stu-id="ea6e8-144">binding</span></span>|<span data-ttu-id="ea6e8-145">Prvek vazby [> \<NetMsmqBinding](netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="ea6e8-145">The binding element of the [\<netMsmqBinding>](netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea6e8-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea6e8-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="ea6e8-147">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ea6e8-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="ea6e8-148">Vazby</span><span class="sxs-lookup"><span data-stu-id="ea6e8-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ea6e8-149">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="ea6e8-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="ea6e8-150">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="ea6e8-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="ea6e8-151">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="ea6e8-151">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="ea6e8-152">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="ea6e8-152">Queues in WCF</span></span>](../../../wcf/feature-details/queues-in-wcf.md)
