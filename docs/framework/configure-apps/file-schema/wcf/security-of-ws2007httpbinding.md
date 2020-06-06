---
title: <security> z <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: e88f55f3651d1ccd55631dce13a0349ac2772624
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736386"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="794f5-102">\<security> z \<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="794f5-102">\<security> of \<ws2007HttpBinding></span></span>
<span data-ttu-id="794f5-103">Představuje nastavení zabezpečení používané s [\<ws2007HttpBinding>](ws2007httpbinding.md) prvkem.</span><span class="sxs-lookup"><span data-stu-id="794f5-103">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="794f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="794f5-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="794f5-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="794f5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="794f5-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="794f5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="794f5-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="794f5-107">Attributes</span></span>  
  
|<span data-ttu-id="794f5-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="794f5-108">Attribute</span></span>|<span data-ttu-id="794f5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="794f5-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="794f5-110">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="794f5-110">-   Optional.</span></span> <span data-ttu-id="794f5-111">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="794f5-111">Specifies the type of security that is applied.</span></span> <span data-ttu-id="794f5-112">Výchozí formát je `Message`.</span><span class="sxs-lookup"><span data-stu-id="794f5-112">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="794f5-113">Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="794f5-113">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="794f5-114">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="794f5-114">Mode Attribute</span></span>  
  
|<span data-ttu-id="794f5-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="794f5-115">Value</span></span>|<span data-ttu-id="794f5-116">Description</span><span class="sxs-lookup"><span data-stu-id="794f5-116">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="794f5-117">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="794f5-117">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="794f5-118">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="794f5-118">Security is provided using HTTPS.</span></span> <span data-ttu-id="794f5-119">Služba musí být nakonfigurovaná s certifikáty SSL (Secure Sockets Layer) (SSL).</span><span class="sxs-lookup"><span data-stu-id="794f5-119">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="794f5-120">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a služba je ověřena klientem pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="794f5-120">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="794f5-121">Ověřování klienta je řízeno `ClientCredentials` atributem [\<transport>](transport-of-ws2007httpbinding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="794f5-121">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="794f5-122">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="794f5-122">Security is provided using SOAP message security.</span></span> <span data-ttu-id="794f5-123">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="794f5-123">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="794f5-124">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty> .</span><span class="sxs-lookup"><span data-stu-id="794f5-124">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="794f5-125">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="794f5-125">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="794f5-126">V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="794f5-126">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="794f5-127">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="794f5-127">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="794f5-128">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="794f5-128">Child Elements</span></span>  
  
|<span data-ttu-id="794f5-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="794f5-129">Element</span></span>|<span data-ttu-id="794f5-130">Description</span><span class="sxs-lookup"><span data-stu-id="794f5-130">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="794f5-131">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="794f5-131">Defines the transport security settings.</span></span> <span data-ttu-id="794f5-132">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="794f5-132">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="794f5-133">Tato nastavení se aplikují jenom v případě, že je režim nastavený na přenos.</span><span class="sxs-lookup"><span data-stu-id="794f5-133">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="794f5-134">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="794f5-134">Defines the security settings for the message.</span></span> <span data-ttu-id="794f5-135">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="794f5-135">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="794f5-136">Tato nastavení se neaplikují, pokud je režim nastavený na přenos.</span><span class="sxs-lookup"><span data-stu-id="794f5-136">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="794f5-137">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="794f5-137">Parent Elements</span></span>  
  
|<span data-ttu-id="794f5-138">Prvek</span><span class="sxs-lookup"><span data-stu-id="794f5-138">Element</span></span>|<span data-ttu-id="794f5-139">Description</span><span class="sxs-lookup"><span data-stu-id="794f5-139">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="794f5-140">Zabezpečená vazba pro aplikace přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="794f5-140">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="794f5-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="794f5-141">Remarks</span></span>  
 <span data-ttu-id="794f5-142">Tento prvek je navržen pro zajištění spolupráce se službami, které implementují specifikace WS-\*.</span><span class="sxs-lookup"><span data-stu-id="794f5-142">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="794f5-143">Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="794f5-143">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="794f5-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="794f5-144">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="794f5-145">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="794f5-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="794f5-146">Vazby</span><span class="sxs-lookup"><span data-stu-id="794f5-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="794f5-147">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="794f5-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="794f5-148">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="794f5-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
