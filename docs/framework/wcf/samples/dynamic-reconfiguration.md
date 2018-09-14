---
title: Dynamická rekonfigurace
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45508195"
---
# <a name="dynamic-reconfiguration"></a>Dynamická rekonfigurace
V této ukázce směrovací službou Windows Communication Foundation (WCF). Směrovací služba je komponenta WCF, který umožňuje snadno do aplikace zahrnout směrovač založené na obsahu. Tato ukázka se přizpůsobí standardní kalkulačky Ukázky WCF na komunikaci pomocí směrovací službou. Tato ukázka předvádí, jak služba směrování můžete dynamicky překonfigurovat za běhu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Za běhu dynamicky rekonfigurovat směrovací službou, této ukázce aktivuje časovač každých pět sekund, který vytvoří nový <xref:System.ServiceModel.Routing.RoutingConfiguration> objektu a použije ho. Tato konfigurace odkazuje běžným koncovým bodem Kalkulačka nebo koncový bod zaokrouhlení kalkulačku. Kalkulačka klientské aplikace má jeho zpráv vrácených z jedné služby nebo druhé, podle toho, která je nakonfigurovaná služba Směrování na trasy, která má v daném čase.  
  
 Směrovací služba capabilitiy pro dynamická Rekonfigurace prostřednictvím vlastního chování se používá. Toto vlastní chování připojí rozšíření služby, který obsahuje jednoduché vláknu časovače, který se aktivuje každých pět sekund, což vede k zpětné volání, aby `UpdateRules` metody. Toto zpětné volání vytvoří a použije novou konfiguraci směrování. V skutečný nasazení by tato zpětné volání provedli pravděpodobně v důsledku jiného typu události, jako je například oznámení události SQL nebo WS-Discovery oznámení.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete DynamicReconfiguration.sln.  
  
2.  Chcete-li otevřít **Průzkumníku řešení**vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
3.  Stisknutím klávesy **F5** nebo **CTRL + SHIFT + B** v sadě Visual Studio.  
  
    1.  Pokud chcete automaticky spouštět nezbytné projektů při stisknutí **F5**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**. Vyberte **spouštěný projekt** pod uzlem **společné vlastnosti** v levém podokně. Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které mají mít **Start** akce.  
  
    2.  Při sestavování projektu s **CTRL + SHIFT + B**, je nutné spustit v následujících aplikacích:  
  
        1.  Kalkulačka klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Kalkulačka služby (. / CalculatorService/bin/service.exe)  
  
        3.  Směrovací služba kalkulačky (. / RoundingCalcService/bin/service.exe)  
  
        4.  Službu RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  V okně konzoly klienta kalkulačky stisknutím klávesy ENTER spustíte klienta a k volání operací služby kalkulačky.  
  
     Směrovací služba provádí směrování zpráv ke kalkulačce zaokrouhlení a pravidelné Kalkulačka střídavě jako změny konfigurace směrování dynamicky každých pět sekund. V závislosti na tom, ke kterému koncovému bodu směrovací služba je nakonfigurovaná k odesílání zpráv do existují jiné výstupy v okně konzoly klienta.  
  
5.  Pokračujte stisknutím klávesy ENTER opakovaně přes více než pět sekund a sledovat změnu v hodnotě výsledky ze služby.  
  
    1.  Zde je, že výstup vrátí, pokud směrovač služba je nakonfigurována pro směrování zpráv služby zaokrouhlení kalkulačku.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Zde je, že výstup vrátí, pokud směrovací služba je nakonfigurována pro směrování zpráv ke službě regulárních kalkulačky.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  Kalkulačka služba a služba zaokrouhlení Kalkulačka také vytisknout protokolu operací vyvolat a jejich odpovídajících konzoly windows.  
  
7.  V okně konzoly klienta typu "Ukončete" a stisknutím klávesy ENTER ukončete.  
  
8.  Stisknutím klávesy ENTER v oknech konzoly služby k ukončení služby.  
  
## <a name="scenario"></a>Scénář  
 Tato ukázka předvádí, směrovač fungujícího jako směrovač založené na obsahu umožňuje více typů nebo implementaci služeb zpřístupní prostřednictvím jeden koncový bod.  
  
### <a name="real-world-scenario"></a>Reálné scénáře  
 Contoso chce, aby se k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes který nabízejí přístup k více různých typů služeb. V tomto případě využívat Služba směrování založené na obsahu směrování schopnosti určit, které by měla být odeslána příchozí požadavky.  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
