---
title: Doporučené nastavení pro trasování a protokolování zpráv
ms.date: 03/30/2017
ms.assetid: c6aca6e8-704e-4779-a9ef-50c46850249e
ms.openlocfilehash: fa6dc74a26f6a76591a15c549a892f31a65c521e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779727"
---
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="fdef1-102">Doporučené nastavení pro trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="fdef1-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="fdef1-103">Toto téma popisuje doporučené trasování a protokolování nastavení zpráv pro různé provozní prostředí.</span><span class="sxs-lookup"><span data-stu-id="fdef1-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="fdef1-104">Doporučená nastavení pro produkční prostředí</span><span class="sxs-lookup"><span data-stu-id="fdef1-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="fdef1-105">Pro produkční prostředí, pokud používáte zdrojů trasování WCF, nastavte `switchValue` na upozornění.</span><span class="sxs-lookup"><span data-stu-id="fdef1-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="fdef1-106">Pokud používáte WCF `System.ServiceModel` trasování, nastavte `switchValue` atribut `Warning` a `propagateActivity` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="fdef1-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="fdef1-107">Pokud používáte zdroj trasování definovaný uživatelem, nastaví `switchValue` atribut `Warning, ActivityTracing`.</span><span class="sxs-lookup"><span data-stu-id="fdef1-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="fdef1-108">To lze provést ručně pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fdef1-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="fdef1-109">Pokud očekáváte není dosaženo výkon, můžete nastavit `switchValue` atribut `Information` v všechny výše uvedené případy, které generují poměrně velké množství dat trasování.</span><span class="sxs-lookup"><span data-stu-id="fdef1-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="fdef1-110">Následující příklad ukazuje doporučené nastavení.</span><span class="sxs-lookup"><span data-stu-id="fdef1-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="fdef1-111">Doporučená nastavení pro nasazení a ladění</span><span class="sxs-lookup"><span data-stu-id="fdef1-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="fdef1-112">Nasazení a prostředí ladění, zvolte `Information` nebo `Verbose`, spolu s `ActivityTracing` pro buď definovanou uživatelem nebo `System.ServiceModel` zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="fdef1-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="fdef1-113">Aby vylepšila, ladění, měli byste také přidat zdroj další trasování (`System.ServiceModel.MessageLogging`) ke konfiguraci povolit protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="fdef1-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="fdef1-114">Všimněte si, že `switchValue` atribut nemá žádný vliv na tento zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="fdef1-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="fdef1-115">Následující příklad ukazuje doporučené nastavení, pomocí sdílené naslouchací proces, který využívá `XmlWriterTraceListener`.</span><span class="sxs-lookup"><span data-stu-id="fdef1-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="fdef1-116">Chcete-li změnit nastavení pomocí rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="fdef1-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="fdef1-117">Chcete-li změnit nastavení konfigurace za běhu můžete použít rozhraní WMI (tím, že `wmiProviderEnabled` atribut v konfiguraci, jak je ukázáno v dříve konfigurace – příklad).</span><span class="sxs-lookup"><span data-stu-id="fdef1-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="fdef1-118">Například můžete použít v rámci nástroje CIM Studio WMI změnit úrovně zdroj trasování z varování na informace v době běhu.</span><span class="sxs-lookup"><span data-stu-id="fdef1-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="fdef1-119">Byste měli vědět, že může být velmi vysoké náklady na živé ladění tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="fdef1-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="fdef1-120">Další informace o používání služby WMI najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="fdef1-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="fdef1-121">Povolit Korelačních událostí v trasování rozhraní ASP.NET</span><span class="sxs-lookup"><span data-stu-id="fdef1-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="fdef1-122">ASP.NET – události nenastavujte ID korelace (ActivityID), pokud je zapnutá trasování událostí pro technologii ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fdef1-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="fdef1-123">Zobrazit korelační události správně, budete muset zapnout ASP.NET – události trasování, pomocí následujícího příkazu v příkazové konzole, který lze vyvolat tak, že přejdete do **Start**, **spustit** a typ **cmd** ,</span><span class="sxs-lookup"><span data-stu-id="fdef1-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="fdef1-124">Chcete-li vypnout trasování událostí pro technologii ASP.NET, použijte následující příkaz,</span><span class="sxs-lookup"><span data-stu-id="fdef1-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```  
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="fdef1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fdef1-125">See also</span></span>

- [<span data-ttu-id="fdef1-126">Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)</span><span class="sxs-lookup"><span data-stu-id="fdef1-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/index.md)
