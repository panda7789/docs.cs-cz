---
title: Trasování pracovních postupů
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 27e56933043c9eb955500cdd1c5bbd06cb33bde8
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45591246"
---
# <a name="workflow-tracing"></a><span data-ttu-id="2d514-102">Trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="2d514-102">Workflow Tracing</span></span>
<span data-ttu-id="2d514-103">Trasování pracovních postupů nabízí způsob, jak k zaznamenání diagnostických informací s použitím rozhraní .NET Framework naslouchacích procesů trasování.</span><span class="sxs-lookup"><span data-stu-id="2d514-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="2d514-104">Trasování může povolit, pokud byl zjištěn problém s aplikací a zakázané znovu, až se problém vyřeší.</span><span class="sxs-lookup"><span data-stu-id="2d514-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="2d514-105">Existují dva způsoby, jak může povolit trasování ladění pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="2d514-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="2d514-106">Můžete je nakonfigurovat pomocí prohlížeče událostí trasování nebo můžete použít <xref:System.Diagnostics> k odesílání trasování událostí do souboru.</span><span class="sxs-lookup"><span data-stu-id="2d514-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="2d514-107">Povolení ladění trasování v trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="2d514-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="2d514-108">Pokud chcete povolit, trasování pomocí trasování událostí pro Windows, povolte ladění kanálu v prohlížeči událostí:</span><span class="sxs-lookup"><span data-stu-id="2d514-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1.  <span data-ttu-id="2d514-109">Přejděte do analýzy a ladit protokoly uzlu v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="2d514-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2.  <span data-ttu-id="2d514-110">Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí -> aplikace a služby protokoly -> Microsoft -> Windows -> aplikace Server-**.</span><span class="sxs-lookup"><span data-stu-id="2d514-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="2d514-111">Klikněte pravým tlačítkem na **aplikace Server-** a vyberte **zobrazení -> Zobrazit protokoly ladění a analýzu**.</span><span class="sxs-lookup"><span data-stu-id="2d514-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="2d514-112">Klikněte pravým tlačítkem na **ladění** a vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="2d514-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3.  <span data-ttu-id="2d514-113">Při spuštění pracovního postupu, ladění a trasování, které jsou emitovány do kanálu ladění trasování událostí pro Windows, můžete zobrazit v prohlížeči událostí.</span><span class="sxs-lookup"><span data-stu-id="2d514-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="2d514-114">Přejděte do **Prohlížeč událostí -> aplikace a služby protokoly -> Microsoft -> Windows -> aplikace Server-**.</span><span class="sxs-lookup"><span data-stu-id="2d514-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="2d514-115">Klikněte pravým tlačítkem na **ladění** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="2d514-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4.  <span data-ttu-id="2d514-116">Výchozí velikost vyrovnávací paměti analytického trasování je jenom 4 kilobajtů (KB); se doporučuje zvýšit velikost na 32 KB.</span><span class="sxs-lookup"><span data-stu-id="2d514-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="2d514-117">Chcete-li to provést, postupujte následovně.</span><span class="sxs-lookup"><span data-stu-id="2d514-117">To do this, perform the following steps.</span></span>  
  
    1.  <span data-ttu-id="2d514-118">V aktuálním adresáři rozhraní framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz: `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="2d514-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2.  <span data-ttu-id="2d514-119">Změnit \<bufferSize > hodnota v souboru Windows.ApplicationServer.Applications.man 32.</span><span class="sxs-lookup"><span data-stu-id="2d514-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  <span data-ttu-id="2d514-120">V aktuálním adresáři rozhraní framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz: `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="2d514-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d514-121">Pokud používáte rozhraní .NET Framework 4 Client Profile, musíte se nejprve zaregistrovat manifestu trasování událostí pro Windows spuštěním následujícího příkazu v adresáři rozhraní .NET Framework 4: `ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="2d514-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="2d514-122">Povolení ladění trasování System.Diagnostics pomocí</span><span class="sxs-lookup"><span data-stu-id="2d514-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="2d514-123">Tyto moduly pro naslouchání lze nastavit v souboru App.config aplikace pracovního postupu nebo soubor Web.config pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="2d514-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="2d514-124">V tomto příkladu [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) je nakonfigurovaný k ukládání informací o trasování do souboru MyTraceLog.txt v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="2d514-124">In this example, a [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d514-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d514-125">See Also</span></span>  
 [<span data-ttu-id="2d514-126">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="2d514-126">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="2d514-127">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="2d514-127">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
