---
title: <security> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738715"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="6fc7a-102">> \<zabezpečení \<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="6fc7a-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="6fc7a-103">Definuje možnosti zabezpečení [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6fc7a-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="6fc7a-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6fc7a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6fc7a-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6fc7a-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6fc7a-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6fc7a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6fc7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6fc7a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="6fc7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="6fc7a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6fc7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="6fc7a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fc7a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fc7a-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fc7a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6fc7a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6fc7a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fc7a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6fc7a-113">Attributes</span></span>  
  
|<span data-ttu-id="6fc7a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="6fc7a-114">Attribute</span></span>|<span data-ttu-id="6fc7a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6fc7a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6fc7a-116">režim</span><span class="sxs-lookup"><span data-stu-id="6fc7a-116">mode</span></span>|<span data-ttu-id="6fc7a-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-117">Optional.</span></span> <span data-ttu-id="6fc7a-118">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="6fc7a-119">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-119">The default is `None`.</span></span> <span data-ttu-id="6fc7a-120">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6fc7a-121">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="6fc7a-121">mode Attribute</span></span>  
  
|<span data-ttu-id="6fc7a-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6fc7a-122">Value</span></span>|<span data-ttu-id="6fc7a-123">Popis</span><span class="sxs-lookup"><span data-stu-id="6fc7a-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6fc7a-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="6fc7a-124">None</span></span>|<span data-ttu-id="6fc7a-125">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="6fc7a-126">Přepravu</span><span class="sxs-lookup"><span data-stu-id="6fc7a-126">Transport</span></span>|<span data-ttu-id="6fc7a-127">Zabezpečení je zajištěno pomocí přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="6fc7a-128">Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="6fc7a-129">Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="6fc7a-130">Klient se ověřuje pomocí dodaného ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="6fc7a-131">Přečtěte si [\<přenosů](transport-of-basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6fc7a-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="6fc7a-132">Zpráva</span><span class="sxs-lookup"><span data-stu-id="6fc7a-132">Message</span></span>|<span data-ttu-id="6fc7a-133">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6fc7a-134">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6fc7a-135">Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="6fc7a-136">Jediná platná `ClientCredentialType` pro tuto vazbu je `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="6fc7a-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6fc7a-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="6fc7a-138">Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="6fc7a-139">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="6fc7a-140">Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="6fc7a-141">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="6fc7a-141">TransportCredentialOnly</span></span>|<span data-ttu-id="6fc7a-142">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="6fc7a-143">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-143">It provides http-based client authentication.</span></span> <span data-ttu-id="6fc7a-144">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-144">This mode should be used with caution.</span></span> <span data-ttu-id="6fc7a-145">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6fc7a-146">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6fc7a-146">Child Elements</span></span>  
  
|<span data-ttu-id="6fc7a-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="6fc7a-147">Element</span></span>|<span data-ttu-id="6fc7a-148">Popis</span><span class="sxs-lookup"><span data-stu-id="6fc7a-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fc7a-149">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="6fc7a-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="6fc7a-150">Definuje nastavení zabezpečení přenosu pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="6fc7a-151">Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="6fc7a-152">> \<zprávy</span><span class="sxs-lookup"><span data-stu-id="6fc7a-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="6fc7a-153">Definuje nastavení zabezpečení zpráv pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="6fc7a-154">Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6fc7a-155">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6fc7a-155">Parent Elements</span></span>  
  
|<span data-ttu-id="6fc7a-156">Prvek</span><span class="sxs-lookup"><span data-stu-id="6fc7a-156">Element</span></span>|<span data-ttu-id="6fc7a-157">Popis</span><span class="sxs-lookup"><span data-stu-id="6fc7a-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6fc7a-158">vazba</span><span class="sxs-lookup"><span data-stu-id="6fc7a-158">binding</span></span>|<span data-ttu-id="6fc7a-159">Prvek vazby [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="6fc7a-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fc7a-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6fc7a-160">Remarks</span></span>  
 <span data-ttu-id="6fc7a-161">Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="6fc7a-162">Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `basicHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="6fc7a-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fc7a-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6fc7a-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="6fc7a-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6fc7a-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6fc7a-165">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="6fc7a-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="6fc7a-166">Vazby</span><span class="sxs-lookup"><span data-stu-id="6fc7a-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6fc7a-167">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="6fc7a-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6fc7a-168">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6fc7a-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6fc7a-169">vazba \<</span><span class="sxs-lookup"><span data-stu-id="6fc7a-169">\<binding></span></span>](bindings.md)
