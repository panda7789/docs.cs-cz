---
title: Vyrovnávání zatížení
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: 572537826074dd51b56f1cae9edb767708bc1c3d
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321023"
---
# <a name="load-balancing"></a>Vyrovnávání zatížení
Jedním ze způsobů, jak zvýšit kapacitu aplikací Windows Communication Foundation (WCF), je jejich horizontální navýšení kapacity jejich nasazením do serverové farmy s vyrovnáváním zatížení. Aplikace WCF je možné vyrovnávat zatížení pomocí standardních technik vyrovnávání zatížení, včetně softwarových nástrojů pro vyrovnávání zatížení, jako je například vyrovnávání zatížení sítě systému Windows a zařízení pro vyrovnávání zátěže na  
  
 Následující části popisují požadavky na Vyrovnávání zatížení aplikací WCF sestavených pomocí různých vazeb poskytovaných systémem.  
  
## <a name="load-balancing-with-the-basic-http-binding"></a>Vyrovnávání zatížení pomocí základní vazby HTTP  
 Z perspektivy vyrovnávání zatížení nejsou aplikace WCF, které komunikují pomocí <xref:System.ServiceModel.BasicHttpBinding>, jiné než jiné běžné typy síťového provozu HTTP (statický obsah HTML, stránky ASP.NET nebo webové služby ASMX). Kanály WCF, které používají tuto vazbu, jsou v podstatě bezstavové a ukončí jejich připojení při zavření kanálu. V takovém případě <xref:System.ServiceModel.BasicHttpBinding> dobře funguje s existujícími technikami vyrovnávání zatížení HTTP.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.BasicHttpBinding> pošle hlavičku HTTP připojení ve zprávách s hodnotou `Keep-Alive`, která klientům umožňuje navázat trvalá připojení ke službám, které je podporují. Tato konfigurace nabízí rozšířenou propustnost, protože dříve vytvořená připojení je možné znovu použít k odeslání dalších zpráv na stejný server. Opakované použití připojení může ale způsobit, že se klienti budou silně přidružit k určitému serveru v rámci farmy s vyrovnáváním zatížení, což snižuje efektivitu vyrovnávání zatížení pomocí kruhového dotazování. Pokud je toto chování nežádoucí, HTTP `Keep-Alive` můžete na serveru zakázat pomocí vlastnosti <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> s <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelsky definovaným <xref:System.ServiceModel.Channels.Binding>. Následující příklad ukazuje, jak to provést pomocí konfigurace.  
  
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
  
 Pomocí zjednodušené konfigurace zavedené v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] je možné dosáhnout stejného chování pomocí následující zjednodušené konfigurace.  
  
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
  
 Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](./samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a>Vyrovnávání zatížení s vazbou WSHttp a vazbou WSDualHttp  
 @No__t-0 i <xref:System.ServiceModel.WSDualHttpBinding> lze vyrovnávat zatížení pomocí technik vyrovnávání zatížení HTTP, který poskytuje několik úprav pro výchozí konfiguraci vazby.  
  
- Vypnutí vytváření kontextu zabezpečení: můžete to provést nastavením vlastnosti <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> v <xref:System.ServiceModel.WSHttpBinding> na `false`. Případně, pokud jsou vyžadovány relace zabezpečení, je možné použít stavové relace zabezpečení, jak je popsáno v tématu [zabezpečené relace](./feature-details/secure-sessions.md) . Stavové relace zabezpečení umožňují, aby služba zůstala Bezstavová, protože všechny stavy relace zabezpečení jsou přenášeny s každou žádostí jako součást tokenu zabezpečení ochrany. Počítejte s tím, že pokud chcete povolit stavovou relaci zabezpečení, je nutné použít <xref:System.ServiceModel.Channels.CustomBinding> nebo uživatelsky definované <xref:System.ServiceModel.Channels.Binding>, protože pro <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.WSDualHttpBinding> poskytované systémem nejsou k dispozici potřebná nastavení konfigurace.  
  
- Nepoužívejte spolehlivé relace. Tato funkce je ve výchozím nastavení vypnutá.  
  
## <a name="load-balancing-the-nettcp-binding"></a>Vyrovnávání zatížení vazby NET. TCP  
 @No__t-0 se dá vyrovnávat zatížení pomocí technik vyrovnávání zatížení vrstvy IP. Ve výchozím nastavení však fondy <xref:System.ServiceModel.NetTcpBinding> odpojovat připojení TCP, aby se snížila latence připojení. Toto je optimalizace, která brání základnímu mechanismu vyrovnávání zatížení. Primární hodnota konfigurace pro optimalizaci <xref:System.ServiceModel.NetTcpBinding> je časový limit zapůjčení, který je součástí nastavení fondu připojení. Sdružování připojení způsobí, že se připojení klienta stanou přidružená ke konkrétním serverům v rámci farmy. Jak se prodlouží doba trvání těchto připojení (faktor řízený nastavením časový limit zapůjčení), bude distribuce zatížení napříč různými servery ve farmě nevyvážená. V důsledku toho se zvýší průměrná doba volání. Takže pokud používáte <xref:System.ServiceModel.NetTcpBinding> ve scénářích s vyrovnáváním zatížení, zvažte snížení výchozího časového limitu zapůjčení používaného vazbou. Časový limit zapůjčení je 30 sekund přiměřeným výchozím bodem pro scénáře s vyrovnáváním zatížení, i když optimální hodnota je závislá na aplikaci. Další informace o vypršení časového limitu zapůjčení kanálu a dalších přenosových kvót najdete v tématu [přenosové kvóty](./feature-details/transport-quotas.md).  
  
 Pro dosažení nejlepšího výkonu ve scénářích s vyrovnáváním zatížení zvažte použití <xref:System.ServiceModel.NetTcpSecurity> (buď <xref:System.ServiceModel.SecurityMode.Transport> nebo <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).  
  
## <a name="see-also"></a>Viz také:

- [Osvědčené postupy hostování Internetové informační služby](./feature-details/internet-information-services-hosting-best-practices.md)
