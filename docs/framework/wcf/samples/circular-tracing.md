---
title: Cyklické sledování
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 4934061243f098c96aaeadddad100860c363445e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950942"
---
# <a name="circular-tracing"></a>Cyklické sledování
Tato ukázka demonstruje implementaci cyklického naslouchacího procesu trasování vyrovnávací paměti. Běžným scénářem provozního provozu je, že služby jsou dostupné po dlouhou dobu a mají povolené protokolování trasování na nízké úrovni. Tyto služby spotřebují spoustu místa na disku. Při řešení potíží se službou jsou nejnovější data v protokolu trasování relevantní pro řešení problému. Tato ukázka předvádí implementaci cyklického naslouchacího procesu trasování vyrovnávací paměti, ve kterém jsou uchovávána pouze nejnovější trasování na disku až do konfigurovatelného množství dat. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a obsahuje vlastní naslouchací proces trasování.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 V této ukázce se předpokládá, že jste obeznámeni s ukázkou [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) a přečetli jste si dokumentaci k ukázce [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .  
  
## <a name="circular-buffer-trace-listener"></a>Cyklická naslouchací proces trasování vyrovnávací paměti  
 Koncept za implementaci cyklického naslouchacího procesu trasování vyrovnávací paměti má dva soubory, které mohou každý z nich uchovávat až polovinu celkových požadovaných dat protokolu trasování. Naslouchací proces vytvoří jeden soubor a zapíše jej do tohoto souboru, dokud nedosáhne limitu poloviny velikosti dat, při které se přepne na druhý soubor. Když naslouchací proces dosáhne limitu pro druhý soubor – přepíše první soubor novými trasováními.  
  
 Tento naslouchací proces je odvozen z `XmlWriteTraceListener` rozhraní a umožňuje zobrazení protokolů pomocí [Nástroje pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Při pokusu o zobrazení protokolů se tyto dva soubory protokolu dají snadno kombinovat otevřením obou souborů protokolu současně v nástroji Service Trace Viewer. Nástroj Prohlížeč trasování služby automaticky postará o řazení trasování, aby se zobrazila ve správném pořadí.  
  
## <a name="configuration"></a>Konfiguraci  
 Službu lze nakonfigurovat tak, aby používala cyklické naslouchací proces trasování vyrovnávací paměti přidáním následujícího kódu pro naslouchací proces a zdrojové prvky. Maximální velikost souboru je určena nastavením `maxFileSizeKB` atributu v konfiguraci cyklického naslouchacího procesu trasování. To je znázorněno v následujícím kódu.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky monitorování technologie AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
