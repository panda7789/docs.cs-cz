---
title: Vyrovnávání zatížení
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a43546b9cbb95cd16c1d94372e786acd103ea0bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921938"
---
# <a name="load-balancing"></a><span data-ttu-id="df94f-102">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="df94f-102">Load Balancing</span></span>
<span data-ttu-id="df94f-103">Jedním ze způsobů navýšení kapacity aplikace Windows Communication Foundation (WCF) je škálování je podle jejich nasazení do farmy s vyrovnáváním zatížení serveru.</span><span class="sxs-lookup"><span data-stu-id="df94f-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="df94f-104">Aplikace WCF mohou být vyrovnávání zatížení pomocí standardní zátěže postupů, včetně nástroje pro vyrovnávání zatížení softwaru jako je například Vyrovnávání zatížení sítě Windows, stejně jako hardwarové zařízení Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="df94f-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="df94f-105">Následující části popisují důležité informace týkající se aplikací služby WCF vytvořené pomocí různých vazeb poskytovaných systémem pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="df94f-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="df94f-106">Vyrovnávání zatížení pomocí vazby Basic HTTP</span><span class="sxs-lookup"><span data-stu-id="df94f-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="df94f-107">Z pohledu Vyrovnávání zatížení, aplikací služby WCF, které komunikují pomocí <xref:System.ServiceModel.BasicHttpBinding> nejsou jiné než jiné běžné typy HTTP síťový provoz (statický obsah ve formátu HTML, stránky technologie ASP.NET nebo webovými službami ASMX).</span><span class="sxs-lookup"><span data-stu-id="df94f-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="df94f-108">Kanály WCF, které tuto vazbu používají jsou ze své podstaty bezstavové a ukončit jejich připojení po zavření kanálu.</span><span class="sxs-lookup"><span data-stu-id="df94f-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="df94f-109">V důsledku toho <xref:System.ServiceModel.BasicHttpBinding> dobře funguje s existujícím služby techniky Vyrovnávání zatížení protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="df94f-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="df94f-110">Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> pošle hlavičku připojení HTTP ve zprávách s `Keep-Alive` hodnotu, která umožňuje klientům navázat trvalé připojení ke službám, které je podporují.</span><span class="sxs-lookup"><span data-stu-id="df94f-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="df94f-111">Tato konfigurace nabízí vyšší propustnost, protože dříve vytvořeno, že připojení lze znovu odeslat další zprávy na stejný server.</span><span class="sxs-lookup"><span data-stu-id="df94f-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="df94f-112">Opakované použití připojení však může způsobit klientům stát asociován k určitému serveru ve farmě s vyrovnáváním zatížení, což snižuje efektivitu Vyrovnávání zatížení s kruhovým.</span><span class="sxs-lookup"><span data-stu-id="df94f-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="df94f-113">Pokud toto chování nežádoucí, HTTP `Keep-Alive` na serveru pomocí se dají zakázat <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> vlastnost s <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelem definovaný <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="df94f-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="df94f-114">Následující příklad ukazuje, jak to udělat pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="df94f-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="df94f-115">Pomocí zjednodušené konfigurace zavedený [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], stejné chování, můžete to provést pomocí následujících zjednodušená konfigurace.</span><span class="sxs-lookup"><span data-stu-id="df94f-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="df94f-116">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="df94f-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="df94f-117">Vyrovnávání zatížení pomocí vazby WSHttp a WSDualHttp vazby</span><span class="sxs-lookup"><span data-stu-id="df94f-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="df94f-118">Jak <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> může být s vyrovnáváním zatížení pomocí metod Vyrovnávání zatížení HTTP, pokud několik změn do výchozí vazby konfigurace.</span><span class="sxs-lookup"><span data-stu-id="df94f-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="df94f-119">Vypněte zařízení kontext zabezpečení: To lze provést nastavením <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost <xref:System.ServiceModel.WSHttpBinding> k `false`.</span><span class="sxs-lookup"><span data-stu-id="df94f-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="df94f-120">Případně, pokud relace zabezpečení vyžaduje, je možné použít stavová bezpečnostních relací, jak je popsáno v [zabezpečení relací](../../../docs/framework/wcf/feature-details/secure-sessions.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="df94f-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](../../../docs/framework/wcf/feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="df94f-121">Stavové bezpečnostních relací Povolit službě a zůstat bezstavové veškerý stav relace zabezpečení se přenášejí spolu s každou žádostí, jako součást tokenu zabezpečení ochrany.</span><span class="sxs-lookup"><span data-stu-id="df94f-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="df94f-122">Všimněte si, že pokud chcete povolit relaci stavové zabezpečení, je nutné použít <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelem definovaný <xref:System.ServiceModel.Channels.Binding> jako nezbytné konfigurace nastavení nejsou přístupná na <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> , které jsou k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="df94f-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="df94f-123">Nepoužívejte spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="df94f-123">Do not use reliable sessions.</span></span> <span data-ttu-id="df94f-124">Tato funkce je ve výchozím nastavení vypnuta.</span><span class="sxs-lookup"><span data-stu-id="df94f-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="df94f-125">Vazba Net.TCP Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="df94f-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="df94f-126"><xref:System.ServiceModel.NetTcpBinding> Může být s vyrovnáváním zatížení pomocí techniky pro vyrovnávání zatížení vrstvy IP.</span><span class="sxs-lookup"><span data-stu-id="df94f-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="df94f-127">Ale <xref:System.ServiceModel.NetTcpBinding> fondů připojení TCP ve výchozím nastavení ke snížení latence připojení.</span><span class="sxs-lookup"><span data-stu-id="df94f-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="df94f-128">Toto je optimalizace, která dochází ke kolizím s základní mechanismus služby Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="df94f-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="df94f-129">Primární konfigurační hodnoty pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, která je součástí nastavení fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="df94f-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="df94f-130">Sdružování připojení způsobí, že připojení klientů k přidružený k konkrétní servery ve farmě.</span><span class="sxs-lookup"><span data-stu-id="df94f-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="df94f-131">Jako dobu života těchto připojení zvýšit (faktor, který řídí nastavení časového limitu zapůjčení), nevyvážené distribuci zatížení napříč různými servery ve farmě.</span><span class="sxs-lookup"><span data-stu-id="df94f-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="df94f-132">Díky tomu průměr volání času zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="df94f-132">As a result the average call time increases.</span></span> <span data-ttu-id="df94f-133">Ano, při použití <xref:System.ServiceModel.NetTcpBinding> ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozí časový limit zapůjčení používá vazba.</span><span class="sxs-lookup"><span data-stu-id="df94f-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="df94f-134">Časový limit 30 sekundách zapůjčení je rozumné výchozí bod pro scénáře s vyrovnáváním zatížení, přestože optimální hodnota závisí na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="df94f-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="df94f-135">Další informace o vypršení časového limitu zapůjčení kanálu a ostatní přenosové kvóty najdete v tématu [přenosové kvóty](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="df94f-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="df94f-136">Pro nejlepší výkon ve scénářích s vyrovnáváním zatížení, zvažte použití <xref:System.ServiceModel.NetTcpSecurity> (buď <xref:System.ServiceModel.SecurityMode.Transport> nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="df94f-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df94f-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df94f-137">See also</span></span>

- [<span data-ttu-id="df94f-138">Osvědčené postupy hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="df94f-138">Internet Information Services Hosting Best Practices</span></span>](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
