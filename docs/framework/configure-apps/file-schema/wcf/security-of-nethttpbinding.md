---
title: <security> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 890cee3271c410a921b3a88f78d0705ba8718252
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399848"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="604eb-102">\<> zabezpečení > \<NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="604eb-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="604eb-103">Definuje možnosti [ \<zabezpečení NetHttpBinding >](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="604eb-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

<span data-ttu-id="604eb-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="604eb-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="604eb-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="604eb-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="604eb-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="604eb-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="604eb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="604eb-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="604eb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="604eb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="604eb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="604eb-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="604eb-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="604eb-110">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="604eb-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="604eb-111">Attributes and elements</span></span>

<span data-ttu-id="604eb-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="604eb-112">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="604eb-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="604eb-113">Attributes</span></span>

|<span data-ttu-id="604eb-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="604eb-114">Attribute</span></span>|<span data-ttu-id="604eb-115">Popis</span><span class="sxs-lookup"><span data-stu-id="604eb-115">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="604eb-116">režim</span><span class="sxs-lookup"><span data-stu-id="604eb-116">mode</span></span>|<span data-ttu-id="604eb-117">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="604eb-117">Optional.</span></span> <span data-ttu-id="604eb-118">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="604eb-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="604eb-119">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="604eb-119">The default is `None`.</span></span> <span data-ttu-id="604eb-120">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="604eb-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="604eb-121">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="604eb-121">mode attribute</span></span>

|<span data-ttu-id="604eb-122">Value</span><span class="sxs-lookup"><span data-stu-id="604eb-122">Value</span></span>|<span data-ttu-id="604eb-123">Popis</span><span class="sxs-lookup"><span data-stu-id="604eb-123">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="604eb-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="604eb-124">None</span></span>|<span data-ttu-id="604eb-125">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="604eb-125">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="604eb-126">Přepravu</span><span class="sxs-lookup"><span data-stu-id="604eb-126">Transport</span></span>|<span data-ttu-id="604eb-127">Zabezpečení je zajištěno pomocí přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="604eb-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="604eb-128">Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="604eb-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="604eb-129">Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="604eb-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="604eb-130">Klient se ověřuje pomocí dodaného ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="604eb-130">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="604eb-131">Message</span><span class="sxs-lookup"><span data-stu-id="604eb-131">Message</span></span>|<span data-ttu-id="604eb-132">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="604eb-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="604eb-133">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="604eb-133">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="604eb-134">Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="604eb-134">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="604eb-135">Tato vazba je `ClientCredentialType` `Certificate`platná pouze pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="604eb-135">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="604eb-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="604eb-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="604eb-137">Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="604eb-137">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="604eb-138">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="604eb-138">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="604eb-139">Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="604eb-139">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="604eb-140">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="604eb-140">TransportCredentialOnly</span></span>|<span data-ttu-id="604eb-141">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="604eb-141">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="604eb-142">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="604eb-142">It provides http-based client authentication.</span></span> <span data-ttu-id="604eb-143">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="604eb-143">This mode should be used with caution.</span></span> <span data-ttu-id="604eb-144">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="604eb-144">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="604eb-145">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="604eb-145">Child elements</span></span>

|<span data-ttu-id="604eb-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="604eb-146">Element</span></span>|<span data-ttu-id="604eb-147">Popis</span><span class="sxs-lookup"><span data-stu-id="604eb-147">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="604eb-148">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="604eb-148">\<transport></span></span>](transport-of-nethttpbinding.md)|<span data-ttu-id="604eb-149">Definuje nastavení zabezpečení přenosu pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="604eb-149">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="604eb-150">Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity>.</span><span class="sxs-lookup"><span data-stu-id="604eb-150">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[<span data-ttu-id="604eb-151">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="604eb-151">\<message></span></span>](message-of-nethttpbinding.md)|<span data-ttu-id="604eb-152">Definuje nastavení zabezpečení zpráv pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="604eb-152">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="604eb-153">Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span><span class="sxs-lookup"><span data-stu-id="604eb-153">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="604eb-154">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="604eb-154">Parent elements</span></span>

|<span data-ttu-id="604eb-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="604eb-155">Element</span></span>|<span data-ttu-id="604eb-156">Popis</span><span class="sxs-lookup"><span data-stu-id="604eb-156">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="604eb-157">vazba</span><span class="sxs-lookup"><span data-stu-id="604eb-157">binding</span></span>|<span data-ttu-id="604eb-158">[ Prvek\<vazby > BasicHttpBinding](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="604eb-158">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="604eb-159">Poznámky</span><span class="sxs-lookup"><span data-stu-id="604eb-159">Remarks</span></span>

 <span data-ttu-id="604eb-160">Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="604eb-160">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="604eb-161">Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `netHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="604eb-161">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="604eb-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="604eb-162">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="604eb-163">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="604eb-163">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="604eb-164">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="604eb-164">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="604eb-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="604eb-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="604eb-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="604eb-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="604eb-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="604eb-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="604eb-168">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="604eb-168">\<binding></span></span>](../../../misc/binding.md)
