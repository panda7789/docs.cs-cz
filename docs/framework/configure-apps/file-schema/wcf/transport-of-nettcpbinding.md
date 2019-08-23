---
title: <transport> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 265b68e058919d1d5c5f1dbcfb1419b57be9aeab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915553"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="06bec-102">\<> přenosu > \<NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="06bec-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="06bec-103">Definuje typ požadavků zabezpečení na úrovni zprávy pro koncový bod nakonfigurovaný s [ \<> NetTcpBinding](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="06bec-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="06bec-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="06bec-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="06bec-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="06bec-105">\<bindings></span></span>  
<span data-ttu-id="06bec-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="06bec-106">\<netTcpBinding></span></span>  
<span data-ttu-id="06bec-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="06bec-107">\<binding></span></span>  
<span data-ttu-id="06bec-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="06bec-108">\<security></span></span>  
<span data-ttu-id="06bec-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="06bec-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06bec-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06bec-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06bec-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="06bec-111">Attributes and Elements</span></span>  
 <span data-ttu-id="06bec-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="06bec-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06bec-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="06bec-113">Attributes</span></span>  
  
|<span data-ttu-id="06bec-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="06bec-114">Attribute</span></span>|<span data-ttu-id="06bec-115">Popis</span><span class="sxs-lookup"><span data-stu-id="06bec-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06bec-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="06bec-116">clientCredentialType</span></span>|<span data-ttu-id="06bec-117">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="06bec-117">Optional.</span></span> <span data-ttu-id="06bec-118">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="06bec-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="06bec-119">– Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="06bec-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="06bec-120">– Tento atribut je typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="06bec-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="06bec-121">Platné</span><span class="sxs-lookup"><span data-stu-id="06bec-121">protectionLevel</span></span>|<span data-ttu-id="06bec-122">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="06bec-122">Optional.</span></span> <span data-ttu-id="06bec-123">Definuje zabezpečení na úrovni přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="06bec-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="06bec-124">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="06bec-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="06bec-125">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="06bec-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="06bec-126">Výchozí hodnota je `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="06bec-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="06bec-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="06bec-127">sslProtocols</span></span>|<span data-ttu-id="06bec-128">Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="06bec-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="06bec-129">Výchozí hodnota je TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="06bec-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="06bec-130">Nastavením PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="06bec-130">policyEnforcement</span></span>|<span data-ttu-id="06bec-131">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="06bec-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="06bec-132">1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="06bec-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="06bec-133">2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="06bec-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="06bec-134">3.  Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="06bec-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="06bec-135">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="06bec-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="06bec-136">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="06bec-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="06bec-137">Value</span><span class="sxs-lookup"><span data-stu-id="06bec-137">Value</span></span>|<span data-ttu-id="06bec-138">Popis</span><span class="sxs-lookup"><span data-stu-id="06bec-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06bec-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="06bec-139">None</span></span>|<span data-ttu-id="06bec-140">Klient je anonymní.</span><span class="sxs-lookup"><span data-stu-id="06bec-140">The client is anonymous.</span></span> <span data-ttu-id="06bec-141">K tomu je potřeba certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="06bec-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="06bec-142">Windows</span><span class="sxs-lookup"><span data-stu-id="06bec-142">Windows</span></span>|<span data-ttu-id="06bec-143">Určuje ověřování systému Windows klienta pomocí vyjednávání SP (vyjednávání protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="06bec-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="06bec-144">Certifikát</span><span class="sxs-lookup"><span data-stu-id="06bec-144">Certificate</span></span>|<span data-ttu-id="06bec-145">Klient se ověřuje pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="06bec-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="06bec-146">Používá se vyjednávání SSL a vyžaduje certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="06bec-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="06bec-147">protectionLevel – atribut</span><span class="sxs-lookup"><span data-stu-id="06bec-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="06bec-148">Value</span><span class="sxs-lookup"><span data-stu-id="06bec-148">Value</span></span>|<span data-ttu-id="06bec-149">Popis</span><span class="sxs-lookup"><span data-stu-id="06bec-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="06bec-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="06bec-150">None</span></span>|<span data-ttu-id="06bec-151">Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="06bec-151">No protection.</span></span>|  
|<span data-ttu-id="06bec-152">Osobě</span><span class="sxs-lookup"><span data-stu-id="06bec-152">Sign</span></span>|<span data-ttu-id="06bec-153">Zprávy jsou podepsány.</span><span class="sxs-lookup"><span data-stu-id="06bec-153">Messages are signed.</span></span>|  
|<span data-ttu-id="06bec-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="06bec-154">EncryptAndSign</span></span>|<span data-ttu-id="06bec-155">– Zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="06bec-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06bec-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="06bec-156">Child Elements</span></span>  
 <span data-ttu-id="06bec-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="06bec-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06bec-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="06bec-158">Parent Elements</span></span>  
  
|<span data-ttu-id="06bec-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="06bec-159">Element</span></span>|<span data-ttu-id="06bec-160">Popis</span><span class="sxs-lookup"><span data-stu-id="06bec-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06bec-161">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="06bec-161">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="06bec-162">Určuje možnosti [ \<zabezpečení NetTcpBinding >](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="06bec-162">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06bec-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06bec-163">Remarks</span></span>  
 <span data-ttu-id="06bec-164">Zabezpečení přenosu použijte pro zajištění integrity a důvěrnosti zprávy SOAP a pro vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="06bec-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="06bec-165">Pokud je ve vazbě vybraný tento režim zabezpečení, zásobník kanálů se nakonfiguruje pomocí zabezpečeného přenosu a zprávy protokolu SOAP se zabezpečují pomocí zabezpečení přenosu, jako je Windows (Negotiate) nebo SSL přes TCP.</span><span class="sxs-lookup"><span data-stu-id="06bec-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06bec-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="06bec-166">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="06bec-167">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="06bec-167">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="06bec-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="06bec-168">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="06bec-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="06bec-169">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="06bec-170">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="06bec-170">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="06bec-171">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="06bec-171">\<binding></span></span>](../../../misc/binding.md)
