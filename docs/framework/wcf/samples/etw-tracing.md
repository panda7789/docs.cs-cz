---
title: Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183705"
---
# <a name="etw-tracing"></a>Trasování událostí pro Windows
Tato ukázka ukazuje, jak implementovat trasování end-to-end (E2E) pomocí trasování `ETWTraceListener` událostí pro Windows (ETW) a který je k dispozici v této ukázce. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a zahrnuje trasování ETW.  
  
> [!NOTE]
> Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Tato ukázka předpokládá, že jste obeznámeni s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Každý zdroj trasování v modelu <xref:System.Diagnostics> trasování může mít více posluchačů trasování, které určují, kde a jak jsou data sledována. Typ naslouchací proces definuje formát, ve kterém jsou protokolována data trasování. Následující ukázka kódu ukazuje, jak přidat naslouchací proces do konfigurace.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 Před použitím tohoto naslouchací proces eTW trace session musí být spuštěna. Tuto relaci lze spustit pomocí logman.exe nebo Tracelog.exe. Soubor SetupETW.bat je součástí této ukázky, takže můžete nastavit eTW trace session spolu se souborem CleanupETW.bat pro zavření relace a dokončení souboru protokolu.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu. Další informace o těchto nástrojích naleznete v tématu<https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 Při použití ETWTraceListener, trasování jsou protokolovány v binárních .etl soubory. Se zapnutou trasování ServiceModel se zobrazí všechna vygenerovaná trasování ve stejném souboru. Nástroj [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) slouží k prohlížení souborů protokolu .etl a .svclog. Prohlížeč vytvoří komplexní zobrazení systému, které umožňuje sledovat zprávu ze zdroje do cílového místa a místa spotřeby.  
  
 ETW naslouchací proces trasování podporuje cyklické protokolování. Chcete-li tuto funkci povolit, `cmd` přejděte na **úvodní**obrazovku , **Spustit** a zadejte spusťte příkazovou konzolu. V následujícím příkazu `<logfilename>` nahraďte parametr názvem souboru protokolu.  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` Přepínače `-max` a jsou volitelné. Určují binární kruhový formát a maximální velikost protokolu 1000 MB. Přepínač `-p` se používá k určení zprostředkovatele trasování. V našem `"{411a0819-c24b-428c-83e2-26b41091702e}"` příkladu je identifikátor GUID pro "XML ETW ukázkový zprostředkovatel".  
  
 Chcete-li relaci spustit, zadejte následující příkaz.  
  
```console  
logman start Wcf  
```  
  
 Po dokončení protokolování můžete relaci zastavit pomocí následujícího příkazu.  
  
```console  
logman stop Wcf  
```  
  
 Tento proces generuje binární cyklické protokoly, které můžete zpracovat pomocí zvoleného nástroje, včetně [nástroje Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.  
  
 Můžete také zkontrolovat [cyklické trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) ukázku pro více informací o alternativní naslouchací proces provádět cyklické protokolování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    > Chcete-li použít příkazy RegisterProvider.bat, SetupETW.bat a CleanupETW.bat, musíte spustit pod účtem místního správce. Pokud používáte systém Windows Vista nebo novější, je nutné spustit také příkazový řádek se zvýšenými oprávněními. Chcete-li tak učinit, klepněte pravým tlačítkem myši na ikonu příkazového řádku a potom klepněte na příkaz **Spustit jako správce**.  
  
3. Před spuštěním ukázky spusťte RegisterProvider.bat na straně klienta a serveru. Tím nastavíte výsledný soubor ETWTracingSampleLog.etl pro generování trasování, které lze číst prohlížečem trasování služby. Tento soubor lze nalézt ve složce C:\logs. Pokud tato složka neexistuje, musí být vytvořena nebo jsou generovány žádné stopy. Potom spusťte SetupETW.bat na počítačích klienta a serveru zahájit relaci trasování ETW. Soubor SetupETW.bat naleznete ve složce CS\Client.  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Po dokončení vzorku spusťte CleanupETW.bat k dokončení vytvoření souboru ETWTracingSampleLog.etl.  
  
6. Otevřete soubor ETWTracingSampleLog.etl z prohlížeče trasování služby. Budete vyzváni k uložení binárního formátovaného souboru jako souboru .svclog.  
  
7. Otevřete nově vytvořený soubor .svclog z prohlížeče trasování služby a zobrazte trasování ETW a ServiceModel.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
