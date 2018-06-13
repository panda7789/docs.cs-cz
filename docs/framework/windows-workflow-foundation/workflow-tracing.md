---
title: Pracovní postup trasování
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: f4ce25efae0e42fa7c95ce5dffe8da8e31db05a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518174"
---
# <a name="workflow-tracing"></a><span data-ttu-id="c69c3-102">Pracovní postup trasování</span><span class="sxs-lookup"><span data-stu-id="c69c3-102">Workflow Tracing</span></span>
<span data-ttu-id="c69c3-103">Pracovní postup trasování nabízí způsob, jak zachytit diagnostických informací s použitím rozhraní .NET Framework trasování – moduly naslouchání.</span><span class="sxs-lookup"><span data-stu-id="c69c3-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="c69c3-104">Trasování můžete povolit, pokud se zjistí problém s aplikací a zakázané znovu, jakmile je problém vyřešen.</span><span class="sxs-lookup"><span data-stu-id="c69c3-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="c69c3-105">Existují dva způsoby, které může povolit trasování ladění pro pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="c69c3-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="c69c3-106">Můžete nakonfigurovat pomocí prohlížeče událostí trasování, nebo můžete použít <xref:System.Diagnostics> odesílat události trasování do souboru.</span><span class="sxs-lookup"><span data-stu-id="c69c3-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="c69c3-107">Povolení ladění, trasování v trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="c69c3-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="c69c3-108">Pokud chcete povolit trasování pomocí trasování událostí pro Windows, povolte ladění kanál v prohlížeči událostí:</span><span class="sxs-lookup"><span data-stu-id="c69c3-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1.  <span data-ttu-id="c69c3-109">Přejděte na analytické a ladicí uzlu protokoly v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="c69c3-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2.  <span data-ttu-id="c69c3-110">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí -> aplikace a protokoly služby -> Microsoft -> Windows -> serveru aplikace – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="c69c3-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="c69c3-111">Klikněte pravým tlačítkem na **serveru aplikace – aplikace** a vyberte **-zobrazení > Zobrazit protokoly pro ladění a**.</span><span class="sxs-lookup"><span data-stu-id="c69c3-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="c69c3-112">Klikněte pravým tlačítkem na **ladění** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="c69c3-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3.  <span data-ttu-id="c69c3-113">Při spuštění pracovního postupu ladění a trasování jsou vygenerované kanálu ladění, trasování událostí pro Windows, lze zobrazit v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="c69c3-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="c69c3-114">Přejděte na **Prohlížeč událostí -> aplikace a protokoly služby -> Microsoft -> Windows -> serveru aplikace – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="c69c3-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="c69c3-115">Klikněte pravým tlačítkem na **ladění** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="c69c3-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4.  <span data-ttu-id="c69c3-116">Výchozí velikost vyrovnávací paměti analytického trasování je jenom 4 kilobajtů (KB); Doporučujeme zvýšit velikost 32 KB.</span><span class="sxs-lookup"><span data-stu-id="c69c3-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="c69c3-117">Chcete-li to provést, proveďte následující kroky.</span><span class="sxs-lookup"><span data-stu-id="c69c3-117">To do this, perform the following steps.</span></span>  
  
    1.  <span data-ttu-id="c69c3-118">V aktuálním adresáři framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz: `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="c69c3-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2.  <span data-ttu-id="c69c3-119">Změna \<bufferSize > v souboru Windows.ApplicationServer.Applications.man 32 znaků. hodnota.</span><span class="sxs-lookup"><span data-stu-id="c69c3-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  <span data-ttu-id="c69c3-120">V aktuálním adresáři framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz: `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="c69c3-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c69c3-121">Pokud používáte profil klienta rozhraní .NET Framework 4, je nutné zaregistrovat manifest trasování událostí pro Windows tak, že spustíte následující příkaz z adresáře, rozhraní .NET Framework 4: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="c69c3-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="c69c3-122">Povolení ladění trasování pomocí System.Diagnostics</span><span class="sxs-lookup"><span data-stu-id="c69c3-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="c69c3-123">Tyto moduly pro naslouchání lze nakonfigurovat v souboru App.config pracovní postup aplikace nebo souboru Web.config pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="c69c3-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="c69c3-124">V tomto příkladu [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424) nakonfigurovaný tak, aby se uložily informace o trasování do souboru MyTraceLog.txt v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="c69c3-124">In this example, a [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="System.Activities" switchValue="Information">  
        <listeners>  
          <add name="textListener" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"  
           type="System.Diagnostics.TextWriterTraceListener"  
           initializeData="MyTraceLog.txt"  
           traceOutputOptions="ProcessId, DateTime" />  
    </sharedListeners>  
    <trace autoflush="true" indentsize="4">  
      <listeners>  
        <add name="textListener" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c69c3-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c69c3-125">See Also</span></span>  
 [<span data-ttu-id="c69c3-126">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="c69c3-126">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="c69c3-127">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="c69c3-127">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
