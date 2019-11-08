---
title: <security> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738578"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="37bf3-102">> \<zabezpečení \<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="37bf3-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="37bf3-103">Představuje možnosti zabezpečení [\<wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="37bf3-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="37bf3-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="37bf3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="37bf3-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="37bf3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="37bf3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="37bf3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="37bf3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="37bf3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="37bf3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="37bf3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="37bf3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="37bf3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37bf3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37bf3-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37bf3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="37bf3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="37bf3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="37bf3-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37bf3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="37bf3-113">Attributes</span></span>  
  
|<span data-ttu-id="37bf3-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="37bf3-114">Attribute</span></span>|<span data-ttu-id="37bf3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="37bf3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37bf3-116">režim</span><span class="sxs-lookup"><span data-stu-id="37bf3-116">mode</span></span>|<span data-ttu-id="37bf3-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="37bf3-117">-   Optional.</span></span> <span data-ttu-id="37bf3-118">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="37bf3-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="37bf3-119">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="37bf3-119">The default is `Message`.</span></span><br /><span data-ttu-id="37bf3-120">– Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="37bf3-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="37bf3-121">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="37bf3-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="37bf3-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="37bf3-122">Value</span></span>|<span data-ttu-id="37bf3-123">Popis</span><span class="sxs-lookup"><span data-stu-id="37bf3-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="37bf3-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="37bf3-124">None</span></span>|<span data-ttu-id="37bf3-125">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="37bf3-125">Security is disabled.</span></span>|  
|<span data-ttu-id="37bf3-126">Přepravu</span><span class="sxs-lookup"><span data-stu-id="37bf3-126">Transport</span></span>|<span data-ttu-id="37bf3-127">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="37bf3-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="37bf3-128">Služba musí být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="37bf3-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="37bf3-129">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a klient je ověřuje pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="37bf3-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="37bf3-130">Ověřování klienta je řízeno pomocí atributu `ClientCredentials`.</span><span class="sxs-lookup"><span data-stu-id="37bf3-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="37bf3-131">[> přenosu\<](transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="37bf3-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="37bf3-132">Zpráva</span><span class="sxs-lookup"><span data-stu-id="37bf3-132">Message</span></span>|<span data-ttu-id="37bf3-133">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="37bf3-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="37bf3-134">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="37bf3-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="37bf3-135">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy prostřednictvím vlastnosti Security. Message.</span><span class="sxs-lookup"><span data-stu-id="37bf3-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="37bf3-136">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="37bf3-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="37bf3-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="37bf3-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="37bf3-138">V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="37bf3-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="37bf3-139">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="37bf3-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37bf3-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="37bf3-140">Child Elements</span></span>  
  
|<span data-ttu-id="37bf3-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="37bf3-141">Element</span></span>|<span data-ttu-id="37bf3-142">Popis</span><span class="sxs-lookup"><span data-stu-id="37bf3-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37bf3-143">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="37bf3-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="37bf3-144">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="37bf3-144">Defines the transport security settings.</span></span> <span data-ttu-id="37bf3-145">Tento prvek odpovídá typu <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="37bf3-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="37bf3-146">> \<zprávy</span><span class="sxs-lookup"><span data-stu-id="37bf3-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="37bf3-147">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="37bf3-147">Defines the security settings for the message.</span></span> <span data-ttu-id="37bf3-148">Tento prvek odpovídá typu <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement>.</span><span class="sxs-lookup"><span data-stu-id="37bf3-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="37bf3-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="37bf3-149">Parent Elements</span></span>  
  
|<span data-ttu-id="37bf3-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="37bf3-150">Element</span></span>|<span data-ttu-id="37bf3-151">Popis</span><span class="sxs-lookup"><span data-stu-id="37bf3-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37bf3-152">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="37bf3-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="37bf3-153">Zabezpečená vazba pro aplikace přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="37bf3-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37bf3-154">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37bf3-154">Remarks</span></span>  
 <span data-ttu-id="37bf3-155">Třída WSHttpBinding je navržena pro zajištění spolupráce se službami, které implementují specifikace WS-\*.</span><span class="sxs-lookup"><span data-stu-id="37bf3-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="37bf3-156">Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="37bf3-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37bf3-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37bf3-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="37bf3-158">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="37bf3-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="37bf3-159">Vazby</span><span class="sxs-lookup"><span data-stu-id="37bf3-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="37bf3-160">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="37bf3-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="37bf3-161">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="37bf3-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="37bf3-162">vazba \<</span><span class="sxs-lookup"><span data-stu-id="37bf3-162">\<binding></span></span>](bindings.md)
