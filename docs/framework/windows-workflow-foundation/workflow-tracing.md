---
title: Trasování pracovních postupů
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 7bca78b24963d94bfa0f2e2245a677b7dce455c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933443"
---
# <a name="workflow-tracing"></a><span data-ttu-id="63917-102">Trasování pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="63917-102">Workflow Tracing</span></span>
<span data-ttu-id="63917-103">Trasování pracovního postupu nabízí způsob, jak zachytit diagnostické informace pomocí posluchačů trasování .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="63917-103">Workflow tracing offers a way to capture diagnostic information using .NET Framework trace listeners.</span></span> <span data-ttu-id="63917-104">Trasování lze povolit, pokud je zjištěn problém s aplikací a následně zakázán po vyřešení problému.</span><span class="sxs-lookup"><span data-stu-id="63917-104">Tracing can be enabled if a problem is detected with the application and then disabled again once the problem is resolved.</span></span> <span data-ttu-id="63917-105">Existují dva způsoby, jak povolit trasování ladění pro pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="63917-105">There are two ways you could enable debug tracing for workflows.</span></span> <span data-ttu-id="63917-106">Můžete ji nakonfigurovat pomocí prohlížeče trasování událostí nebo můžete použít <xref:System.Diagnostics> k odeslání událostí trasování do souboru.</span><span class="sxs-lookup"><span data-stu-id="63917-106">You can configure it using the Event Trace viewer or you can use <xref:System.Diagnostics> to send trace events to a file.</span></span>  
  
## <a name="enabling-debug-tracing-in-etw"></a><span data-ttu-id="63917-107">Povolení trasování ladění v ETW</span><span class="sxs-lookup"><span data-stu-id="63917-107">Enabling Debug Tracing in ETW</span></span>  
 <span data-ttu-id="63917-108">Pokud chcete povolit trasování pomocí ETW, povolte ladicí kanál v Prohlížeč událostí:</span><span class="sxs-lookup"><span data-stu-id="63917-108">To enable tracing using ETW, enable the Debug channel in Event Viewer:</span></span>  
  
1. <span data-ttu-id="63917-109">Přejděte na uzel analytické a ladicí protokoly v Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="63917-109">Navigate to analytic and debug logs node in Event Viewer.</span></span>  
  
2. <span data-ttu-id="63917-110">Ve stromovém zobrazení v Prohlížeč událostí přejděte na **protokoly Prohlížeč událostí > aplikace a služby – > Microsoft-> Windows-> aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="63917-110">In the tree view in Event Viewer, navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="63917-111">Klikněte pravým tlačítkem na **aplikační server – aplikace** a vyberte **Zobrazit – > Zobrazit protokoly pro ladění a ladění**.</span><span class="sxs-lookup"><span data-stu-id="63917-111">Right-click **Application Server-Applications** and select **View->Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="63917-112">Klikněte pravým tlačítkem na **ladit** a vyberte **Povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="63917-112">Right-click **Debug** and select **Enable Log**.</span></span>  
  
3. <span data-ttu-id="63917-113">Když pracovní postup spustí ladění a trasování se vysílá do ladicího kanálu ETW, můžou se zobrazit v Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="63917-113">When a workflow runs the debug and traces are emitted to ETW debug channel, they can be viewed in the Event Viewer.</span></span> <span data-ttu-id="63917-114">Přejděte na **Prohlížeč událostí > protokoly aplikací a služeb – > Microsoft-> Windows-> aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="63917-114">Navigate to **Event Viewer->Applications and Services Logs->Microsoft->Windows->Application Server-Applications**.</span></span> <span data-ttu-id="63917-115">Klikněte pravým tlačítkem na **ladit** a vyberte **aktualizovat**.</span><span class="sxs-lookup"><span data-stu-id="63917-115">Right-click **Debug** and select **Refresh**.</span></span>  
  
4. <span data-ttu-id="63917-116">Výchozí velikost vyrovnávací paměti analytického trasování je jenom 4 kilobajty (KB); doporučuje se zvětšit velikost na 32 KB.</span><span class="sxs-lookup"><span data-stu-id="63917-116">The default analytic trace buffer size is only 4 kilobytes (KB); it is recommended to increase the size to 32 KB.</span></span> <span data-ttu-id="63917-117">Chcete-li to provést, postupujte následovně.</span><span class="sxs-lookup"><span data-stu-id="63917-117">To do this, perform the following steps.</span></span>  
  
    1. <span data-ttu-id="63917-118">Spusťte následující příkaz v aktuálním adresáři rozhraní (například C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="63917-118">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
    2. <span data-ttu-id="63917-119">Změňte hodnotu hodnoty bufferSize > v souboru Windows. ApplicationServer. Applications. Man na 32. \<</span><span class="sxs-lookup"><span data-stu-id="63917-119">Change the \<bufferSize> value in the Windows.ApplicationServer.Applications.man file to 32.</span></span>  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. <span data-ttu-id="63917-120">Spusťte následující příkaz v aktuálním adresáři rozhraní (například C:\Windows\Microsoft.NET\Framework\v4.0.21203):`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span><span class="sxs-lookup"><span data-stu-id="63917-120">Execute the following command in the current framework directory (for example, C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63917-121">Pokud používáte profil klienta .NET Framework 4, je nutné nejprve zaregistrovat manifest ETW spuštěním následujícího příkazu z adresáře .NET Framework 4:`ServiceModelReg.exe –i –c:etw`</span><span class="sxs-lookup"><span data-stu-id="63917-121">If you are using the .NET Framework 4 Client Profile, you must first register the ETW manifest by running the following command from the .NET Framework 4 directory: `ServiceModelReg.exe –i –c:etw`</span></span>  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a><span data-ttu-id="63917-122">Povolení trasování ladění pomocí System. Diagnostics</span><span class="sxs-lookup"><span data-stu-id="63917-122">Enabling Debug Tracing using System.Diagnostics</span></span>  
 <span data-ttu-id="63917-123">Tyto naslouchací procesy lze konfigurovat v souboru App. config aplikace pracovního postupu nebo souboru Web. config pro službu pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="63917-123">These listeners can be configured in the App.config file of the workflow application, or the Web.config for a workflow service.</span></span> <span data-ttu-id="63917-124">V tomto příkladu je [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) nakonfigurovaný pro uložení trasovacích informací do souboru MyTraceLog. txt v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="63917-124">In this example, a [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) is configured to save tracing information to the MyTraceLog.txt file in the current directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="63917-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63917-125">See also</span></span>

- [<span data-ttu-id="63917-126">Monitorování Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="63917-126">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="63917-127">Monitorování aplikací pomocí prostředků infrastruktury aplikace</span><span class="sxs-lookup"><span data-stu-id="63917-127">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
