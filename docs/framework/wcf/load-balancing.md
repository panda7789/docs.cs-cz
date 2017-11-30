---
title: "Vyrovnávání zatížení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d068332d5dc51e6e0e5a713b29c4eb45c4e51598
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="load-balancing"></a><span data-ttu-id="866d5-102">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="866d5-102">Load Balancing</span></span>
<span data-ttu-id="866d5-103">Jeden ze způsobů, jak zvýšit kapacitu [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikací je odhlašování škálovat podle jejich nasazení do Vyrovnávání zatížení sítě serverové farmy.</span><span class="sxs-lookup"><span data-stu-id="866d5-103">One way to increase the capacity of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications is to scale them out by deploying them into a load-balanced server farm.</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="866d5-104">aplikace může být Vyrovnávané pomocí vyrovnávání techniky, včetně služby Vyrovnávání zatížení softwaru jako je například Vyrovnávání zatížení sítě Windows standardní zatížení, jakož i hardwarové zařízení pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="866d5-104"> applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="866d5-105">Následující části popisují důležité informace pro vyrovnávání zatížení [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace vytvořené pomocí různých vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="866d5-105">The following sections discuss considerations for load balancing [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="866d5-106">Vyrovnávání zatížení s vazby základní HTTP</span><span class="sxs-lookup"><span data-stu-id="866d5-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="866d5-107">Z hlediska vyrovnávání zatížení [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace, které komunikují pomocí <xref:System.ServiceModel.BasicHttpBinding> nejsou jiné než jiné běžné typy HTTP síťový provoz (statický obsah HTML, stránek ASP.NET nebo webovými službami ASMX).</span><span class="sxs-lookup"><span data-stu-id="866d5-107">From the perspective of load balancing, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="866d5-108">kanály, které tuto vazbu používají jsou ze své podstaty bezstavové a ukončit jejich připojení Zavře kanál.</span><span class="sxs-lookup"><span data-stu-id="866d5-108"> channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="866d5-109">Jako takový <xref:System.ServiceModel.BasicHttpBinding> pracuje s existující HTTP rozložení zátěže techniky.</span><span class="sxs-lookup"><span data-stu-id="866d5-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="866d5-110">Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> pošle hlavičku připojení protokolu HTTP v zprávy s `Keep-Alive` hodnotu, která umožňuje klientům vytvořit trvalé připojení ke službám, které je podporují.</span><span class="sxs-lookup"><span data-stu-id="866d5-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="866d5-111">Tato konfigurace nabízí lepší propustnost, protože dříve vytvořeno, že připojení lze opětovně použít k odeslání dalších zpráv na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="866d5-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="866d5-112">Opakované použití připojení však může způsobit klientů se důrazně přidružené k určitému serveru ve farmě Vyrovnávání zatížení sítě, což snižuje efektivitu Vyrovnávání zatížení pomocí kruhového dotazování.</span><span class="sxs-lookup"><span data-stu-id="866d5-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="866d5-113">Pokud je toto chování žádoucí, HTTP `Keep-Alive` lze vypnout na serveru pomocí <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> vlastnost s <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelsky definovaných <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="866d5-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="866d5-114">Následující příklad ukazuje, jak to provést pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="866d5-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="866d5-115">Pomocí zjednodušená konfigurace byla zavedená v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], stejné chování lze provést pomocí následujících zjednodušená konfigurace.</span><span class="sxs-lookup"><span data-stu-id="866d5-115">Using the simplified configuration introduced in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="866d5-116">výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="866d5-116"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="866d5-117">Vyrovnávání zatížení s WSHttp vazby a WSDualHttp vazby</span><span class="sxs-lookup"><span data-stu-id="866d5-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="866d5-118">Jak <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> může být s vyrovnáváním zatížení pomocí techniky Vyrovnávání zatížení HTTP zadaný několik úprav výchozí vazby konfigurace.</span><span class="sxs-lookup"><span data-stu-id="866d5-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
-   <span data-ttu-id="866d5-119">Vypnout navázání kontextu zabezpečení: To lze provést nastavení <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost <xref:System.ServiceModel.WSHttpBinding> k `false`.</span><span class="sxs-lookup"><span data-stu-id="866d5-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="866d5-120">Případně, pokud zabezpečení relací, je možné použít stavová zabezpečení relace, jak je popsáno v [zabezpečené relace](../../../docs/framework/wcf/feature-details/secure-sessions.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="866d5-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](../../../docs/framework/wcf/feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="866d5-121">Stavová zabezpečení relací povolit službu zůstat bezstavové jako všechny stavu pro relaci zabezpečení se přenášejí při každém požadavku jako součást ochrany token zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="866d5-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="866d5-122">Všimněte si, že pokud chcete povolit relaci stavová zabezpečení, je potřeba použít <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelsky definovaných <xref:System.ServiceModel.Channels.Binding> jako nezbytné konfigurace nastavení se nezobrazí na <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> jsou k dispozici v systému.</span><span class="sxs-lookup"><span data-stu-id="866d5-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
-   <span data-ttu-id="866d5-123">Nepoužívejte spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="866d5-123">Do not use reliable sessions.</span></span> <span data-ttu-id="866d5-124">Tato funkce je ve výchozím nastavení vypnutý.</span><span class="sxs-lookup"><span data-stu-id="866d5-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="866d5-125">Vazba Net.TCP Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="866d5-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="866d5-126"><xref:System.ServiceModel.NetTcpBinding> Může být s vyrovnáváním zatížení pomocí techniky pro vyrovnávání zatížení vrstvy IP.</span><span class="sxs-lookup"><span data-stu-id="866d5-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="866d5-127">Ale <xref:System.ServiceModel.NetTcpBinding> fondy připojení TCP ve výchozím nastavení ke snížení latence připojení.</span><span class="sxs-lookup"><span data-stu-id="866d5-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="866d5-128">Toto je optimalizace, která brání systému základní mechanismus Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="866d5-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="866d5-129">Hodnota primární konfigurace pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, která je součástí fondu nastavení připojení.</span><span class="sxs-lookup"><span data-stu-id="866d5-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="866d5-130">Sdružování připojení způsobí, že připojení klientů k přidružené ke konkrétním serverům v rámci farmy.</span><span class="sxs-lookup"><span data-stu-id="866d5-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="866d5-131">Stejně jako životnost tato připojení zvýšit (faktor, který řídí nastavení časový limit zapůjčení), je distribuce zatížení mezi různými servery ve farmě se stane nevyváženou.</span><span class="sxs-lookup"><span data-stu-id="866d5-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="866d5-132">V důsledku volání průměr prodlužuje čas.</span><span class="sxs-lookup"><span data-stu-id="866d5-132">As a result the average call time increases.</span></span> <span data-ttu-id="866d5-133">Ano, při použití <xref:System.ServiceModel.NetTcpBinding> ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozí časový limit zapůjčení používané vazby.</span><span class="sxs-lookup"><span data-stu-id="866d5-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="866d5-134">Vypršení časového limitu 30 sekund zapůjčení je přiměřené výchozím bodem pro scénáře s vyrovnáváním zatížení, i když optimální hodnota je aplikace závislá.</span><span class="sxs-lookup"><span data-stu-id="866d5-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="866d5-135">Další informace o časový limit zapůjčení kanálu a ostatní přenosové kvóty najdete v tématu [přenosové kvóty](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="866d5-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](../../../docs/framework/wcf/feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="866d5-136">Chcete-li dosáhnout optimálního výkonu ve scénářích s vyrovnáváním zatížení, zvažte použití <xref:System.ServiceModel.NetTcpSecurity> (buď <xref:System.ServiceModel.SecurityMode.Transport> nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="866d5-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="866d5-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="866d5-137">See Also</span></span>  
 [<span data-ttu-id="866d5-138">Doporučené postupy hostování internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="866d5-138">Internet Information Services Hosting Best Practices</span></span>](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
