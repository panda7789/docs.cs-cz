---
title: <security> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: f84f6c0f9988dd2d07377bf694286922db9d8364
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936806"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="4a4e2-102">\<> zabezpečení > \<BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="4a4e2-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="4a4e2-103">Definuje možnosti [ \<zabezpečení BasicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4a4e2-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="4a4e2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a4e2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a4e2-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="4a4e2-105">\<bindings></span></span>  
<span data-ttu-id="4a4e2-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4a4e2-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="4a4e2-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="4a4e2-107">\<binding></span></span>  
<span data-ttu-id="4a4e2-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4a4e2-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a4e2-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a4e2-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a4e2-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4a4e2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4a4e2-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a4e2-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="4a4e2-112">Attributes</span></span>  
  
|<span data-ttu-id="4a4e2-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="4a4e2-113">Attribute</span></span>|<span data-ttu-id="4a4e2-114">Popis</span><span class="sxs-lookup"><span data-stu-id="4a4e2-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4a4e2-115">režim</span><span class="sxs-lookup"><span data-stu-id="4a4e2-115">mode</span></span>|<span data-ttu-id="4a4e2-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-116">Optional.</span></span> <span data-ttu-id="4a4e2-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-117">Specifies the type of security that is used.</span></span> <span data-ttu-id="4a4e2-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-118">The default is `None`.</span></span> <span data-ttu-id="4a4e2-119">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-119">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="4a4e2-120">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="4a4e2-120">mode Attribute</span></span>  
  
|<span data-ttu-id="4a4e2-121">Value</span><span class="sxs-lookup"><span data-stu-id="4a4e2-121">Value</span></span>|<span data-ttu-id="4a4e2-122">Popis</span><span class="sxs-lookup"><span data-stu-id="4a4e2-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4a4e2-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="4a4e2-123">None</span></span>|<span data-ttu-id="4a4e2-124">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-124">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="4a4e2-125">Přepravu</span><span class="sxs-lookup"><span data-stu-id="4a4e2-125">Transport</span></span>|<span data-ttu-id="4a4e2-126">Zabezpečení je zajištěno pomocí přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-126">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="4a4e2-127">Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-127">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="4a4e2-128">Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-128">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="4a4e2-129">Klient se ověřuje pomocí dodaného ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-129">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="4a4e2-130">Přečtěte si [> přenosů.\<](transport-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="4a4e2-130">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="4a4e2-131">Message</span><span class="sxs-lookup"><span data-stu-id="4a4e2-131">Message</span></span>|<span data-ttu-id="4a4e2-132">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="4a4e2-133">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="4a4e2-134">Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="4a4e2-135">Tato vazba je `ClientCredentialType` `Certificate`platná pouze pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="4a4e2-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4a4e2-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="4a4e2-137">Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="4a4e2-138">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="4a4e2-139">Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="4a4e2-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="4a4e2-140">TransportCredentialOnly</span></span>|<span data-ttu-id="4a4e2-141">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="4a4e2-142">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-142">It provides http-based client authentication.</span></span> <span data-ttu-id="4a4e2-143">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-143">This mode should be used with caution.</span></span> <span data-ttu-id="4a4e2-144">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a4e2-145">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4a4e2-145">Child Elements</span></span>  
  
|<span data-ttu-id="4a4e2-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a4e2-146">Element</span></span>|<span data-ttu-id="4a4e2-147">Popis</span><span class="sxs-lookup"><span data-stu-id="4a4e2-147">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a4e2-148">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="4a4e2-148">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="4a4e2-149">Definuje nastavení zabezpečení přenosu pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="4a4e2-150">Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="4a4e2-151">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="4a4e2-151">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="4a4e2-152">Definuje nastavení zabezpečení zpráv pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="4a4e2-153">Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4a4e2-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4a4e2-154">Parent Elements</span></span>  
  
|<span data-ttu-id="4a4e2-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="4a4e2-155">Element</span></span>|<span data-ttu-id="4a4e2-156">Popis</span><span class="sxs-lookup"><span data-stu-id="4a4e2-156">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4a4e2-157">vazba</span><span class="sxs-lookup"><span data-stu-id="4a4e2-157">binding</span></span>|<span data-ttu-id="4a4e2-158">[ Prvek\<vazby > BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="4a4e2-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a4e2-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4a4e2-159">Remarks</span></span>  
 <span data-ttu-id="4a4e2-160">Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="4a4e2-161">Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `basicHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="4a4e2-161">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a4e2-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a4e2-162">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="4a4e2-163">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4a4e2-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4a4e2-164">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="4a4e2-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="4a4e2-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="4a4e2-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4a4e2-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4a4e2-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4a4e2-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="4a4e2-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="4a4e2-168">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="4a4e2-168">\<binding></span></span>](../../../misc/binding.md)
