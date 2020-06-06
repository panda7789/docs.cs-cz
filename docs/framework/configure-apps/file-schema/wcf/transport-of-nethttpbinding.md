---
title: <transport> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73732821"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="f3c64-102">\<transport> z \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f3c64-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="f3c64-103">Definuje vlastnosti, které řídí parametry ověřování pro přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3c64-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="f3c64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3c64-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3c64-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3c64-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f3c64-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3c64-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3c64-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3c64-107">Attributes</span></span>  
  
|<span data-ttu-id="f3c64-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3c64-108">Attribute</span></span>|<span data-ttu-id="f3c64-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f3c64-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3c64-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f3c64-110">clientCredentialType</span></span>|<span data-ttu-id="f3c64-111">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů pomocí ověřování protokolem HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3c64-111">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="f3c64-112">Výchozí formát je `None`.</span><span class="sxs-lookup"><span data-stu-id="f3c64-112">The default is `None`.</span></span> <span data-ttu-id="f3c64-113">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="f3c64-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="f3c64-114">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="f3c64-114">proxyCredentialType</span></span>|<span data-ttu-id="f3c64-115">– Určuje typ přihlašovacích údajů, které se mají použít při ověřování klientů v rámci domény pomocí proxy serveru přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3c64-115">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="f3c64-116">Tento atribut je použitelný pouze v případě, že `mode` je atribut nadřazeného `security` prvku `Transport` nebo `TransportCredentialsOnly` .</span><span class="sxs-lookup"><span data-stu-id="f3c64-116">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="f3c64-117">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="f3c64-117">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="f3c64-118">sféry</span><span class="sxs-lookup"><span data-stu-id="f3c64-118">realm</span></span>|<span data-ttu-id="f3c64-119">Řetězec určující sféru, která je používána schématem ověřování protokolu HTTP pro ověřování algoritmem Digest nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="f3c64-119">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="f3c64-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f3c64-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="f3c64-121">Nastavením PolicyEnforcement</span><span class="sxs-lookup"><span data-stu-id="f3c64-121">policyEnforcement</span></span>|<span data-ttu-id="f3c64-122">Tento výčet Určuje, kdy se <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> má vyhovět.</span><span class="sxs-lookup"><span data-stu-id="f3c64-122">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="f3c64-123">1. nikdy – zásada se nikdy vynutila (Rozšířená ochrana je zakázaná).</span><span class="sxs-lookup"><span data-stu-id="f3c64-123">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="f3c64-124">2. WhenSupported – zásada se vynutila jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="f3c64-124">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="f3c64-125">3. Always – zásada se vždycky vynutila.</span><span class="sxs-lookup"><span data-stu-id="f3c64-125">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="f3c64-126">Nepůjde ověřit klienty, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="f3c64-126">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="f3c64-127">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="f3c64-127">protectionScenario</span></span>|<span data-ttu-id="f3c64-128">Tento výčet Určuje scénář ochrany, který zásady vynutily.</span><span class="sxs-lookup"><span data-stu-id="f3c64-128">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f3c64-129">clientCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="f3c64-129">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f3c64-130">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3c64-130">Value</span></span>|<span data-ttu-id="f3c64-131">Description</span><span class="sxs-lookup"><span data-stu-id="f3c64-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3c64-132">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3c64-132">None</span></span>|<span data-ttu-id="f3c64-133">Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="f3c64-133">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="f3c64-134">Základní</span><span class="sxs-lookup"><span data-stu-id="f3c64-134">Basic</span></span>|<span data-ttu-id="f3c64-135">Určuje základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="f3c64-135">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="f3c64-136">Otisk</span><span class="sxs-lookup"><span data-stu-id="f3c64-136">Digest</span></span>|<span data-ttu-id="f3c64-137">Určuje ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="f3c64-137">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="f3c64-138">NTLM</span><span class="sxs-lookup"><span data-stu-id="f3c64-138">Ntlm</span></span>|<span data-ttu-id="f3c64-139">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="f3c64-139">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="f3c64-140">Windows</span><span class="sxs-lookup"><span data-stu-id="f3c64-140">Windows</span></span>|<span data-ttu-id="f3c64-141">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f3c64-141">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="f3c64-142">proxyCredentialType – atribut</span><span class="sxs-lookup"><span data-stu-id="f3c64-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f3c64-143">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3c64-143">Value</span></span>|<span data-ttu-id="f3c64-144">Description</span><span class="sxs-lookup"><span data-stu-id="f3c64-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3c64-145">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3c64-145">None</span></span>|<span data-ttu-id="f3c64-146">– Zprávy nejsou během přenosu zabezpečeny.</span><span class="sxs-lookup"><span data-stu-id="f3c64-146">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="f3c64-147">Základní</span><span class="sxs-lookup"><span data-stu-id="f3c64-147">Basic</span></span>|<span data-ttu-id="f3c64-148">Určuje základní ověřování definované v dokumentu RFC 2617 – ověřování protokolem HTTP: základní a ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="f3c64-148">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="f3c64-149">Otisk</span><span class="sxs-lookup"><span data-stu-id="f3c64-149">Digest</span></span>|<span data-ttu-id="f3c64-150">Určuje ověřování hodnotou hash definované v dokumentu RFC 2617 – ověřování protokolem HTTP: základní a ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="f3c64-150">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="f3c64-151">NTLM</span><span class="sxs-lookup"><span data-stu-id="f3c64-151">Ntlm</span></span>|<span data-ttu-id="f3c64-152">Určuje ověřování NTLM, pokud je to možné, a pokud se ověřování systému Windows nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="f3c64-152">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="f3c64-153">Windows</span><span class="sxs-lookup"><span data-stu-id="f3c64-153">Windows</span></span>|<span data-ttu-id="f3c64-154">Určuje integrované ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f3c64-154">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="f3c64-155">Certifikát</span><span class="sxs-lookup"><span data-stu-id="f3c64-155">Certificate</span></span>|<span data-ttu-id="f3c64-156">Provádí ověřování klientů pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="f3c64-156">Performs client authentication using a certificate.</span></span> <span data-ttu-id="f3c64-157">Tato možnost funguje pouze v případě, že `Mode` atribut nadřazeného `security` elementu je nastaven na hodnotu Transport a nebude fungovat, pokud je nastaven na TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="f3c64-157">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3c64-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3c64-158">Child Elements</span></span>  
 <span data-ttu-id="f3c64-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3c64-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3c64-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3c64-160">Parent Elements</span></span>  
  
|<span data-ttu-id="f3c64-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3c64-161">Element</span></span>|<span data-ttu-id="f3c64-162">Description</span><span class="sxs-lookup"><span data-stu-id="f3c64-162">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nethttpbinding.md)|<span data-ttu-id="f3c64-163">Definuje možnosti zabezpečení pro [\<netHttpBinding>](nethttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f3c64-163">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3c64-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3c64-164">Example</span></span>  
 <span data-ttu-id="f3c64-165">Následující příklad ukazuje použití zabezpečení přenosu SSL se základní vazbou.</span><span class="sxs-lookup"><span data-stu-id="f3c64-165">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="f3c64-166">Základní vazba standardně podporuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f3c64-166">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3c64-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3c64-167">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="f3c64-168">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f3c64-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f3c64-169">Vazby</span><span class="sxs-lookup"><span data-stu-id="f3c64-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3c64-170">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f3c64-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f3c64-171">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f3c64-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
