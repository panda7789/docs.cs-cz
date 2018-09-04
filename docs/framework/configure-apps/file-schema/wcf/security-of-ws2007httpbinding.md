---
title: '&lt;security&gt; – &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 00d1f43cb2d3f3aa67e72ee7ae405041bd2842ac
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509121"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="539f7-102">&lt;security&gt; – &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="539f7-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="539f7-103">Představuje nastavení zabezpečení použité s [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="539f7-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="539f7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="539f7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="539f7-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="539f7-105">\<bindings></span></span>  
<span data-ttu-id="539f7-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="539f7-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="539f7-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="539f7-107">\<binding></span></span>  
<span data-ttu-id="539f7-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="539f7-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="539f7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="539f7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="539f7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="539f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="539f7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="539f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="539f7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="539f7-112">Attributes</span></span>  
  
|<span data-ttu-id="539f7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="539f7-113">Attribute</span></span>|<span data-ttu-id="539f7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="539f7-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="539f7-115">– Volitelné.</span><span class="sxs-lookup"><span data-stu-id="539f7-115">-   Optional.</span></span> <span data-ttu-id="539f7-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="539f7-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="539f7-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="539f7-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="539f7-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="539f7-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="539f7-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="539f7-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="539f7-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="539f7-120">Value</span></span>|<span data-ttu-id="539f7-121">Popis</span><span class="sxs-lookup"><span data-stu-id="539f7-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="539f7-122">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="539f7-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="539f7-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="539f7-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="539f7-124">Služba musí být nakonfigurovaný s certifikáty vrstvy SSL (Secure Sockets).</span><span class="sxs-lookup"><span data-stu-id="539f7-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="539f7-125">Zprávu je zcela zabezpečené pomocí protokolu HTTPS a služba je ověřený pomocí klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="539f7-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="539f7-126">Ověření klienta je řízen pomocí `ClientCredentials` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="539f7-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="539f7-127">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="539f7-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="539f7-128">Ve výchozím nastavení je SOAP body šifrované a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="539f7-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="539f7-129">Tento režim nabízí širokou škálu funkcí, jako je například, jestli přihlašovací údaje služby najdete na adrese klienta vzdáleně, sada algoritmů, které chcete použít a jaké úroveň ochrany a platí pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="539f7-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="539f7-130">Ověření klienta se provádí jednou pro každou relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="539f7-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="539f7-131">V tomto režimu HTTPS poskytuje integritu, šifrování a ověřování serveru a zabezpečení zpráv SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="539f7-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="539f7-132">Ve výchozím nastavení ověření klienta se provádí jednou pro každou relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="539f7-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="539f7-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="539f7-133">Child Elements</span></span>  
  
|<span data-ttu-id="539f7-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="539f7-134">Element</span></span>|<span data-ttu-id="539f7-135">Popis</span><span class="sxs-lookup"><span data-stu-id="539f7-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="539f7-136">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="539f7-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="539f7-137">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="539f7-137">Defines the transport security settings.</span></span> <span data-ttu-id="539f7-138">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="539f7-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="539f7-139">Tato nastavení se použijí jenom v případě, režim je nastaven na Transport.</span><span class="sxs-lookup"><span data-stu-id="539f7-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="539f7-140">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="539f7-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="539f7-141">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="539f7-141">Defines the security settings for the message.</span></span> <span data-ttu-id="539f7-142">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="539f7-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="539f7-143">Tato nastavení se nepoužijí, když režim je nastaven na Transport.</span><span class="sxs-lookup"><span data-stu-id="539f7-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="539f7-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="539f7-144">Parent Elements</span></span>  
  
|<span data-ttu-id="539f7-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="539f7-145">Element</span></span>|<span data-ttu-id="539f7-146">Popis</span><span class="sxs-lookup"><span data-stu-id="539f7-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="539f7-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="539f7-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="539f7-148">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="539f7-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="539f7-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="539f7-149">Remarks</span></span>  
 <span data-ttu-id="539f7-150">Tento element je určen pro spolupráci se službami, které implementují WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="539f7-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="539f7-151">Zabezpečení přenosu pro tuto vazbu je vrstva SSL (Secure Sockets) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="539f7-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="539f7-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="539f7-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="539f7-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="539f7-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="539f7-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="539f7-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="539f7-155">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="539f7-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="539f7-156">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="539f7-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="539f7-157">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="539f7-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
