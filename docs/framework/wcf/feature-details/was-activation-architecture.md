---
title: Architektura aktivace WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 0c91ebd605fbe503dd11da7167512648afd86449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="was-activation-architecture"></a>Architektura aktivace WAS
Toto téma rozepisuje a součástí aktivační služba procesů systému Windows (WAS).  
  
## <a name="activation-components"></a>Aktivace součásti  
 SE skládá z několika součástí architektury:  
  
-   Naslouchací proces adaptéry. Služby systému Windows, které přijímat zprávy na konkrétních síťových protokolech a komunikovat se službou WAS pro směrování příchozích zpráv do správné pracovního procesu.  
  
-   BYLA. Služba systému Windows, která spravuje vytváření a dobu života pracovních procesů.  
  
-   Obecný pracovní proces spustitelný soubor (w3wp.exe).  
  
-   Správce aplikací. Spravuje vytváření a dobu života aplikační domény, které zpracovávají hostování aplikací v rámci pracovního procesu.  
  
-   Obslužné rutiny protokolu. Protokol konkrétní součásti, které spustit v pracovním procesu a spravovat komunikaci mezi pracovního procesu a adaptéry pro jednotlivé naslouchací proces. Existují dva typy obslužných rutin protokolů: zpracovat obslužných rutin protokolů a obslužných rutin protokolů doménu aplikace.  
  
 Když WAS aktivuje instance procesu pracovního procesu, obslužné rutiny protokolu proces vyžaduje do pracovní proces načítá a používá k vytvoření domény aplikace k hostování aplikace Správce aplikací. Doména aplikace načte kódu aplikace a také protokol AppDomain obslužných rutin, které používá síťové protokoly aplikace potřebují.  
  
 ![Architektura byla](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")  
  
### <a name="listener-adapters"></a>Naslouchací proces adaptéry  
 Naslouchací proces adaptéry jsou jednotlivé služby systému Windows, které implementují logiku komunikace sítě slouží k přijímání zpráv pomocí síťového protokolu, na kterém naslouchat. Následující tabulka uvádí adaptéry naslouchací proces pro protokoly systému Windows Communication Foundation (WCF).  
  
|Název služby adaptér naslouchání|Protokol|Poznámky|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|Běžné komponenta, která poskytuje aktivace protokolu HTTP pro službu IIS 7.0 a WCF.|  
|NetTcpActivator|net.tcp|Závisí na službě NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|NET.MSMQ|Pro použití s aplikacemi na základě WCF služby Řízení front zpráv.|  
|NetMsmqActivator|MSMQ.formatname|Poskytuje zpětné kompatibilitě se stávajícími aplikacemi služby Řízení front zpráv.|  
  
 Adaptéry naslouchací proces pro konkrétní protokoly jsou registrované během instalace v souboru applicationHost.config, jak je znázorněno v následujícím příkladu kódu XML.  
  
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
 Proces a obslužných rutin protokolů doménu aplikace pro konkrétní protokoly jsou zaregistrovány v souboru Web.config úrovni počítače.  
  
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
 [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Hostování funkcí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
