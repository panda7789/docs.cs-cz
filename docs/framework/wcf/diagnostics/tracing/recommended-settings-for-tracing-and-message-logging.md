---
title: Doporučené nastavení pro trasování a protokolování zpráv
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: 9d2586570a3f590735c2a8e1ca176580886c8d92
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578913"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a>Doporučené nastavení pro trasování a protokolování zpráv
Toto téma popisuje doporučené trasování a nastavení protokolování zpráv pro různá operační prostředí.  
  
## <a name="recommended-settings-for-a-production-environment"></a>Doporučené nastavení pro produkční prostředí  
 V případě produkčního prostředí, pokud používáte zdroje trasování WCF, nastavte na `switchValue` upozornění. Pokud používáte `System.ServiceModel` zdroj trasování WCF, nastavte `switchValue` atribut na `Warning` a `propagateActivity` atribut na `true` . Pokud používáte zdroj trasování definovaný uživatelem, nastavte `switchValue` atribut na `Warning, ActivityTracing` . To lze provést ručně pomocí [nástroje Configuration Editor (SvcConfigEditor. exe)](../../configuration-editor-tool-svcconfigeditor-exe.md). Pokud nepředpokládáte, že dojde ke zvýšení výkonu, můžete nastavit `switchValue` atribut na `Information` ve všech dříve uvedených případech, které generují poměrně velký objem dat trasování. Následující příklad znázorňuje Tato doporučená nastavení.  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a>Doporučené nastavení pro nasazení nebo ladění  
 Pro prostředí nasazení nebo ladění vyberte možnost `Information` nebo `Verbose` , společně s `ActivityTracing` pro uživatelem definovaný nebo `System.ServiceModel` zdroj trasování. Chcete-li zlepšit ladění, měli byste také přidat další zdroj trasování ( `System.ServiceModel.MessageLogging` ) do konfigurace, aby bylo možné protokolování zpráv povolit. Všimněte si, že `switchValue` atribut nemá žádný vliv na tento zdroj trasování.  
  
 Následující příklad ukazuje Doporučené nastavení pomocí sdíleného naslouchacího procesu, který využívá rozhraní `XmlWriterTraceListener` .  
  
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
  
## <a name="using-wmi-to-modify-settings"></a>Úprava nastavení pomocí rozhraní WMI  
 Rozhraní WMI můžete použít ke změně nastavení konfigurace za běhu (povolením `wmiProviderEnabled` atributu v konfiguraci, jak je znázorněno v předchozím příkladu konfigurace). Pomocí rozhraní WMI v rámci CIM Studio můžete například změnit úrovně zdroje trasování z upozornění na informace za běhu. Měli byste si uvědomit, že náklady na výkon živého ladění tímto způsobem můžou být velmi vysoké. Další informace o používání rozhraní WMI naleznete v tématu [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](../wmi/index.md) .  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a>Povolit korelační události v trasování ASP.NET  
 ASP.NET události nenastaví korelační ID (ActivityID), pokud není zapnuté trasování událostí ASP.NET. Chcete-li zobrazit korelační události správně, je nutné zapnout trasování událostí ASP.NET pomocí následujícího příkazu v konzole příkazů, který lze vyvolat spuštěním příkazu **Start**, **Run** a Type **cmd**.  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 Pokud chcete vypnout trasování událostí ASP.NET, použijte následující příkaz:  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a>Viz také

- [Použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](../wmi/index.md)
