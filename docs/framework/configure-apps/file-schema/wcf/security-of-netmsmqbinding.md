---
title: <security> z <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 001d11a9-7439-498c-b09d-fca20eaf8cd3
ms.openlocfilehash: acb4d04663d841a9b494153caa180855959c145e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670505"
---
# <a name="security-of-netmsmqbinding"></a><span data-ttu-id="5e17a-102">\<zabezpečení > z \<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="5e17a-102">\<security> of \<netMsmqBinding></span></span>
<span data-ttu-id="5e17a-103">Definuje nastavení zabezpečení pro vazby služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e17a-103">Defines the security settings for a MSMQ binding.</span></span> <span data-ttu-id="5e17a-104">Určuje, zda je povolen přenos nebo SOAP zabezpečení, a pokud ano, jaké úrovně režimu a ochranu ověřování se používají.</span><span class="sxs-lookup"><span data-stu-id="5e17a-104">It specifies whether transport or SOAP security is enabled and, if so, what authentication mode and protection levels are in use.</span></span>  
  
 <span data-ttu-id="5e17a-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5e17a-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e17a-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5e17a-106">\<bindings></span></span>  
<span data-ttu-id="5e17a-107">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="5e17a-107">\<netMsmqBinding></span></span>  
<span data-ttu-id="5e17a-108">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5e17a-108">\<binding></span></span>  
<span data-ttu-id="5e17a-109">\<security></span><span class="sxs-lookup"><span data-stu-id="5e17a-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e17a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e17a-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e17a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5e17a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5e17a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5e17a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e17a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5e17a-113">Attributes</span></span>  
  
|<span data-ttu-id="5e17a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="5e17a-114">Attribute</span></span>|<span data-ttu-id="5e17a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5e17a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e17a-116">režim</span><span class="sxs-lookup"><span data-stu-id="5e17a-116">mode</span></span>|<span data-ttu-id="5e17a-117">Určuje typ zabezpečení, které řídí integrity, šifrování a ověřování.</span><span class="sxs-lookup"><span data-stu-id="5e17a-117">Specifies the type of security that controls integrity, confidentiality and authentication.</span></span> <span data-ttu-id="5e17a-118">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="5e17a-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5e17a-119">-Žádný: Zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5e17a-119">-   None: This disables security.</span></span><br /><span data-ttu-id="5e17a-120">-Přenos: Ochrana a ověřování se nabízejí Transport.</span><span class="sxs-lookup"><span data-stu-id="5e17a-120">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="5e17a-121">To platí pro zabezpečení zpráv mezi správci fronty dvě.</span><span class="sxs-lookup"><span data-stu-id="5e17a-121">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="5e17a-122">Neexistuje žádné zabezpečení nabízené mezi aplikací a správce fronty.</span><span class="sxs-lookup"><span data-stu-id="5e17a-122">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="5e17a-123">Existující aplikacím služby Msmq jsou funkčně ekvivalentní s tímto typem režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5e17a-123">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><span data-ttu-id="5e17a-124">– Zprávy: Určuje koncové zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="5e17a-124">-   Message: Specifies end-end application security.</span></span> <span data-ttu-id="5e17a-125">Neexistuje žádné zabezpečení k dispozici v přenosové vrstvě.</span><span class="sxs-lookup"><span data-stu-id="5e17a-125">There is no security offered at the transport layer.</span></span> <span data-ttu-id="5e17a-126">To se podobá zabezpečení nabízené ostatní standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="5e17a-126">This is similar to the security offered by other standard bindings.</span></span><br /><span data-ttu-id="5e17a-127">-Obojí: Nabízí zabezpečení přenosu a vrstvě zasílání zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="5e17a-127">-   Both: Offers security at both the transport and SOAP messaging layer.</span></span> <span data-ttu-id="5e17a-128">Na obou úrovních se vyžadují stejné přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="5e17a-128">The same credential is required at both the levels.</span></span><br /><br /> <span data-ttu-id="5e17a-129">Výchozí hodnota je přenos.</span><span class="sxs-lookup"><span data-stu-id="5e17a-129">The default value is Transport.</span></span> <span data-ttu-id="5e17a-130">Tento atribut je typu <xref:System.ServiceModel.NetMsmqSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="5e17a-130">This attribute is of type <xref:System.ServiceModel.NetMsmqSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e17a-131">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5e17a-131">Child Elements</span></span>  
  
|<span data-ttu-id="5e17a-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e17a-132">Element</span></span>|<span data-ttu-id="5e17a-133">Popis</span><span class="sxs-lookup"><span data-stu-id="5e17a-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e17a-134">\<message></span><span class="sxs-lookup"><span data-stu-id="5e17a-134">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-netmsmqbinding.md)|<span data-ttu-id="5e17a-135">Definuje nastavení zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="5e17a-135">Defines the SOAP message security settings.</span></span> <span data-ttu-id="5e17a-136">Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span><span class="sxs-lookup"><span data-stu-id="5e17a-136">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>.</span></span>|  
|[<span data-ttu-id="5e17a-137">\<transport></span><span class="sxs-lookup"><span data-stu-id="5e17a-137">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netmsmqbinding.md)|<span data-ttu-id="5e17a-138">Definuje nastavení zabezpečení přenosu služby MSMQ.</span><span class="sxs-lookup"><span data-stu-id="5e17a-138">Defines the security settings for the MSMQ transport.</span></span> <span data-ttu-id="5e17a-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="5e17a-139">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e17a-140">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5e17a-140">Parent Elements</span></span>  
  
|<span data-ttu-id="5e17a-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="5e17a-141">Element</span></span>|<span data-ttu-id="5e17a-142">Popis</span><span class="sxs-lookup"><span data-stu-id="5e17a-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e17a-143">vazba</span><span class="sxs-lookup"><span data-stu-id="5e17a-143">binding</span></span>|<span data-ttu-id="5e17a-144">Prvek vazby [ \<netMsmqBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5e17a-144">The binding element of the [\<netMsmqBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e17a-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e17a-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement>
- <xref:System.ServiceModel.NetMsmqBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetMsmqBindingElement.Security%2A>
- <xref:System.ServiceModel.NetMsmqSecurity>
- [<span data-ttu-id="5e17a-146">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5e17a-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5e17a-147">Vazby</span><span class="sxs-lookup"><span data-stu-id="5e17a-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="5e17a-148">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5e17a-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5e17a-149">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5e17a-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5e17a-150">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="5e17a-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="5e17a-151">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="5e17a-151">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)
