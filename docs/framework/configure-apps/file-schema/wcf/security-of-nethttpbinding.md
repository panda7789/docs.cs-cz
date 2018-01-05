---
title: "&lt;security&gt; – &lt;netHttpBinding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1caae9411ca0ba8896613a38b446a3f0d190bb18
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnethttpbinding"></a><span data-ttu-id="5a356-102">&lt;security&gt; – &lt;netHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5a356-102">&lt;security&gt; of &lt;netHttpBinding</span></span>
<span data-ttu-id="5a356-103">Definuje možnosti zabezpečení [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5a356-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="5a356-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5a356-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a356-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="5a356-105">\<bindings></span></span>  
<span data-ttu-id="5a356-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="5a356-106">\<netHttpBinding></span></span>  
<span data-ttu-id="5a356-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="5a356-107">\<binding></span></span>  
<span data-ttu-id="5a356-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="5a356-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a356-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a356-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a356-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5a356-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a356-111">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a356-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a356-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="5a356-112">Attributes</span></span>  
  
|<span data-ttu-id="5a356-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="5a356-113">Attribute</span></span>|<span data-ttu-id="5a356-114">Popis</span><span class="sxs-lookup"><span data-stu-id="5a356-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a356-115">režim</span><span class="sxs-lookup"><span data-stu-id="5a356-115">mode</span></span>|<span data-ttu-id="5a356-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="5a356-116">Optional.</span></span> <span data-ttu-id="5a356-117">Určuje typ zabezpečení, který se používá.</span><span class="sxs-lookup"><span data-stu-id="5a356-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="5a356-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="5a356-118">The default is `None`.</span></span> <span data-ttu-id="5a356-119">Tento atribut je typu <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> --> `System.ServiceModel.NetHttpSecurityMode`.</span><span class="sxs-lookup"><span data-stu-id="5a356-119">This attribute is of type <!--zz <xref:System.ServiceModel.NetHttpSecurityMode> -->`System.ServiceModel.NetHttpSecurityMode`.</span></span>|
  
## <a name="mode-attribute"></a><span data-ttu-id="5a356-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="5a356-120">mode Attribute</span></span>  
  
|<span data-ttu-id="5a356-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5a356-121">Value</span></span>|<span data-ttu-id="5a356-122">Popis</span><span class="sxs-lookup"><span data-stu-id="5a356-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5a356-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="5a356-123">None</span></span>|<span data-ttu-id="5a356-124">-Zprávy není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="5a356-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="5a356-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="5a356-125">Transport</span></span>|<span data-ttu-id="5a356-126">Zabezpečení je k dispozici použití přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a356-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="5a356-127">Protokolu SOAP zprávy jsou zabezpečené pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="5a356-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="5a356-128">Služba je ověřen u klienta pomocí certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="5a356-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="5a356-129">Klient je ověřen pomocí ClientCredentialType zadaný.</span><span class="sxs-lookup"><span data-stu-id="5a356-129">The client is authenticated using the ClientCredentialType supplied.</span></span>|  
|<span data-ttu-id="5a356-130">Zpráva</span><span class="sxs-lookup"><span data-stu-id="5a356-130">Message</span></span>|<span data-ttu-id="5a356-131">Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5a356-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="5a356-132">Ve výchozím nastavení je text šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="5a356-132">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="5a356-133">Pro tuto vazbu systému vyžaduje, aby certifikát serveru poskytnuta klientovi vzdálené správy.</span><span class="sxs-lookup"><span data-stu-id="5a356-133">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="5a356-134">Jediné platné `ClientCredentialType` pro tuto vazbu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="5a356-134">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="5a356-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="5a356-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="5a356-136">Ověření integrity a důvěrnosti serveru jsou poskytovány zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="5a356-136">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="5a356-137">Ověření klienta je k dispozici prostřednictvím zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="5a356-137">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="5a356-138">Tento režim je důležité, když se uživatel ověřuje pomocí uživatelského jména a hesla a je stávajícího nasazení HTTP pro přenos zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5a356-138">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="5a356-139">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="5a356-139">TransportCredentialOnly</span></span>|<span data-ttu-id="5a356-140">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="5a356-140">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="5a356-141">Poskytuje ověření klienta založené na protokolu http.</span><span class="sxs-lookup"><span data-stu-id="5a356-141">It provides http-based client authentication.</span></span> <span data-ttu-id="5a356-142">Tento režim musí být použit s opatrní.</span><span class="sxs-lookup"><span data-stu-id="5a356-142">This mode should be used with caution.</span></span> <span data-ttu-id="5a356-143">By být používána v prostředích, kde se jiným způsobem (například IPSec) zajišťuje zabezpečení přenosu a zajišťuje pouze ověřování klienta [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="5a356-143">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a356-144">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5a356-144">Child Elements</span></span>  
  
|<span data-ttu-id="5a356-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a356-145">Element</span></span>|<span data-ttu-id="5a356-146">Popis</span><span class="sxs-lookup"><span data-stu-id="5a356-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a356-147">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="5a356-147">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nethttpbinding.md)|<span data-ttu-id="5a356-148">Definuje nastavení zabezpečení přenosu pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a356-148">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="5a356-149">Tento element odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="5a356-149">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="5a356-150">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="5a356-150">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-nethttpbinding.md)|<span data-ttu-id="5a356-151">Definuje nastavení zabezpečení zpráv pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a356-151">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="5a356-152">Tento element odpovídá <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="5a356-152">This element corresponds to <!--zz <xref:System.ServiceModel.NetHttpMessageSecurity> --> `System.ServiceModel.NetHttpMessageSecurity`.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a356-153">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5a356-153">Parent Elements</span></span>  
  
|<span data-ttu-id="5a356-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="5a356-154">Element</span></span>|<span data-ttu-id="5a356-155">Popis</span><span class="sxs-lookup"><span data-stu-id="5a356-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5a356-156">vazba</span><span class="sxs-lookup"><span data-stu-id="5a356-156">binding</span></span>|<span data-ttu-id="5a356-157">Element vazby [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5a356-157">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a356-158">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a356-158">Remarks</span></span>  
 <span data-ttu-id="5a356-159">Ve výchozím nastavení není zabezpečené zprávu protokolu SOAP a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="5a356-159">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="5a356-160">Tento element umožňuje konfigurovat nastavení dalšího ověření zabezpečení pro `netHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="5a356-160">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a356-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a356-161">See Also</span></span>  
 <xref:System.ServiceModel.NetHttpBinding.Security%2A>  
 <span data-ttu-id="5a356-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span><span class="sxs-lookup"><span data-stu-id="5a356-162"><xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A></span></span>    
 [<span data-ttu-id="5a356-163">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5a356-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5a356-164">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="5a356-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="5a356-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="5a356-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5a356-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5a356-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5a356-167">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="5a356-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="5a356-168">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="5a356-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
