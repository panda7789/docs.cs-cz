---
title: <security> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: dc41f6f7-cabc-4a64-9fa0-ceabf861b348
ms.openlocfilehash: 97c52fa4f062ed0c65d5b1a8ca47a1439ab04cf5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736489"
---
# <a name="security-of-nethttpbinding"></a><span data-ttu-id="3c44d-102">\<security> z \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="3c44d-102">\<security> of \<netHttpBinding></span></span>

<span data-ttu-id="3c44d-103">Definuje možnosti zabezpečení [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3c44d-103">Defines the security capabilities of the [\<netHttpBinding>](nethttpbinding.md).</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  

## <a name="syntax"></a><span data-ttu-id="3c44d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3c44d-104">Syntax</span></span>

```xml
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c44d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3c44d-105">Attributes and elements</span></span>

<span data-ttu-id="3c44d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3c44d-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c44d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3c44d-107">Attributes</span></span>

|<span data-ttu-id="3c44d-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3c44d-108">Attribute</span></span>|<span data-ttu-id="3c44d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3c44d-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="3c44d-110">režim</span><span class="sxs-lookup"><span data-stu-id="3c44d-110">mode</span></span>|<span data-ttu-id="3c44d-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3c44d-111">Optional.</span></span> <span data-ttu-id="3c44d-112">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="3c44d-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="3c44d-113">Výchozí formát je `None`.</span><span class="sxs-lookup"><span data-stu-id="3c44d-113">The default is `None`.</span></span> <span data-ttu-id="3c44d-114">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="3c44d-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|

## <a name="mode-attribute"></a><span data-ttu-id="3c44d-115">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="3c44d-115">mode attribute</span></span>

|<span data-ttu-id="3c44d-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3c44d-116">Value</span></span>|<span data-ttu-id="3c44d-117">Description</span><span class="sxs-lookup"><span data-stu-id="3c44d-117">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="3c44d-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="3c44d-118">None</span></span>|<span data-ttu-id="3c44d-119">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="3c44d-119">-   Messages are not secured during transfer.</span></span>|
|<span data-ttu-id="3c44d-120">Přenos</span><span class="sxs-lookup"><span data-stu-id="3c44d-120">Transport</span></span>|<span data-ttu-id="3c44d-121">Zabezpečení je zajištěno pomocí přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c44d-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="3c44d-122">Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3c44d-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="3c44d-123">Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="3c44d-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="3c44d-124">Klient se ověřuje pomocí dodaného ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="3c44d-124">The client is authenticated using the ClientCredentialType supplied.</span></span>|
|<span data-ttu-id="3c44d-125">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3c44d-125">Message</span></span>|<span data-ttu-id="3c44d-126">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="3c44d-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3c44d-127">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="3c44d-127">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="3c44d-128">Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="3c44d-128">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="3c44d-129">`ClientCredentialType`Tato vazba je platná pouze pro tuto vazbu `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="3c44d-129">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|
|<span data-ttu-id="3c44d-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3c44d-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="3c44d-131">Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="3c44d-131">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="3c44d-132">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="3c44d-132">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="3c44d-133">Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="3c44d-133">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|
|<span data-ttu-id="3c44d-134">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="3c44d-134">TransportCredentialOnly</span></span>|<span data-ttu-id="3c44d-135">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="3c44d-135">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="3c44d-136">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3c44d-136">It provides http-based client authentication.</span></span> <span data-ttu-id="3c44d-137">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="3c44d-137">This mode should be used with caution.</span></span> <span data-ttu-id="3c44d-138">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="3c44d-138">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="3c44d-139">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="3c44d-139">Child elements</span></span>

|<span data-ttu-id="3c44d-140">Prvek</span><span class="sxs-lookup"><span data-stu-id="3c44d-140">Element</span></span>|<span data-ttu-id="3c44d-141">Description</span><span class="sxs-lookup"><span data-stu-id="3c44d-141">Description</span></span>|
|-------------|-----------------|
|[\<transport>](transport-of-nethttpbinding.md)|<span data-ttu-id="3c44d-142">Definuje nastavení zabezpečení přenosu pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3c44d-142">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="3c44d-143">Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="3c44d-143">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|
|[\<message>](message-of-nethttpbinding.md)|<span data-ttu-id="3c44d-144">Definuje nastavení zabezpečení zpráv pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3c44d-144">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="3c44d-145">Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="3c44d-145">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c44d-146">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="3c44d-146">Parent elements</span></span>

|<span data-ttu-id="3c44d-147">Prvek</span><span class="sxs-lookup"><span data-stu-id="3c44d-147">Element</span></span>|<span data-ttu-id="3c44d-148">Description</span><span class="sxs-lookup"><span data-stu-id="3c44d-148">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="3c44d-149">vazba</span><span class="sxs-lookup"><span data-stu-id="3c44d-149">binding</span></span>|<span data-ttu-id="3c44d-150">Prvek vazby prvku [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3c44d-150">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c44d-151">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3c44d-151">Remarks</span></span>

 <span data-ttu-id="3c44d-152">Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="3c44d-152">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="3c44d-153">Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `netHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="3c44d-153">This element enables you to configure additional security settings for the `netHttpBinding` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c44d-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="3c44d-154">See also</span></span>

- <xref:System.ServiceModel.NetHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetHttpBindingElement.Security%2A>  
- [<span data-ttu-id="3c44d-155">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3c44d-155">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3c44d-156">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="3c44d-156">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="3c44d-157">Vazby</span><span class="sxs-lookup"><span data-stu-id="3c44d-157">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3c44d-158">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3c44d-158">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3c44d-159">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3c44d-159">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
