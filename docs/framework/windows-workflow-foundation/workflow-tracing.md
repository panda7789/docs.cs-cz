---
title: Trasování pracovních postupů
ms.date: 03/30/2017
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
ms.openlocfilehash: 8dba5706ee37f243c15befb483ab4f9f2a8e3b9c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655725"
---
# <a name="workflow-tracing"></a>Trasování pracovních postupů
Trasování pracovních postupů nabízí způsob, jak k zaznamenání diagnostických informací s použitím rozhraní .NET Framework naslouchacích procesů trasování. Trasování může povolit, pokud byl zjištěn problém s aplikací a zakázané znovu, až se problém vyřeší. Existují dva způsoby, jak může povolit trasování ladění pracovních postupů. Můžete je nakonfigurovat pomocí prohlížeče událostí trasování nebo můžete použít <xref:System.Diagnostics> k odesílání trasování událostí do souboru.  
  
## <a name="enabling-debug-tracing-in-etw"></a>Povolení ladění trasování v trasování událostí pro Windows  
 Pokud chcete povolit, trasování pomocí trasování událostí pro Windows, povolte ladění kanálu v prohlížeči událostí:  
  
1. Přejděte do analýzy a ladit protokoly uzlu v prohlížeči událostí.  
  
2. Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí -> aplikace a služby protokoly -> Microsoft -> Windows -> aplikace Server-**. Klikněte pravým tlačítkem na **aplikace Server-** a vyberte **zobrazení -> Zobrazit protokoly ladění a analýzu**. Klikněte pravým tlačítkem na **ladění** a vyberte **povolit protokol**.  
  
3. Při spuštění pracovního postupu, ladění a trasování, které jsou emitovány do kanálu ladění trasování událostí pro Windows, můžete zobrazit v prohlížeči událostí. Přejděte do **Prohlížeč událostí -> aplikace a služby protokoly -> Microsoft -> Windows -> aplikace Server-**. Klikněte pravým tlačítkem na **ladění** a vyberte **aktualizovat**.  
  
4. Výchozí velikost vyrovnávací paměti analytického trasování je jenom 4 kilobajtů (KB); se doporučuje zvýšit velikost na 32 KB. Chcete-li to provést, postupujte následovně.  
  
    1. V aktuálním adresáři rozhraní framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz: `wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2. Změnit \<bufferSize > hodnota v souboru Windows.ApplicationServer.Applications.man 32.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3. V aktuálním adresáři rozhraní framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz: `wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  Pokud používáte rozhraní .NET Framework 4 Client Profile, musíte se nejprve zaregistrovat manifestu trasování událostí pro Windows spuštěním následujícího příkazu v adresáři rozhraní .NET Framework 4: `ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Povolení ladění trasování System.Diagnostics pomocí  
 Tyto moduly pro naslouchání lze nastavit v souboru App.config aplikace pracovního postupu nebo soubor Web.config pro službu pracovního postupu. V tomto příkladu [TextWriterTraceListener](https://go.microsoft.com/fwlink/?LinkId=165424) je nakonfigurovaný k ukládání informací o trasování do souboru MyTraceLog.txt v aktuálním adresáři.  
  
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

- [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
