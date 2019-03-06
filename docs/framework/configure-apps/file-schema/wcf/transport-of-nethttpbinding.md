---
title: <transport> z <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 4d84d99660e4804a5eff2e343ba01c2983520b8f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379728"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="9d5bc-102">\<přenos > z \<netHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9d5bc-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="9d5bc-103">Definuje vlastnosti, které řídí parametry ověřování pro přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="9d5bc-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="9d5bc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="9d5bc-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="9d5bc-105">\<bindings></span></span>  
<span data-ttu-id="9d5bc-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="9d5bc-106">\<netHttpBinding></span></span>  
<span data-ttu-id="9d5bc-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="9d5bc-107">\<binding></span></span>  
<span data-ttu-id="9d5bc-108">\<security></span><span class="sxs-lookup"><span data-stu-id="9d5bc-108">\<security></span></span>  
<span data-ttu-id="9d5bc-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="9d5bc-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d5bc-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d5bc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d5bc-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d5bc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9d5bc-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d5bc-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d5bc-113">Attributes</span></span>  
  
|<span data-ttu-id="9d5bc-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d5bc-114">Attribute</span></span>|<span data-ttu-id="9d5bc-115">Popis</span><span class="sxs-lookup"><span data-stu-id="9d5bc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d5bc-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="9d5bc-116">clientCredentialType</span></span>|<span data-ttu-id="9d5bc-117">: Určuje typ pověření pro použití při ověřování klientů pomocí ověřování protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="9d5bc-118">Výchozí hodnota je `None`.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-118">The default is `None`.</span></span> <span data-ttu-id="9d5bc-119">Tento atribut je typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="9d5bc-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="9d5bc-120">proxyCredentialType</span></span>|<span data-ttu-id="9d5bc-121">: Určuje typ pověření pro použití při ověřování klienta z v rámci domény pomocí proxy serveru prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="9d5bc-122">Tento atribut je použitelné pouze tehdy, když `mode` atributu nadřazeného elementu `security` element je `Transport` nebo `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="9d5bc-123">Tento atribut je typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="9d5bc-124">Sféra</span><span class="sxs-lookup"><span data-stu-id="9d5bc-124">realm</span></span>|<span data-ttu-id="9d5bc-125">Řetězec určující sféru, který používá schéma ověřování protokolu HTTP pro ověřování algoritmem digest nebo základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="9d5bc-126">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="9d5bc-127">Parametr policyenforcement na hodnotu</span><span class="sxs-lookup"><span data-stu-id="9d5bc-127">policyEnforcement</span></span>|<span data-ttu-id="9d5bc-128">Tento výčet Určuje, kdy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> by se měly vynucovat.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="9d5bc-129">1.  Nikdy – zásady se vynucují nikdy (rozšířené ochrany je zakázáno).</span><span class="sxs-lookup"><span data-stu-id="9d5bc-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="9d5bc-130">2.  WhenSupported – zásady se vynucuje jenom v případě, že klient podporuje rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="9d5bc-131">3.  Vždy – je vždy zásady vynucují.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="9d5bc-132">K ověření se nezdaří klientů, kteří nepodporují rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="9d5bc-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="9d5bc-133">protectionScenario</span></span>|<span data-ttu-id="9d5bc-134">Tento výčet určuje scénář ochrany vynucuje daná zásada.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="9d5bc-135">clientCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="9d5bc-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9d5bc-136">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9d5bc-136">Value</span></span>|<span data-ttu-id="9d5bc-137">Popis</span><span class="sxs-lookup"><span data-stu-id="9d5bc-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d5bc-138">Žádná</span><span class="sxs-lookup"><span data-stu-id="9d5bc-138">None</span></span>|<span data-ttu-id="9d5bc-139">Zprávy nejsou zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="9d5bc-140">Základní</span><span class="sxs-lookup"><span data-stu-id="9d5bc-140">Basic</span></span>|<span data-ttu-id="9d5bc-141">Určuje základní ověřování.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="9d5bc-142">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="9d5bc-142">Digest</span></span>|<span data-ttu-id="9d5bc-143">Určuje, ověřování hodnotou hash.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="9d5bc-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="9d5bc-144">Ntlm</span></span>|<span data-ttu-id="9d5bc-145">Určuje ověřování protokolem NTLM, pokud je to možné a pokud se nezdaří ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="9d5bc-146">Windows</span><span class="sxs-lookup"><span data-stu-id="9d5bc-146">Windows</span></span>|<span data-ttu-id="9d5bc-147">Určuje integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="9d5bc-148">proxyCredentialType Attribute</span><span class="sxs-lookup"><span data-stu-id="9d5bc-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="9d5bc-149">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9d5bc-149">Value</span></span>|<span data-ttu-id="9d5bc-150">Popis</span><span class="sxs-lookup"><span data-stu-id="9d5bc-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9d5bc-151">Žádná</span><span class="sxs-lookup"><span data-stu-id="9d5bc-151">None</span></span>|<span data-ttu-id="9d5bc-152">-Zprávy nejsou zabezpečená při přenosu.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="9d5bc-153">Základní</span><span class="sxs-lookup"><span data-stu-id="9d5bc-153">Basic</span></span>|<span data-ttu-id="9d5bc-154">Základní ověřování určuje, jak jsou definovány v dokumentu RFC 2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="9d5bc-155">ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="9d5bc-155">Digest</span></span>|<span data-ttu-id="9d5bc-156">Ověřování algoritmem digest Určuje, jak jsou definovány v dokumentu RFC 2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="9d5bc-157">Ntlm</span><span class="sxs-lookup"><span data-stu-id="9d5bc-157">Ntlm</span></span>|<span data-ttu-id="9d5bc-158">Určuje ověřování protokolem NTLM, pokud je to možné a pokud se nezdaří ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="9d5bc-159">Windows</span><span class="sxs-lookup"><span data-stu-id="9d5bc-159">Windows</span></span>|<span data-ttu-id="9d5bc-160">Určuje integrované ověřování Windows.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="9d5bc-161">Certifikát</span><span class="sxs-lookup"><span data-stu-id="9d5bc-161">Certificate</span></span>|<span data-ttu-id="9d5bc-162">Provádí pomocí certifikátu ověřování klienta.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="9d5bc-163">Tato možnost funguje jenom v případě, `Mode` atributu nadřazeného elementu `security` element je nastavena na přenos a nebude fungovat, pokud je nastaveno na TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d5bc-164">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d5bc-164">Child Elements</span></span>  
 <span data-ttu-id="9d5bc-165">Žádná</span><span class="sxs-lookup"><span data-stu-id="9d5bc-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d5bc-166">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d5bc-166">Parent Elements</span></span>  
  
|<span data-ttu-id="9d5bc-167">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d5bc-167">Element</span></span>|<span data-ttu-id="9d5bc-168">Popis</span><span class="sxs-lookup"><span data-stu-id="9d5bc-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d5bc-169">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="9d5bc-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="9d5bc-170">Definuje možnosti zabezpečení pro [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9d5bc-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d5bc-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d5bc-171">Example</span></span>  
 <span data-ttu-id="9d5bc-172">Následující příklad ukazuje použití zabezpečení přenosu SSL s základní vazby.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="9d5bc-173">Základní vazby ve výchozím nastavení podporuje komunikaci pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="9d5bc-173">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d5bc-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d5bc-174">See also</span></span>
- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="9d5bc-175">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9d5bc-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9d5bc-176">Vazby</span><span class="sxs-lookup"><span data-stu-id="9d5bc-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9d5bc-177">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="9d5bc-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9d5bc-178">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9d5bc-178">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9d5bc-179">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="9d5bc-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
