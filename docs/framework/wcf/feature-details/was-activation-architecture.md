---
title: Architektura aktivace WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184243"
---
# <a name="was-activation-architecture"></a>Architektura aktivace WAS
Toto téma rozepisuje a popisuje součásti služby aktivace procesů systému Windows (označované také jako WAS).  
  
## <a name="activation-components"></a>Aktivační součásti  
 WAS se skládá z několika architektonických složek:  
  
- Adaptéry naslouchacího procesu. Služby systému Windows, které přijímají zprávy na konkrétních síťových protokolech a komunikují s službou WAS směrovat příchozí zprávy do správného pracovního procesu.  
  
- Byl. Služba systému Windows, která spravuje vytváření a životnost pracovních procesů.  
  
- Spustitelný soubor obecného pracovního procesu (w3wp.exe).  
  
- Správce aplikací. Spravuje vytváření a životnost aplikačních domén, které hostují aplikace v rámci pracovního procesu.  
  
- Obslužné rutiny protokolu. Součásti specifické pro protokol, které se spouštějí v pracovním procesu a spravují komunikaci mezi pracovníproces a adaptéry jednotlivých naslouchacích procesů. Existují dva typy obslužných rutin protokolu: obslužné rutiny protokolu procesu a obslužné rutiny protokolu AppDomain.  
  
 Když služba WAS aktivuje instanci pracovního procesu, načte obslužné rutiny protokolu procesu požadované do pracovního procesu a pomocí správce aplikací vytvoří doménu aplikace pro hostování aplikace. Doména aplikace načte kód aplikace a obslužné rutiny protokolu AppDomain, které vyžadují síťové protokoly používané aplikací.  
  
 ![Snímek obrazovky, který zobrazuje architekturu WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptéry posluchače  
 Naslouchací proces adaptéry jsou jednotlivé služby systému Windows, které implementují logiku síťové komunikace používané k přijímání zpráv pomocí síťového protokolu, na kterém naslouchají. V následující tabulce jsou uvedeny adaptéry naslouchacího procesu pro protokoly WCF (Windows Communication Foundation).  
  
|Název služby adaptéru naslouchacího procesu|Protocol (Protokol)|Poznámky|  
|-----------------------------------|--------------|-----------|  
|W3svc|HTTP|Běžná součást, která poskytuje aktivaci protokolu HTTP pro iis 7.0 a WCF.|  
|NetTcpAktivátor|net.tcp|Závisí na službě NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqAktivátor|net.msmq|Pro použití s aplikacemi služby Řízení front zpráv založených na wcf.|  
|NetMsmqAktivátor|název formátu msmq.|Poskytuje zpětnou kompatibilitu s existujícími aplikacemi služby Řízení front zpráv.|  
  
 Adaptéry naslouchacího procesu pro určité protokoly jsou registrovány během instalace v souboru applicationHost.config, jak je znázorněno v následujícím příkladu XML.  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a>Obslužné rutiny protokolu  
 Obslužné rutiny protokolu Process a AppDomain pro určité protokoly jsou registrovány v souboru Web.config na úrovni počítače.  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a>Viz také

- [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Funkce hostování prostředků pro aplikace systému Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
