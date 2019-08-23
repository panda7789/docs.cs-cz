---
title: <transport> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: af5852c3c7850f91686d50294c8846f85574e909
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918636"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="aad7f-102">\<> přenosu > \<BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="aad7f-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="aad7f-103">Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="aad7f-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="aad7f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="aad7f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aad7f-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="aad7f-105">\<bindings></span></span>  
<span data-ttu-id="aad7f-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="aad7f-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="aad7f-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="aad7f-107">\<binding></span></span>  
<span data-ttu-id="aad7f-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="aad7f-108">\<security></span></span>  
<span data-ttu-id="aad7f-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="aad7f-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad7f-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aad7f-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aad7f-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aad7f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="aad7f-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aad7f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aad7f-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="aad7f-113">Attributes</span></span>  
  
|<span data-ttu-id="aad7f-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="aad7f-114">Attribute</span></span>|<span data-ttu-id="aad7f-115">Popis</span><span class="sxs-lookup"><span data-stu-id="aad7f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aad7f-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="aad7f-116">clientCredentialType</span></span>|<span data-ttu-id="aad7f-117">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí ověřování protokolem HTTP.</span><span class="sxs-lookup"><span data-stu-id="aad7f-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="aad7f-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="aad7f-118">The default is `None`.</span></span> <span data-ttu-id="aad7f-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="aad7f-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="aad7f-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="aad7f-120">proxyCredentialType</span></span>|<span data-ttu-id="aad7f-121">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů v rámci domény pomocí proxy serveru přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="aad7f-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="aad7f-122">Tento atribut je použitelný pouze v případě `mode` , že je `Transport` atribut `security` nadřazeného prvku nebo `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="aad7f-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="aad7f-123">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="aad7f-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="aad7f-124">sféry</span><span class="sxs-lookup"><span data-stu-id="aad7f-124">realm</span></span>|<span data-ttu-id="aad7f-125">Řetězec určující sféru, která je používána schématem ověřování protokolu HTTP pro ověřování algoritmem Digest nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="aad7f-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="aad7f-126">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="aad7f-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="aad7f-127">Nastavením PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="aad7f-127">policyEnforcement</span></span>|<span data-ttu-id="aad7f-128">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="aad7f-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="aad7f-129">1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="aad7f-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="aad7f-130">2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="aad7f-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="aad7f-131">3.  Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="aad7f-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="aad7f-132">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="aad7f-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="aad7f-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="aad7f-133">protectionScenario</span></span>|<span data-ttu-id="aad7f-134">Tento výčet Určuje scénář ochrany, který zásady vynutily.</span><span class="sxs-lookup"><span data-stu-id="aad7f-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="aad7f-135">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="aad7f-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="aad7f-136">Value</span><span class="sxs-lookup"><span data-stu-id="aad7f-136">Value</span></span>|<span data-ttu-id="aad7f-137">Popis</span><span class="sxs-lookup"><span data-stu-id="aad7f-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aad7f-138">Žádné</span><span class="sxs-lookup"><span data-stu-id="aad7f-138">None</span></span>|<span data-ttu-id="aad7f-139">Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="aad7f-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="aad7f-140">Základní</span><span class="sxs-lookup"><span data-stu-id="aad7f-140">Basic</span></span>|<span data-ttu-id="aad7f-141">Určuje základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="aad7f-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="aad7f-142">Otisk</span><span class="sxs-lookup"><span data-stu-id="aad7f-142">Digest</span></span>|<span data-ttu-id="aad7f-143">Určuje ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="aad7f-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="aad7f-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="aad7f-144">Ntlm</span></span>|<span data-ttu-id="aad7f-145">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="aad7f-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="aad7f-146">Windows</span><span class="sxs-lookup"><span data-stu-id="aad7f-146">Windows</span></span>|<span data-ttu-id="aad7f-147">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="aad7f-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="aad7f-148">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="aad7f-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="aad7f-149">Value</span><span class="sxs-lookup"><span data-stu-id="aad7f-149">Value</span></span>|<span data-ttu-id="aad7f-150">Popis</span><span class="sxs-lookup"><span data-stu-id="aad7f-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="aad7f-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="aad7f-151">None</span></span>|<span data-ttu-id="aad7f-152">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="aad7f-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="aad7f-153">Základní</span><span class="sxs-lookup"><span data-stu-id="aad7f-153">Basic</span></span>|<span data-ttu-id="aad7f-154">Určuje základní ověřování definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="aad7f-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="aad7f-155">Otisk</span><span class="sxs-lookup"><span data-stu-id="aad7f-155">Digest</span></span>|<span data-ttu-id="aad7f-156">Určuje ověřování hodnotou hash definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="aad7f-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="aad7f-157">NTLM</span><span class="sxs-lookup"><span data-stu-id="aad7f-157">Ntlm</span></span>|<span data-ttu-id="aad7f-158">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="aad7f-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="aad7f-159">Windows</span><span class="sxs-lookup"><span data-stu-id="aad7f-159">Windows</span></span>|<span data-ttu-id="aad7f-160">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="aad7f-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="aad7f-161">Certifikát</span><span class="sxs-lookup"><span data-stu-id="aad7f-161">Certificate</span></span>|<span data-ttu-id="aad7f-162">Provádí ověřování klientů pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="aad7f-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="aad7f-163">Tato možnost funguje pouze v `Mode` případě, že atribut nadřazeného `security` elementu je nastaven na hodnotu Transport a nebude fungovat, pokud je nastaven na TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="aad7f-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aad7f-164">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aad7f-164">Child Elements</span></span>  
 <span data-ttu-id="aad7f-165">Žádné</span><span class="sxs-lookup"><span data-stu-id="aad7f-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aad7f-166">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aad7f-166">Parent Elements</span></span>  
  
|<span data-ttu-id="aad7f-167">Prvek</span><span class="sxs-lookup"><span data-stu-id="aad7f-167">Element</span></span>|<span data-ttu-id="aad7f-168">Popis</span><span class="sxs-lookup"><span data-stu-id="aad7f-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aad7f-169">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="aad7f-169">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="aad7f-170">Definuje možnosti [ \<zabezpečení BasicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="aad7f-170">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="aad7f-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="aad7f-171">Example</span></span>  
 <span data-ttu-id="aad7f-172">Následující příklad ukazuje použití zabezpečení přenosu SSL se základní vazbou.</span><span class="sxs-lookup"><span data-stu-id="aad7f-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="aad7f-173">Základní vazba standardně podporuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="aad7f-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="aad7f-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aad7f-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="aad7f-175">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="aad7f-175">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="aad7f-176">Vazby</span><span class="sxs-lookup"><span data-stu-id="aad7f-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aad7f-177">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="aad7f-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="aad7f-178">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="aad7f-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="aad7f-179">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="aad7f-179">\<binding></span></span>](../../../misc/binding.md)
