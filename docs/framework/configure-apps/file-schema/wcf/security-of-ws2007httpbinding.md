---
title: <security> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736386"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="118b1-102">> \<zabezpečení \<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="118b1-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="118b1-103">Představuje nastavení zabezpečení používané [> elementu\<WS2007HttpBinding](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="118b1-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
<span data-ttu-id="118b1-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="118b1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="118b1-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="118b1-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="118b1-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="118b1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="118b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ws2007HttpBinding >** ](ws2007httpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="118b1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)</span></span>\
<span data-ttu-id="118b1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="118b1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="118b1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="118b1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="118b1-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="118b1-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="118b1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="118b1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="118b1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="118b1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="118b1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="118b1-113">Attributes</span></span>  
  
|<span data-ttu-id="118b1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="118b1-114">Attribute</span></span>|<span data-ttu-id="118b1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="118b1-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="118b1-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="118b1-116">-   Optional.</span></span> <span data-ttu-id="118b1-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="118b1-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="118b1-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="118b1-118">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="118b1-119">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="118b1-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="118b1-120">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="118b1-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="118b1-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="118b1-121">Value</span></span>|<span data-ttu-id="118b1-122">Popis</span><span class="sxs-lookup"><span data-stu-id="118b1-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="118b1-123">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="118b1-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="118b1-124">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="118b1-124">Security is provided using HTTPS.</span></span> <span data-ttu-id="118b1-125">Služba musí být nakonfigurovaná s certifikáty SSL (Secure Sockets Layer) (SSL).</span><span class="sxs-lookup"><span data-stu-id="118b1-125">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="118b1-126">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="118b1-126">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="118b1-127">Ověřování klienta je řízeno pomocí atributu `ClientCredentials` elementu [\<transport >](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="118b1-127">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="118b1-128">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="118b1-128">Security is provided using SOAP message security.</span></span> <span data-ttu-id="118b1-129">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="118b1-129">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="118b1-130">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici na klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="118b1-130">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="118b1-131">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="118b1-131">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="118b1-132">V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="118b1-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="118b1-133">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="118b1-133">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="118b1-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="118b1-134">Child Elements</span></span>  
  
|<span data-ttu-id="118b1-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="118b1-135">Element</span></span>|<span data-ttu-id="118b1-136">Popis</span><span class="sxs-lookup"><span data-stu-id="118b1-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="118b1-137">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="118b1-137">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="118b1-138">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="118b1-138">Defines the transport security settings.</span></span> <span data-ttu-id="118b1-139">Tento prvek odpovídá typu <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="118b1-139">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="118b1-140">Tato nastavení se aplikují jenom v případě, že je režim nastavený na přenos.</span><span class="sxs-lookup"><span data-stu-id="118b1-140">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="118b1-141">> \<zprávy</span><span class="sxs-lookup"><span data-stu-id="118b1-141">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="118b1-142">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="118b1-142">Defines the security settings for the message.</span></span> <span data-ttu-id="118b1-143">Tento prvek odpovídá typu <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="118b1-143">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="118b1-144">Tato nastavení se neaplikují, pokud je režim nastavený na přenos.</span><span class="sxs-lookup"><span data-stu-id="118b1-144">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="118b1-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="118b1-145">Parent Elements</span></span>  
  
|<span data-ttu-id="118b1-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="118b1-146">Element</span></span>|<span data-ttu-id="118b1-147">Popis</span><span class="sxs-lookup"><span data-stu-id="118b1-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="118b1-148">\<ws2007HttpBinding ></span><span class="sxs-lookup"><span data-stu-id="118b1-148">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="118b1-149">Zabezpečená vazba pro aplikace přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="118b1-149">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="118b1-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="118b1-150">Remarks</span></span>  
 <span data-ttu-id="118b1-151">Tento prvek je navržen pro zajištění spolupráce se službami, které implementují specifikace WS-\*.</span><span class="sxs-lookup"><span data-stu-id="118b1-151">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="118b1-152">Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="118b1-152">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="118b1-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="118b1-153">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="118b1-154">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="118b1-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="118b1-155">Vazby</span><span class="sxs-lookup"><span data-stu-id="118b1-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="118b1-156">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="118b1-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="118b1-157">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="118b1-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="118b1-158">vazba \<</span><span class="sxs-lookup"><span data-stu-id="118b1-158">\<binding></span></span>](bindings.md)
