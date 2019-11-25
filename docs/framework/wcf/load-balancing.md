---
title: Vyrovnávání zatížení
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: c9a1e889ab5adcb8f0eb5ea851c81a4f9ee56e95
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138542"
---
# <a name="load-balancing"></a><span data-ttu-id="a7ba4-102">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="a7ba4-102">Load Balancing</span></span>
<span data-ttu-id="a7ba4-103">Jedním ze způsobů, jak zvýšit kapacitu aplikací Windows Communication Foundation (WCF), je jejich horizontální navýšení kapacity jejich nasazením do serverové farmy s vyrovnáváním zatížení.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="a7ba4-104">Aplikace WCF je možné vyrovnávat zatížení pomocí standardních technik vyrovnávání zatížení, včetně softwarových nástrojů pro vyrovnávání zatížení, jako je například vyrovnávání zatížení sítě systému Windows a zařízení pro vyrovnávání zátěže na</span><span class="sxs-lookup"><span data-stu-id="a7ba4-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="a7ba4-105">Následující části popisují požadavky na Vyrovnávání zatížení aplikací WCF sestavených pomocí různých vazeb poskytovaných systémem.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="a7ba4-106">Vyrovnávání zatížení pomocí základní vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="a7ba4-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="a7ba4-107">Z perspektivy vyrovnávání zatížení nejsou aplikace WCF, které komunikují pomocí <xref:System.ServiceModel.BasicHttpBinding>, jiné než jiné běžné typy síťových přenosů HTTP (statický obsah HTML, stránky ASP.NET nebo webové služby ASMX).</span><span class="sxs-lookup"><span data-stu-id="a7ba4-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="a7ba4-108">Kanály WCF, které používají tuto vazbu, jsou v podstatě bezstavové a ukončí jejich připojení při zavření kanálu.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="a7ba4-109"><xref:System.ServiceModel.BasicHttpBinding> dobře funguje s existujícími technikami vyrovnávání zatížení HTTP.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="a7ba4-110">Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> odesílá hlavičku HTTP připojení ve zprávách s `Keep-Alive` hodnotou, která klientům umožňuje navázat trvalá připojení ke službám, které je podporují.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="a7ba4-111">Tato konfigurace nabízí rozšířenou propustnost, protože dříve vytvořená připojení je možné znovu použít k odeslání dalších zpráv na stejný server.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="a7ba4-112">Opakované použití připojení může ale způsobit, že se klienti budou silně přidružit k určitému serveru v rámci farmy s vyrovnáváním zatížení, což snižuje efektivitu vyrovnávání zatížení pomocí kruhového dotazování.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="a7ba4-113">Pokud je toto chování nežádoucí, `Keep-Alive` HTTP můžete na serveru zakázat pomocí vlastnosti <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> s <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelem definovaným <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="a7ba4-114">Následující příklad ukazuje, jak to provést pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service   
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"   
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="a7ba4-115">Pomocí zjednodušené konfigurace představené v .NET Framework 4 je možné dosáhnout stejného chování pomocí následující zjednodušené konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="a7ba4-116">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a7ba4-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="a7ba4-117">Vyrovnávání zatížení s vazbou WSHttp a vazbou WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="a7ba4-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="a7ba4-118">U <xref:System.ServiceModel.WSHttpBinding> i <xref:System.ServiceModel.WSDualHttpBinding> se dá vyrovnávat zatížení pomocí technik vyrovnávání zatížení HTTP, který poskytuje několik úprav pro výchozí konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="a7ba4-119">Vypnutí vytváření kontextu zabezpečení: můžete to provést nastavením vlastnosti <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> v <xref:System.ServiceModel.WSHttpBinding> na `false`.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="a7ba4-120">Případně, pokud jsou vyžadovány relace zabezpečení, je možné použít stavové relace zabezpečení, jak je popsáno v tématu [zabezpečené relace](./feature-details/secure-sessions.md) .</span><span class="sxs-lookup"><span data-stu-id="a7ba4-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="a7ba4-121">Stavové relace zabezpečení umožňují, aby služba zůstala Bezstavová, protože všechny stavy relace zabezpečení jsou přenášeny s každou žádostí jako součást tokenu zabezpečení ochrany.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="a7ba4-122">Počítejte s tím, že pokud chcete povolit stavovou relaci zabezpečení, je nutné použít <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelsky definované <xref:System.ServiceModel.Channels.Binding>, protože potřebná nastavení konfigurace nejsou vystavena v <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding>, která jsou k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="a7ba4-123">Nepoužívejte spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-123">Do not use reliable sessions.</span></span> <span data-ttu-id="a7ba4-124">Tato funkce je ve výchozím nastavení vypnutá.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="a7ba4-125">Vyrovnávání zatížení vazby NET. TCP</span><span class="sxs-lookup"><span data-stu-id="a7ba4-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="a7ba4-126"><xref:System.ServiceModel.NetTcpBinding> se dá vyrovnávat zatížení pomocí technik vyrovnávání zatížení vrstvy IP.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="a7ba4-127">Ve výchozím nastavení ale <xref:System.ServiceModel.NetTcpBinding> fondy připojení TCP, aby se snížila latence připojení.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="a7ba4-128">Toto je optimalizace, která brání základnímu mechanismu vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="a7ba4-129">Primární hodnotou konfigurace pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, který je součástí nastavení fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="a7ba4-130">Sdružování připojení způsobí, že se připojení klienta stanou přidružená ke konkrétním serverům v rámci farmy.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="a7ba4-131">Jak se prodlouží doba trvání těchto připojení (faktor řízený nastavením časový limit zapůjčení), bude distribuce zatížení napříč různými servery ve farmě nevyvážená.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="a7ba4-132">V důsledku toho se zvýší průměrná doba volání.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-132">As a result the average call time increases.</span></span> <span data-ttu-id="a7ba4-133">Takže pokud používáte <xref:System.ServiceModel.NetTcpBinding> ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozího časového limitu zapůjčení používaného vazbou.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="a7ba4-134">Časový limit zapůjčení je 30 sekund přiměřeným výchozím bodem pro scénáře s vyrovnáváním zatížení, i když optimální hodnota je závislá na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a7ba4-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="a7ba4-135">Další informace o vypršení časového limitu zapůjčení kanálu a dalších přenosových kvót najdete v tématu [přenosové kvóty](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="a7ba4-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="a7ba4-136">Pro dosažení nejlepšího výkonu ve scénářích s vyrovnáváním zatížení zvažte použití <xref:System.ServiceModel.NetTcpSecurity> (<xref:System.ServiceModel.SecurityMode.Transport> nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="a7ba4-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ba4-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7ba4-137">See also</span></span>

- [<span data-ttu-id="a7ba4-138">Osvědčené postupy hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="a7ba4-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
