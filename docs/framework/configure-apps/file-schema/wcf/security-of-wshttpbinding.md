---
title: "&lt;security&gt; – &lt;wsHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: dda6e48d3d2fec7f3ad6b9dd665e8a1092a47d60
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="e6a7c-102">&lt;security&gt; – &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e6a7c-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="e6a7c-103">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e6a7c-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="e6a7c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6a7c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6a7c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="e6a7c-105">\<bindings></span></span>  
<span data-ttu-id="e6a7c-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e6a7c-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="e6a7c-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="e6a7c-107">\<binding></span></span>  
<span data-ttu-id="e6a7c-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="e6a7c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a7c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6a7c-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">  
   <transport  
         clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string"   
      defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      defaultRealm="string" />  
   <message  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
       establishSecurityContext="Boolean"   
      negotiateServiceCredential="Boolean"/>  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6a7c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e6a7c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6a7c-111">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e6a7c-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6a7c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e6a7c-112">Attributes</span></span>  
  
|<span data-ttu-id="e6a7c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e6a7c-113">Attribute</span></span>|<span data-ttu-id="e6a7c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e6a7c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6a7c-115">režim</span><span class="sxs-lookup"><span data-stu-id="e6a7c-115">mode</span></span>|<span data-ttu-id="e6a7c-116">-Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-116">-   Optional.</span></span> <span data-ttu-id="e6a7c-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e6a7c-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-118">The default is `Message`.</span></span><br /><span data-ttu-id="e6a7c-119">-Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e6a7c-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="e6a7c-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="e6a7c-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e6a7c-121">Value</span></span>|<span data-ttu-id="e6a7c-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e6a7c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e6a7c-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="e6a7c-123">None</span></span>|<span data-ttu-id="e6a7c-124">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-124">Security is disabled.</span></span>|  
|<span data-ttu-id="e6a7c-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="e6a7c-125">Transport</span></span>|<span data-ttu-id="e6a7c-126">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="e6a7c-127">Službu je potřeba nakonfigurovat s certifikáty protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="e6a7c-128">Zpráva je zcela zabezpečené pomocí protokolu HTTPS a ověření klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="e6a7c-129">Ověření klienta je řízen pomocí `ClientCredentials` atribut.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="e6a7c-130">z [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e6a7c-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="e6a7c-131">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e6a7c-131">Message</span></span>|<span data-ttu-id="e6a7c-132">Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="e6a7c-133">Ve výchozím nastavení těla protokolu SOAP je zašifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="e6a7c-134">Tento režim nabízí celou řadu funkcí, např. zda jsou k dispozici na straně klienta vzdálené správy, sada algoritmů, které chcete použít, přihlašovací údaje služby a jakou úroveň ochrany, která platí pro tělo zprávy prostřednictvím vlastnosti Security.Message.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="e6a7c-135">Ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="e6a7c-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e6a7c-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="e6a7c-137">V tomto režimu HTTPS poskytuje integrity, šifrování a ověřování serveru a zabezpečení zpráv protokolu SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="e6a7c-138">Ve výchozím nastavení ověření klienta se provádí jednou za relace a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6a7c-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e6a7c-139">Child Elements</span></span>  
  
|<span data-ttu-id="e6a7c-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6a7c-140">Element</span></span>|<span data-ttu-id="e6a7c-141">Popis</span><span class="sxs-lookup"><span data-stu-id="e6a7c-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6a7c-142">\<transport></span><span class="sxs-lookup"><span data-stu-id="e6a7c-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="e6a7c-143">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-143">Defines the transport security settings.</span></span> <span data-ttu-id="e6a7c-144">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="e6a7c-145">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="e6a7c-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="e6a7c-146">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-146">Defines the security settings for the message.</span></span> <span data-ttu-id="e6a7c-147">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e6a7c-148">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e6a7c-148">Parent Elements</span></span>  
  
|<span data-ttu-id="e6a7c-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6a7c-149">Element</span></span>|<span data-ttu-id="e6a7c-150">Popis</span><span class="sxs-lookup"><span data-stu-id="e6a7c-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6a7c-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e6a7c-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="e6a7c-152">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6a7c-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6a7c-153">Remarks</span></span>  
 <span data-ttu-id="e6a7c-154">Třída WSHttpBinding je navržena pro vzájemná spolupráce pomocí služby, které implementují WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="e6a7c-155">Zabezpečení přenosu pro tuto vazbu Secure Sockets Layer (SSL) je protokol HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e6a7c-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6a7c-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6a7c-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="e6a7c-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e6a7c-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e6a7c-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="e6a7c-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e6a7c-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="e6a7c-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e6a7c-160">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="e6a7c-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e6a7c-161">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="e6a7c-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
