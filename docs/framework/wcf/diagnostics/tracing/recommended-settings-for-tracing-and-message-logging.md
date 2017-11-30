---
title: "Doporučené nastavení pro trasování a protokolování zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b6986c775db50ea5b763288f8f3b9bdcf1bf7e67
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Doporučené nastavení pro trasování a protokolování zpráv
Toto téma popisuje doporučené trasování a nastavení protokolování zpráv pro různá provozní prostředí.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Doporučená nastavení pro produkční prostředí  
 Pro produkční prostředí, pokud používáte zdrojů trasování WCF, nastavte `switchValue` na upozornění. Pokud používáte WCF `System.ServiceModel` zdroj trasování, nastavte `switchValue` atribut `Warning` a `propagateActivity` atribut `true`. Pokud používáte zdroj trasování definovaný uživatelem, nastavte `switchValue` atribut `Warning, ActivityTracing`. To lze provést ručně pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Pokud očekáváte není podle výkonu, můžete nastavit `switchValue` atribut `Information` ve všech výše uvedených případech, který generuje poměrně velké množství dat trasování. Následující příklad ukazuje tyto doporučené nastavení.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Warning"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Warning, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Doporučená nastavení pro nasazení nebo ladění  
 Pro nasazení nebo ladění prostředí, zvolte `Information` nebo `Verbose`, spolu s `ActivityTracing` pro buď uživatelem definované nebo `System.ServiceModel` zdroj trasování. K vylepšení, ladění, měli byste také přidat na další trasování zdroj (`System.ServiceModel.MessageLogging`) ke konfiguraci povolit protokolování zpráv. Všimněte si, že `switchValue` atribut nemá žádný vliv na tento zdroj trasování.  
  
 Následující příklad ukazuje doporučená nastavení, pomocí sdílené naslouchací proces, který využívá `XmlWriterTraceListener`.  
  
```xml  
<configuration>  
 <system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel"  
            switchValue="Information, ActivityTracing"  
            propagateActivity="true" >  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
    <source name="myUserTraceSource"  
            switchValue="Information, ActivityTracing">  
      <listeners>  
        <add name="xml"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="xml"  
         type="System.Diagnostics.XmlWriterTraceListener"  
               initializeData="C:\logs\Traces.svclog" />  
  </sharedListeners>  
 </system.diagnostics>  
  
 <system.serviceModel>  
  <diagnostics wmiProviderEnabled="true">  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="true"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="true"  
           maxMessagesToLog="3000"   
       />  
  </diagnostics>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="using-wmi-to-modify-settings"></a>WMI používá k úpravě nastavení  
 Chcete-li změnit nastavení konfigurace v době běhu můžete použít rozhraní WMI (povolením `wmiProviderEnabled` atribut v konfiguraci, jak je předvedeno v dříve příklad konfigurace). Například můžete v rámci nástroje CIM Studio WMI Pokud chcete změnit úrovně zdroj trasování z upozornění na informace za běhu. Byste měli vědět, že mohou být velmi vysoký výkon náklady za provozu ladění tímto způsobem. Další informace o používání rozhraní WMI najdete v tématu [pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tématu.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Povolit korelační události v trasování rozhraní ASP.NET  
 Události ASP.NET nenastavujte ID korelace (ID), pokud je zapnutá trasování událostí ASP.NET. Zobrazte korelační události správně, budete muset zapnout ASP.NET události trasování, pomocí následujícího příkazu v konzole pro příkaz, který lze vyvolat přechodem na **spustit**, **spustit** a typ **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Chcete-li vypnout trasování událostí pro technologii ASP.NET, použijte následující příkaz,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Viz také  
 [Pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
