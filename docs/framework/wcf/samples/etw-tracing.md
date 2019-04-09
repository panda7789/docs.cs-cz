---
title: Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 964c8fbe04f61ebf7a68e1bf36f9efdaab841e7a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105427"
---
# <a name="etw-tracing"></a>Trasování událostí pro Windows
Tato ukázka předvádí, jak implementovat začátku do konce (E2E) trasování pomocí Event Tracing for Windows (ETW) a `ETWTraceListener` , který je součástí této ukázky. Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a obsahuje trasování událostí pro Windows.  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tento příklad předpokládá, že máte zkušenosti s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Každý zdroj trasování v <xref:System.Diagnostics> model trasování může mít několik naslouchacích procesů trasování, které určují, kde a jak se data trasovány. Typ naslouchacího procesu definuje formát, ve které se protokolují tato data trasování. Následující příklad kódu ukazuje, jak přidat naslouchací proces konfigurace.  
  
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
  
 Před použitím tohoto modulu pro naslouchání, musí se spustit relaci trasování ETW. Tato relace můžete spustit pomocí Logman.exe nebo Tracelog.exe. SetupETW.bat souboru je zahrnuta v této ukázce tak, že můžete nastavit relaci sledování ETW spolu se souborem CleanupETW.bat pro zavření relace a dokončení souboru protokolu.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu. Další informace o těchto nástrojích najdete v tématu [https://go.microsoft.com/fwlink/?LinkId=56580](https://go.microsoft.com/fwlink/?LinkId=56580)  
  
 Při použití ETWTraceListener přihlášeni trasování .etl binární soubory. S ServiceModel trasování zapnuté, všechna trasování vygenerovaný objeví ve stejném souboru. Použití [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pro zobrazení ETL a .svclog souborů protokolů. V prohlížeči vytvoří pohledu začátku do konce systému, který umožňuje trasování zprávy z jeho zdroje do cíle a bod spotřeby.  
  
 Naslouchací proces trasování ETW podporuje cyklické protokolování. Pokud chcete tuto funkci povolit, přejděte na **spustit**, **spustit** a typ `cmd` ke spuštění nástroje command console. V následujícím příkazu nahraďte `<logfilename>` parametr s názvem souboru protokolu.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` a `-max` přepínače jsou volitelné. Určí cyklický binárních a maximální velikost protokolu 1000 MB v uvedeném pořadí. `-p` Přepínače se používá k určení zprostředkovatel trasování. V našem příkladu `"{411a0819-c24b-428c-83e2-26b41091702e}"` je identifikátor GUID pro "Zprostředkovateli ukázek trasování událostí pro Windows XML".  
  
 Spustit relaci, zadejte následující příkaz.  
  
```  
Logman start Wcf  
```  
  
 Po dokončení protokolování, můžete zastavit relaci pomocí následujícího příkazu.  
  
```  
Logman stop Wcf  
```  
  
 Tento proces vygeneruje binární cyklické protokoly, které můžete zpracovat nástroj podle vlastního výběru, včetně [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.  
  
 Můžete také zkontrolovat [cyklické trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) ukázky pro další informace o alternativních naslouchací proces provádět cyklické protokolování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  Chcete-li použít příkazy RegisterProvider.bat, SetupETW.bat a CleanupETW.bat, musíte spustit pod účtem místního správce. Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo novější, musíte také spustit příkazový řádek se zvýšenými oprávněními. Chcete-li tak učinit, klepněte pravým tlačítkem myši na ikonu příkazového řádku a potom klikněte na **spustit jako správce**.  
  
3.  Před spuštěním ukázky, spusťte RegisterProvider.bat na klienta a serveru. Tím se nastaví výsledný soubor ETWTracingSampleLog.etl ke generování trasování, které lze číst pomocí prohlížeče trasování služeb. Tento soubor najdete ve složce C:\logs. Pokud tato složka neexistuje, je nutné vytvořit nebo jsou generovány žádné trasování. Potom spusťte SetupETW.bat klientských a serverových počítačů zahájit relaci sledování ETW. SetupETW.bat soubor najdete ve složce CS\Client.  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Po dokončení ukázku spusťte CleanupETW.bat k dokončení vytvoření ETWTracingSampleLog.etl souboru.  
  
6.  Otevřete soubor ETWTracingSampleLog.etl z prohlížeče trasování služeb. Zobrazí se výzva k uložení binárního souboru formátovaný jako soubor .svclog.  
  
7.  Otevřete soubor nově vytvořený .svclog z prohlížeče trasování služeb k zobrazení trasování ETW a ServiceModel.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
