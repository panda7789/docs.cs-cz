---
title: "&lt;security&gt; – &lt;netTcpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 08e9f1f3b2145d94f491933639211a6eabd3c9fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="f1b4b-102">&lt;security&gt; – &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f1b4b-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="f1b4b-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="f1b4b-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1b4b-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-105">\<bindings></span></span>  
<span data-ttu-id="f1b4b-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-106">\<netTcpBinding></span></span>  
<span data-ttu-id="f1b4b-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-107">\<binding></span></span>  
<span data-ttu-id="f1b4b-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1b4b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1b4b-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1b4b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1b4b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f1b4b-111">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1b4b-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1b4b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1b4b-112">Attributes</span></span>  
  
|<span data-ttu-id="f1b4b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f1b4b-113">Attribute</span></span>|<span data-ttu-id="f1b4b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f1b4b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1b4b-115">režim</span><span class="sxs-lookup"><span data-stu-id="f1b4b-115">mode</span></span>|<span data-ttu-id="f1b4b-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-116">Optional.</span></span> <span data-ttu-id="f1b4b-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="f1b4b-118">Platné hodnoty jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-118">Valid values are shown below.</span></span> <span data-ttu-id="f1b4b-119">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="f1b4b-120">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f1b4b-121">režim atribut</span><span class="sxs-lookup"><span data-stu-id="f1b4b-121">mode Attribute</span></span>  
  
|<span data-ttu-id="f1b4b-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f1b4b-122">Value</span></span>|<span data-ttu-id="f1b4b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="f1b4b-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f1b4b-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="f1b4b-124">None</span></span>|<span data-ttu-id="f1b4b-125">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-125">Security is disabled.</span></span>|  
|<span data-ttu-id="f1b4b-126">Přenos</span><span class="sxs-lookup"><span data-stu-id="f1b4b-126">Transport</span></span>|<span data-ttu-id="f1b4b-127">Zabezpečení přenosu je k dispozici přes TCP nebo SPNego používá protokol TLS.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="f1b4b-128">Služba pravděpodobně nutné nakonfigurovat s certifikáty protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="f1b4b-129">Je možné kontrolovat úroveň ochrany s Tento režim.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="f1b4b-130">Zpráva</span><span class="sxs-lookup"><span data-stu-id="f1b4b-130">Message</span></span>|<span data-ttu-id="f1b4b-131">Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f1b4b-132">Ve výchozím nastavení je SOAP body šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="f1b4b-133">Tento režim nabízí celou řadu funkcí, např. zda jsou k dispozici na straně klienta vzdálené správy, sada algoritmů, které chcete použít, přihlašovací údaje služby a jakou úroveň ochrany, která platí pro tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="f1b4b-134">Ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="f1b4b-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="f1b4b-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="f1b4b-136">Zabezpečení přenosu je spolu s zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="f1b4b-137">Zabezpečení přenosu zajišťuje TLS přes TCP nebo SPNego a k zajištění integrity, šifrování a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="f1b4b-138">Zabezpečení zpráv protokolu SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="f1b4b-139">Ve výchozím nastavení ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1b4b-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1b4b-140">Child Elements</span></span>  
  
|<span data-ttu-id="f1b4b-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1b4b-141">Element</span></span>|<span data-ttu-id="f1b4b-142">Popis</span><span class="sxs-lookup"><span data-stu-id="f1b4b-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1b4b-143">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="f1b4b-144">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="f1b4b-145">Tento element je typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="f1b4b-146">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="f1b4b-147">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-147">Defines the security settings for the message.</span></span> <span data-ttu-id="f1b4b-148">Tento element je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1b4b-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1b4b-149">Parent Elements</span></span>  
  
|<span data-ttu-id="f1b4b-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1b4b-150">Element</span></span>|<span data-ttu-id="f1b4b-151">Popis</span><span class="sxs-lookup"><span data-stu-id="f1b4b-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1b4b-152">vazba</span><span class="sxs-lookup"><span data-stu-id="f1b4b-152">binding</span></span>|<span data-ttu-id="f1b4b-153">Element vazby [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="f1b4b-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1b4b-154">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1b4b-154">Remarks</span></span>  
 <span data-ttu-id="f1b4b-155">Všechny standardní vazby poskytuje parametry pro řízení požadavky na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="f1b4b-156">Tyto parametry obvykle zahrnují režim zabezpečení, který zadat, jestli se používá zabezpečení na úrovni zpráv nebo transportní vrstvy a výběr typu pověření klienta.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="f1b4b-157">Na základě volby možností tyto existuje, parametry zásobníku kanál je vytvořený pomocí příslušné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="f1b4b-158">Vazby poskytované systémem zadaný ve Windows Communication Foundation (WCF) jsou navržené tak, aby splňovaly některé z nejběžnějších požadavků scénáře sady.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="f1b4b-159">Každý z těchto vazeb umožňuje specifikaci požadavky na zabezpečení u některých konkrétních cílových scénářů.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="f1b4b-160">Tento element konfigurace poskytuje zabezpečení specifikace pro `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="f1b4b-161">Toto je bezpečné, spolehlivé a optimalizované vazbu vhodný pro komunikaci mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="f1b4b-162">Ve výchozím nastavení vygeneruje podpora protokolu TCP pro doručování zpráv a zabezpečení systému Windows pro zabezpečení zpráv a ověřování, WS-ReliableMessaging spolehlivost a zprávy v binární kódování runtime komunikačního balíku.</span><span class="sxs-lookup"><span data-stu-id="f1b4b-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1b4b-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1b4b-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="f1b4b-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f1b4b-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f1b4b-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="f1b4b-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f1b4b-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f1b4b-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f1b4b-167">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="f1b4b-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f1b4b-168">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="f1b4b-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
