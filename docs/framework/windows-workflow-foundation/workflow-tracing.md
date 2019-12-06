---
title: Trasování pracovních postupů
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 972520aae7a2af950ed1ba079769861173784148
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837503"
---
# <a name="workflow-tracing"></a>Trasování pracovních postupů
Trasování pracovního postupu nabízí způsob, jak zachytit diagnostické informace pomocí posluchačů trasování .NET Framework. Trasování lze povolit, pokud je zjištěn problém s aplikací a následně zakázán po vyřešení problému. Existují dva způsoby, jak povolit trasování ladění pro pracovní postupy. Můžete ji nakonfigurovat pomocí prohlížeče trasování událostí nebo můžete použít <xref:System.Diagnostics> k odeslání událostí trasování do souboru.  
  
## <a name="enabling-debug-tracing-in-etw"></a>Povolení trasování ladění v ETW  
 Pokud chcete povolit trasování pomocí ETW, povolte ladicí kanál v Prohlížeč událostí:  
  
1. Přejděte na uzel analytické a ladicí protokoly v Prohlížeč událostí.  
  
2. Ve stromovém zobrazení v Prohlížeč událostí přejděte na **protokoly Prohlížeč událostí > aplikace a služby – > Microsoft-> Windows-> aplikační server – aplikace**. Klikněte pravým tlačítkem na **aplikační server – aplikace** a vyberte **Zobrazit – > Zobrazit protokoly pro ladění a ladění**. Klikněte pravým tlačítkem na **ladit** a vyberte **Povolit protokol**.  
  
3. Když pracovní postup spustí ladění a trasování se vysílá do ladicího kanálu ETW, můžou se zobrazit v Prohlížeč událostí. Přejděte na **Prohlížeč událostí > protokoly aplikací a služeb – > Microsoft-> Windows-> aplikační server – aplikace**. Klikněte pravým tlačítkem na **ladit** a vyberte **aktualizovat**.  
  
4. Výchozí velikost vyrovnávací paměti analytického trasování je jenom 4 kilobajty (KB); doporučuje se zvětšit velikost na 32 KB. Chcete-li to provést, postupujte následovně.  
  
    1. Spusťte následující příkaz v aktuálním adresáři rozhraní (například C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2. Změňte hodnotu \<hodnoty bufferSize > v souboru Windows. ApplicationServer. Applications. Man na 32.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. Spusťte následující příkaz v aktuálním adresáři rozhraní (například C:\Windows\Microsoft.NET\Framework\v4.0.21203): `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
> Pokud používáte profil klienta .NET Framework 4, je nutné nejprve zaregistrovat manifest ETW spuštěním následujícího příkazu ze složky .NET Framework 4: `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Povolení trasování ladění pomocí System. Diagnostics  
 Tyto naslouchací procesy lze konfigurovat v souboru App. config aplikace pracovního postupu nebo souboru Web. config pro službu pracovního postupu. V tomto příkladu je <xref:System.Diagnostics.TextWriterTraceListener> nakonfigurovaná tak, aby ukládala trasovací informace do souboru MyTraceLog. txt v aktuálním adresáři.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))
