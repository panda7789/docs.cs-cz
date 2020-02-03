---
title: Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: a62403e61e0566d5e7b753ff951bf4b316209b6f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742110"
---
# <a name="etw-tracing"></a>Trasování událostí pro Windows
Tato ukázka předvádí, jak implementovat E2E (end to-end) trasování pomocí trasování událostí pro Windows (ETW) a `ETWTraceListener`, které jsou k dispozici v této ukázce. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a zahrnuje trasování ETW.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Tato ukázka předpokládá, že máte zkušenosti s [trasováním a protokolováním zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Každý zdroj trasování v modelu trasování <xref:System.Diagnostics> může mít několik posluchačů trasování, které určují, kde a jak se budou data trasovat. Typ naslouchacího procesu definuje formát, ve kterém jsou data trasování protokolována. Následující ukázka kódu ukazuje, jak přidat naslouchací proces do konfigurace.  
  
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
  
 Před použitím tohoto naslouchacího procesu musí být spuštěná relace trasování ETW. Tuto relaci lze spustit pomocí programu Logman. exe nebo nástroji tracelog. exe. Tato ukázka obsahuje soubor SetupETW. bat, takže můžete nastavit relaci trasování ETW spolu se souborem CleanupETW. bat pro ukončení relace a dokončení souboru protokolu.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu. Další informace o těchto nástrojích najdete v tématu <https://go.microsoft.com/fwlink/?LinkId=56580>  
  
 Při použití ETWTraceListener se trasování zaznamenávají do binárních souborů. ETL. Když je zapnuté trasování ServiceModel, všechna vygenerovaná trasování se zobrazí ve stejném souboru. Pro zobrazení souborů protokolu ETL a. svclog použijte [Nástroj Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) . Prohlížeč vytvoří ucelený pohled na systém, který umožňuje trasovat zprávu z jejího zdroje do jejího cíle a bodu spotřeby.  
  
 Naslouchací proces trasování ETW podporuje cyklické protokolování. Tuto funkci povolíte tak, že přejdete na **Start**, **spustíte** a zadáte `cmd` a spustíte konzolu příkazů. V následujícím příkazu nahraďte parametr `<logfilename>` názvem souboru protokolu.  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 Přepínače `-f` a `-max` jsou volitelné. Určují binární cyklický formát a maximální velikost protokolu až 000 MB v uvedeném pořadí. K určení poskytovatele trasování se používá `-p` přepínač. V našem příkladu je `"{411a0819-c24b-428c-83e2-26b41091702e}"` identifikátor GUID pro "Ukázkový poskytovatel XML ETW".  
  
 Chcete-li spustit relaci, zadejte následující příkaz.  
  
```console  
logman start Wcf  
```  
  
 Po dokončení protokolování můžete zastavit relaci pomocí následujícího příkazu.  
  
```console  
logman stop Wcf  
```  
  
 Tento proces generuje binární cyklické protokoly, které můžete zpracovat s vámi zvoleným nástrojem, včetně [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.  
  
 Můžete si také projít ukázku [cyklického trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) , kde najdete další informace o alternativním naslouchacího procesu, který provede cyklické protokolování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    > Chcete-li použít příkazy RegisterProvider. bat, SetupETW. bat a CleanupETW. bat, je nutné spustit pod účtem místního správce. Pokud používáte systém Windows Vista nebo novější, musíte spustit také příkazový řádek se zvýšenými oprávněními. Provedete to tak, že kliknete pravým tlačítkem na ikonu příkazového řádku a potom kliknete na **Spustit jako správce**.  
  
3. Před spuštěním ukázky spusťte na klientech a na serveru RegisterProvider. bat. Tím se vytvoří výsledný soubor ETWTracingSampleLog. ETL, který vygeneruje trasování, které může číst prohlížeč trasování služby. Tento soubor najdete ve složce C:\Logs. Pokud tato složka neexistuje, je nutné ji vytvořit nebo nebudou vygenerována žádná trasování. Pak na klientských a serverovém počítači spusťte SetupETW. bat a zahajte tak relaci trasování ETW. Soubor SetupETW. bat najdete ve složce CS\Client.  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5. Po dokončení ukázky spusťte CleanupETW. bat, aby se dokončilo vytváření souboru ETWTracingSampleLog. ETL.  
  
6. V prohlížeči trasování služby otevřete soubor ETWTracingSampleLog. ETL. Zobrazí se výzva k uložení binárního naformátovaného souboru jako souboru. svclog.  
  
7. Otevřete nově vytvořený soubor. svclog z prohlížeče trasování služby a zobrazte trasování ETW a ServiceModel.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Viz také

- [Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
