---
title: "&lt;security&gt; – &lt;netMsmqBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: c6f0f2a6da3b5bc5cb33d20118c135b3b7652986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnetmsmqbindinggt"></a><span data-ttu-id="21e28-102">&lt;security&gt; – &lt;netMsmqBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="21e28-102">&lt;security&gt; of &lt;netMsmqBinding&gt;</span></span>
<span data-ttu-id="21e28-103">Definuje nastavení zabezpečení pro vazby služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="21e28-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="21e28-104">Určuje, zda je povolen přenos nebo SOAP zabezpečení, a pokud ano, jaké úrovně režimu a ochranu ověřování se používají.</span><span class="sxs-lookup"><span data-stu-id="21e28-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="21e28-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="21e28-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="21e28-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="21e28-106">\<bindings></span></span>  
<span data-ttu-id="21e28-107">\<– netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="21e28-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="21e28-108">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="21e28-108">\<binding></span></span>  
<span data-ttu-id="21e28-109">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="21e28-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e28-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21e28-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/Both">  
   <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"  
      msmqEncryptionAlgorithm="RC4Stream/AES"  
      msmqProtectionLevel="None/Sign/EncryptAndSign"  
      msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
      <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="None/Windows/UserName/Certificate/CardSpace"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21e28-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21e28-111">Attributes and Elements</span></span>  
 <span data-ttu-id="21e28-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21e28-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21e28-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="21e28-113">Attributes</span></span>  
  
|<span data-ttu-id="21e28-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="21e28-114">Attribute</span></span>|<span data-ttu-id="21e28-115">Popis</span><span class="sxs-lookup"><span data-stu-id="21e28-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21e28-116">režim</span><span class="sxs-lookup"><span data-stu-id="21e28-116">mode</span></span>|<span data-ttu-id="21e28-117">Určuje typ zabezpečení, které řídí integrity, šifrování a ověřování.</span><span class="sxs-lookup"><span data-stu-id="21e28-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="21e28-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="21e28-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="21e28-119">-None: To zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21e28-119">-   None: This disables security.</span></span><br /><span data-ttu-id="21e28-120">-Přenos: Ochrana a ověřování jsou nabízeny přenosu.</span><span class="sxs-lookup"><span data-stu-id="21e28-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="21e28-121">To platí pro zabezpečení zpráv mezi dvěma fronty správci.</span><span class="sxs-lookup"><span data-stu-id="21e28-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="21e28-122">Neexistuje žádné zabezpečení nabízené mezi aplikací a správce front.</span><span class="sxs-lookup"><span data-stu-id="21e28-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="21e28-123">Existující aplikacím služby Msmq jsou funkčně srovnatelný s tímto typem režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="21e28-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="21e28-124">-Zpráva: Určuje koncovou zabezpečení aplikací.</span><span class="sxs-lookup"><span data-stu-id="21e28-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="21e28-125">Neexistuje žádné zabezpečení nabízené v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="21e28-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="21e28-126">Toto je podobná zabezpečení, které nabízí další standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="21e28-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="21e28-127">-Obě: Nabízí zabezpečení v přenosu a zasílání zpráv vrstvy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="21e28-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="21e28-128">Na obou úrovních vyžádáním stejných přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="21e28-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="21e28-129">Výchozí hodnota je přenos.</span><span class="sxs-lookup"><span data-stu-id="21e28-129">The default value is Transport.</span></span> <span data-ttu-id="21e28-130">Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="21e28-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21e28-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21e28-131">Child Elements</span></span>  
  
|<span data-ttu-id="21e28-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="21e28-132">Element</span></span>|<span data-ttu-id="21e28-133">Popis</span><span class="sxs-lookup"><span data-stu-id="21e28-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21e28-134">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="21e28-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="21e28-135">Definuje nastavení zabezpečení protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="21e28-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="21e28-136">Tento element je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="21e28-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="21e28-137">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="21e28-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="21e28-138">Definuje nastavení zabezpečení pro přenos MSMQ.</span><span class="sxs-lookup"><span data-stu-id="21e28-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="21e28-139">Tento element je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="21e28-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21e28-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21e28-140">Parent Elements</span></span>  
  
|<span data-ttu-id="21e28-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="21e28-141">Element</span></span>|<span data-ttu-id="21e28-142">Popis</span><span class="sxs-lookup"><span data-stu-id="21e28-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21e28-143">vazba</span><span class="sxs-lookup"><span data-stu-id="21e28-143">binding</span></span>|<span data-ttu-id="21e28-144">Element vazby [ \<– netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="21e28-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21e28-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="21e28-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>  
 <xref:System.ServiceModel.NetMsmqBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>  
 <xref:System.ServiceModel.NetMsmqSecurity>  
 [<span data-ttu-id="21e28-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="21e28-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="21e28-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="21e28-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="21e28-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="21e28-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="21e28-149">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="21e28-149">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="21e28-150">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="21e28-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="21e28-151">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="21e28-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
