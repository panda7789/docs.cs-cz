---
title: Architektura aktivace WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 71546bf6fb13c9d2fecf09b79460a953f60e4e3b
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465756"
---
# <a name="was-activation-architecture"></a>Architektura aktivace WAS
V tomto tématu najdete výčet a tento článek popisuje komponenty služby Aktivace procesu Windows (WAS).  
  
## <a name="activation-components"></a>Aktivace součásti  
 SE skládá z několika komponent architektury:  
  
-   Naslouchací proces adaptéry. Služby Windows, které přijímají zprávy na konkrétních síťových protokolech a komunikovat s WAS můžete směrovat příchozí zprávy správné pracovního procesu.  
  
-   BYLA. Služba Windows, která spravuje vytváření a dobu života pracovních procesů.  
  
-   Obecný pracovní proces spustitelný soubor (w3wp.exe).  
  
-   Správce aplikací. Spravuje vytváření a dobu života aplikační domény, které zpracovávají hostování aplikací v rámci pracovního procesu.  
  
-   Obslužné rutiny protokolu. Konkrétní součásti, které běží v procesu pracovního procesu a správu komunikace mezi pracovního procesu a adaptéry jednotlivý naslouchací proces. Existují dva typy obslužné rutiny protokolu: zpracování obslužné rutiny protokolu a obslužné rutiny protokolu domény aplikace.  
  
 Když služba WAS aktivuje instance procesu pracovního procesu, načítá obslužné rutiny protokolu procesu vyžaduje do pracovního procesu a používá správce aplikace pro vytvoření domény aplikace pro hostování aplikace. Doména aplikace načte kódu vaší aplikace, stejně jako obslužné rutiny protokolu domény aplikace, které používá síťové protokoly aplikace vyžadovat.  
  
 ![Snímek obrazovky zobrazující architektura WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptéry naslouchací proces  
 Naslouchací proces adaptéry jsou jednotlivé služby Windows, které implementují logiku komunikace sítě používá pro příjem zpráv pomocí síťového protokolu se naslouchat. V následující tabulce jsou uvedeny adaptéry naslouchací proces pro protokoly Windows Communication Foundation (WCF).  
  
|Název služby adaptér naslouchací proces|Protocol (Protokol)|Poznámky|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|Běžné komponenty, která poskytuje Aktivace protokolem HTTP pro internetové informační služby 7.0 nebo WCF.|  
|NetTcpActivator|net.tcp|Závisí na konfiguraci služby NetTcpPortSharing službě.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|Pro použití s aplikací na základě WCF služby Řízení front zpráv.|  
|NetMsmqActivator|msmq.formatname|Poskytuje zpětné kompatibilitě se stávajícími aplikacemi služby Řízení front zpráv.|  
  
 Adaptéry naslouchací proces pro konkrétní protokoly jsou registrovány během instalace v souboru applicationHost.config, jak je znázorněno v následujícím příkladu XML.  
  
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
 Proces a obslužné rutiny protokolu domény aplikace pro konkrétní protokoly jsou registrované v souboru Web.config úrovni počítače.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Konfigurace WAS pro použití s WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Hostování funkcí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
