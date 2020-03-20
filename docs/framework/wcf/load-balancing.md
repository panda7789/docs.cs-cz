---
title: Vyrovnávání zatížení
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: a444df2b05803ec54c5bd9030ce12209cfe9bd07
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183984"
---
# <a name="load-balancing"></a><span data-ttu-id="4833f-102">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="4833f-102">Load Balancing</span></span>
<span data-ttu-id="4833f-103">Jedním ze způsobů, jak zvýšit kapacitu aplikací WCF (Windows Communication Foundation), je jejich horizontální navýšení kapacity jejich nasazením do serverové farmy s vyrovnáváním zatížení.</span><span class="sxs-lookup"><span data-stu-id="4833f-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="4833f-104">Aplikace WCF lze vyvážit zatížení pomocí standardních technik vyrovnávání zatížení, včetně softwarových nástrojů pro vyrovnávání zatížení, jako je vyrovnávání zatížení sítě Systému Windows, stejně jako hardwarová zařízení pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="4833f-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="4833f-105">V následujících částech jsou popsány důležité informace pro vyrovnávání zatížení WCF aplikace vytvořené pomocí různých vazby poskytované systémem.</span><span class="sxs-lookup"><span data-stu-id="4833f-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="4833f-106">Vyrovnávání zatížení pomocí základní vazby HTTP</span><span class="sxs-lookup"><span data-stu-id="4833f-106">Load Balancing with the Basic HTTP Binding</span></span>  
 <span data-ttu-id="4833f-107">Z hlediska vyrovnávání zatížení wcf aplikace, <xref:System.ServiceModel.BasicHttpBinding> které komunikují pomocí se neliší od jiných běžných typů síťového provozu HTTP (statický obsah HTML, ASP.NET stránky nebo ASMX webové služby).</span><span class="sxs-lookup"><span data-stu-id="4833f-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="4833f-108">WCF kanály, které používají tuto vazbu jsou ze své podstaty bezstavové a ukončit jejich připojení při ukončení kanálu.</span><span class="sxs-lookup"><span data-stu-id="4833f-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="4833f-109">Jako takové <xref:System.ServiceModel.BasicHttpBinding> funguje dobře s existující mise vyrovnávání zatížení HTTP.</span><span class="sxs-lookup"><span data-stu-id="4833f-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="4833f-110">Ve výchozím <xref:System.ServiceModel.BasicHttpBinding> nastavení odešle hlavičku HTTP `Keep-Alive` připojení ve zprávách s hodnotou, která umožňuje klientům navázat trvalá připojení ke službám, které je podporují.</span><span class="sxs-lookup"><span data-stu-id="4833f-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="4833f-111">Tato konfigurace nabízí rozšířenou propustnost, protože dříve vytvořená připojení lze znovu použít k odesílání následných zpráv na stejný server.</span><span class="sxs-lookup"><span data-stu-id="4833f-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="4833f-112">Opakované použití připojení však může způsobit, že klienti budou silně přidruženi k určitému serveru v rámci farmy s vyrovnáváním zatížení, což snižuje účinnost vyrovnávání zatížení kruhového dotazování.</span><span class="sxs-lookup"><span data-stu-id="4833f-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="4833f-113">Pokud je toto chování `Keep-Alive` nežádoucí, http lze <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> zakázat <xref:System.ServiceModel.Channels.CustomBinding> na serveru <xref:System.ServiceModel.Channels.Binding>pomocí vlastnosti s nebo uživatelem definované .</span><span class="sxs-lookup"><span data-stu-id="4833f-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="4833f-114">Následující příklad ukazuje, jak to provést pomocí konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4833f-114">The following example shows how to do this using configuration.</span></span>  
  
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
  
 <span data-ttu-id="4833f-115">Pomocí zjednodušené konfigurace zavedené v rozhraní .NET Framework 4 lze stejné chování provést pomocí následující zjednodušené konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4833f-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
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
  
 <span data-ttu-id="4833f-116">Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4833f-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="4833f-117">Vyrovnávání zatížení pomocí vazby WSHttp a vazby WSDualHttp</span><span class="sxs-lookup"><span data-stu-id="4833f-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  
 <span data-ttu-id="4833f-118">Oba <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> lze zatížení pomocí techniky vyrovnávání zatížení HTTP za předpokladu, že několik změn jsou provedeny na výchozí konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="4833f-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="4833f-119">Vypnout kontextzabezpečení zabezpečení: to lze provést <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> nastavenívlastnost <xref:System.ServiceModel.WSHttpBinding> na `false`to .</span><span class="sxs-lookup"><span data-stu-id="4833f-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="4833f-120">Případně pokud jsou vyžadovány relace zabezpečení, je možné použít stavové relace zabezpečení, jak je popsáno v tématu [Zabezpečené relace.](./feature-details/secure-sessions.md)</span><span class="sxs-lookup"><span data-stu-id="4833f-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="4833f-121">Stavové relace zabezpečení umožňují, aby služba zůstala bezstavová, protože celý stav relace zabezpečení je přenášen s každým požadavkem jako součást tokenu zabezpečení ochrany.</span><span class="sxs-lookup"><span data-stu-id="4833f-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="4833f-122">Všimněte si, že k povolení relace stavu <xref:System.ServiceModel.Channels.CustomBinding> zabezpečení, je <xref:System.ServiceModel.Channels.Binding> nutné použít nebo uživatelem <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSDualHttpBinding> definované jako potřebná nastavení konfigurace nejsou vystaveny a které jsou poskytovány systémem.</span><span class="sxs-lookup"><span data-stu-id="4833f-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="4833f-123">Nepoužívejte spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="4833f-123">Do not use reliable sessions.</span></span> <span data-ttu-id="4833f-124">Tato funkce je ve výchozím nastavení vypnutá.</span><span class="sxs-lookup"><span data-stu-id="4833f-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="4833f-125">Vyrovnávání zatížení vazby Net.TCP</span><span class="sxs-lookup"><span data-stu-id="4833f-125">Load Balancing the Net.TCP Binding</span></span>  
 <span data-ttu-id="4833f-126">Lze <xref:System.ServiceModel.NetTcpBinding> vyvážit zatížení pomocí technik vyrovnávání zatížení vrstvy IP.</span><span class="sxs-lookup"><span data-stu-id="4833f-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="4833f-127">Ve výchozím <xref:System.ServiceModel.NetTcpBinding> nastavení však fondy připojení TCP ve výchozím nastavení snížit latenci připojení.</span><span class="sxs-lookup"><span data-stu-id="4833f-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="4833f-128">Jedná se o optimalizaci, která narušuje základní mechanismus vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="4833f-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="4833f-129">Primární hodnota konfigurace pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, který je součástí nastavení fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="4833f-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="4833f-130">Sdružování připojení způsobí, že připojení klientů se stanou přidružené k určitým serverům v rámci farmy.</span><span class="sxs-lookup"><span data-stu-id="4833f-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="4833f-131">S tím, jak se zvyšuje životnost těchto připojení (faktor řízený nastavením časového limitu zapůjčení), rozdělení zatížení mezi různé servery ve farmě se stává nevyváženým.</span><span class="sxs-lookup"><span data-stu-id="4833f-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="4833f-132">V důsledku toho se průměrná doba hovoru zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="4833f-132">As a result the average call time increases.</span></span> <span data-ttu-id="4833f-133">Takže při <xref:System.ServiceModel.NetTcpBinding> použití ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozí časový limit zapůjčení používá vazba.</span><span class="sxs-lookup"><span data-stu-id="4833f-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="4833f-134">Časový čas zapůjčení 30 sekund je přiměřeným výchozím bodem pro scénáře s vyrovnáváním zatížení, i když optimální hodnota závisí na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4833f-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="4833f-135">Další informace o časovém rámci zapůjčení kanálu a dalších kvótách přenosu naleznete v [tématu Transport Quotas](./feature-details/transport-quotas.md).</span><span class="sxs-lookup"><span data-stu-id="4833f-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="4833f-136">Pro nejlepší výkon ve scénářích <xref:System.ServiceModel.NetTcpSecurity> s <xref:System.ServiceModel.SecurityMode.Transport> vyrovnáváním zatížení zvažte použití (buď nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span><span class="sxs-lookup"><span data-stu-id="4833f-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4833f-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="4833f-137">See also</span></span>

- [<span data-ttu-id="4833f-138">Doporučené postupy hostování Internetové informační služby</span><span class="sxs-lookup"><span data-stu-id="4833f-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
