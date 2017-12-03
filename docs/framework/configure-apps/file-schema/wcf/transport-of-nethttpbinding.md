---
title: "&lt;transport&gt; – &lt;netHttpBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3128ac2f36d778bc502fe56b776a15c51f1fda69
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a><span data-ttu-id="108de-102">&lt;transport&gt; – &lt;netHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="108de-102">&lt;transport&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="108de-103">Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="108de-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="108de-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="108de-104">\<system.serviceModel></span></span>  
<span data-ttu-id="108de-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="108de-105">\<bindings></span></span>  
<span data-ttu-id="108de-106">\<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="108de-106">\<netHttpBinding></span></span>  
<span data-ttu-id="108de-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="108de-107">\<binding></span></span>  
<span data-ttu-id="108de-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="108de-108">\<security></span></span>  
<span data-ttu-id="108de-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="108de-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="108de-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="108de-110">Syntax</span></span>  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="108de-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="108de-111">Attributes and Elements</span></span>  
 <span data-ttu-id="108de-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="108de-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="108de-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="108de-113">Attributes</span></span>  
  
|<span data-ttu-id="108de-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="108de-114">Attribute</span></span>|<span data-ttu-id="108de-115">Popis</span><span class="sxs-lookup"><span data-stu-id="108de-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="108de-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="108de-116">clientCredentialType</span></span>|<span data-ttu-id="108de-117">-Určuje typ pověření, který se má použít při ověřování klienta pomocí ověřování protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="108de-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="108de-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="108de-118">The default is `None`.</span></span> <span data-ttu-id="108de-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="108de-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="108de-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="108de-120">proxyCredentialType</span></span>|<span data-ttu-id="108de-121">-Určuje typ pověření, který se má použít při ověřování klienta z v rámci domény použitím proxy serveru pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="108de-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="108de-122">Tento atribut je platí pouze tehdy, když `mode` atribut nadřazené `security` element je `Transport` nebo `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="108de-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="108de-123">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="108de-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="108de-124">sféry</span><span class="sxs-lookup"><span data-stu-id="108de-124">realm</span></span>|<span data-ttu-id="108de-125">Řetězec, který určuje sféry, který je používán schéma HTTP ověřování hodnotou hash nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="108de-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="108de-126">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="108de-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="108de-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="108de-127">policyEnforcement</span></span>|<span data-ttu-id="108de-128">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="108de-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="108de-129">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="108de-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="108de-130">2.  WhenSupported – zásady se vynucují jenom v případě, že klient podporuje rozšířené ochrany.</span><span class="sxs-lookup"><span data-stu-id="108de-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="108de-131">3.  Vždy – je vždy tato zásada vynucená.</span><span class="sxs-lookup"><span data-stu-id="108de-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="108de-132">Klienti, které nepodporují rozšířené ochrany se nepodaří ověřit.</span><span class="sxs-lookup"><span data-stu-id="108de-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="108de-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="108de-133">protectionScenario</span></span>|<span data-ttu-id="108de-134">Tento výčet určuje scénář ochrany vynucují zásady.</span><span class="sxs-lookup"><span data-stu-id="108de-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="108de-135">clientCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="108de-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="108de-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="108de-136">Value</span></span>|<span data-ttu-id="108de-137">Popis</span><span class="sxs-lookup"><span data-stu-id="108de-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="108de-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="108de-138">None</span></span>|<span data-ttu-id="108de-139">Zprávy není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="108de-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="108de-140">Základní</span><span class="sxs-lookup"><span data-stu-id="108de-140">Basic</span></span>|<span data-ttu-id="108de-141">Určuje základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="108de-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="108de-142">Ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="108de-142">Digest</span></span>|<span data-ttu-id="108de-143">Určuje, ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="108de-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="108de-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="108de-144">Ntlm</span></span>|<span data-ttu-id="108de-145">Určuje ověřování NTLM, pokud je to možné, a pokud ověřování systému Windows selže.</span><span class="sxs-lookup"><span data-stu-id="108de-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="108de-146">Windows</span><span class="sxs-lookup"><span data-stu-id="108de-146">Windows</span></span>|<span data-ttu-id="108de-147">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="108de-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="108de-148">proxyCredentialType atribut</span><span class="sxs-lookup"><span data-stu-id="108de-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="108de-149">Hodnota</span><span class="sxs-lookup"><span data-stu-id="108de-149">Value</span></span>|<span data-ttu-id="108de-150">Popis</span><span class="sxs-lookup"><span data-stu-id="108de-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="108de-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="108de-151">None</span></span>|<span data-ttu-id="108de-152">-Zprávy není zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="108de-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="108de-153">Základní</span><span class="sxs-lookup"><span data-stu-id="108de-153">Basic</span></span>|<span data-ttu-id="108de-154">Určuje základní ověřování podle definice dokumentu RFC 2617 – ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="108de-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="108de-155">Ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="108de-155">Digest</span></span>|<span data-ttu-id="108de-156">Ověřování hodnotou hash podle určuje RFC 2617 – ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="108de-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="108de-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="108de-157">Ntlm</span></span>|<span data-ttu-id="108de-158">Určuje ověřování NTLM, pokud je to možné, a pokud ověřování systému Windows selže.</span><span class="sxs-lookup"><span data-stu-id="108de-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="108de-159">Windows</span><span class="sxs-lookup"><span data-stu-id="108de-159">Windows</span></span>|<span data-ttu-id="108de-160">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="108de-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="108de-161">certifikát</span><span class="sxs-lookup"><span data-stu-id="108de-161">Certificate</span></span>|<span data-ttu-id="108de-162">Provede používá certifikát ověření klienta.</span><span class="sxs-lookup"><span data-stu-id="108de-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="108de-163">Tato možnost funguje jenom v případě `Mode` atribut nadřazené `security` elementu je nastaven na přenos a nebude fungovat, pokud je nastavena na možnost TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="108de-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="108de-164">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="108de-164">Child Elements</span></span>  
 <span data-ttu-id="108de-165">Žádné</span><span class="sxs-lookup"><span data-stu-id="108de-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="108de-166">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="108de-166">Parent Elements</span></span>  
  
|<span data-ttu-id="108de-167">Prvek</span><span class="sxs-lookup"><span data-stu-id="108de-167">Element</span></span>|<span data-ttu-id="108de-168">Popis</span><span class="sxs-lookup"><span data-stu-id="108de-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="108de-169">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="108de-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="108de-170">Definuje možnosti zabezpečení pro [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="108de-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="108de-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="108de-171">Example</span></span>  
 <span data-ttu-id="108de-172">Následující příklad ukazuje použití protokolu SSL zabezpečení přenosu s základní vazby.</span><span class="sxs-lookup"><span data-stu-id="108de-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="108de-173">Základní vazby ve výchozím nastavení podporuje komunikaci prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="108de-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="108de-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="108de-174">See Also</span></span>  
 <span data-ttu-id="108de-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport><xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span><span class="sxs-lookup"><span data-stu-id="108de-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="108de-176">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="108de-176">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="108de-177">Vazby</span><span class="sxs-lookup"><span data-stu-id="108de-177">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="108de-178">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="108de-178">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="108de-179">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="108de-179">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="108de-180">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="108de-180">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
