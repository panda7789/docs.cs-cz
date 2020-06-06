---
title: <security> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: aa01e906ddd2f15007c72bfc2a45122cfb15ba2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736368"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="3ee39-102">\<security> z \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="3ee39-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="3ee39-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="3ee39-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="3ee39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ee39-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ee39-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ee39-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3ee39-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ee39-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ee39-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ee39-107">Attributes</span></span>  
  
|<span data-ttu-id="3ee39-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ee39-108">Attribute</span></span>|<span data-ttu-id="3ee39-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3ee39-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ee39-110">režim</span><span class="sxs-lookup"><span data-stu-id="3ee39-110">mode</span></span>|<span data-ttu-id="3ee39-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="3ee39-111">Optional.</span></span> <span data-ttu-id="3ee39-112">Určuje typ zabezpečení, který se použije.</span><span class="sxs-lookup"><span data-stu-id="3ee39-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="3ee39-113">Platné hodnoty jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="3ee39-113">Valid values are shown below.</span></span> <span data-ttu-id="3ee39-114">Výchozí hodnota je `Transport`.</span><span class="sxs-lookup"><span data-stu-id="3ee39-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="3ee39-115">Tento atribut je typu <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="3ee39-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3ee39-116">mode – atribut</span><span class="sxs-lookup"><span data-stu-id="3ee39-116">mode Attribute</span></span>  
  
|<span data-ttu-id="3ee39-117">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3ee39-117">Value</span></span>|<span data-ttu-id="3ee39-118">Description</span><span class="sxs-lookup"><span data-stu-id="3ee39-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ee39-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ee39-119">None</span></span>|<span data-ttu-id="3ee39-120">Zabezpečení je zakázané.</span><span class="sxs-lookup"><span data-stu-id="3ee39-120">Security is disabled.</span></span>|  
|<span data-ttu-id="3ee39-121">Přenos</span><span class="sxs-lookup"><span data-stu-id="3ee39-121">Transport</span></span>|<span data-ttu-id="3ee39-122">Zabezpečení přenosu se zajišťuje pomocí protokolu TLS přes TCP nebo SPNego.</span><span class="sxs-lookup"><span data-stu-id="3ee39-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="3ee39-123">Je možné, že služba bude muset být nakonfigurovaná s certifikáty SSL.</span><span class="sxs-lookup"><span data-stu-id="3ee39-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="3ee39-124">Úroveň ochrany je možné řídit pomocí tohoto režimu.</span><span class="sxs-lookup"><span data-stu-id="3ee39-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="3ee39-125">Zpráva</span><span class="sxs-lookup"><span data-stu-id="3ee39-125">Message</span></span>|<span data-ttu-id="3ee39-126">Zabezpečení je k dispozici pomocí protokolu SOAP Message Security.</span><span class="sxs-lookup"><span data-stu-id="3ee39-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3ee39-127">Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="3ee39-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="3ee39-128">Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici na klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy.</span><span class="sxs-lookup"><span data-stu-id="3ee39-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="3ee39-129">Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="3ee39-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="3ee39-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3ee39-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="3ee39-131">Zabezpečení přenosu se zapojí se zabezpečením zpráv.</span><span class="sxs-lookup"><span data-stu-id="3ee39-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="3ee39-132">Zabezpečení přenosu je zajišťováno protokolem TLS přes TCP nebo SPNego a zajišťuje integritu, důvěrnost a ověřování serveru.</span><span class="sxs-lookup"><span data-stu-id="3ee39-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="3ee39-133">Zabezpečení zpráv SOAP poskytuje ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="3ee39-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="3ee39-134">Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.</span><span class="sxs-lookup"><span data-stu-id="3ee39-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ee39-135">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ee39-135">Child Elements</span></span>  
  
|<span data-ttu-id="3ee39-136">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ee39-136">Element</span></span>|<span data-ttu-id="3ee39-137">Description</span><span class="sxs-lookup"><span data-stu-id="3ee39-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="3ee39-138">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="3ee39-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="3ee39-139">Tento prvek je typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="3ee39-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="3ee39-140">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="3ee39-140">Defines the security settings for the message.</span></span> <span data-ttu-id="3ee39-141">Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> .</span><span class="sxs-lookup"><span data-stu-id="3ee39-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3ee39-142">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ee39-142">Parent Elements</span></span>  
  
|<span data-ttu-id="3ee39-143">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ee39-143">Element</span></span>|<span data-ttu-id="3ee39-144">Description</span><span class="sxs-lookup"><span data-stu-id="3ee39-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3ee39-145">vazba</span><span class="sxs-lookup"><span data-stu-id="3ee39-145">binding</span></span>|<span data-ttu-id="3ee39-146">Prvek vazby prvku [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3ee39-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ee39-147">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ee39-147">Remarks</span></span>  
 <span data-ttu-id="3ee39-148">Každá ze standardních vazeb poskytuje parametry pro řízení požadavků na zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="3ee39-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="3ee39-149">Mezi tyto parametry obvykle patří režim zabezpečení, který určuje, jestli se používá zabezpečení na úrovni zprávy nebo přenosu, a volba typu přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="3ee39-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="3ee39-150">V závislosti na výběru možností, které jsou k dispozici, je zásobník kanálů vytvořen s odpovídajícím zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="3ee39-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="3ee39-151">Vazby poskytnuté systémem, které poskytuje Windows Communication Foundation (WCF), jsou sady navržené tak, aby splňovaly některé z nejběžnějších požadavků na scénář.</span><span class="sxs-lookup"><span data-stu-id="3ee39-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="3ee39-152">Každá z těchto vazeb umožňuje specifikaci požadavků zabezpečení pro některé konkrétní cílené scénáře.</span><span class="sxs-lookup"><span data-stu-id="3ee39-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="3ee39-153">Tento prvek konfigurace poskytuje specifikace zabezpečení pro `netTcpBinding` .</span><span class="sxs-lookup"><span data-stu-id="3ee39-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="3ee39-154">Toto je zabezpečená, spolehlivá a optimalizovaná vazba vhodná pro komunikaci mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="3ee39-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="3ee39-155">Ve výchozím nastavení vygeneruje komunikační zásobník za běhu podporující protokol TCP pro doručování zpráv a zabezpečení systému Windows pro zabezpečení a ověřování zpráv, WS-ReliableMessaging pro zajištění spolehlivosti a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="3ee39-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee39-156">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ee39-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="3ee39-157">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3ee39-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3ee39-158">Vazby</span><span class="sxs-lookup"><span data-stu-id="3ee39-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3ee39-159">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3ee39-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3ee39-160">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3ee39-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
