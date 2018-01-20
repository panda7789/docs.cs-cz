---
title: "&lt;security&gt; – &lt;basicHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
caps.latest.revision: "16"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 8d61075bc96427736f7e6f5a39302bbd59d434f9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a><span data-ttu-id="133c7-102">&lt;security&gt; – &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="133c7-102">&lt;security&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="133c7-103">Definuje možnosti zabezpečení [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="133c7-103">Defines the security capabilities of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="133c7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="133c7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="133c7-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="133c7-105">\<bindings></span></span>  
<span data-ttu-id="133c7-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="133c7-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="133c7-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="133c7-107">\<binding></span></span>  
<span data-ttu-id="133c7-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="133c7-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="133c7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="133c7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="133c7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="133c7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="133c7-111">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="133c7-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="133c7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="133c7-112">Attributes</span></span>  
  
|<span data-ttu-id="133c7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="133c7-113">Attribute</span></span>|<span data-ttu-id="133c7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="133c7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="133c7-115">režim</span><span class="sxs-lookup"><span data-stu-id="133c7-115">mode</span></span>|<span data-ttu-id="133c7-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="133c7-116">Optional.</span></span> <span data-ttu-id="133c7-117">Určuje typ zabezpečení, který se používá.</span><span class="sxs-lookup"><span data-stu-id="133c7-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="133c7-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="133c7-118">The default is `None`.</span></span> <span data-ttu-id="133c7-119">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="133c7-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="133c7-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="133c7-120">mode Attribute</span></span>  
  
|<span data-ttu-id="133c7-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="133c7-121">Value</span></span>|<span data-ttu-id="133c7-122">Popis</span><span class="sxs-lookup"><span data-stu-id="133c7-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="133c7-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="133c7-123">None</span></span>|<span data-ttu-id="133c7-124">-Zprávy není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="133c7-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="133c7-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="133c7-125">Transport</span></span>|<span data-ttu-id="133c7-126">Zabezpečení je k dispozici použití přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="133c7-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="133c7-127">Protokolu SOAP zprávy jsou zabezpečené pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="133c7-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="133c7-128">Služba je ověřen u klienta pomocí certifikátu X.509 služby.</span><span class="sxs-lookup"><span data-stu-id="133c7-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="133c7-129">Klient je ověřen pomocí ClientCredentialType zadaný.</span><span class="sxs-lookup"><span data-stu-id="133c7-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="133c7-130">Najdete v článku [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="133c7-130">See the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="133c7-131">Zpráva</span><span class="sxs-lookup"><span data-stu-id="133c7-131">Message</span></span>|<span data-ttu-id="133c7-132">Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="133c7-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="133c7-133">Ve výchozím nastavení je text šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="133c7-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="133c7-134">Pro tuto vazbu systému vyžaduje, aby certifikát serveru poskytnuta klientovi vzdálené správy.</span><span class="sxs-lookup"><span data-stu-id="133c7-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="133c7-135">Jediné platné `ClientCredentialType` pro tuto vazbu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="133c7-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="133c7-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="133c7-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="133c7-137">Ověření integrity a důvěrnosti serveru jsou poskytovány zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="133c7-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="133c7-138">Ověření klienta je k dispozici prostřednictvím zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="133c7-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="133c7-139">Tento režim je důležité, když se uživatel ověřuje pomocí uživatelského jména a hesla a je stávajícího nasazení HTTP pro přenos zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="133c7-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="133c7-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="133c7-140">TransportCredentialOnly</span></span>|<span data-ttu-id="133c7-141">Tento režim neposkytuje integrity a důvěrnosti zpráv.</span><span class="sxs-lookup"><span data-stu-id="133c7-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="133c7-142">Poskytuje ověření klienta založené na protokolu http.</span><span class="sxs-lookup"><span data-stu-id="133c7-142">It provides http-based client authentication.</span></span> <span data-ttu-id="133c7-143">Tento režim musí být použit s opatrní.</span><span class="sxs-lookup"><span data-stu-id="133c7-143">This mode should be used with caution.</span></span> <span data-ttu-id="133c7-144">By být používána v prostředích, kde se jiným způsobem (například IPSec) zajišťuje zabezpečení přenosu a zajišťuje pouze ověřování klienta [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="133c7-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="133c7-145">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="133c7-145">Child Elements</span></span>  
  
|<span data-ttu-id="133c7-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="133c7-146">Element</span></span>|<span data-ttu-id="133c7-147">Popis</span><span class="sxs-lookup"><span data-stu-id="133c7-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="133c7-148">\<transport></span><span class="sxs-lookup"><span data-stu-id="133c7-148">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|<span data-ttu-id="133c7-149">Definuje nastavení zabezpečení přenosu pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="133c7-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="133c7-150">Tento element odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="133c7-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="133c7-151">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="133c7-151">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|<span data-ttu-id="133c7-152">Definuje nastavení zabezpečení zpráv pro základní služba HTTP.</span><span class="sxs-lookup"><span data-stu-id="133c7-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="133c7-153">Tento element odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="133c7-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="133c7-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="133c7-154">Parent Elements</span></span>  
  
|<span data-ttu-id="133c7-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="133c7-155">Element</span></span>|<span data-ttu-id="133c7-156">Popis</span><span class="sxs-lookup"><span data-stu-id="133c7-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="133c7-157">vazba</span><span class="sxs-lookup"><span data-stu-id="133c7-157">binding</span></span>|<span data-ttu-id="133c7-158">Element vazby [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="133c7-158">The binding element of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="133c7-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="133c7-159">Remarks</span></span>  
 <span data-ttu-id="133c7-160">Ve výchozím nastavení není zabezpečené zprávu protokolu SOAP a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="133c7-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="133c7-161">Tento element umožňuje konfigurovat nastavení dalšího ověření zabezpečení pro `basicHttpBinding` elementu.</span><span class="sxs-lookup"><span data-stu-id="133c7-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="133c7-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="133c7-162">See Also</span></span>  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="133c7-163">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="133c7-163">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="133c7-164">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="133c7-164">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="133c7-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="133c7-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="133c7-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="133c7-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="133c7-167">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="133c7-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="133c7-168">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="133c7-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
