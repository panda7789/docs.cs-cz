---
title: '&lt;security&gt; – &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
author: BrucePerlerMS
ms.openlocfilehash: cee14a1ed8aa9f11aa77006ee2ed4e205ceedbe3
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086365"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="3aa20-102">&lt;security&gt; – &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3aa20-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="3aa20-103">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3aa20-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="3aa20-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3aa20-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3aa20-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3aa20-105">\<bindings></span></span>  
<span data-ttu-id="3aa20-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3aa20-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="3aa20-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3aa20-107">\<binding></span></span>  
<span data-ttu-id="3aa20-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3aa20-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa20-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aa20-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3aa20-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3aa20-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3aa20-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3aa20-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3aa20-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3aa20-112">Attributes</span></span>  
  
|<span data-ttu-id="3aa20-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3aa20-113">Attribute</span></span>|<span data-ttu-id="3aa20-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3aa20-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3aa20-115">režim</span><span class="sxs-lookup"><span data-stu-id="3aa20-115">mode</span></span>|<span data-ttu-id="3aa20-116">– Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3aa20-116">-   Optional.</span></span> <span data-ttu-id="3aa20-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="3aa20-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="3aa20-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="3aa20-118">The default is `Message`.</span></span><br /><span data-ttu-id="3aa20-119">– Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3aa20-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3aa20-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="3aa20-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="3aa20-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3aa20-121">Value</span></span>|<span data-ttu-id="3aa20-122">Popis</span><span class="sxs-lookup"><span data-stu-id="3aa20-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3aa20-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="3aa20-123">None</span></span>|<span data-ttu-id="3aa20-124">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="3aa20-124">Security is disabled.</span></span>|  
|<span data-ttu-id="3aa20-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="3aa20-125">Transport</span></span>|<span data-ttu-id="3aa20-126">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3aa20-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="3aa20-127">Služba je potřeba nakonfigurovat s využitím certifikátů SSL.</span><span class="sxs-lookup"><span data-stu-id="3aa20-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="3aa20-128">Zprávu je zcela zabezpečené pomocí protokolu HTTPS a je ověřený pomocí klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="3aa20-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="3aa20-129">Ověření klienta je řízen pomocí `ClientCredentials` atribut.</span><span class="sxs-lookup"><span data-stu-id="3aa20-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="3aa20-130">nástroje [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3aa20-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="3aa20-131">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3aa20-131">Message</span></span>|<span data-ttu-id="3aa20-132">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3aa20-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3aa20-133">Ve výchozím nastavení těle SOAP je šifrovaný a podpisu.</span><span class="sxs-lookup"><span data-stu-id="3aa20-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="3aa20-134">Tento režim nabízí širokou škálu funkcí, jako je například, jestli přihlašovací údaje služby najdete na adrese klienta vzdáleně, sada algoritmů, které chcete použít a jaké úroveň ochrany a platí pro tělo zprávy prostřednictvím vlastnosti Security.Message.</span><span class="sxs-lookup"><span data-stu-id="3aa20-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="3aa20-135">Ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="3aa20-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="3aa20-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3aa20-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="3aa20-137">V tomto režimu HTTPS poskytuje integritu, šifrování a ověřování serveru a zabezpečení zpráv SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="3aa20-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="3aa20-138">Ve výchozím nastavení ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="3aa20-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3aa20-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3aa20-139">Child Elements</span></span>  
  
|<span data-ttu-id="3aa20-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="3aa20-140">Element</span></span>|<span data-ttu-id="3aa20-141">Popis</span><span class="sxs-lookup"><span data-stu-id="3aa20-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aa20-142">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="3aa20-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="3aa20-143">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="3aa20-143">Defines the transport security settings.</span></span> <span data-ttu-id="3aa20-144">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="3aa20-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="3aa20-145">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="3aa20-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="3aa20-146">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="3aa20-146">Defines the security settings for the message.</span></span> <span data-ttu-id="3aa20-147">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="3aa20-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3aa20-148">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3aa20-148">Parent Elements</span></span>  
  
|<span data-ttu-id="3aa20-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="3aa20-149">Element</span></span>|<span data-ttu-id="3aa20-150">Popis</span><span class="sxs-lookup"><span data-stu-id="3aa20-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3aa20-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3aa20-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="3aa20-152">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="3aa20-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3aa20-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3aa20-153">Remarks</span></span>  
 <span data-ttu-id="3aa20-154">Třída WSHttpBinding je navržena pro spolupráci se službami, které implementují WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="3aa20-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="3aa20-155">Zabezpečení přenosu pro tuto vazbu je vrstva SSL (Secure Sockets) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3aa20-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa20-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="3aa20-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="3aa20-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3aa20-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3aa20-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="3aa20-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3aa20-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3aa20-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3aa20-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3aa20-160">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="3aa20-161">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3aa20-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
