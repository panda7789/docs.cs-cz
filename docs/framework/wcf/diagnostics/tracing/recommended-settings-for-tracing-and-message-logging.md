---
title: Doporučené nastavení pro trasování a protokolování zpráv
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 604aae2c0a0c5390428e7f1a2c99e17e90ee76a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185732"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Doporučené nastavení pro trasování a protokolování zpráv
Toto téma popisuje doporučené nastavení trasování a protokolování zpráv pro různá operační prostředí.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Doporučená nastavení pro produkční prostředí  
 Pro produkční prostředí, pokud používáte WCF trasovací zdroje, nastavte `switchValue` upozornění. Pokud používáte zdroj `System.ServiceModel` trasování WCF, nastavte `switchValue` `propagateActivity` atribut `true` `Warning` a atribut na . Pokud používáte uživatelem definovaný zdroj trasování, nastavte `switchValue` atribut na `Warning, ActivityTracing`. To lze provést ručně pomocí [nástroje Editor konfigurace (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Pokud neočekáváte požadavek na dosažení výkonu, `switchValue` můžete `Information` nastavit atribut ve všech výše uvedených případech, které generuje poměrně velké množství dat trasování. Následující příklad ukazuje tato doporučená nastavení.  
  
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
 Pro prostředí nasazení nebo ladění `Information` zvolte `Verbose`nebo `ActivityTracing` spolu s pro `System.ServiceModel` uživatelem definovaný zdroj nebo zdroj trasování. Chcete-li zlepšit ladění, měli byste také přidat`System.ServiceModel.MessageLogging`další zdroj trasování ( ) do konfigurace povolit protokolování zpráv. Všimněte `switchValue` si, že atribut nemá žádný vliv na tento zdroj trasování.  
  
 Následující příklad ukazuje doporučená nastavení pomocí sdíleného naslouchací proces, který využívá `XmlWriterTraceListener`.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Změna nastavení pomocí služby WMI  
 Službu WMI můžete použít ke změně nastavení `wmiProviderEnabled` konfigurace za běhu (povolením atributu v konfiguraci, jak je znázorněno v předchozím příkladu konfigurace). Pomocí technologie WMI v rámci aplikace CIM Studio můžete například změnit úrovně zdroje trasování z upozornění na informace za běhu. Měli byste si být vědomi toho, že náklady na výkon živé ladění tímto způsobem může být velmi vysoká. Další informace o použití služby WMI naleznete v tématu [Použití nástroje pro diagnostiku systému Windows.](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Povolit korelační události v ASP.NET trasování  
 ASP.NET události nenastavují ID korelace (ActivityID), pokud není zapnuto ASP.NET trasování událostí. Chcete-li zobrazit korelační události správně, je třeba zapnout trasování událostí ASP.NET pomocí následujícího příkazu v konzole příkazů, který lze vyvolat tak, že přejdete na **Start**, **Run** a zadejte **cmd**,  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Chcete-li vypnout trasování událostí ASP.NET, použijte následující příkaz,  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Viz také

- [Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
