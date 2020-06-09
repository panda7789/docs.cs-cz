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
# <a name="recommended-settings-for-tracing-and-message-logging"></a><span data-ttu-id="50331-102">Doporučené nastavení pro trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="50331-102">Recommended Settings for Tracing and Message Logging</span></span>
<span data-ttu-id="50331-103">Toto téma popisuje doporučené trasování a nastavení protokolování zpráv pro různá operační prostředí.</span><span class="sxs-lookup"><span data-stu-id="50331-103">This topic describes recommended tracing and message logging settings for different operating environments.</span></span>  
  
## <a name="recommended-settings-for-a-production-environment"></a><span data-ttu-id="50331-104">Doporučené nastavení pro produkční prostředí</span><span class="sxs-lookup"><span data-stu-id="50331-104">Recommended Settings for a Production Environment</span></span>  
 <span data-ttu-id="50331-105">V případě produkčního prostředí, pokud používáte zdroje trasování WCF, nastavte na `switchValue` upozornění.</span><span class="sxs-lookup"><span data-stu-id="50331-105">For a production environment, if you are using WCF trace sources, set the `switchValue` to Warning.</span></span> <span data-ttu-id="50331-106">Pokud používáte `System.ServiceModel` zdroj trasování WCF, nastavte `switchValue` atribut na `Warning` a `propagateActivity` atribut na `true` .</span><span class="sxs-lookup"><span data-stu-id="50331-106">If you are using the WCF `System.ServiceModel` trace source, set the `switchValue` attribute to `Warning` and the `propagateActivity` attribute to `true`.</span></span> <span data-ttu-id="50331-107">Pokud používáte zdroj trasování definovaný uživatelem, nastavte `switchValue` atribut na `Warning, ActivityTracing` .</span><span class="sxs-lookup"><span data-stu-id="50331-107">If you are using a user-defined trace source, set the `switchValue` attribute to `Warning, ActivityTracing`.</span></span> <span data-ttu-id="50331-108">To lze provést ručně pomocí [nástroje Configuration Editor (SvcConfigEditor. exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="50331-108">This can be done manually using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../configuration-editor-tool-svcconfigeditor-exe.md).</span></span> <span data-ttu-id="50331-109">Pokud nepředpokládáte, že dojde ke zvýšení výkonu, můžete nastavit `switchValue` atribut na `Information` ve všech dříve uvedených případech, které generují poměrně velký objem dat trasování.</span><span class="sxs-lookup"><span data-stu-id="50331-109">If you do not anticipate a hit in performance, you can set the `switchValue` attribute to `Information` in all the previously mentioned cases, which generates a fairly large amount of trace data.</span></span> <span data-ttu-id="50331-110">Následující příklad znázorňuje Tato doporučená nastavení.</span><span class="sxs-lookup"><span data-stu-id="50331-110">The following example demonstrates these recommended settings.</span></span>  
  
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
  
## <a name="recommended-settings-for-deployment-or-debugging"></a><span data-ttu-id="50331-111">Doporučené nastavení pro nasazení nebo ladění</span><span class="sxs-lookup"><span data-stu-id="50331-111">Recommended Settings for Deployment or Debugging</span></span>  
 <span data-ttu-id="50331-112">Pro prostředí nasazení nebo ladění vyberte možnost `Information` nebo `Verbose` , společně s `ActivityTracing` pro uživatelem definovaný nebo `System.ServiceModel` zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="50331-112">For deployment or debugging environment, choose `Information` or `Verbose`, along with `ActivityTracing` for either a user-defined or `System.ServiceModel` trace source.</span></span> <span data-ttu-id="50331-113">Chcete-li zlepšit ladění, měli byste také přidat další zdroj trasování ( `System.ServiceModel.MessageLogging` ) do konfigurace, aby bylo možné protokolování zpráv povolit.</span><span class="sxs-lookup"><span data-stu-id="50331-113">To enhance debugging, you should also add an additional trace source (`System.ServiceModel.MessageLogging`) to the configuration to enable message logging.</span></span> <span data-ttu-id="50331-114">Všimněte si, že `switchValue` atribut nemá žádný vliv na tento zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="50331-114">Notice that the `switchValue` attribute has no impact on this trace source.</span></span>  
  
 <span data-ttu-id="50331-115">Následující příklad ukazuje Doporučené nastavení pomocí sdíleného naslouchacího procesu, který využívá rozhraní `XmlWriterTraceListener` .</span><span class="sxs-lookup"><span data-stu-id="50331-115">The following example demonstrates the recommended settings, using a shared listener that utilizes the `XmlWriterTraceListener`.</span></span>  
  
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
  
## <a name="using-wmi-to-modify-settings"></a><span data-ttu-id="50331-116">Úprava nastavení pomocí rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="50331-116">Using WMI to Modify Settings</span></span>  
 <span data-ttu-id="50331-117">Rozhraní WMI můžete použít ke změně nastavení konfigurace za běhu (povolením `wmiProviderEnabled` atributu v konfiguraci, jak je znázorněno v předchozím příkladu konfigurace).</span><span class="sxs-lookup"><span data-stu-id="50331-117">You can use WMI to change configuration settings at runtime (by enabling the `wmiProviderEnabled` attribute in the configuration, as demonstrated in the previously configuration example).</span></span> <span data-ttu-id="50331-118">Pomocí rozhraní WMI v rámci CIM Studio můžete například změnit úrovně zdroje trasování z upozornění na informace za běhu.</span><span class="sxs-lookup"><span data-stu-id="50331-118">For example, you can use WMI within the CIM Studio to change the trace source levels from Warning to Information at runtime.</span></span> <span data-ttu-id="50331-119">Měli byste si uvědomit, že náklady na výkon živého ladění tímto způsobem můžou být velmi vysoké.</span><span class="sxs-lookup"><span data-stu-id="50331-119">You should be aware that the performance cost of live debugging in this way can be very high.</span></span> <span data-ttu-id="50331-120">Další informace o používání rozhraní WMI naleznete v tématu [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](../wmi/index.md) .</span><span class="sxs-lookup"><span data-stu-id="50331-120">For more information about using WMI, see the [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md) topic.</span></span>  
  
## <a name="enable-correlated-events-in-aspnet-tracing"></a><span data-ttu-id="50331-121">Povolit korelační události v trasování ASP.NET</span><span class="sxs-lookup"><span data-stu-id="50331-121">Enable Correlated Events in ASP.NET Tracing</span></span>  
 <span data-ttu-id="50331-122">ASP.NET události nenastaví korelační ID (ActivityID), pokud není zapnuté trasování událostí ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="50331-122">ASP.NET events do not set the correlation ID (ActivityID) unless ASP.NET event tracing is turned on.</span></span> <span data-ttu-id="50331-123">Chcete-li zobrazit korelační události správně, je nutné zapnout trasování událostí ASP.NET pomocí následujícího příkazu v konzole příkazů, který lze vyvolat spuštěním příkazu **Start**, **Run** a Type **cmd**.</span><span class="sxs-lookup"><span data-stu-id="50331-123">To see correlated events properly, you have to turn on ASP.NET events tracing using the following command in the command console, which can be invoked by going to **Start**, **Run** and type **cmd**,</span></span>  
  
```console  
logman start mytrace -pf logman.providers -o test.etl –ets  
```  
  
 <span data-ttu-id="50331-124">Pokud chcete vypnout trasování událostí ASP.NET, použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="50331-124">To turn off tracing of ASP.NET events, use the following command,</span></span>  
  
```console
logman stop mytrace -ets  
```  
  
## <a name="see-also"></a><span data-ttu-id="50331-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="50331-125">See also</span></span>

- [<span data-ttu-id="50331-126">Použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku</span><span class="sxs-lookup"><span data-stu-id="50331-126">Using Windows Management Instrumentation for Diagnostics</span></span>](../wmi/index.md)
