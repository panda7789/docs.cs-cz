---
title: Cyklické sledování
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 1f6c5287e6a53ed26ee5c9ed477e08dafc512e3f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45638425"
---
# <a name="circular-tracing"></a>Cyklické sledování
Tento příklad ukazuje implementaci naslouchací proces trasování cyklické vyrovnávací paměti. Běžný scénář pro produkční služby je potřeba mít služby, které jsou k dispozici pro dlouhou dobu a povoleno na nízké úrovni protokolování trasování. Tyto služby využívat velké množství místa na disku. Při odstraňování služby, nejnovější data v protokolech trasování je relevantní pro řešení problémů. Tento příklad ukazuje implementaci pro posluchače trasování cyklické vyrovnávací paměti, ve kterém jsou pouze nejnovější trasování uchovávat na disku, až po konfigurovatelnou data. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a obsahuje naslouchací proces trasování vlastní.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tento příklad předpokládá, že máte zkušenosti s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázky a přečetl(a) v dokumentaci k [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) vzorku.  
  
## <a name="circular-buffer-trace-listener"></a>Naslouchací proces trasování cyklické vyrovnávací paměti  
 Koncept za implementaci naslouchací služby stopy cyklické vyrovnávací paměti je, aby dva soubory, které může každý ukládat až polovinu data protokolu celkové požadované trasování. Naslouchací proces vytvoří jeden soubor a zapíše do tohoto souboru, dokud nebude dosaženo limitu polovina velikosti dat, v tomto okamžiku přepne do druhého souboru. Naslouchací proces dosáhne limitu pro druhý soubor - přepíše první soubor s nová trasování.  
  
 Je odvozena z tohoto modulu pro naslouchání `XmlWriteTraceListener` a umožňuje na protokoly, kde se dají zobrazit [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Při pokusu o zobrazení protokolů, dva soubory protokolů můžete snadno rekombinované tak, že otevřete oba soubory protokolu ve stejnou dobu v nástroji prohlížeče trasování služeb. Nástroj prohlížeče trasování služeb automaticky postará o řazení trasování tak, aby byly zobrazeny ve správném pořadí.  
  
## <a name="configuration"></a>Konfigurace  
 Službu lze nastavit používat naslouchací služby stopy cyklické vyrovnávací paměti tak, že přidáte následující kód pro naslouchací proces a zdrojové elementy. Maximální velikost souboru je určený nastavením `maxFileSizeKB` atribut v konfiguraci naslouchacího procesu cyklické trasování. To je ukázáno v následujícím kódu.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
