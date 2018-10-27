---
title: '&lt;security&gt; – &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: f552e12e98e1fd760a9b36f6984a41a32f96533f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192522"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="e4e62-102">&lt;security&gt; – &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e4e62-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="e4e62-103">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e4e62-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="e4e62-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e4e62-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e4e62-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="e4e62-105">\<bindings></span></span>  
<span data-ttu-id="e4e62-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e4e62-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="e4e62-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="e4e62-107">\<binding></span></span>  
<span data-ttu-id="e4e62-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="e4e62-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4e62-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4e62-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4e62-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e4e62-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e4e62-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4e62-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4e62-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4e62-112">Attributes</span></span>  
  
|<span data-ttu-id="e4e62-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4e62-113">Attribute</span></span>|<span data-ttu-id="e4e62-114">Popis</span><span class="sxs-lookup"><span data-stu-id="e4e62-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4e62-115">režim</span><span class="sxs-lookup"><span data-stu-id="e4e62-115">mode</span></span>|<span data-ttu-id="e4e62-116">– Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e4e62-116">-   Optional.</span></span> <span data-ttu-id="e4e62-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="e4e62-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="e4e62-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="e4e62-118">The default is `Message`.</span></span><br /><span data-ttu-id="e4e62-119">– Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e4e62-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="e4e62-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="e4e62-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="e4e62-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e4e62-121">Value</span></span>|<span data-ttu-id="e4e62-122">Popis</span><span class="sxs-lookup"><span data-stu-id="e4e62-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e4e62-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="e4e62-123">None</span></span>|<span data-ttu-id="e4e62-124">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="e4e62-124">Security is disabled.</span></span>|  
|<span data-ttu-id="e4e62-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="e4e62-125">Transport</span></span>|<span data-ttu-id="e4e62-126">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e4e62-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="e4e62-127">Služba je potřeba nakonfigurovat s využitím certifikátů SSL.</span><span class="sxs-lookup"><span data-stu-id="e4e62-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="e4e62-128">Zprávu je zcela zabezpečené pomocí protokolu HTTPS a je ověřený pomocí klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="e4e62-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="e4e62-129">Ověření klienta je řízen pomocí `ClientCredentials` atribut.</span><span class="sxs-lookup"><span data-stu-id="e4e62-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="e4e62-130">nástroje [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e4e62-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="e4e62-131">Zpráva</span><span class="sxs-lookup"><span data-stu-id="e4e62-131">Message</span></span>|<span data-ttu-id="e4e62-132">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e4e62-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="e4e62-133">Ve výchozím nastavení těle SOAP je šifrovaný a podpisu.</span><span class="sxs-lookup"><span data-stu-id="e4e62-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="e4e62-134">Tento režim nabízí širokou škálu funkcí, jako je například, jestli přihlašovací údaje služby najdete na adrese klienta vzdáleně, sada algoritmů, které chcete použít a jaké úroveň ochrany a platí pro tělo zprávy prostřednictvím vlastnosti Security.Message.</span><span class="sxs-lookup"><span data-stu-id="e4e62-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="e4e62-135">Ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="e4e62-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="e4e62-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e4e62-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="e4e62-137">V tomto režimu HTTPS poskytuje integritu, šifrování a ověřování serveru a zabezpečení zpráv SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="e4e62-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="e4e62-138">Ve výchozím nastavení ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="e4e62-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4e62-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e4e62-139">Child Elements</span></span>  
  
|<span data-ttu-id="e4e62-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4e62-140">Element</span></span>|<span data-ttu-id="e4e62-141">Popis</span><span class="sxs-lookup"><span data-stu-id="e4e62-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4e62-142">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="e4e62-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="e4e62-143">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="e4e62-143">Defines the transport security settings.</span></span> <span data-ttu-id="e4e62-144">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="e4e62-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="e4e62-145">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="e4e62-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="e4e62-146">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="e4e62-146">Defines the security settings for the message.</span></span> <span data-ttu-id="e4e62-147">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="e4e62-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4e62-148">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e4e62-148">Parent Elements</span></span>  
  
|<span data-ttu-id="e4e62-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4e62-149">Element</span></span>|<span data-ttu-id="e4e62-150">Popis</span><span class="sxs-lookup"><span data-stu-id="e4e62-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4e62-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="e4e62-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="e4e62-152">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4e62-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4e62-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4e62-153">Remarks</span></span>  
 <span data-ttu-id="e4e62-154">Třída WSHttpBinding je navržena pro spolupráci se službami, které implementují WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="e4e62-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="e4e62-155">Zabezpečení přenosu pro tuto vazbu je vrstva SSL (Secure Sockets) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e4e62-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e62-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4e62-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="e4e62-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e4e62-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e4e62-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="e4e62-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e4e62-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="e4e62-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e4e62-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e4e62-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="e4e62-161">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="e4e62-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
