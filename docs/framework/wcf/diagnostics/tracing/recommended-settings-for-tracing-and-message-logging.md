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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="bbe76-102">Doporučené nastavení pro trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="bbe76-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="bbe76-103">Toto téma popisuje doporučené nastavení trasování a protokolování zpráv pro různá operační prostředí.</span><span class="sxs-lookup"><span data-stu-id="bbe76-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="bbe76-104">Doporučená nastavení pro produkční prostředí</span><span class="sxs-lookup"><span data-stu-id="bbe76-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="bbe76-105">Pro produkční prostředí, pokud používáte WCF trasovací zdroje, nastavte `switchValue` upozornění.</span><span class="sxs-lookup"><span data-stu-id="bbe76-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="bbe76-106">Pokud používáte zdroj `System.ServiceModel` trasování WCF, nastavte `switchValue` `propagateActivity` atribut `true` `Warning` a atribut na .</span><span class="sxs-lookup"><span data-stu-id="bbe76-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="bbe76-107">Pokud používáte uživatelem definovaný zdroj trasování, nastavte `switchValue` atribut na `Warning, ActivityTracing`.</span><span class="sxs-lookup"><span data-stu-id="bbe76-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="bbe76-108">To lze provést ručně pomocí [nástroje Editor konfigurace (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="bbe76-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="bbe76-109">Pokud neočekáváte požadavek na dosažení výkonu, `switchValue` můžete `Information` nastavit atribut ve všech výše uvedených případech, které generuje poměrně velké množství dat trasování.</span><span class="sxs-lookup"><span data-stu-id="bbe76-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="bbe76-110">Následující příklad ukazuje tato doporučená nastavení.</span><span class="sxs-lookup"><span data-stu-id="bbe76-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="bbe76-111">Doporučená nastavení pro nasazení nebo ladění</span><span class="sxs-lookup"><span data-stu-id="bbe76-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="bbe76-112">Pro prostředí nasazení nebo ladění `Information` zvolte `Verbose`nebo `ActivityTracing` spolu s pro `System.ServiceModel` uživatelem definovaný zdroj nebo zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="bbe76-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="bbe76-113">Chcete-li zlepšit ladění, měli byste také přidat`System.ServiceModel.MessageLogging`další zdroj trasování ( ) do konfigurace povolit protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="bbe76-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="bbe76-114">Všimněte `switchValue` si, že atribut nemá žádný vliv na tento zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="bbe76-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="bbe76-115">Následující příklad ukazuje doporučená nastavení pomocí sdíleného naslouchací proces, který využívá `XmlWriterTraceListener`.</span><span class="sxs-lookup"><span data-stu-id="bbe76-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="bbe76-116">Změna nastavení pomocí služby WMI</span><span class="sxs-lookup"><span data-stu-id="bbe76-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="bbe76-117">Službu WMI můžete použít ke změně nastavení `wmiProviderEnabled` konfigurace za běhu (povolením atributu v konfiguraci, jak je znázorněno v předchozím příkladu konfigurace).</span><span class="sxs-lookup"><span data-stu-id="bbe76-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="bbe76-118">Pomocí technologie WMI v rámci aplikace CIM Studio můžete například změnit úrovně zdroje trasování z upozornění na informace za běhu.</span><span class="sxs-lookup"><span data-stu-id="bbe76-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="bbe76-119">Měli byste si být vědomi toho, že náklady na výkon živé ladění tímto způsobem může být velmi vysoká.</span><span class="sxs-lookup"><span data-stu-id="bbe76-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="bbe76-120">Další informace o použití služby WMI naleznete v tématu [Použití nástroje pro diagnostiku systému Windows.](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)</span><span class="sxs-lookup"><span data-stu-id="bbe76-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="bbe76-121">Povolit korelační události v ASP.NET trasování</span><span class="sxs-lookup"><span data-stu-id="bbe76-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="bbe76-122">ASP.NET události nenastavují ID korelace (ActivityID), pokud není zapnuto ASP.NET trasování událostí.</span><span class="sxs-lookup"><span data-stu-id="bbe76-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="bbe76-123">Chcete-li zobrazit korelační události správně, je třeba zapnout trasování událostí ASP.NET pomocí následujícího příkazu v konzole příkazů, který lze vyvolat tak, že přejdete na **Start**, **Run** a zadejte **cmd**,</span><span class="sxs-lookup"><span data-stu-id="bbe76-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="bbe76-124">Chcete-li vypnout trasování událostí ASP.NET, použijte následující příkaz,</span><span class="sxs-lookup"><span data-stu-id="bbe76-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbe76-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bbe76-125">See also</span></span>

- [<span data-ttu-id="bbe76-126">Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="bbe76-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
