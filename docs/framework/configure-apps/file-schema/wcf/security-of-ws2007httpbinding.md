---
title: <security> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: a895df027bee7430e51e76c480136a49b6b2a0be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936578"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="adc9b-102">\<> zabezpečení > \<WS2007HttpBinding</span><span class="sxs-lookup"><span data-stu-id="adc9b-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="adc9b-103">Představuje nastavení zabezpečení používané s [ \<prvkem WS2007HttpBinding >](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="adc9b-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="adc9b-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="adc9b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="adc9b-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="adc9b-105">\<bindings></span></span>  
<span data-ttu-id="adc9b-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="adc9b-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="adc9b-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="adc9b-107">\<binding></span></span>  
<span data-ttu-id="adc9b-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="adc9b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adc9b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adc9b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="adc9b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="adc9b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="adc9b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="adc9b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="adc9b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="adc9b-112">Attributes</span></span>  
  
|<span data-ttu-id="adc9b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="adc9b-113">Attribute</span></span>|<span data-ttu-id="adc9b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="adc9b-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="adc9b-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="adc9b-115">-   Optional.</span></span> <span data-ttu-id="adc9b-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="adc9b-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="adc9b-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="adc9b-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="adc9b-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="adc9b-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="adc9b-119">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="adc9b-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="adc9b-120">Value</span><span class="sxs-lookup"><span data-stu-id="adc9b-120">Value</span></span>|<span data-ttu-id="adc9b-121">Popis</span><span class="sxs-lookup"><span data-stu-id="adc9b-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="adc9b-122">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="adc9b-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="adc9b-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="adc9b-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="adc9b-124">Služba musí být nakonfigurovaná s certifikáty SSL (Secure Sockets Layer) (SSL).</span><span class="sxs-lookup"><span data-stu-id="adc9b-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="adc9b-125">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="adc9b-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="adc9b-126">Ověřování klienta je řízeno pomocí `ClientCredentials` atributu [ \<> elementu transportu](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="adc9b-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="adc9b-127">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="adc9b-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="adc9b-128">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="adc9b-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="adc9b-129">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy <xref:System.ServiceModel.Security.SecurityMessageProperty>prostřednictvím.</span><span class="sxs-lookup"><span data-stu-id="adc9b-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="adc9b-130">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="adc9b-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="adc9b-131">V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="adc9b-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="adc9b-132">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="adc9b-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="adc9b-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="adc9b-133">Child Elements</span></span>  
  
|<span data-ttu-id="adc9b-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="adc9b-134">Element</span></span>|<span data-ttu-id="adc9b-135">Popis</span><span class="sxs-lookup"><span data-stu-id="adc9b-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adc9b-136">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="adc9b-136">\<transport></span></span>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="adc9b-137">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="adc9b-137">Defines the transport security settings.</span></span> <span data-ttu-id="adc9b-138">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="adc9b-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="adc9b-139">Tato nastavení se aplikují jenom v případě, že je režim nastavený na přenos.</span><span class="sxs-lookup"><span data-stu-id="adc9b-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="adc9b-140">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="adc9b-140">\<message></span></span>](message-of-ws2007httpbinding.md)|<span data-ttu-id="adc9b-141">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="adc9b-141">Defines the security settings for the message.</span></span> <span data-ttu-id="adc9b-142">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="adc9b-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="adc9b-143">Tato nastavení se neaplikují, pokud je režim nastavený na přenos.</span><span class="sxs-lookup"><span data-stu-id="adc9b-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="adc9b-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="adc9b-144">Parent Elements</span></span>  
  
|<span data-ttu-id="adc9b-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="adc9b-145">Element</span></span>|<span data-ttu-id="adc9b-146">Popis</span><span class="sxs-lookup"><span data-stu-id="adc9b-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="adc9b-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="adc9b-147">\<ws2007HttpBinding></span></span>](ws2007httpbinding.md)|<span data-ttu-id="adc9b-148">Zabezpečená vazba pro aplikace přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="adc9b-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="adc9b-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adc9b-149">Remarks</span></span>  
 <span data-ttu-id="adc9b-150">Tento prvek je navržen pro zajištění spolupráce se službami, které implementují specifikace WS-\*.</span><span class="sxs-lookup"><span data-stu-id="adc9b-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="adc9b-151">Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="adc9b-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc9b-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adc9b-152">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="adc9b-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="adc9b-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="adc9b-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="adc9b-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="adc9b-155">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="adc9b-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="adc9b-156">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="adc9b-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="adc9b-157">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="adc9b-157">\<binding></span></span>](../../../misc/binding.md)
