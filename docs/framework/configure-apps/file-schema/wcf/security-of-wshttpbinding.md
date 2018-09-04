---
title: '&lt;security&gt; – &lt;wsHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: de2fc0f562b079d5310ed2cd81211e14d4257515
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509693"
---
# <a name="ltsecuritygt-of-ltwshttpbindinggt"></a><span data-ttu-id="cdf74-102">&lt;security&gt; – &lt;wsHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="cdf74-102">&lt;security&gt; of &lt;wsHttpBinding&gt;</span></span>
<span data-ttu-id="cdf74-103">Představuje možnosti zabezpečení [ \<wsHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cdf74-103">Represents the security capabilities of the [\<wsHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="cdf74-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cdf74-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cdf74-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cdf74-105">\<bindings></span></span>  
<span data-ttu-id="cdf74-106">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cdf74-106">\<wsHttpBinding></span></span>  
<span data-ttu-id="cdf74-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="cdf74-107">\<binding></span></span>  
<span data-ttu-id="cdf74-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cdf74-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdf74-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdf74-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdf74-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cdf74-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cdf74-111">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cdf74-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdf74-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cdf74-112">Attributes</span></span>  
  
|<span data-ttu-id="cdf74-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cdf74-113">Attribute</span></span>|<span data-ttu-id="cdf74-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cdf74-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdf74-115">režim</span><span class="sxs-lookup"><span data-stu-id="cdf74-115">mode</span></span>|<span data-ttu-id="cdf74-116">– Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cdf74-116">-   Optional.</span></span> <span data-ttu-id="cdf74-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="cdf74-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="cdf74-118">Výchozí hodnota je `Message`.</span><span class="sxs-lookup"><span data-stu-id="cdf74-118">The default is `Message`.</span></span><br /><span data-ttu-id="cdf74-119">– Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="cdf74-119">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="cdf74-120">režim atribut</span><span class="sxs-lookup"><span data-stu-id="cdf74-120">Mode Attribute</span></span>  
  
|<span data-ttu-id="cdf74-121">Hodnota</span><span class="sxs-lookup"><span data-stu-id="cdf74-121">Value</span></span>|<span data-ttu-id="cdf74-122">Popis</span><span class="sxs-lookup"><span data-stu-id="cdf74-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cdf74-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="cdf74-123">None</span></span>|<span data-ttu-id="cdf74-124">Zabezpečení je zakázaná.</span><span class="sxs-lookup"><span data-stu-id="cdf74-124">Security is disabled.</span></span>|  
|<span data-ttu-id="cdf74-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="cdf74-125">Transport</span></span>|<span data-ttu-id="cdf74-126">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cdf74-126">Security is provided using HTTPS.</span></span> <span data-ttu-id="cdf74-127">Služba je potřeba nakonfigurovat s využitím certifikátů SSL.</span><span class="sxs-lookup"><span data-stu-id="cdf74-127">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="cdf74-128">Zprávu je zcela zabezpečené pomocí protokolu HTTPS a je ověřený pomocí klienta pomocí certifikátu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="cdf74-128">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="cdf74-129">Ověření klienta je řízen pomocí `ClientCredentials` atribut.</span><span class="sxs-lookup"><span data-stu-id="cdf74-129">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="cdf74-130">nástroje [ \<přenosu >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="cdf74-130">of the [\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="cdf74-131">Zpráva</span><span class="sxs-lookup"><span data-stu-id="cdf74-131">Message</span></span>|<span data-ttu-id="cdf74-132">Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="cdf74-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="cdf74-133">Ve výchozím nastavení těle SOAP je šifrovaný a podpisu.</span><span class="sxs-lookup"><span data-stu-id="cdf74-133">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="cdf74-134">Tento režim nabízí širokou škálu funkcí, jako je například, jestli přihlašovací údaje služby najdete na adrese klienta vzdáleně, sada algoritmů, které chcete použít a jaké úroveň ochrany a platí pro tělo zprávy prostřednictvím vlastnosti Security.Message.</span><span class="sxs-lookup"><span data-stu-id="cdf74-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="cdf74-135">Ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="cdf74-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="cdf74-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="cdf74-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="cdf74-137">V tomto režimu HTTPS poskytuje integritu, šifrování a ověřování serveru a zabezpečení zpráv SOAP poskytuje ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="cdf74-137">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="cdf74-138">Ve výchozím nastavení ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="cdf74-138">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdf74-139">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cdf74-139">Child Elements</span></span>  
  
|<span data-ttu-id="cdf74-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="cdf74-140">Element</span></span>|<span data-ttu-id="cdf74-141">Popis</span><span class="sxs-lookup"><span data-stu-id="cdf74-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdf74-142">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="cdf74-142">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)|<span data-ttu-id="cdf74-143">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="cdf74-143">Defines the transport security settings.</span></span> <span data-ttu-id="cdf74-144">Tento element odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="cdf74-144">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="cdf74-145">\<Zpráva ></span><span class="sxs-lookup"><span data-stu-id="cdf74-145">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)|<span data-ttu-id="cdf74-146">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="cdf74-146">Defines the security settings for the message.</span></span> <span data-ttu-id="cdf74-147">Tento element odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="cdf74-147">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cdf74-148">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cdf74-148">Parent Elements</span></span>  
  
|<span data-ttu-id="cdf74-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="cdf74-149">Element</span></span>|<span data-ttu-id="cdf74-150">Popis</span><span class="sxs-lookup"><span data-stu-id="cdf74-150">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdf74-151">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="cdf74-151">\<wsHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="cdf74-152">Zabezpečené vazby pro aplikace přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="cdf74-152">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdf74-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cdf74-153">Remarks</span></span>  
 <span data-ttu-id="cdf74-154">Třída WSHttpBinding je navržena pro spolupráci se službami, které implementují WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="cdf74-154">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="cdf74-155">Zabezpečení přenosu pro tuto vazbu je vrstva SSL (Secure Sockets) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="cdf74-155">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf74-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="cdf74-156">See Also</span></span>  
 <xref:System.ServiceModel.WSHttpSecurity>  
 <xref:System.ServiceModel.WSHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>  
 [<span data-ttu-id="cdf74-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="cdf74-157">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cdf74-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="cdf74-158">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cdf74-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="cdf74-159">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cdf74-160">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="cdf74-160">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cdf74-161">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="cdf74-161">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
