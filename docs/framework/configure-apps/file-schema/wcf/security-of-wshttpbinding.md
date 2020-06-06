---
title: <security> z <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738578"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="50d07-102">\<security> z \<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="50d07-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="50d07-103">Představuje možnosti zabezpečení [\<wsHttpBinding>](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="50d07-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="50d07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50d07-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50d07-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="50d07-105">Attributes and Elements</span></span>  
 <span data-ttu-id="50d07-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="50d07-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50d07-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="50d07-107">Attributes</span></span>  
  
|<span data-ttu-id="50d07-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="50d07-108">Attribute</span></span>|<span data-ttu-id="50d07-109">Popis</span><span class="sxs-lookup"><span data-stu-id="50d07-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50d07-110">režim</span><span class="sxs-lookup"><span data-stu-id="50d07-110">mode</span></span>|<span data-ttu-id="50d07-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="50d07-111">-   Optional.</span></span> <span data-ttu-id="50d07-112">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="50d07-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="50d07-113">Výchozí formát je `Message`.</span><span class="sxs-lookup"><span data-stu-id="50d07-113">The default is `Message`.</span></span><br /><span data-ttu-id="50d07-114">– Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="50d07-114">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="50d07-115">Mode – atribut</span><span class="sxs-lookup"><span data-stu-id="50d07-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="50d07-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="50d07-116">Value</span></span>|<span data-ttu-id="50d07-117">Description</span><span class="sxs-lookup"><span data-stu-id="50d07-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50d07-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="50d07-118">None</span></span>|<span data-ttu-id="50d07-119">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="50d07-119">Security is disabled.</span></span>|  
|<span data-ttu-id="50d07-120">Přenos</span><span class="sxs-lookup"><span data-stu-id="50d07-120">Transport</span></span>|<span data-ttu-id="50d07-121">Zabezpečení je k dispozici pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="50d07-121">Security is provided using HTTPS.</span></span> <span data-ttu-id="50d07-122">Služba musí být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="50d07-122">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="50d07-123">Zpráva je zcela zabezpečená pomocí protokolu HTTPS a klient je ověřuje pomocí certifikátu protokolu SSL služby.</span><span class="sxs-lookup"><span data-stu-id="50d07-123">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="50d07-124">Ověřování klienta je řízeno pomocí `ClientCredentials` atributu.</span><span class="sxs-lookup"><span data-stu-id="50d07-124">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="50d07-125">z [\<transport>](transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="50d07-125">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="50d07-126">Zpráva</span><span class="sxs-lookup"><span data-stu-id="50d07-126">Message</span></span>|<span data-ttu-id="50d07-127">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="50d07-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="50d07-128">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="50d07-128">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="50d07-129">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici v klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy prostřednictvím vlastnosti Security. Message.</span><span class="sxs-lookup"><span data-stu-id="50d07-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="50d07-130">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="50d07-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="50d07-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="50d07-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="50d07-132">V tomto režimu poskytuje protokol HTTPS ověření identity, důvěrnosti a ověřování serveru a zabezpečení zpráv SOAP zajišťuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="50d07-132">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="50d07-133">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="50d07-133">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50d07-134">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="50d07-134">Child Elements</span></span>  
  
|<span data-ttu-id="50d07-135">Prvek</span><span class="sxs-lookup"><span data-stu-id="50d07-135">Element</span></span>|<span data-ttu-id="50d07-136">Description</span><span class="sxs-lookup"><span data-stu-id="50d07-136">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-wshttpbinding.md)|<span data-ttu-id="50d07-137">Definuje nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="50d07-137">Defines the transport security settings.</span></span> <span data-ttu-id="50d07-138">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> typu.</span><span class="sxs-lookup"><span data-stu-id="50d07-138">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[\<message>](message-of-wshttpbinding.md)|<span data-ttu-id="50d07-139">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="50d07-139">Defines the security settings for the message.</span></span> <span data-ttu-id="50d07-140">Tento prvek odpovídá <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> typu.</span><span class="sxs-lookup"><span data-stu-id="50d07-140">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="50d07-141">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="50d07-141">Parent Elements</span></span>  
  
|<span data-ttu-id="50d07-142">Prvek</span><span class="sxs-lookup"><span data-stu-id="50d07-142">Element</span></span>|<span data-ttu-id="50d07-143">Description</span><span class="sxs-lookup"><span data-stu-id="50d07-143">Description</span></span>|  
|-------------|-----------------|  
|[\<wsHttpBinding>](wshttpbinding.md)|<span data-ttu-id="50d07-144">Zabezpečená vazba pro aplikace přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="50d07-144">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50d07-145">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50d07-145">Remarks</span></span>  
 <span data-ttu-id="50d07-146">Třída WSHttpBinding je navržena pro zajištění spolupráce se službami, které implementují specifikace WS-\*.</span><span class="sxs-lookup"><span data-stu-id="50d07-146">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="50d07-147">Zabezpečení přenosu této vazby je SSL (Secure Sockets Layer) (SSL) prostřednictvím protokolu HTTP nebo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="50d07-147">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d07-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="50d07-148">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="50d07-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="50d07-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="50d07-150">Vazby</span><span class="sxs-lookup"><span data-stu-id="50d07-150">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="50d07-151">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="50d07-151">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="50d07-152">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="50d07-152">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
