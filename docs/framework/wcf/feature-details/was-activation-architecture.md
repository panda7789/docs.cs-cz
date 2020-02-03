---
title: Architektura aktivace WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 01c30db1182ece6dd968b69cc4efcaa2d9fabd79
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737511"
---
# <a name="was-activation-architecture"></a>Architektura aktivace WAS
Toto téma rozepisuje a popisuje komponenty aktivační služby procesů systému Windows (označované také jako).  
  
## <a name="activation-components"></a>Aktivační součásti  
 Se skládá z několika součástí architektury:  
  
- Adaptéry naslouchacího procesu. Služby systému Windows, které přijímají zprávy o konkrétních síťových protokolech a komunikují se službou WAS ke směrování příchozích zpráv do správného pracovního procesu.  
  
- Vytvořen. Služba systému Windows, která spravuje vytváření a životnost pracovních procesů.  
  
- Obecný spustitelný soubor pracovního procesu (W3wp. exe).  
  
- Správce aplikací. Spravuje vytváření a životnost aplikačních domén, které hostují aplikace v rámci pracovního procesu.  
  
- Obslužné rutiny protokolu. Komponenty specifické pro protokol, které se spouštějí v pracovním procesu a spravují komunikaci mezi pracovním procesem a jednotlivými adaptéry naslouchacího procesu. Existují dva typy obslužných rutin protokolu: obslužné rutiny protokolu procesu a obslužné rutiny protokolu AppDomain.  
  
 Když nástroj aktivoval instanci pracovního procesu, načte obslužné rutiny protokolu procesu požadované do pracovního procesu a pomocí Správce aplikací vytvoří doménu aplikace pro hostování aplikace. Doména aplikace načte kód aplikace a také obslužné rutiny protokolu AppDomain, které vyžadují síťové protokoly používané aplikací.  
  
 ![Snímek obrazovky znázorňující architekturu](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptéry naslouchacího procesu  
 Adaptéry naslouchacího procesu jsou jednotlivé služby systému Windows, které implementují logiku síťové komunikace používané pro příjem zpráv pomocí síťového protokolu, na kterém naslouchá. V následující tabulce jsou uvedeny adaptéry naslouchacího procesu pro protokoly Windows Communication Foundation (WCF).  
  
|Název služby adaptéru naslouchacího procesu|Protocol (Protokol)|Poznámky:|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|Společná součást, která poskytuje aktivaci protokolem HTTP pro IIS 7,0 a WCF.|  
|NetTcpActivator|net.tcp|Závisí na službě NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|NET. MSMQ|Pro použití s aplikacemi služby Řízení front zpráv založeným na WCF.|  
|NetMsmqActivator|MSMQ. FormatName|Poskytuje zpětnou kompatibilitu se stávajícími aplikacemi služby Řízení front zpráv.|  
  
 Adaptéry naslouchacího procesu pro konkrétní protokoly jsou registrovány během instalace v souboru applicationHost. config, jak je znázorněno v následujícím příkladu jazyka XML.  
  
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
 Obslužné rutiny protokolu procesů a AppDomain pro konkrétní protokoly jsou registrovány v souboru Web. config na úrovni počítače.  
  
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
- [Funkce hostování technologie Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
