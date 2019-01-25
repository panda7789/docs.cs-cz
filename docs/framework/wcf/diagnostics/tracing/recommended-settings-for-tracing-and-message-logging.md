---
title: Doporučené nastavení pro trasování a protokolování zpráv
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: dff4b20547cccca628ac76afc890a2817e838907
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585208"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Doporučené nastavení pro trasování a protokolování zpráv
Toto téma popisuje doporučené trasování a protokolování nastavení zpráv pro různé provozní prostředí.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Doporučená nastavení pro produkční prostředí  
 Pro produkční prostředí, pokud používáte zdrojů trasování WCF, nastavte `switchValue` na upozornění. Pokud používáte WCF `System.ServiceModel` trasování, nastavte `switchValue` atribut `Warning` a `propagateActivity` atribut `true`. Pokud používáte zdroj trasování definovaný uživatelem, nastaví `switchValue` atribut `Warning, ActivityTracing`. To lze provést ručně pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). Pokud očekáváte není dosaženo výkon, můžete nastavit `switchValue` atribut `Information` v všechny výše uvedené případy, které generují poměrně velké množství dat trasování. Následující příklad ukazuje doporučené nastavení.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Doporučená nastavení pro nasazení a ladění  
 Nasazení a prostředí ladění, zvolte `Information` nebo `Verbose`, spolu s `ActivityTracing` pro buď definovanou uživatelem nebo `System.ServiceModel` zdroje trasování. Aby vylepšila, ladění, měli byste také přidat zdroj další trasování (`System.ServiceModel.MessageLogging`) ke konfiguraci povolit protokolování zpráv. Všimněte si, že `switchValue` atribut nemá žádný vliv na tento zdroj trasování.  
  
 Následující příklad ukazuje doporučené nastavení, pomocí sdílené naslouchací proces, který využívá `XmlWriterTraceListener`.  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Chcete-li změnit nastavení pomocí rozhraní WMI  
 Chcete-li změnit nastavení konfigurace za běhu můžete použít rozhraní WMI (tím, že `wmiProviderEnabled` atribut v konfiguraci, jak je ukázáno v dříve konfigurace – příklad). Například můžete použít v rámci nástroje CIM Studio WMI změnit úrovně zdroj trasování z varování na informace v době běhu. Byste měli vědět, že může být velmi vysoké náklady na živé ladění tímto způsobem. Další informace o používání služby WMI najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tématu.  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Povolit Korelačních událostí v trasování rozhraní ASP.NET  
 ASP.NET – události nenastavujte ID korelace (ActivityID), pokud je zapnutá trasování událostí pro technologii ASP.NET. Zobrazit korelační události správně, budete muset zapnout ASP.NET – události trasování, pomocí následujícího příkazu v příkazové konzole, který lze vyvolat tak, že přejdete do **Start**, **spustit** a typ **cmd** ,  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Chcete-li vypnout trasování událostí pro technologii ASP.NET, použijte následující příkaz,  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Viz také:
- [Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
