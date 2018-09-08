---
title: '&lt;security&gt; – &lt;msmqIntegrationBinding&gt;'
ms.date: 03/30/2017
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6419c2157281d00cf79de16d4f494fc52bcee598
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195592"
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a><span data-ttu-id="33424-102">&lt;security&gt; – &lt;msmqIntegrationBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="33424-102">&lt;security&gt; of &lt;msmqIntegrationBinding&gt;</span></span>
<span data-ttu-id="33424-103">Definuje nastavení zabezpečení přenosu pro kanál integrace služby Řízení front zpráv (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="33424-103">Defines the transport security settings for the Message Queuing (MSMQ) integration channel.</span></span>  
  
 <span data-ttu-id="33424-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="33424-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="33424-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="33424-105">\<bindings></span></span>  
<span data-ttu-id="33424-106">msmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="33424-106">msmqIntegrationBinding</span></span>  
<span data-ttu-id="33424-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="33424-107">\<binding></span></span>  
<span data-ttu-id="33424-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="33424-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33424-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33424-109">Syntax</span></span>  
  
```xml  
<msmqIntegrationBinding>  
   <binding>   
       <security mode="None/Transport">  
         <transport msmqAuthenticationMode="None/Windows/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                        clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
            defaultProtectionLevel="None/Sign/EncryptAndSign" />  
       </security>  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33424-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33424-110">Attributes and Elements</span></span>  
 <span data-ttu-id="33424-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="33424-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33424-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="33424-112">Attributes</span></span>  
  
|<span data-ttu-id="33424-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="33424-113">Attribute</span></span>|<span data-ttu-id="33424-114">Popis</span><span class="sxs-lookup"><span data-stu-id="33424-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33424-115">režim</span><span class="sxs-lookup"><span data-stu-id="33424-115">mode</span></span>|<span data-ttu-id="33424-116">Určuje typ zabezpečení této kontroly integrity, šifrování a ověřování s kanálem integrace služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="33424-116">Specifies the type of security that controls integrity, confidentiality and authentication with the Message Queuing integration channel.</span></span> <span data-ttu-id="33424-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="33424-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="33424-118">-Žádný: Zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="33424-118">-   None: This disables security.</span></span><br /><span data-ttu-id="33424-119">-Přenos: Ochrana a ověřování se nabízejí Transport.</span><span class="sxs-lookup"><span data-stu-id="33424-119">-   Transport: Protection and authentication are offered by the transport.</span></span> <span data-ttu-id="33424-120">To platí pro zabezpečení zpráv mezi správci fronty dvě.</span><span class="sxs-lookup"><span data-stu-id="33424-120">This applies to the message security between the two queue managers.</span></span> <span data-ttu-id="33424-121">Neexistuje žádné zabezpečení nabízené mezi aplikací a správce fronty.</span><span class="sxs-lookup"><span data-stu-id="33424-121">There is no security offered between the application and queue manager.</span></span> <span data-ttu-id="33424-122">Existující aplikacím služby Msmq jsou funkčně ekvivalentní s tímto typem režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="33424-122">Existing Msmq applications are functionally equivalent with this type of security mode.</span></span><br /><br /> <span data-ttu-id="33424-123">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="33424-123">The default value is `Transport`.</span></span> <span data-ttu-id="33424-124">Tento atribut je typu <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="33424-124">This attribute is of type <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33424-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="33424-125">Child Elements</span></span>  
  
|<span data-ttu-id="33424-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="33424-126">Element</span></span>|<span data-ttu-id="33424-127">Popis</span><span class="sxs-lookup"><span data-stu-id="33424-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33424-128">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="33424-128">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|<span data-ttu-id="33424-129">Definuje nastavení zabezpečení pro přenos integrace služby Řízení front zpráv.</span><span class="sxs-lookup"><span data-stu-id="33424-129">Defines the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="33424-130">Tento prvek je typu <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="33424-130">This element is of type <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33424-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="33424-131">Parent Elements</span></span>  
  
|<span data-ttu-id="33424-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="33424-132">Element</span></span>|<span data-ttu-id="33424-133">Popis</span><span class="sxs-lookup"><span data-stu-id="33424-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="33424-134">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="33424-134">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="33424-135">Prvek vazby [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span><span class="sxs-lookup"><span data-stu-id="33424-135">The binding element of the [\<msmqIntegrationBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33424-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="33424-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [<span data-ttu-id="33424-137">Fronty ve WCF</span><span class="sxs-lookup"><span data-stu-id="33424-137">Queues in WCF</span></span>](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [<span data-ttu-id="33424-138">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="33424-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="33424-139">Vazby</span><span class="sxs-lookup"><span data-stu-id="33424-139">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="33424-140">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="33424-140">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="33424-141">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="33424-141">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="33424-142">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="33424-142">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="33424-143">\<msmqIntegrationBinding ></span><span class="sxs-lookup"><span data-stu-id="33424-143">\<msmqIntegrationBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
