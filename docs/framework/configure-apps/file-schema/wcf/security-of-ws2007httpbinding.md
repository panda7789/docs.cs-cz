---
title: "&lt;security&gt; – &lt;ws2007HttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 355fa3a7031c9650d52d258b9d5ef67b291e6e17
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="cfe29-102">&lt;security&gt; – &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="cfe29-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="cfe29-103">Představuje nastavení zabezpečení použité s [ \<– ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="cfe29-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="cfe29-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cfe29-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cfe29-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cfe29-105">\<bindings></span></span>  
<span data-ttu-id="cfe29-106">\<– ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cfe29-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="cfe29-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cfe29-107">\<binding></span></span>  
<span data-ttu-id="cfe29-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cfe29-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfe29-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfe29-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <bindings>  
        <ws2007HttpBinding>  
            <binding name = "string">  
              <security mode="None/Message/Transport/TransportWithMessageCredential">  
                  <transport>  
                  </transport>  
                  <message>  
                  </message>  
              </security  
        </ws2007HttpBinding>  
    </bindings>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cfe29-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cfe29-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cfe29-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cfe29-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cfe29-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cfe29-112">Attributes</span></span>  
  
|<span data-ttu-id="cfe29-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cfe29-113">Attribute</span></span>|<span data-ttu-id="cfe29-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cfe29-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="cfe29-115">-Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cfe29-115">-   Optional.</span></span> <span data-ttu-id="cfe29-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="cfe29-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="cfe29-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="cfe29-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="cfe29-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="cfe29-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="cfe29-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="cfe29-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="cfe29-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cfe29-120">Value</span></span>|<span data-ttu-id="cfe29-121">Popis</span><span class="sxs-lookup"><span data-stu-id="cfe29-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="cfe29-122">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="cfe29-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="cfe29-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cfe29-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="cfe29-124">Služba musí být nakonfigurován pomocí certifikátů Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="cfe29-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="cfe29-125">Zpráva zcela zabezpečené pomocí protokolu HTTPS a službu ověření klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="cfe29-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="cfe29-126">Ověření klienta je řízen pomocí `ClientCredentials` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="cfe29-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="cfe29-127">Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="cfe29-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="cfe29-128">Ve výchozím nastavení je SOAP body šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="cfe29-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="cfe29-129">Tento režim nabízí celou řadu funkcí, např. zda jsou k dispozici na straně klienta vzdálené správy, sada algoritmů, které chcete použít, přihlašovací údaje služby a jakou úroveň ochrany, která platí pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="cfe29-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="cfe29-130">Ověření klienta se provádí jednou pro každou relaci a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="cfe29-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="cfe29-131">V tomto režimu HTTPS poskytuje integrity, šifrování a ověřování serveru a zabezpečení zpráv protokolu SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="cfe29-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="cfe29-132">Ve výchozím nastavení ověření klienta se provádí jednou pro každou relaci a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="cfe29-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cfe29-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cfe29-133">Child Elements</span></span>  
  
|<span data-ttu-id="cfe29-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="cfe29-134">Element</span></span>|<span data-ttu-id="cfe29-135">Popis</span><span class="sxs-lookup"><span data-stu-id="cfe29-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfe29-136">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="cfe29-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="cfe29-137">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="cfe29-137">Defines the transport security settings.</span></span> <span data-ttu-id="cfe29-138">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="cfe29-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="cfe29-139">Tato nastavení se použijí jenom v případě, že režim je nastaven na přenos.</span><span class="sxs-lookup"><span data-stu-id="cfe29-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="cfe29-140">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="cfe29-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="cfe29-141">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="cfe29-141">Defines the security settings for the message.</span></span> <span data-ttu-id="cfe29-142">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="cfe29-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="cfe29-143">Tato nastavení se nepoužívají, pokud režim je nastaven na přenos.</span><span class="sxs-lookup"><span data-stu-id="cfe29-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cfe29-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cfe29-144">Parent Elements</span></span>  
  
|<span data-ttu-id="cfe29-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="cfe29-145">Element</span></span>|<span data-ttu-id="cfe29-146">Popis</span><span class="sxs-lookup"><span data-stu-id="cfe29-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cfe29-147">\<– ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="cfe29-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="cfe29-148">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="cfe29-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfe29-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfe29-149">Remarks</span></span>  
 <span data-ttu-id="cfe29-150">Tento element je určená pro vzájemná spolupráce pomocí služby, které implementují WS-* specifikace.</span><span class="sxs-lookup"><span data-stu-id="cfe29-150">This element is designed for interoperation with services that implement WS-* specifications.</span></span> <span data-ttu-id="cfe29-151">Zabezpečení přenosu pro tuto vazbu Secure Sockets Layer (SSL) je protokol HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cfe29-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfe29-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfe29-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="cfe29-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="cfe29-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cfe29-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="cfe29-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cfe29-155">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="cfe29-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cfe29-156">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="cfe29-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cfe29-157">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cfe29-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
