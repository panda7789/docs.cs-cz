---
title: '&lt;security&gt; – &lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b7644e0cf9148cb489618b352ad09901799ceaa6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751087"
---
# <a name="ltsecuritygt-of-ltws2007httpbindinggt"></a><span data-ttu-id="965f4-102">&lt;security&gt; – &lt;ws2007HttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="965f4-102">&lt;security&gt; of &lt;ws2007HttpBinding&gt;</span></span>
<span data-ttu-id="965f4-103">Představuje nastavení zabezpečení použité s [ \<– ws2007HttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="965f4-103">Represents the security settings used with the [\<ws2007HttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) element.</span></span>  
  
 <span data-ttu-id="965f4-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="965f4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="965f4-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="965f4-105">\<bindings></span></span>  
<span data-ttu-id="965f4-106">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="965f4-106">\<ws2007HttpBinding></span></span>  
<span data-ttu-id="965f4-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="965f4-107">\<binding></span></span>  
<span data-ttu-id="965f4-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="965f4-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="965f4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="965f4-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="965f4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="965f4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="965f4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="965f4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="965f4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="965f4-112">Attributes</span></span>  
  
|<span data-ttu-id="965f4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="965f4-113">Attribute</span></span>|<span data-ttu-id="965f4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="965f4-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="965f4-115">-Volitelné.</span><span class="sxs-lookup"><span data-stu-id="965f4-115">-   Optional.</span></span> <span data-ttu-id="965f4-116">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="965f4-116">Specifies the type of security that is applied.</span></span> <span data-ttu-id="965f4-117">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="965f4-117">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="965f4-118">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="965f4-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="965f4-119">režim atribut</span><span class="sxs-lookup"><span data-stu-id="965f4-119">Mode Attribute</span></span>  
  
|<span data-ttu-id="965f4-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="965f4-120">Value</span></span>|<span data-ttu-id="965f4-121">Popis</span><span class="sxs-lookup"><span data-stu-id="965f4-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="965f4-122">Zabezpečení je vypnuté.</span><span class="sxs-lookup"><span data-stu-id="965f4-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="965f4-123">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="965f4-123">Security is provided using HTTPS.</span></span> <span data-ttu-id="965f4-124">Služba musí být nakonfigurován pomocí certifikátů Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="965f4-124">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="965f4-125">Zpráva zcela zabezpečené pomocí protokolu HTTPS a službu ověření klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="965f4-125">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="965f4-126">Ověření klienta je řízen pomocí `ClientCredentials` atribut [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="965f4-126">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="965f4-127">Zabezpečení je k dispozici pomocí zabezpečení zpráv protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="965f4-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="965f4-128">Ve výchozím nastavení je SOAP body šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="965f4-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="965f4-129">Tento režim nabízí celou řadu funkcí, např. zda jsou k dispozici na straně klienta vzdálené správy, sada algoritmů, které chcete použít, přihlašovací údaje služby a jakou úroveň ochrany, která platí pro tělo zprávy prostřednictvím <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span><span class="sxs-lookup"><span data-stu-id="965f4-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="965f4-130">Ověření klienta se provádí jednou pro každou relaci a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="965f4-130">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="965f4-131">V tomto režimu HTTPS poskytuje integrity, šifrování a ověřování serveru a zabezpečení zpráv protokolu SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="965f4-131">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="965f4-132">Ve výchozím nastavení ověření klienta se provádí jednou pro každou relaci a výsledky ověřování jsou uloženy v mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="965f4-132">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="965f4-133">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="965f4-133">Child Elements</span></span>  
  
|<span data-ttu-id="965f4-134">Prvek</span><span class="sxs-lookup"><span data-stu-id="965f4-134">Element</span></span>|<span data-ttu-id="965f4-135">Popis</span><span class="sxs-lookup"><span data-stu-id="965f4-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="965f4-136">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="965f4-136">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-ws2007httpbinding.md)|<span data-ttu-id="965f4-137">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="965f4-137">Defines the transport security settings.</span></span> <span data-ttu-id="965f4-138">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="965f4-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="965f4-139">Tato nastavení se použijí jenom v případě, že režim je nastaven na přenos.</span><span class="sxs-lookup"><span data-stu-id="965f4-139">These settings are applied only when the mode is set to Transport.</span></span>|  
|[<span data-ttu-id="965f4-140">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="965f4-140">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-ws2007httpbinding.md)|<span data-ttu-id="965f4-141">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="965f4-141">Defines the security settings for the message.</span></span> <span data-ttu-id="965f4-142">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="965f4-142">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="965f4-143">Tato nastavení se nepoužívají, pokud režim je nastaven na přenos.</span><span class="sxs-lookup"><span data-stu-id="965f4-143">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="965f4-144">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="965f4-144">Parent Elements</span></span>  
  
|<span data-ttu-id="965f4-145">Prvek</span><span class="sxs-lookup"><span data-stu-id="965f4-145">Element</span></span>|<span data-ttu-id="965f4-146">Popis</span><span class="sxs-lookup"><span data-stu-id="965f4-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="965f4-147">\<ws2007HttpBinding></span><span class="sxs-lookup"><span data-stu-id="965f4-147">\<ws2007HttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|<span data-ttu-id="965f4-148">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="965f4-148">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="965f4-149">Poznámky</span><span class="sxs-lookup"><span data-stu-id="965f4-149">Remarks</span></span>  
 <span data-ttu-id="965f4-150">Tento element je určená pro vzájemná spolupráce pomocí služby, které implementují WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="965f4-150">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="965f4-151">Zabezpečení přenosu pro tuto vazbu Secure Sockets Layer (SSL) je protokol HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="965f4-151">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="965f4-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="965f4-152">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [<span data-ttu-id="965f4-153">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="965f4-153">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="965f4-154">Vazby</span><span class="sxs-lookup"><span data-stu-id="965f4-154">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="965f4-155">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="965f4-155">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="965f4-156">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="965f4-156">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="965f4-157">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="965f4-157">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
