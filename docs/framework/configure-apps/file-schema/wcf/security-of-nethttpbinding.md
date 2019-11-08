---
title: <security> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736489"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="3b828-102">> \<zabezpečení \<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="3b828-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="3b828-103">Definuje možnosti zabezpečení [\<netHttpBinding >](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3b828-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="3b828-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3b828-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3b828-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="3b828-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="3b828-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="3b828-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="3b828-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="3b828-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="3b828-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="3b828-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="3b828-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="3b828-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="3b828-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b828-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3b828-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b828-111">Attributes and elements</span></span>

<span data-ttu-id="3b828-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b828-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3b828-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b828-113">Attributes</span></span>

|<span data-ttu-id="3b828-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3b828-114">Attribute</span></span>|<span data-ttu-id="3b828-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3b828-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3b828-116">režim</span><span class="sxs-lookup"><span data-stu-id="3b828-116">mode</span></span>|<span data-ttu-id="3b828-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="3b828-117">Optional.</span></span> <span data-ttu-id="3b828-118">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="3b828-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="3b828-119">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="3b828-119">The default is `None`.</span></span> <span data-ttu-id="3b828-120">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="3b828-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="3b828-121">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="3b828-121">mode attribute</span></span>

|<span data-ttu-id="3b828-122">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3b828-122">Value</span></span>|<span data-ttu-id="3b828-123">Popis</span><span class="sxs-lookup"><span data-stu-id="3b828-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="3b828-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="3b828-124">None</span></span>|<span data-ttu-id="3b828-125">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="3b828-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="3b828-126">Přepravu</span><span class="sxs-lookup"><span data-stu-id="3b828-126">Transport</span></span>|<span data-ttu-id="3b828-127">Zabezpečení je zajištěno pomocí přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3b828-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="3b828-128">Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3b828-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="3b828-129">Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="3b828-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="3b828-130">Klient se ověřuje pomocí dodaného ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="3b828-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="3b828-131">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3b828-131">Message</span></span>|<span data-ttu-id="3b828-132">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="3b828-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3b828-133">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="3b828-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="3b828-134">Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="3b828-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="3b828-135">Jediná platná `ClientCredentialType` pro tuto vazbu je `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="3b828-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="3b828-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3b828-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="3b828-137">Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="3b828-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="3b828-138">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="3b828-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="3b828-139">Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="3b828-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="3b828-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="3b828-140">TransportCredentialOnly</span></span>|<span data-ttu-id="3b828-141">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="3b828-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="3b828-142">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b828-142">It provides http-based client authentication.</span></span> <span data-ttu-id="3b828-143">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="3b828-143">This mode should be used with caution.</span></span> <span data-ttu-id="3b828-144">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="3b828-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3b828-145">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="3b828-145">Child elements</span></span>

|<span data-ttu-id="3b828-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b828-146">Element</span></span>|<span data-ttu-id="3b828-147">Popis</span><span class="sxs-lookup"><span data-stu-id="3b828-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3b828-148">> přenos \<</span><span class="sxs-lookup"><span data-stu-id="3b828-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="3b828-149">Definuje nastavení zabezpečení přenosu pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b828-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="3b828-150">Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="3b828-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="3b828-151">> \<zprávy</span><span class="sxs-lookup"><span data-stu-id="3b828-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="3b828-152">Definuje nastavení zabezpečení zpráv pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3b828-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="3b828-153">Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="3b828-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3b828-154">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="3b828-154">Parent elements</span></span>

|<span data-ttu-id="3b828-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b828-155">Element</span></span>|<span data-ttu-id="3b828-156">Popis</span><span class="sxs-lookup"><span data-stu-id="3b828-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="3b828-157">vazba</span><span class="sxs-lookup"><span data-stu-id="3b828-157">binding</span></span>|<span data-ttu-id="3b828-158">Prvek vazby [\<basicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="3b828-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="3b828-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b828-159">Remarks</span></span>

 <span data-ttu-id="3b828-160">Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="3b828-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="3b828-161">Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `netHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="3b828-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b828-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b828-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="3b828-163">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3b828-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3b828-164">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="3b828-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="3b828-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="3b828-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3b828-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3b828-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3b828-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3b828-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="3b828-168">vazba \<</span><span class="sxs-lookup"><span data-stu-id="3b828-168">\<binding></span></span>](bindings.md)
