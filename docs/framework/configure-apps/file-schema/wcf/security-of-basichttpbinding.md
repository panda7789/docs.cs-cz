---
title: <security> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738715"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="feb11-102">\<security> z \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="feb11-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="feb11-103">Definuje možnosti zabezpečení [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="feb11-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="feb11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="feb11-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="feb11-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="feb11-105">Attributes and Elements</span></span>  
 <span data-ttu-id="feb11-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="feb11-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="feb11-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="feb11-107">Attributes</span></span>  
  
|<span data-ttu-id="feb11-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="feb11-108">Attribute</span></span>|<span data-ttu-id="feb11-109">Popis</span><span class="sxs-lookup"><span data-stu-id="feb11-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="feb11-110">režim</span><span class="sxs-lookup"><span data-stu-id="feb11-110">mode</span></span>|<span data-ttu-id="feb11-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="feb11-111">Optional.</span></span> <span data-ttu-id="feb11-112">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="feb11-112">Specifies the type of security that is used.</span></span> <span data-ttu-id="feb11-113">Výchozí formát je `None`.</span><span class="sxs-lookup"><span data-stu-id="feb11-113">The default is `None`.</span></span> <span data-ttu-id="feb11-114">Tento atribut je typu <xref:System.ServiceModel.BasicHttpSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="feb11-114">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="feb11-115">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="feb11-115">mode Attribute</span></span>  
  
|<span data-ttu-id="feb11-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="feb11-116">Value</span></span>|<span data-ttu-id="feb11-117">Description</span><span class="sxs-lookup"><span data-stu-id="feb11-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="feb11-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="feb11-118">None</span></span>|<span data-ttu-id="feb11-119">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="feb11-119">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="feb11-120">Přenos</span><span class="sxs-lookup"><span data-stu-id="feb11-120">Transport</span></span>|<span data-ttu-id="feb11-121">Zabezpečení je zajištěno pomocí přenosu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="feb11-121">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="feb11-122">Zprávy SOAP jsou zabezpečeny pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="feb11-122">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="feb11-123">Služba se ověřuje pro klienta pomocí certifikátu X. 509 služby.</span><span class="sxs-lookup"><span data-stu-id="feb11-123">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="feb11-124">Klient se ověřuje pomocí dodaného ClientCredentialType.</span><span class="sxs-lookup"><span data-stu-id="feb11-124">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="feb11-125">Viz [\<transport>](transport-of-basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="feb11-125">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="feb11-126">Zpráva</span><span class="sxs-lookup"><span data-stu-id="feb11-126">Message</span></span>|<span data-ttu-id="feb11-127">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="feb11-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="feb11-128">Ve výchozím nastavení je text zašifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="feb11-128">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="feb11-129">Pro tuto vazbu systému vyžaduje, aby byl certifikát serveru poskytnutý klientovi mimo IP síť.</span><span class="sxs-lookup"><span data-stu-id="feb11-129">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="feb11-130">`ClientCredentialType`Tato vazba je platná pouze pro tuto vazbu `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="feb11-130">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="feb11-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="feb11-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="feb11-132">Zabezpečení přenosu zajišťuje integrita, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="feb11-132">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="feb11-133">Ověřování klientů je zajištěno prostřednictvím zabezpečení zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="feb11-133">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="feb11-134">Tento režim je vhodný v případě, že se uživatel ověřuje pomocí uživatelského jména a hesla a existuje stávající nasazení HTTP pro zabezpečení přenosu zpráv.</span><span class="sxs-lookup"><span data-stu-id="feb11-134">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="feb11-135">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="feb11-135">TransportCredentialOnly</span></span>|<span data-ttu-id="feb11-136">Tento režim neposkytuje integritu a důvěrnost zpráv.</span><span class="sxs-lookup"><span data-stu-id="feb11-136">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="feb11-137">Poskytuje ověřování klientů založené na protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="feb11-137">It provides http-based client authentication.</span></span> <span data-ttu-id="feb11-138">Tento režim by se měl používat opatrně.</span><span class="sxs-lookup"><span data-stu-id="feb11-138">This mode should be used with caution.</span></span> <span data-ttu-id="feb11-139">Měl by se používat v prostředích, kde je zabezpečení přenosu poskytované jiným způsobem (například IPSec) a infrastrukturou WCF poskytuje jenom ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="feb11-139">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="feb11-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="feb11-140">Child Elements</span></span>  
  
|<span data-ttu-id="feb11-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="feb11-141">Element</span></span>|<span data-ttu-id="feb11-142">Description</span><span class="sxs-lookup"><span data-stu-id="feb11-142">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-basichttpbinding.md)|<span data-ttu-id="feb11-143">Definuje nastavení zabezpečení přenosu pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="feb11-143">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="feb11-144">Tento prvek odpovídá <xref:System.ServiceModel.HttpTransportSecurity> .</span><span class="sxs-lookup"><span data-stu-id="feb11-144">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[\<message>](message-of-basichttpbinding.md)|<span data-ttu-id="feb11-145">Definuje nastavení zabezpečení zpráv pro základní službu HTTP.</span><span class="sxs-lookup"><span data-stu-id="feb11-145">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="feb11-146">Tento prvek odpovídá <xref:System.ServiceModel.BasicHttpMessageSecurity> .</span><span class="sxs-lookup"><span data-stu-id="feb11-146">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="feb11-147">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="feb11-147">Parent Elements</span></span>  
  
|<span data-ttu-id="feb11-148">Prvek</span><span class="sxs-lookup"><span data-stu-id="feb11-148">Element</span></span>|<span data-ttu-id="feb11-149">Description</span><span class="sxs-lookup"><span data-stu-id="feb11-149">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="feb11-150">vazba</span><span class="sxs-lookup"><span data-stu-id="feb11-150">binding</span></span>|<span data-ttu-id="feb11-151">Prvek vazby prvku [\<basicHttpBinding>](basichttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="feb11-151">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feb11-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="feb11-152">Remarks</span></span>  
 <span data-ttu-id="feb11-153">Ve výchozím nastavení není zpráva SOAP zabezpečená a klient není ověřen.</span><span class="sxs-lookup"><span data-stu-id="feb11-153">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="feb11-154">Tento prvek umožňuje nakonfigurovat další nastavení zabezpečení pro `basicHttpBinding` element.</span><span class="sxs-lookup"><span data-stu-id="feb11-154">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb11-155">Viz také</span><span class="sxs-lookup"><span data-stu-id="feb11-155">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="feb11-156">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="feb11-156">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="feb11-157">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="feb11-157">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="feb11-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="feb11-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="feb11-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="feb11-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="feb11-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="feb11-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
