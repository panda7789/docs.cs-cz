---
title: <transport> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: f9f784329081f6a18560991378a4527c731f4d31
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934709"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="2a982-102">\<> přenosu > \<NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2a982-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="2a982-103">Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="2a982-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="2a982-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2a982-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2a982-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="2a982-105">\<bindings></span></span>  
<span data-ttu-id="2a982-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="2a982-106">\<netHttpBinding></span></span>  
<span data-ttu-id="2a982-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="2a982-107">\<binding></span></span>  
<span data-ttu-id="2a982-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2a982-108">\<security></span></span>  
<span data-ttu-id="2a982-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="2a982-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a982-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2a982-110">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a982-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2a982-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2a982-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2a982-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a982-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="2a982-113">Attributes</span></span>  
  
|<span data-ttu-id="2a982-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="2a982-114">Attribute</span></span>|<span data-ttu-id="2a982-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2a982-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2a982-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="2a982-116">clientCredentialType</span></span>|<span data-ttu-id="2a982-117">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí ověřování protokolem HTTP.</span><span class="sxs-lookup"><span data-stu-id="2a982-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="2a982-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="2a982-118">The default is `None`.</span></span> <span data-ttu-id="2a982-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2a982-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="2a982-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="2a982-120">proxyCredentialType</span></span>|<span data-ttu-id="2a982-121">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů v rámci domény pomocí proxy serveru přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="2a982-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="2a982-122">Tento atribut je použitelný pouze v případě `mode` , že je `Transport` atribut `security` nadřazeného prvku nebo `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="2a982-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="2a982-123">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="2a982-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="2a982-124">sféry</span><span class="sxs-lookup"><span data-stu-id="2a982-124">realm</span></span>|<span data-ttu-id="2a982-125">Řetězec určující sféru, která je používána schématem ověřování protokolu HTTP pro ověřování algoritmem Digest nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="2a982-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="2a982-126">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a982-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="2a982-127">Nastavením PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="2a982-127">policyEnforcement</span></span>|<span data-ttu-id="2a982-128">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="2a982-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="2a982-129">1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="2a982-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="2a982-130">2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="2a982-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="2a982-131">3.  Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="2a982-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="2a982-132">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="2a982-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="2a982-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="2a982-133">protectionScenario</span></span>|<span data-ttu-id="2a982-134">Tento výčet Určuje scénář ochrany, který zásady vynutily.</span><span class="sxs-lookup"><span data-stu-id="2a982-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="2a982-135">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="2a982-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2a982-136">Value</span><span class="sxs-lookup"><span data-stu-id="2a982-136">Value</span></span>|<span data-ttu-id="2a982-137">Popis</span><span class="sxs-lookup"><span data-stu-id="2a982-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a982-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a982-138">None</span></span>|<span data-ttu-id="2a982-139">Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="2a982-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="2a982-140">Základní</span><span class="sxs-lookup"><span data-stu-id="2a982-140">Basic</span></span>|<span data-ttu-id="2a982-141">Určuje základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="2a982-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="2a982-142">Otisk</span><span class="sxs-lookup"><span data-stu-id="2a982-142">Digest</span></span>|<span data-ttu-id="2a982-143">Určuje ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="2a982-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="2a982-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="2a982-144">Ntlm</span></span>|<span data-ttu-id="2a982-145">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="2a982-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="2a982-146">Windows</span><span class="sxs-lookup"><span data-stu-id="2a982-146">Windows</span></span>|<span data-ttu-id="2a982-147">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2a982-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="2a982-148">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="2a982-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="2a982-149">Value</span><span class="sxs-lookup"><span data-stu-id="2a982-149">Value</span></span>|<span data-ttu-id="2a982-150">Popis</span><span class="sxs-lookup"><span data-stu-id="2a982-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2a982-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a982-151">None</span></span>|<span data-ttu-id="2a982-152">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="2a982-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="2a982-153">Základní</span><span class="sxs-lookup"><span data-stu-id="2a982-153">Basic</span></span>|<span data-ttu-id="2a982-154">Určuje základní ověřování definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="2a982-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="2a982-155">Otisk</span><span class="sxs-lookup"><span data-stu-id="2a982-155">Digest</span></span>|<span data-ttu-id="2a982-156">Určuje ověřování hodnotou hash definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="2a982-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="2a982-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="2a982-157">Ntlm</span></span>|<span data-ttu-id="2a982-158">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="2a982-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="2a982-159">Windows</span><span class="sxs-lookup"><span data-stu-id="2a982-159">Windows</span></span>|<span data-ttu-id="2a982-160">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2a982-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="2a982-161">Certifikát</span><span class="sxs-lookup"><span data-stu-id="2a982-161">Certificate</span></span>|<span data-ttu-id="2a982-162">Provádí ověřování klientů pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="2a982-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="2a982-163">Tato možnost funguje pouze v `Mode` případě, že atribut nadřazeného `security` elementu je nastaven na hodnotu Transport a nebude fungovat, pokud je nastaven na TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="2a982-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a982-164">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2a982-164">Child Elements</span></span>  
 <span data-ttu-id="2a982-165">Žádné</span><span class="sxs-lookup"><span data-stu-id="2a982-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a982-166">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2a982-166">Parent Elements</span></span>  
  
|<span data-ttu-id="2a982-167">Prvek</span><span class="sxs-lookup"><span data-stu-id="2a982-167">Element</span></span>|<span data-ttu-id="2a982-168">Popis</span><span class="sxs-lookup"><span data-stu-id="2a982-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a982-169">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2a982-169">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="2a982-170">Definuje možnosti [ \<zabezpečení NetHttpBinding >](nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2a982-170">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2a982-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a982-171">Example</span></span>  
 <span data-ttu-id="2a982-172">Následující příklad ukazuje použití zabezpečení přenosu SSL se základní vazbou.</span><span class="sxs-lookup"><span data-stu-id="2a982-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="2a982-173">Základní vazba standardně podporuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="2a982-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="2a982-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a982-174">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="2a982-175">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2a982-175">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="2a982-176">Vazby</span><span class="sxs-lookup"><span data-stu-id="2a982-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="2a982-177">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="2a982-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="2a982-178">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="2a982-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="2a982-179">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="2a982-179">\<binding></span></span>](../../../misc/binding.md)
