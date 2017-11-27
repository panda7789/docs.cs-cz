---
title: "Cyklické sledování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b86867793424d6d0b42a18d6a2fbd6175bc1a47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="circular-tracing"></a>Cyklické sledování
Tento příklad znázorňuje implementaci naslouchací cyklický vyrovnávací paměti. Běžný scénář pro produkční služby je potřeba mít služby, které jsou k dispozici pro dlouhou dobu a povoleno na nízké úrovni protokolování trasování. Tyto služby využívat velké množství místa na disku. Při odstraňování problémů s služby, aby nejnovější data v protokolu trasování je relevantní pro řešení problému. Tento příklad znázorňuje implementaci ve kterém jsou uchovány pouze nejnovější trasování na disku až konfigurovat množství dat naslouchací cyklický vyrovnávací paměti. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) i vlastní trasování naslouchací proces.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Tato ukázka se předpokládá, že jste obeznámeni s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázkové a přečetli v dokumentaci k [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázka.  
  
## <a name="circular-buffer-trace-listener"></a>Naslouchací proces trasování cyklické vyrovnávací paměti  
 Koncept za implementace naslouchací proces trasování cyklické vyrovnávací paměti je mít dva soubory, které může každý ukládat až polovinu data protokolu celkový požadované trasování. Naslouchací proces vytvoří jeden soubor a zapíše do tohoto souboru, dokud nebude dosaženo limitu polovinu velikost dat, na který bod přepíná na druhý soubor. Když se dosáhne naslouchací proces limit pro druhý soubor - přepíše první soubor se nová trasování.  
  
 Tato naslouchací proces je odvozena z `XmlWriteTraceListener` a umožňuje prohlížení s protokoly [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Při pokusu o zobrazení protokolů, dva soubory protokolů můžete snadno rekombinované oba soubory protokolu otevřením současně v nástroji prohlížeče trasování služeb. Nástroj prohlížeče trasování služeb automaticky postará řazení trasování tak, aby byly uvedeny ve správném pořadí.  
  
## <a name="configuration"></a>Konfigurace  
 Službu lze nakonfigurovat k využívání cyklické vyrovnávací paměti trasování modulu naslouchání přidáním následujícího kódu pro naslouchací proces a zdrojové elementy. Maximální velikost je určený nastavením `maxFileSizeKB` atribut v konfiguraci naslouchacího procesu cyklické trasování. Tento postup je znázorněn v následujícím kódu.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
