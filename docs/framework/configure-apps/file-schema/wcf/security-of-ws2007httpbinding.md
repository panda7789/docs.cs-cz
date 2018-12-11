---
title: '&lt;security&gt; – &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: fb92e7549b86a2c4a4a8453d13f6c4f08d696348
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129776"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="8c98a-102">&lt;security&gt; – &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="8c98a-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="8c98a-103">Představuje nastavení zabezpečení použité s [ \<ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="8c98a-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="8c98a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8c98a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="8c98a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8c98a-105">\<bindings></span></span>  
<span data-ttu-id="8c98a-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="8c98a-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="8c98a-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8c98a-107">\<binding></span></span>  
<span data-ttu-id="8c98a-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="8c98a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c98a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c98a-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c98a-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8c98a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8c98a-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8c98a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c98a-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="8c98a-112">Attributes</span></span>  
  
|<span data-ttu-id="8c98a-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="8c98a-113">Attribute</span></span>|<span data-ttu-id="8c98a-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8c98a-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="8c98a-115">– Volitelné.</span><span class="sxs-lookup"><span data-stu-id="8c98a-115">-   Optional.</span></span> <span data-ttu-id="8c98a-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="8c98a-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="8c98a-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="8c98a-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="8c98a-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="8c98a-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="8c98a-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="8c98a-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="8c98a-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8c98a-120">Value</span></span>|<span data-ttu-id="8c98a-121">Popis</span><span class="sxs-lookup"><span data-stu-id="8c98a-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="8c98a-122">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="8c98a-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="8c98a-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8c98a-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="8c98a-124">Služba musí být nakonfigurovaný s certifikáty vrstvy SSL (Secure Sockets).</span><span class="sxs-lookup"><span data-stu-id="8c98a-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="8c98a-125">Zprávu je zcela zabezpečené pomocí protokolu HTTPS a služba je ověřený pomocí klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="8c98a-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="8c98a-126">Ověření klienta je řízen pomocí `ClientCredentials` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="8c98a-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="8c98a-127">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8c98a-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="8c98a-128">Ve výchozím nastavení je SOAP body šifrované a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="8c98a-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="8c98a-129">Tento režim nabízí širokou škálu funkcí, jako je například, jestli přihlašovací údaje služby najdete na adrese klienta vzdáleně, sada algoritmů, které chcete použít a jaké úroveň ochrany a platí pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="8c98a-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="8c98a-130">Ověření klienta se provádí jednou pro každou relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="8c98a-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="8c98a-131">V tomto režimu HTTPS poskytuje integritu, šifrování a ověřování serveru a zabezpečení zpráv SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="8c98a-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="8c98a-132">Ve výchozím nastavení ověření klienta se provádí jednou pro každou relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="8c98a-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c98a-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8c98a-133">Child Elements</span></span>  
  
|<span data-ttu-id="8c98a-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c98a-134">Element</span></span>|<span data-ttu-id="8c98a-135">Popis</span><span class="sxs-lookup"><span data-stu-id="8c98a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c98a-136">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="8c98a-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="8c98a-137">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="8c98a-137">Defines the transport security settings.</span></span> <span data-ttu-id="8c98a-138">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="8c98a-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="8c98a-139">Tato nastavení se použijí jenom v případě, režim je nastaven na Transport.</span><span class="sxs-lookup"><span data-stu-id="8c98a-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="8c98a-140">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="8c98a-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="8c98a-141">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="8c98a-141">Defines the security settings for the message.</span></span> <span data-ttu-id="8c98a-142">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="8c98a-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="8c98a-143">Tato nastavení se nepoužijí, když režim je nastaven na Transport.</span><span class="sxs-lookup"><span data-stu-id="8c98a-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8c98a-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8c98a-144">Parent Elements</span></span>  
  
|<span data-ttu-id="8c98a-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="8c98a-145">Element</span></span>|<span data-ttu-id="8c98a-146">Popis</span><span class="sxs-lookup"><span data-stu-id="8c98a-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c98a-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="8c98a-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="8c98a-148">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="8c98a-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8c98a-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8c98a-149">Remarks</span></span>  
 <span data-ttu-id="8c98a-150">Tento element je určen pro spolupráci se službami, které implementují WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="8c98a-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="8c98a-151">Zabezpečení přenosu pro tuto vazbu je vrstva SSL (Secure Sockets) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8c98a-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c98a-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="8c98a-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="8c98a-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8c98a-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8c98a-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="8c98a-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8c98a-155">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="8c98a-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8c98a-156">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="8c98a-156">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="8c98a-157">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8c98a-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
