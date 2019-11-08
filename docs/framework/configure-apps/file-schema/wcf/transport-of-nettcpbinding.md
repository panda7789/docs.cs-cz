---
title: <transport> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735930"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="d83d6-102">> \<přenosů \<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="d83d6-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="d83d6-103">Definuje typ požadavků zabezpečení na úrovni zprávy pro koncový bod nakonfigurovaný pomocí [\<netTcpBinding >](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d83d6-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
<span data-ttu-id="d83d6-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d83d6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d83d6-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d83d6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d83d6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d83d6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d83d6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d83d6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)</span></span>\
<span data-ttu-id="d83d6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="d83d6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d83d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d83d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)</span></span>\
<span data-ttu-id="d83d6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="d83d6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83d6-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d83d6-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d83d6-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d83d6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d83d6-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d83d6-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d83d6-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="d83d6-114">Attributes</span></span>  
  
|<span data-ttu-id="d83d6-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="d83d6-115">Attribute</span></span>|<span data-ttu-id="d83d6-116">Popis</span><span class="sxs-lookup"><span data-stu-id="d83d6-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d83d6-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="d83d6-117">clientCredentialType</span></span>|<span data-ttu-id="d83d6-118">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d83d6-118">Optional.</span></span> <span data-ttu-id="d83d6-119">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="d83d6-119">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="d83d6-120">-Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="d83d6-120">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="d83d6-121">– Tento atribut je typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d83d6-121">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="d83d6-122">Platné</span><span class="sxs-lookup"><span data-stu-id="d83d6-122">protectionLevel</span></span>|<span data-ttu-id="d83d6-123">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d83d6-123">Optional.</span></span> <span data-ttu-id="d83d6-124">Definuje zabezpečení na úrovni přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="d83d6-124">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="d83d6-125">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="d83d6-125">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="d83d6-126">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="d83d6-126">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="d83d6-127">Výchozí hodnota je `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="d83d6-127">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="d83d6-128">SslProtocols určující</span><span class="sxs-lookup"><span data-stu-id="d83d6-128">sslProtocols</span></span>|<span data-ttu-id="d83d6-129">Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="d83d6-129">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="d83d6-130">Výchozí hodnota je TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="d83d6-130">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="d83d6-131">Nastavením PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="d83d6-131">policyEnforcement</span></span>|<span data-ttu-id="d83d6-132">Tento výčet Určuje, kdy se má vyhovět <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>.</span><span class="sxs-lookup"><span data-stu-id="d83d6-132">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="d83d6-133">1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="d83d6-133">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="d83d6-134">2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="d83d6-134">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="d83d6-135">3. Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="d83d6-135">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="d83d6-136">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="d83d6-136">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="d83d6-137">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="d83d6-137">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d83d6-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d83d6-138">Value</span></span>|<span data-ttu-id="d83d6-139">Popis</span><span class="sxs-lookup"><span data-stu-id="d83d6-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d83d6-140">Žádné</span><span class="sxs-lookup"><span data-stu-id="d83d6-140">None</span></span>|<span data-ttu-id="d83d6-141">Klient je anonymní.</span><span class="sxs-lookup"><span data-stu-id="d83d6-141">The client is anonymous.</span></span> <span data-ttu-id="d83d6-142">K tomu je potřeba certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="d83d6-142">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="d83d6-143">Windows</span><span class="sxs-lookup"><span data-stu-id="d83d6-143">Windows</span></span>|<span data-ttu-id="d83d6-144">Určuje ověřování systému Windows klienta pomocí vyjednávání SP (vyjednávání protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="d83d6-144">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="d83d6-145">Certifikát</span><span class="sxs-lookup"><span data-stu-id="d83d6-145">Certificate</span></span>|<span data-ttu-id="d83d6-146">Klient se ověřuje pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d83d6-146">The client is authenticated using a certificate.</span></span> <span data-ttu-id="d83d6-147">Používá se vyjednávání SSL a vyžaduje certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="d83d6-147">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="d83d6-148">protectionLevel – atribut</span><span class="sxs-lookup"><span data-stu-id="d83d6-148">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="d83d6-149">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d83d6-149">Value</span></span>|<span data-ttu-id="d83d6-150">Popis</span><span class="sxs-lookup"><span data-stu-id="d83d6-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d83d6-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="d83d6-151">None</span></span>|<span data-ttu-id="d83d6-152">Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="d83d6-152">No protection.</span></span>|  
|<span data-ttu-id="d83d6-153">Osobě</span><span class="sxs-lookup"><span data-stu-id="d83d6-153">Sign</span></span>|<span data-ttu-id="d83d6-154">Zprávy jsou podepsány.</span><span class="sxs-lookup"><span data-stu-id="d83d6-154">Messages are signed.</span></span>|  
|<span data-ttu-id="d83d6-155">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="d83d6-155">EncryptAndSign</span></span>|<span data-ttu-id="d83d6-156">– Zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="d83d6-156">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d83d6-157">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d83d6-157">Child Elements</span></span>  
 <span data-ttu-id="d83d6-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="d83d6-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d83d6-159">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d83d6-159">Parent Elements</span></span>  
  
|<span data-ttu-id="d83d6-160">Prvek</span><span class="sxs-lookup"><span data-stu-id="d83d6-160">Element</span></span>|<span data-ttu-id="d83d6-161">Popis</span><span class="sxs-lookup"><span data-stu-id="d83d6-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d83d6-162">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="d83d6-162">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="d83d6-163">Určuje možnosti zabezpečení [\<netTcpBinding >](nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d83d6-163">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d83d6-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d83d6-164">Remarks</span></span>  
 <span data-ttu-id="d83d6-165">Zabezpečení přenosu použijte pro zajištění integrity a důvěrnosti zprávy SOAP a pro vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="d83d6-165">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="d83d6-166">Pokud je ve vazbě vybraný tento režim zabezpečení, zásobník kanálů se nakonfiguruje pomocí zabezpečeného přenosu a zprávy protokolu SOAP se zabezpečují pomocí zabezpečení přenosu, jako je Windows (Negotiate) nebo SSL přes TCP.</span><span class="sxs-lookup"><span data-stu-id="d83d6-166">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83d6-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d83d6-167">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="d83d6-168">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d83d6-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d83d6-169">Vazby</span><span class="sxs-lookup"><span data-stu-id="d83d6-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d83d6-170">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d83d6-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d83d6-171">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d83d6-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d83d6-172">vazba \<</span><span class="sxs-lookup"><span data-stu-id="d83d6-172">\<binding></span></span>](bindings.md)
