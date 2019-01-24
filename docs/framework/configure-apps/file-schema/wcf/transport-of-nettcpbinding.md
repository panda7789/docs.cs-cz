---
title: '&lt;transport&gt; – &lt;netTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 7372b94bde8325ec00116ee7022739f1b17a1ac9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555489"
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="d2c96-102">&lt;transport&gt; – &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="d2c96-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="d2c96-103">Definuje typ požadavky zabezpečení na úrovni zpráva koncovým bodem nakonfigurovaným s [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d2c96-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="d2c96-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2c96-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2c96-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="d2c96-105">\<bindings></span></span>  
<span data-ttu-id="d2c96-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="d2c96-106">\<netTcpBinding></span></span>  
<span data-ttu-id="d2c96-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d2c96-107">\<binding></span></span>  
<span data-ttu-id="d2c96-108">\<security></span><span class="sxs-lookup"><span data-stu-id="d2c96-108">\<security></span></span>  
<span data-ttu-id="d2c96-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="d2c96-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c96-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2c96-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2c96-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d2c96-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d2c96-112">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d2c96-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2c96-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d2c96-113">Attributes</span></span>  
  
|<span data-ttu-id="d2c96-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="d2c96-114">Attribute</span></span>|<span data-ttu-id="d2c96-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c96-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d2c96-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="d2c96-116">clientCredentialType</span></span>|<span data-ttu-id="d2c96-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d2c96-117">Optional.</span></span> <span data-ttu-id="d2c96-118">Určuje typ přihlašovacích údajů pro použití při ověřování klientů pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="d2c96-119">– Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="d2c96-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="d2c96-120">– Tento atribut je typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="d2c96-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="d2c96-121">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="d2c96-121">protectionLevel</span></span>|<span data-ttu-id="d2c96-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="d2c96-122">Optional.</span></span> <span data-ttu-id="d2c96-123">Definuje zabezpečení na úrovni přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="d2c96-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="d2c96-124">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="d2c96-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="d2c96-125">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="d2c96-126">Výchozí hodnota je `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="d2c96-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="d2c96-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="d2c96-127">sslProtocols</span></span>|<span data-ttu-id="d2c96-128">SslProtocols příznak hodnotu výčtu, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="d2c96-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="d2c96-129">Výchozí hodnota je Tls&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="d2c96-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="d2c96-130">Parametr policyenforcement na hodnotu</span><span class="sxs-lookup"><span data-stu-id="d2c96-130">policyEnforcement</span></span>|<span data-ttu-id="d2c96-131">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="d2c96-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="d2c96-132">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="d2c96-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="d2c96-133">2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="d2c96-134">3.  Vždy – je vždy zásady vynucují.</span><span class="sxs-lookup"><span data-stu-id="d2c96-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="d2c96-135">K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="d2c96-136">clientCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="d2c96-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d2c96-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d2c96-137">Value</span></span>|<span data-ttu-id="d2c96-138">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c96-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d2c96-139">Žádná</span><span class="sxs-lookup"><span data-stu-id="d2c96-139">None</span></span>|<span data-ttu-id="d2c96-140">Klient je anonymní.</span><span class="sxs-lookup"><span data-stu-id="d2c96-140">The client is anonymous.</span></span> <span data-ttu-id="d2c96-141">To vyžaduje certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="d2c96-142">Windows</span><span class="sxs-lookup"><span data-stu-id="d2c96-142">Windows</span></span>|<span data-ttu-id="d2c96-143">Určuje ověřování Windows z klienta pomocí vyjednávání SP (vyjednávání protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="d2c96-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="d2c96-144">Certifikát</span><span class="sxs-lookup"><span data-stu-id="d2c96-144">Certificate</span></span>|<span data-ttu-id="d2c96-145">Klient je ověřený pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="d2c96-146">Využívá vyjednávání protokolu SSL a vyžaduje certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="d2c96-147">Třída protectionLevel atribut</span><span class="sxs-lookup"><span data-stu-id="d2c96-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="d2c96-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d2c96-148">Value</span></span>|<span data-ttu-id="d2c96-149">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c96-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d2c96-150">Žádná</span><span class="sxs-lookup"><span data-stu-id="d2c96-150">None</span></span>|<span data-ttu-id="d2c96-151">Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="d2c96-151">No protection.</span></span>|  
|<span data-ttu-id="d2c96-152">přihlášení</span><span class="sxs-lookup"><span data-stu-id="d2c96-152">Sign</span></span>|<span data-ttu-id="d2c96-153">Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="d2c96-153">Messages are signed.</span></span>|  
|<span data-ttu-id="d2c96-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="d2c96-154">EncryptAndSign</span></span>|<span data-ttu-id="d2c96-155">-Zprávy jsou zašifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="d2c96-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d2c96-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d2c96-156">Child Elements</span></span>  
 <span data-ttu-id="d2c96-157">Žádná</span><span class="sxs-lookup"><span data-stu-id="d2c96-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d2c96-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d2c96-158">Parent Elements</span></span>  
  
|<span data-ttu-id="d2c96-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="d2c96-159">Element</span></span>|<span data-ttu-id="d2c96-160">Popis</span><span class="sxs-lookup"><span data-stu-id="d2c96-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2c96-161">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="d2c96-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="d2c96-162">Určuje schopnosti zabezpečení [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="d2c96-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d2c96-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d2c96-163">Remarks</span></span>  
 <span data-ttu-id="d2c96-164">Pro integritu a důvěrnost zprávu protokolu SOAP a vzájemné ověřování, použijte zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="d2c96-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="d2c96-165">Pokud u vazby je vybraný tento režim zabezpečení, zásobník kanál je nakonfigurován pomocí zabezpečeného přenosu a zprávy protokolu SOAP jsou zabezpečené pomocí zabezpečení přenosu, jako je například Windows (Negotiate) nebo SSL přes TCP.</span><span class="sxs-lookup"><span data-stu-id="d2c96-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c96-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2c96-166">See also</span></span>
- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="d2c96-167">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d2c96-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d2c96-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="d2c96-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d2c96-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="d2c96-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d2c96-170">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="d2c96-170">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d2c96-171">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="d2c96-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
