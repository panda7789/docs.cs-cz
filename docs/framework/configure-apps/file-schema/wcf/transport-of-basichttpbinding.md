---
title: <transport> z <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 2cf69c48a51ce2c687ebcfe9f87f7c22f5f86084
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399386"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="5c601-102">\<> přenosu > \<BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5c601-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="5c601-103">Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="5c601-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="5c601-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5c601-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5c601-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5c601-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5c601-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5c601-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5c601-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5c601-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="5c601-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="5c601-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5c601-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="5c601-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="5c601-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**</span><span class="sxs-lookup"><span data-stu-id="5c601-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c601-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c601-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c601-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5c601-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5c601-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5c601-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c601-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="5c601-114">Attributes</span></span>  
  
|<span data-ttu-id="5c601-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="5c601-115">Attribute</span></span>|<span data-ttu-id="5c601-116">Popis</span><span class="sxs-lookup"><span data-stu-id="5c601-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c601-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="5c601-117">clientCredentialType</span></span>|<span data-ttu-id="5c601-118">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí ověřování protokolem HTTP.</span><span class="sxs-lookup"><span data-stu-id="5c601-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="5c601-119">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="5c601-119">The default is `None`.</span></span> <span data-ttu-id="5c601-120">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5c601-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="5c601-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="5c601-121">proxyCredentialType</span></span>|<span data-ttu-id="5c601-122">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů v rámci domény pomocí proxy serveru přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="5c601-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="5c601-123">Tento atribut je použitelný pouze v případě `mode` , že je `Transport` atribut `security` nadřazeného prvku nebo `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="5c601-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="5c601-124">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5c601-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="5c601-125">sféry</span><span class="sxs-lookup"><span data-stu-id="5c601-125">realm</span></span>|<span data-ttu-id="5c601-126">Řetězec určující sféru, která je používána schématem ověřování protokolu HTTP pro ověřování algoritmem Digest nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5c601-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="5c601-127">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="5c601-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="5c601-128">Nastavením PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="5c601-128">policyEnforcement</span></span>|<span data-ttu-id="5c601-129">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> se má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="5c601-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5c601-130">1.  Nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="5c601-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5c601-131">2.  WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="5c601-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5c601-132">3.  Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="5c601-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5c601-133">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="5c601-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="5c601-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="5c601-134">protectionScenario</span></span>|<span data-ttu-id="5c601-135">Tento výčet Určuje scénář ochrany, který zásady vynutily.</span><span class="sxs-lookup"><span data-stu-id="5c601-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5c601-136">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="5c601-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5c601-137">Value</span><span class="sxs-lookup"><span data-stu-id="5c601-137">Value</span></span>|<span data-ttu-id="5c601-138">Popis</span><span class="sxs-lookup"><span data-stu-id="5c601-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c601-139">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c601-139">None</span></span>|<span data-ttu-id="5c601-140">Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="5c601-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="5c601-141">Základní</span><span class="sxs-lookup"><span data-stu-id="5c601-141">Basic</span></span>|<span data-ttu-id="5c601-142">Určuje základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="5c601-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="5c601-143">Otisk</span><span class="sxs-lookup"><span data-stu-id="5c601-143">Digest</span></span>|<span data-ttu-id="5c601-144">Určuje ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="5c601-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="5c601-145">NTLM</span><span class="sxs-lookup"><span data-stu-id="5c601-145">Ntlm</span></span>|<span data-ttu-id="5c601-146">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5c601-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="5c601-147">Windows</span><span class="sxs-lookup"><span data-stu-id="5c601-147">Windows</span></span>|<span data-ttu-id="5c601-148">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5c601-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5c601-149">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="5c601-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5c601-150">Value</span><span class="sxs-lookup"><span data-stu-id="5c601-150">Value</span></span>|<span data-ttu-id="5c601-151">Popis</span><span class="sxs-lookup"><span data-stu-id="5c601-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5c601-152">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c601-152">None</span></span>|<span data-ttu-id="5c601-153">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="5c601-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="5c601-154">Základní</span><span class="sxs-lookup"><span data-stu-id="5c601-154">Basic</span></span>|<span data-ttu-id="5c601-155">Určuje základní ověřování definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="5c601-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="5c601-156">Otisk</span><span class="sxs-lookup"><span data-stu-id="5c601-156">Digest</span></span>|<span data-ttu-id="5c601-157">Určuje ověřování hodnotou hash definované v dokumentu RFC 2617 – ověřování protokolem HTTP: Základní ověřování a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="5c601-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="5c601-158">NTLM</span><span class="sxs-lookup"><span data-stu-id="5c601-158">Ntlm</span></span>|<span data-ttu-id="5c601-159">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="5c601-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="5c601-160">Windows</span><span class="sxs-lookup"><span data-stu-id="5c601-160">Windows</span></span>|<span data-ttu-id="5c601-161">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5c601-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="5c601-162">Certifikát</span><span class="sxs-lookup"><span data-stu-id="5c601-162">Certificate</span></span>|<span data-ttu-id="5c601-163">Provádí ověřování klientů pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="5c601-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="5c601-164">Tato možnost funguje pouze v `Mode` případě, že atribut nadřazeného `security` elementu je nastaven na hodnotu Transport a nebude fungovat, pokud je nastaven na TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="5c601-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c601-165">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5c601-165">Child Elements</span></span>  
 <span data-ttu-id="5c601-166">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c601-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c601-167">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5c601-167">Parent Elements</span></span>  
  
|<span data-ttu-id="5c601-168">Prvek</span><span class="sxs-lookup"><span data-stu-id="5c601-168">Element</span></span>|<span data-ttu-id="5c601-169">Popis</span><span class="sxs-lookup"><span data-stu-id="5c601-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c601-170">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5c601-170">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="5c601-171">Definuje možnosti [ \<zabezpečení BasicHttpBinding >](basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5c601-171">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5c601-172">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c601-172">Example</span></span>  
 <span data-ttu-id="5c601-173">Následující příklad ukazuje použití zabezpečení přenosu SSL se základní vazbou.</span><span class="sxs-lookup"><span data-stu-id="5c601-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="5c601-174">Základní vazba standardně podporuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5c601-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c601-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c601-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="5c601-176">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5c601-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5c601-177">Vazby</span><span class="sxs-lookup"><span data-stu-id="5c601-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5c601-178">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5c601-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5c601-179">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5c601-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5c601-180">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5c601-180">\<binding></span></span>](../../../misc/binding.md)
