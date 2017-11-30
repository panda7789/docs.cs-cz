---
title: "Trasování událostí pro Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
caps.latest.revision: "42"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d45852a8e03ac63ea6412e6f5b176f06fe83eb03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="etw-tracing"></a>Trasování událostí pro Windows
Tento příklad ukazuje, jak implementovat trasování začátku do konce (E2E) pomocí události trasování událostí pro Windows (ETW) a `ETWTraceListener` je součástí této ukázky. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a zahrnuje trasování událostí pro Windows.  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka se předpokládá, že jste obeznámeni s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Každý zdroj trasování v <xref:System.Diagnostics> trasování model může mít více modulů naslouchání trasování, které určují, kdy a jak je sledovat data. Typ naslouchací proces definuje formát, ve kterém se protokolují data trasování. Následující příklad kódu ukazuje, jak přidat naslouchací proces do konfigurace.  
  
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
  
 Před použitím této naslouchací proces, je nutné spustit relaci trasování ETW. Pomocí Logman.exe nebo Tracelog.exe lze spustit tuto relaci. Soubor SetupETW.bat je součástí této ukázky, takže můžete nastavit relaci trasování ETW souborem CleanupETW.bat pro zavření relace a dokončení souboru protokolu.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu. Další informace o těchto nástrojích najdete v tématu [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)  
  
 Při použití ETWTraceListener, trasování jsou protokolovány v souborech binární ETL. Pomocí trasování ServiceModel zapnuta, zobrazí všechny vygenerované trasování ve stejném souboru. Použití [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pro zobrazení ETL a .svclog souborů protokolu. Prohlížeč vytvoří zobrazení o začátku do konce systému, který umožňuje trasování zprávy z zdroje do cíle a bod spotřeby.  
  
 Naslouchací proces trasování ETW podporuje cyklické protokolování. Chcete-li povolit tuto funkci, přejděte na **spustit**, **spustit** a typ `cmd` a spusťte příkaz konzolu. V následujícím příkazu nahraďte `<logfilename>` parametr s názvem souboru protokolu.  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 `-f` a `-max` přepínače jsou volitelné. Určí binární formát cyklické a protokolu maximální velikost 1000MB v uvedeném pořadí. `-p` Přepínač slouží k určení zprostředkovatel trasování. V našem příkladu `"{411a0819-c24b-428c-83e2-26b41091702e}"` je identifikátor GUID pro "XML ETW ukázka zprostředkovatele".  
  
 Chcete-li spustit relaci, zadejte následující příkaz.  
  
```  
Logman start Wcf  
```  
  
 Po dokončení protokolování, můžete zastavit relace pomocí následujícího příkazu.  
  
```  
Logman stop Wcf  
```  
  
 Tento proces vytvoří binární cyklické protokoly, které můžete zpracovat vaše nástroje, včetně [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.  
  
 Můžete také zkontrolovat [cyklické trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) ukázku Další informace o naslouchací proces alternativní postup cyklické protokolování.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
    > [!NOTE]
    >  Pokud chcete používat příkazy RegisterProvider.bat, SetupETW.bat a CleanupETW.bat, musíte spustit pod účtem místního správce. Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo novější, je nutné spustit také příkazovém řádku se zvýšenými oprávněními. Chcete-li to provést, klikněte pravým tlačítkem na ikonu příkazového řádku a potom klikněte na **spustit jako správce**.  
  
3.  Před spuštěním ukázky, spusťte RegisterProvider.bat na klientovi a serveru. Výsledný soubor ETWTracingSampleLog.etl nastavíte ke generování trasování, které mohou být přečteny prohlížeče trasování služeb. Tento soubor naleznete ve složce C:\logs. Pokud tato složka neexistuje, musí být vytvořen nebo jsou generovány žádné trasování. Potom spusťte SetupETW.bat na počítače klienta a serveru, které chcete zahájit relaci trasování ETW. SetupETW.bat soubor naleznete ve složce CS\Client.  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
5.  Po dokončení ukázku spusťte CleanupETW.bat vytvoření souboru ETWTracingSampleLog.etl.  
  
6.  Otevřete soubor ETWTracingSampleLog.etl z v rámci prohlížeče trasování služeb. Zobrazí se výzva k uložení binárního souboru formátovaný jako soubor .svclog.  
  
7.  Otevřete nově vytvořený .svclog souboru v rámci prohlížeče trasování služeb k zobrazení trasování událostí pro Windows a ServiceModel trasování.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
