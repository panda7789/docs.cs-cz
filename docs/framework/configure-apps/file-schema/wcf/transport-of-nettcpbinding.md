---
title: "&lt;transport&gt; – &lt;netTcpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ad2271b86d37d9063ac54d9a4e45681d132eb1d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="e55e2-102">&lt;transport&gt; – &lt;netTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e55e2-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="e55e2-103">Definuje typ požadavků na zabezpečení na úrovni zpráv pro koncový bod nakonfigurované [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e55e2-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="e55e2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e55e2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e55e2-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="e55e2-105">\<bindings></span></span>  
<span data-ttu-id="e55e2-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="e55e2-106">\<netTcpBinding></span></span>  
<span data-ttu-id="e55e2-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="e55e2-107">\<binding></span></span>  
<span data-ttu-id="e55e2-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="e55e2-108">\<security></span></span>  
<span data-ttu-id="e55e2-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="e55e2-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55e2-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e55e2-110">Syntax</span></span>  
  
```xml  
<netTcpBinding>  
    <binding>  
        <security  
         mode="None|Transport|Message|TransportWithMessageCredential">  
            <transport clientCredentialType="None|Windows|Certificate"  
             protectionLevel="None|Sign|EncryptAndSign"             sslProtocols="Tls|Tls11|Tls12">  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</netTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e55e2-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e55e2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e55e2-112">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e55e2-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e55e2-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e55e2-113">Attributes</span></span>  
  
|<span data-ttu-id="e55e2-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="e55e2-114">Attribute</span></span>|<span data-ttu-id="e55e2-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e55e2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e55e2-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e55e2-116">clientCredentialType</span></span>|<span data-ttu-id="e55e2-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e55e2-117">Optional.</span></span> <span data-ttu-id="e55e2-118">Určuje typ pověření, který se má použít při ověřování klienta pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="e55e2-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="e55e2-119">-Výchozí hodnota je `Windows`.</span><span class="sxs-lookup"><span data-stu-id="e55e2-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="e55e2-120">-Tento atribut je typu <xref:System.ServiceModel.TcpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="e55e2-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="e55e2-121">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="e55e2-121">protectionLevel</span></span>|<span data-ttu-id="e55e2-122">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="e55e2-122">Optional.</span></span> <span data-ttu-id="e55e2-123">Definuje zabezpečení na úrovni přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="e55e2-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="e55e2-124">Podepisování zpráv snižuje riziko třetích stran manipulaci s zprávy při jejich přenosu.</span><span class="sxs-lookup"><span data-stu-id="e55e2-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="e55e2-125">Během přenosu zajišťuje šifrování dat na úrovni o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="e55e2-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="e55e2-126">Výchozí hodnota je `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="e55e2-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="e55e2-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="e55e2-127">sslProtocols</span></span>|<span data-ttu-id="e55e2-128">Hodnotu výčtu příznak SslProtocols, která určuje, které SslProtocols jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="e55e2-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="e55e2-129">Výchozí hodnota je Tls &#124; Tls11 &#124; Tls12.</span><span class="sxs-lookup"><span data-stu-id="e55e2-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="e55e2-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="e55e2-130">policyEnforcement</span></span>|<span data-ttu-id="e55e2-131">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="e55e2-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e55e2-132">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="e55e2-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e55e2-133">2.  WhenSupported – zásady se vynucují jenom v případě, že klient podporuje rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="e55e2-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e55e2-134">3.  Vždy – je vždy tato zásada vynucená.</span><span class="sxs-lookup"><span data-stu-id="e55e2-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e55e2-135">Klienti, které nepodporují rozšířené ochrany se nepodaří ověřit.</span><span class="sxs-lookup"><span data-stu-id="e55e2-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e55e2-136">clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="e55e2-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e55e2-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e55e2-137">Value</span></span>|<span data-ttu-id="e55e2-138">Popis</span><span class="sxs-lookup"><span data-stu-id="e55e2-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e55e2-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="e55e2-139">None</span></span>|<span data-ttu-id="e55e2-140">Klient je anonymní.</span><span class="sxs-lookup"><span data-stu-id="e55e2-140">The client is anonymous.</span></span> <span data-ttu-id="e55e2-141">To vyžaduje certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="e55e2-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="e55e2-142">Windows</span><span class="sxs-lookup"><span data-stu-id="e55e2-142">Windows</span></span>|<span data-ttu-id="e55e2-143">Určuje ověřování systému Windows z klienta pomocí SP vyjednávání (vyjednávání protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="e55e2-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="e55e2-144">certifikát</span><span class="sxs-lookup"><span data-stu-id="e55e2-144">Certificate</span></span>|<span data-ttu-id="e55e2-145">Používá certifikát ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="e55e2-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="e55e2-146">To se používá vyjednávání SSL a vyžaduje certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="e55e2-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="e55e2-147">Atribut protectionLevel</span><span class="sxs-lookup"><span data-stu-id="e55e2-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="e55e2-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e55e2-148">Value</span></span>|<span data-ttu-id="e55e2-149">Popis</span><span class="sxs-lookup"><span data-stu-id="e55e2-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e55e2-150">Žádné</span><span class="sxs-lookup"><span data-stu-id="e55e2-150">None</span></span>|<span data-ttu-id="e55e2-151">Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="e55e2-151">No protection.</span></span>|  
|<span data-ttu-id="e55e2-152">Přihlášení</span><span class="sxs-lookup"><span data-stu-id="e55e2-152">Sign</span></span>|<span data-ttu-id="e55e2-153">Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="e55e2-153">Messages are signed.</span></span>|  
|<span data-ttu-id="e55e2-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="e55e2-154">EncryptAndSign</span></span>|<span data-ttu-id="e55e2-155">-Zprávy jsou šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="e55e2-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e55e2-156">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e55e2-156">Child Elements</span></span>  
 <span data-ttu-id="e55e2-157">Žádné</span><span class="sxs-lookup"><span data-stu-id="e55e2-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e55e2-158">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e55e2-158">Parent Elements</span></span>  
  
|<span data-ttu-id="e55e2-159">Prvek</span><span class="sxs-lookup"><span data-stu-id="e55e2-159">Element</span></span>|<span data-ttu-id="e55e2-160">Popis</span><span class="sxs-lookup"><span data-stu-id="e55e2-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e55e2-161">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="e55e2-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="e55e2-162">Určuje možnosti zabezpečení [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="e55e2-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e55e2-163">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e55e2-163">Remarks</span></span>  
 <span data-ttu-id="e55e2-164">Pro integrity a důvěrnosti zpráv protokolu SOAP a vzájemné ověřování, použijte zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="e55e2-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="e55e2-165">Pokud je tento režim zabezpečení na vazbu, zásobník kanál je nakonfigurován pomocí zabezpečení přenosu a protokolu SOAP zprávy jsou zabezpečené pomocí zabezpečení přenosu, například Windows (Negotiate) nebo SSL přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="e55e2-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55e2-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="e55e2-166">See Also</span></span>  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="e55e2-167">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e55e2-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e55e2-168">Vazby</span><span class="sxs-lookup"><span data-stu-id="e55e2-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e55e2-169">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="e55e2-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e55e2-170">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="e55e2-170">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e55e2-171">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="e55e2-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
