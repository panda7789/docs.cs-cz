---
title: "Pracovní postup trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18737989-0502-4367-b5f6-617ebfb77c96
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4332b93175f4cb751ba88c7d2b05e4b462de7748
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="workflow-tracing"></a>Pracovní postup trasování
Pracovní postup trasování nabízí způsob, jak zachytit diagnostických informací s použitím rozhraní .NET Framework trasování – moduly naslouchání. Trasování můžete povolit, pokud se zjistí problém s aplikací a zakázané znovu, jakmile je problém vyřešen. Existují dva způsoby, které může povolit trasování ladění pro pracovní postupy. Můžete nakonfigurovat pomocí prohlížeče událostí trasování, nebo můžete použít <xref:System.Diagnostics> odesílat události trasování do souboru.  
  
## <a name="enabling-debug-tracing-in-etw"></a>Povolení ladění, trasování v trasování událostí pro Windows  
 Pokud chcete povolit trasování pomocí trasování událostí pro Windows, povolte ladění kanál v prohlížeči událostí:  
  
1.  Přejděte na analytické a ladicí uzlu protokoly v prohlížeči událostí.  
  
2.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí -> aplikace a protokoly služby -> Microsoft -> Windows -> serveru aplikace – aplikace**. Klikněte pravým tlačítkem na **serveru aplikace – aplikace** a vyberte **-zobrazení > Zobrazit protokoly pro ladění a**. Klikněte pravým tlačítkem na **ladění** a vyberte **povolit protokol**.  
  
3.  Při spuštění pracovního postupu ladění a trasování jsou vygenerované kanálu ladění, trasování událostí pro Windows, lze zobrazit v prohlížeči událostí. Přejděte na **Prohlížeč událostí -> aplikace a protokoly služby -> Microsoft -> Windows -> serveru aplikace – aplikace**. Klikněte pravým tlačítkem na **ladění** a vyberte **aktualizovat**.  
  
4.  Výchozí velikost vyrovnávací paměti analytického trasování je jenom 4 kilobajtů (KB); Doporučujeme zvýšit velikost 32 KB. Chcete-li to provést, proveďte následující kroky.  
  
    1.  V aktuálním adresáři framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz:`wevtutil um Microsoft.Windows.ApplicationServer.Applications.man`  
  
    2.  Změna \<bufferSize > v souboru Windows.ApplicationServer.Applications.man 32 znaků. hodnota.  
  
        ```xml  
        <channel name="Microsoft-Windows-Application Server-Applications/Analytic" chid="ANALYTIC_CHANNEL" symbol="ANALYTIC_CHANNEL" type="Analytic" enabled="false" isolation="Application" message="$(string.MICROSOFT_WINDOWS_APPLICATIONSERVER_APPLICATIONS.channel.ANALYTIC_CHANNEL.message)" >  
                    <publishing>  
                      <bufferSize>32</bufferSize>  
                    </publishing>  
                  </channel>  
        ```  
  
    3.  V aktuálním adresáři framework (například C:\Windows\Microsoft.NET\Framework\v4.0.21203) spusťte následující příkaz:`wevtutil im Microsoft.Windows.ApplicationServer.Applications.man`  
  
> [!NOTE]
>  Pokud používáte profil klienta rozhraní .NET Framework 4, je nutné zaregistrovat manifest trasování událostí pro Windows tak, že spustíte následující příkaz z adresáře, rozhraní .NET Framework 4:`ServiceModelReg.exe –i –c:etw`  
  
## <a name="enabling-debug-tracing-using-systemdiagnostics"></a>Povolení ladění trasování pomocí System.Diagnostics  
 Tyto moduly pro naslouchání lze nakonfigurovat v souboru App.config pracovní postup aplikace nebo souboru Web.config pro službu pracovního postupu. V tomto příkladu [TextWriterTraceListener](http://go.microsoft.com/fwlink/?LinkId=165424) nakonfigurovaný tak, aby se uložily informace o trasování do souboru MyTraceLog.txt v aktuálním adresáři.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
