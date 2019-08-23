---
title: <security> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 04e7e94f47be37dc9c4cbf404a269b9784281d7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936612"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="967fd-102">\<> zabezpečení > \<NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="967fd-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="967fd-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="967fd-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="967fd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="967fd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="967fd-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="967fd-105">\<bindings></span></span>  
<span data-ttu-id="967fd-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="967fd-106">\<netTcpBinding></span></span>  
<span data-ttu-id="967fd-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="967fd-107">\<binding></span></span>  
<span data-ttu-id="967fd-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="967fd-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="967fd-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="967fd-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="967fd-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="967fd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="967fd-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="967fd-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="967fd-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="967fd-112">Attributes</span></span>  
  
|<span data-ttu-id="967fd-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="967fd-113">Attribute</span></span>|<span data-ttu-id="967fd-114">Popis</span><span class="sxs-lookup"><span data-stu-id="967fd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="967fd-115">režim</span><span class="sxs-lookup"><span data-stu-id="967fd-115">mode</span></span>|<span data-ttu-id="967fd-116">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="967fd-116">Optional.</span></span> <span data-ttu-id="967fd-117">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="967fd-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="967fd-118">Platné hodnoty jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="967fd-118">Valid values are shown below.</span></span> <span data-ttu-id="967fd-119">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="967fd-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="967fd-120">Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="967fd-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="967fd-121">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="967fd-121">mode Attribute</span></span>  
  
|<span data-ttu-id="967fd-122">Value</span><span class="sxs-lookup"><span data-stu-id="967fd-122">Value</span></span>|<span data-ttu-id="967fd-123">Popis</span><span class="sxs-lookup"><span data-stu-id="967fd-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="967fd-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="967fd-124">None</span></span>|<span data-ttu-id="967fd-125">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="967fd-125">Security is disabled.</span></span>|  
|<span data-ttu-id="967fd-126">Přepravu</span><span class="sxs-lookup"><span data-stu-id="967fd-126">Transport</span></span>|<span data-ttu-id="967fd-127">Zabezpečení přenosu se zajišťuje pomocí protokolu TLS přes TCP nebo SPNego.</span><span class="sxs-lookup"><span data-stu-id="967fd-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="967fd-128">Je možné, že služba bude muset být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="967fd-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="967fd-129">Úroveň ochrany je možné řídit pomocí tohoto režimu.</span><span class="sxs-lookup"><span data-stu-id="967fd-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="967fd-130">Message</span><span class="sxs-lookup"><span data-stu-id="967fd-130">Message</span></span>|<span data-ttu-id="967fd-131">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="967fd-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="967fd-132">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="967fd-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="967fd-133">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici na klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="967fd-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="967fd-134">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="967fd-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="967fd-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="967fd-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="967fd-136">Zabezpečení přenosu se zapojí se zabezpečením zpráv.</span><span class="sxs-lookup"><span data-stu-id="967fd-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="967fd-137">Zabezpečení přenosu je zajišťováno protokolem TLS přes TCP nebo SPNego a zajišťuje integritu, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="967fd-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="967fd-138">Zabezpečení zpráv SOAP poskytuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="967fd-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="967fd-139">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="967fd-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="967fd-140">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="967fd-140">Child Elements</span></span>  
  
|<span data-ttu-id="967fd-141">Prvek</span><span class="sxs-lookup"><span data-stu-id="967fd-141">Element</span></span>|<span data-ttu-id="967fd-142">Popis</span><span class="sxs-lookup"><span data-stu-id="967fd-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="967fd-143">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="967fd-143">\<transport></span></span>](transport-of-nettcpbinding.md)|<span data-ttu-id="967fd-144">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="967fd-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="967fd-145">Tento prvek je typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="967fd-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="967fd-146">\<> zprávy</span><span class="sxs-lookup"><span data-stu-id="967fd-146">\<message></span></span>](message-element-of-nettcpbinding.md)|<span data-ttu-id="967fd-147">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="967fd-147">Defines the security settings for the message.</span></span> <span data-ttu-id="967fd-148">Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span><span class="sxs-lookup"><span data-stu-id="967fd-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="967fd-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="967fd-149">Parent Elements</span></span>  
  
|<span data-ttu-id="967fd-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="967fd-150">Element</span></span>|<span data-ttu-id="967fd-151">Popis</span><span class="sxs-lookup"><span data-stu-id="967fd-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="967fd-152">vazba</span><span class="sxs-lookup"><span data-stu-id="967fd-152">binding</span></span>|<span data-ttu-id="967fd-153">[ Prvek\<vazby > NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="967fd-153">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="967fd-154">Poznámky</span><span class="sxs-lookup"><span data-stu-id="967fd-154">Remarks</span></span>  
 <span data-ttu-id="967fd-155">Každá ze standardních vazeb poskytuje parametry pro řízení požadavků na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="967fd-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="967fd-156">Mezi tyto parametry obvykle patří režim zabezpečení, který určuje, jestli se používá zabezpečení na úrovni zprávy nebo přenosu, a volba typu přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="967fd-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="967fd-157">V závislosti na výběru možností, které jsou k dispozici, je zásobník kanálů vytvořen s odpovídajícím zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="967fd-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="967fd-158">Vazby poskytnuté systémem, které poskytuje Windows Communication Foundation (WCF), jsou sady navržené tak, aby splňovaly některé z nejběžnějších požadavků na scénář.</span><span class="sxs-lookup"><span data-stu-id="967fd-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="967fd-159">Každá z těchto vazeb umožňuje specifikaci požadavků zabezpečení pro některé konkrétní cílené scénáře.</span><span class="sxs-lookup"><span data-stu-id="967fd-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="967fd-160">Tento prvek konfigurace poskytuje specifikace zabezpečení pro `netTcpBinding`.</span><span class="sxs-lookup"><span data-stu-id="967fd-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="967fd-161">Toto je zabezpečená, spolehlivá a optimalizovaná vazba vhodná pro komunikaci mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="967fd-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="967fd-162">Ve výchozím nastavení vygeneruje komunikační zásobník za běhu podporující protokol TCP pro doručování zpráv a zabezpečení systému Windows pro zabezpečení a ověřování zpráv, WS-ReliableMessaging pro zajištění spolehlivosti a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="967fd-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="967fd-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="967fd-163">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="967fd-164">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="967fd-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="967fd-165">Vazby</span><span class="sxs-lookup"><span data-stu-id="967fd-165">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="967fd-166">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="967fd-166">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="967fd-167">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="967fd-167">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="967fd-168">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="967fd-168">\<binding></span></span>](../../../misc/binding.md)
