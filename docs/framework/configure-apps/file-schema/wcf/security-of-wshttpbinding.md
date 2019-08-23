---
title: <security> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: e627a63221d0013c89495d7ff81e02047a03df89
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936510"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="1ae7b-102">\<> zabezpečení > \<WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="1ae7b-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="1ae7b-103">Představuje možnosti [ \<zabezpečení wsHttpBinding >](wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="1ae7b-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="1ae7b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1ae7b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1ae7b-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="1ae7b-105">\<bindings></span></span>  
<span data-ttu-id="1ae7b-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1ae7b-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="1ae7b-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1ae7b-107">\<binding></span></span>  
<span data-ttu-id="1ae7b-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1ae7b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ae7b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ae7b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ae7b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ae7b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ae7b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ae7b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ae7b-112">Attributes</span></span>  
  
|<span data-ttu-id="1ae7b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1ae7b-113">Attribute</span></span>|<span data-ttu-id="1ae7b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1ae7b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ae7b-115">režim</span><span class="sxs-lookup"><span data-stu-id="1ae7b-115">mode</span></span>|<span data-ttu-id="1ae7b-116">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-116">-   Optional.</span></span> <span data-ttu-id="1ae7b-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="1ae7b-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-118">The default is `Message`.</span></span><br /><span data-ttu-id="1ae7b-119">– Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1ae7b-120">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="1ae7b-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="1ae7b-121">Value</span><span class="sxs-lookup"><span data-stu-id="1ae7b-121">Value</span></span>|<span data-ttu-id="1ae7b-122">Popis</span><span class="sxs-lookup"><span data-stu-id="1ae7b-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1ae7b-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="1ae7b-123">None</span></span>|<span data-ttu-id="1ae7b-124">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-124">Security is disabled.</span></span>|  
|<span data-ttu-id="1ae7b-125">Přepravu</span><span class="sxs-lookup"><span data-stu-id="1ae7b-125">Transport</span></span>|<span data-ttu-id="1ae7b-126">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="1ae7b-127">Služba musí být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="1ae7b-128">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a klient je ověřuje pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="1ae7b-129">Ověřování klienta je řízeno pomocí `ClientCredentials` atributu.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="1ae7b-130">transportního >. [ \<](transport-of-wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="1ae7b-130">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="1ae7b-131">Message</span><span class="sxs-lookup"><span data-stu-id="1ae7b-131">Message</span></span>|<span data-ttu-id="1ae7b-132">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="1ae7b-133">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="1ae7b-134">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy prostřednictvím vlastnosti Security. Message.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="1ae7b-135">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="1ae7b-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="1ae7b-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="1ae7b-137">V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="1ae7b-138">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ae7b-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ae7b-139">Child Elements</span></span>  
  
|<span data-ttu-id="1ae7b-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ae7b-140">Element</span></span>|<span data-ttu-id="1ae7b-141">Popis</span><span class="sxs-lookup"><span data-stu-id="1ae7b-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ae7b-142">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="1ae7b-142">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="1ae7b-143">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-143">Defines the transport security settings.</span></span> <span data-ttu-id="1ae7b-144">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="1ae7b-145">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="1ae7b-145">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="1ae7b-146">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-146">Defines the security settings for the message.</span></span> <span data-ttu-id="1ae7b-147">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1ae7b-148">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ae7b-148">Parent Elements</span></span>  
  
|<span data-ttu-id="1ae7b-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ae7b-149">Element</span></span>|<span data-ttu-id="1ae7b-150">Popis</span><span class="sxs-lookup"><span data-stu-id="1ae7b-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ae7b-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="1ae7b-151">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="1ae7b-152">Zabezpečená vazba pro aplikace přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ae7b-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ae7b-153">Remarks</span></span>  
 <span data-ttu-id="1ae7b-154">Třída WSHttpBinding je navržena pro zajištění spolupráce se službami, které implementují specifikace WS-\*.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="1ae7b-155">Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1ae7b-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ae7b-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ae7b-156">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="1ae7b-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1ae7b-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="1ae7b-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="1ae7b-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1ae7b-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="1ae7b-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="1ae7b-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="1ae7b-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="1ae7b-161">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1ae7b-161">\<binding></span></span>](../../../misc/binding.md)
