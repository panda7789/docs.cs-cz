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
# <a name="load-balancing"></a>Vyrovnávání zatížení
Jedním ze způsobů navýšení kapacity aplikace Windows Communication Foundation (WCF) je škálování je podle jejich nasazení do farmy s vyrovnáváním zatížení serveru. Aplikace WCF mohou být vyrovnávání zatížení pomocí standardní zátěže postupů, včetně nástroje pro vyrovnávání zatížení softwaru jako je například Vyrovnávání zatížení sítě Windows, stejně jako hardwarové zařízení Vyrovnávání zatížení.  
  
 Následující části popisují důležité informace týkající se aplikací služby WCF vytvořené pomocí různých vazeb poskytovaných systémem pro vyrovnávání zatížení.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Vyrovnávání zatížení pomocí vazby Basic HTTP  
 Z pohledu Vyrovnávání zatížení, aplikací služby WCF, které komunikují pomocí <xref:System.ServiceModel.BasicHttpBinding> nejsou jiné než jiné běžné typy HTTP síťový provoz (statický obsah ve formátu HTML, stránky technologie ASP.NET nebo webovými službami ASMX). Kanály WCF, které tuto vazbu používají jsou ze své podstaty bezstavové a ukončit jejich připojení po zavření kanálu. V důsledku toho <xref:System.ServiceModel.BasicHttpBinding> dobře funguje s existujícím služby techniky Vyrovnávání zatížení protokolu HTTP.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> pošle hlavičku připojení HTTP ve zprávách s `Keep-Alive` hodnotu, která umožňuje klientům navázat trvalé připojení ke službám, které je podporují. Tato konfigurace nabízí vyšší propustnost, protože dříve vytvořeno, že připojení lze znovu odeslat další zprávy na stejný server. Opakované použití připojení však může způsobit klientům stát asociován k určitému serveru ve farmě s vyrovnáváním zatížení, což snižuje efektivitu Vyrovnávání zatížení s kruhovým. Pokud toto chování nežádoucí, HTTP `Keep-Alive` na serveru pomocí se dají zakázat <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> vlastnost s <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelem definovaný <xref:System.ServiceModel.Channels.Binding>. Následující příklad ukazuje, jak to udělat pomocí konfigurace.  
  
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
  
 Pomocí zjednodušené konfigurace zavedený [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], stejné chování, můžete to provést pomocí následujících zjednodušená konfigurace.  
  
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
  
 Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Vyrovnávání zatížení pomocí vazby WSHttp a WSDualHttp vazby  
 Jak <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> může být s vyrovnáváním zatížení pomocí metod Vyrovnávání zatížení HTTP, pokud několik změn do výchozí vazby konfigurace.  
  
- Vypněte zařízení kontext zabezpečení: To lze provést nastavením <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost <xref:System.ServiceModel.WSHttpBinding> k `false`. Případně, pokud relace zabezpečení vyžaduje, je možné použít stavová bezpečnostních relací, jak je popsáno v [zabezpečení relací](../../../docs/framework/wcf/feature-details/secure-sessions.md) tématu. Stavové bezpečnostních relací Povolit službě a zůstat bezstavové veškerý stav relace zabezpečení se přenášejí spolu s každou žádostí, jako součást tokenu zabezpečení ochrany. Všimněte si, že pokud chcete povolit relaci stavové zabezpečení, je nutné použít <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelem definovaný <xref:System.ServiceModel.Channels.Binding> jako nezbytné konfigurace nastavení nejsou přístupná na <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> , které jsou k dispozici v systému.  
  
- Nepoužívejte spolehlivé relace. Tato funkce je ve výchozím nastavení vypnuta.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Vazba Net.TCP Vyrovnávání zatížení  
 <xref:System.ServiceModel.NetTcpBinding> Může být s vyrovnáváním zatížení pomocí techniky pro vyrovnávání zatížení vrstvy IP. Ale <xref:System.ServiceModel.NetTcpBinding> fondů připojení TCP ve výchozím nastavení ke snížení latence připojení. Toto je optimalizace, která dochází ke kolizím s základní mechanismus služby Vyrovnávání zatížení. Primární konfigurační hodnoty pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, která je součástí nastavení fondu připojení. Sdružování připojení způsobí, že připojení klientů k přidružený k konkrétní servery ve farmě. Jako dobu života těchto připojení zvýšit (faktor, který řídí nastavení časového limitu zapůjčení), nevyvážené distribuci zatížení napříč různými servery ve farmě. Díky tomu průměr volání času zvyšuje. Ano, při použití <xref:System.ServiceModel.NetTcpBinding> ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozí časový limit zapůjčení používá vazba. Časový limit 30 sekundách zapůjčení je rozumné výchozí bod pro scénáře s vyrovnáváním zatížení, přestože optimální hodnota závisí na aplikaci. Další informace o vypršení časového limitu zapůjčení kanálu a ostatní přenosové kvóty najdete v tématu [přenosové kvóty](../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
 Pro nejlepší výkon ve scénářích s vyrovnáváním zatížení, zvažte použití <xref:System.ServiceModel.NetTcpSecurity> (buď <xref:System.ServiceModel.SecurityMode.Transport> nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Viz také:

- [Osvědčené postupy hostování Internetové informační služby](../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
