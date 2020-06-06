---
title: <transport> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735930"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="e1c41-102">\<transport> z \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="e1c41-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="e1c41-103">Definuje typ požadavků zabezpečení na úrovni zprávy pro koncový bod nakonfigurovaný pomocí [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e1c41-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="e1c41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1c41-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1c41-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e1c41-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e1c41-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e1c41-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1c41-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e1c41-107">Attributes</span></span>  
  
|<span data-ttu-id="e1c41-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="e1c41-108">Attribute</span></span>|<span data-ttu-id="e1c41-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e1c41-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e1c41-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e1c41-110">clientCredentialType</span></span>|<span data-ttu-id="e1c41-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e1c41-111">Optional.</span></span> <span data-ttu-id="e1c41-112">Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="e1c41-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="e1c41-113">– Výchozí hodnota je `Windows` .</span><span class="sxs-lookup"><span data-stu-id="e1c41-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="e1c41-114">– Tento atribut je typu <xref:System.ServiceModel.TcpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="e1c41-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="e1c41-115">Platné</span><span class="sxs-lookup"><span data-stu-id="e1c41-115">protectionLevel</span></span>|<span data-ttu-id="e1c41-116">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="e1c41-116">Optional.</span></span> <span data-ttu-id="e1c41-117">Definuje zabezpečení na úrovni přenosu protokolu TCP.</span><span class="sxs-lookup"><span data-stu-id="e1c41-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="e1c41-118">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="e1c41-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="e1c41-119">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="e1c41-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="e1c41-120">Výchozí hodnota je `EncryptAndSign`.</span><span class="sxs-lookup"><span data-stu-id="e1c41-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="e1c41-121">SslProtocols určující</span><span class="sxs-lookup"><span data-stu-id="e1c41-121">sslProtocols</span></span>|<span data-ttu-id="e1c41-122">Hodnota příznaku výčtu SslProtocols určující, která určuje, které SslProtocols určující jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="e1c41-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="e1c41-123">Výchozí hodnota je TLS&#124;Tls11&#124;Tls12.</span><span class="sxs-lookup"><span data-stu-id="e1c41-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="e1c41-124">Nastavením PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="e1c41-124">policyEnforcement</span></span>|<span data-ttu-id="e1c41-125">Tento výčet Určuje, kdy se <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="e1c41-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="e1c41-126">1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="e1c41-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="e1c41-127">2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="e1c41-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="e1c41-128">3. Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="e1c41-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="e1c41-129">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="e1c41-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="e1c41-130">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="e1c41-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="e1c41-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e1c41-131">Value</span></span>|<span data-ttu-id="e1c41-132">Description</span><span class="sxs-lookup"><span data-stu-id="e1c41-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e1c41-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="e1c41-133">None</span></span>|<span data-ttu-id="e1c41-134">Klient je anonymní.</span><span class="sxs-lookup"><span data-stu-id="e1c41-134">The client is anonymous.</span></span> <span data-ttu-id="e1c41-135">K tomu je potřeba certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="e1c41-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="e1c41-136">Windows</span><span class="sxs-lookup"><span data-stu-id="e1c41-136">Windows</span></span>|<span data-ttu-id="e1c41-137">Určuje ověřování systému Windows klienta pomocí vyjednávání SP (vyjednávání protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="e1c41-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="e1c41-138">Certifikát</span><span class="sxs-lookup"><span data-stu-id="e1c41-138">Certificate</span></span>|<span data-ttu-id="e1c41-139">Klient se ověřuje pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="e1c41-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="e1c41-140">Používá se vyjednávání SSL a vyžaduje certifikát pro službu.</span><span class="sxs-lookup"><span data-stu-id="e1c41-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="e1c41-141">protectionLevel – atribut</span><span class="sxs-lookup"><span data-stu-id="e1c41-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="e1c41-142">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e1c41-142">Value</span></span>|<span data-ttu-id="e1c41-143">Description</span><span class="sxs-lookup"><span data-stu-id="e1c41-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e1c41-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="e1c41-144">None</span></span>|<span data-ttu-id="e1c41-145">Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="e1c41-145">No protection.</span></span>|  
|<span data-ttu-id="e1c41-146">Znaménko</span><span class="sxs-lookup"><span data-stu-id="e1c41-146">Sign</span></span>|<span data-ttu-id="e1c41-147">Zprávy jsou podepsány.</span><span class="sxs-lookup"><span data-stu-id="e1c41-147">Messages are signed.</span></span>|  
|<span data-ttu-id="e1c41-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="e1c41-148">EncryptAndSign</span></span>|<span data-ttu-id="e1c41-149">– Zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="e1c41-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1c41-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e1c41-150">Child Elements</span></span>  
 <span data-ttu-id="e1c41-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="e1c41-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1c41-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e1c41-152">Parent Elements</span></span>  
  
|<span data-ttu-id="e1c41-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="e1c41-153">Element</span></span>|<span data-ttu-id="e1c41-154">Description</span><span class="sxs-lookup"><span data-stu-id="e1c41-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="e1c41-155">Určuje možnosti zabezpečení [\<netTcpBinding>](nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e1c41-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1c41-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1c41-156">Remarks</span></span>  
 <span data-ttu-id="e1c41-157">Zabezpečení přenosu použijte pro zajištění integrity a důvěrnosti zprávy SOAP a pro vzájemné ověřování.</span><span class="sxs-lookup"><span data-stu-id="e1c41-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="e1c41-158">Pokud je ve vazbě vybraný tento režim zabezpečení, zásobník kanálů se nakonfiguruje pomocí zabezpečeného přenosu a zprávy protokolu SOAP se zabezpečují pomocí zabezpečení přenosu, jako je Windows (Negotiate) nebo SSL přes TCP.</span><span class="sxs-lookup"><span data-stu-id="e1c41-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c41-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1c41-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="e1c41-160">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e1c41-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="e1c41-161">Vazby</span><span class="sxs-lookup"><span data-stu-id="e1c41-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e1c41-162">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="e1c41-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e1c41-163">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="e1c41-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
