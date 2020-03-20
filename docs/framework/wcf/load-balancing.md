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
# <a name="load-balancing"></a>Vyrovnávání zatížení
Jedním ze způsobů, jak zvýšit kapacitu aplikací WCF (Windows Communication Foundation), je jejich horizontální navýšení kapacity jejich nasazením do serverové farmy s vyrovnáváním zatížení. Aplikace WCF lze vyvážit zatížení pomocí standardních technik vyrovnávání zatížení, včetně softwarových nástrojů pro vyrovnávání zatížení, jako je vyrovnávání zatížení sítě Systému Windows, stejně jako hardwarová zařízení pro vyrovnávání zatížení.  
  
 V následujících částech jsou popsány důležité informace pro vyrovnávání zatížení WCF aplikace vytvořené pomocí různých vazby poskytované systémem.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Vyrovnávání zatížení pomocí základní vazby HTTP  
 Z hlediska vyrovnávání zatížení wcf aplikace, <xref:System.ServiceModel.BasicHttpBinding> které komunikují pomocí se neliší od jiných běžných typů síťového provozu HTTP (statický obsah HTML, ASP.NET stránky nebo ASMX webové služby). WCF kanály, které používají tuto vazbu jsou ze své podstaty bezstavové a ukončit jejich připojení při ukončení kanálu. Jako takové <xref:System.ServiceModel.BasicHttpBinding> funguje dobře s existující mise vyrovnávání zatížení HTTP.  
  
 Ve výchozím <xref:System.ServiceModel.BasicHttpBinding> nastavení odešle hlavičku HTTP `Keep-Alive` připojení ve zprávách s hodnotou, která umožňuje klientům navázat trvalá připojení ke službám, které je podporují. Tato konfigurace nabízí rozšířenou propustnost, protože dříve vytvořená připojení lze znovu použít k odesílání následných zpráv na stejný server. Opakované použití připojení však může způsobit, že klienti budou silně přidruženi k určitému serveru v rámci farmy s vyrovnáváním zatížení, což snižuje účinnost vyrovnávání zatížení kruhového dotazování. Pokud je toto chování `Keep-Alive` nežádoucí, http lze <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> zakázat <xref:System.ServiceModel.Channels.CustomBinding> na serveru <xref:System.ServiceModel.Channels.Binding>pomocí vlastnosti s nebo uživatelem definované . Následující příklad ukazuje, jak to provést pomocí konfigurace.  
  
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
  
 Pomocí zjednodušené konfigurace zavedené v rozhraní .NET Framework 4 lze stejné chování provést pomocí následující zjednodušené konfigurace.  
  
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
  
 Další informace o výchozích koncových bodech, vazbách a chování naleznete v [tématu Zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Vyrovnávání zatížení pomocí vazby WSHttp a vazby WSDualHttp  
 Oba <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> lze zatížení pomocí techniky vyrovnávání zatížení HTTP za předpokladu, že několik změn jsou provedeny na výchozí konfiguraci vazby.  
  
- Vypnout kontextzabezpečení zabezpečení: to lze provést <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> nastavenívlastnost <xref:System.ServiceModel.WSHttpBinding> na `false`to . Případně pokud jsou vyžadovány relace zabezpečení, je možné použít stavové relace zabezpečení, jak je popsáno v tématu [Zabezpečené relace.](./feature-details/secure-sessions.md) Stavové relace zabezpečení umožňují, aby služba zůstala bezstavová, protože celý stav relace zabezpečení je přenášen s každým požadavkem jako součást tokenu zabezpečení ochrany. Všimněte si, že k povolení relace stavu <xref:System.ServiceModel.Channels.CustomBinding> zabezpečení, je <xref:System.ServiceModel.Channels.Binding> nutné použít nebo uživatelem <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.WSDualHttpBinding> definované jako potřebná nastavení konfigurace nejsou vystaveny a které jsou poskytovány systémem.  
  
- Nepoužívejte spolehlivé relace. Tato funkce je ve výchozím nastavení vypnutá.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Vyrovnávání zatížení vazby Net.TCP  
 Lze <xref:System.ServiceModel.NetTcpBinding> vyvážit zatížení pomocí technik vyrovnávání zatížení vrstvy IP. Ve výchozím <xref:System.ServiceModel.NetTcpBinding> nastavení však fondy připojení TCP ve výchozím nastavení snížit latenci připojení. Jedná se o optimalizaci, která narušuje základní mechanismus vyrovnávání zatížení. Primární hodnota konfigurace pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, který je součástí nastavení fondu připojení. Sdružování připojení způsobí, že připojení klientů se stanou přidružené k určitým serverům v rámci farmy. S tím, jak se zvyšuje životnost těchto připojení (faktor řízený nastavením časového limitu zapůjčení), rozdělení zatížení mezi různé servery ve farmě se stává nevyváženým. V důsledku toho se průměrná doba hovoru zvyšuje. Takže při <xref:System.ServiceModel.NetTcpBinding> použití ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozí časový limit zapůjčení používá vazba. Časový čas zapůjčení 30 sekund je přiměřeným výchozím bodem pro scénáře s vyrovnáváním zatížení, i když optimální hodnota závisí na aplikaci. Další informace o časovém rámci zapůjčení kanálu a dalších kvótách přenosu naleznete v [tématu Transport Quotas](./feature-details/transport-quotas.md).  
  
 Pro nejlepší výkon ve scénářích <xref:System.ServiceModel.NetTcpSecurity> s <xref:System.ServiceModel.SecurityMode.Transport> vyrovnáváním zatížení zvažte použití (buď nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Viz také

- [Doporučené postupy hostování Internetové informační služby](./feature-details/internet-information-services-hosting-best-practices.md)
