---
title: Dynamická rekonfigurace
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: 81a2b494c48476e683053e12e58264e756201124
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="dynamic-reconfiguration"></a>Dynamická rekonfigurace
Tento příklad znázorňuje směrování služby Windows Communication Foundation (WCF). Služba Směrování je součást WCF, který usnadňuje do aplikace zahrnout směrovač podle obsahu. Tato ukázka přizpůsobuje standardní ukázka kalkulačku WCF komunikovat pomocí služby směrování. Tento příklad ukazuje, jak službu směrování můžete dynamicky překonfigurovat za běhu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Dynamicky znovu nakonfigurovat službu Směrování za běhu, aktivuje se tato ukázka časovače každých pět sekund, který vytvoří nový <xref:System.ServiceModel.Routing.RoutingConfiguration> objektu a použije ji. Tato konfigurace odkazuje regulární koncový bod kalkulačky nebo zaokrouhlení kalkulačky koncový bod. Kalkulačky klientská aplikace má jeho zpráv vrácených z jedné služby nebo dalších, podle toho, která je nakonfigurovaná služba Směrování pro trasy, která má v daném čase.  
  
 Směrovací služba capabilitiy pro dynamická Rekonfigurace prostřednictvím vlastní chování se používá. Toto vlastní chování připojí rozšíření služby, který obsahuje jednoduché vlákno časovač, který aktivuje každých pět sekund, což vede k zpětné volání pro `UpdateRules` metoda. Tento zpětného volání vytvoří a použije se nová konfigurace směrování. V skutečné nasazení by tento zpětného volání dosáhnout pravděpodobně v důsledku jiný typ události, jako je například oznámení o události SQL nebo WS-Discovery oznámení.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete DynamicReconfiguration.sln.  
  
2.  Chcete-li otevřít **Průzkumníku řešení**, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.  
  
3.  Stiskněte klávesu **F5** nebo **CTRL + SHIFT + B** v sadě Visual Studio.  
  
    1.  Pokud byste chtěli automaticky spouštěné projekty potřebné při stisknutí volby **F5**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**. Vyberte **spouštěný projekt** pod uzlem **společných vlastností** v levém podokně. Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které chcete mít **spustit** akce.  
  
    2.  Pokud vytvoříte projekt pomocí **CTRL + SHIFT + B**, musíte spustit následující aplikace:  
  
        1.  Klient kalkulačky (. / CalculatorClient/bin/client.exe)  
  
        2.  Službu kalkulačky (. / CalculatorService/bin/service.exe)  
  
        3.  Směrovací služba provádí kalkulačky (. / RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (. / RoutingService/bin/RoutingService.exe)  
  
4.  V okně konzoly klienta kalkulačky stiskněte klávesu ENTER k spuštění klienta a volání operací služby kalkulačky.  
  
     Směrovací služba provádí směrování zpráv kalkulačky zaokrouhlení a regulární kalkulačky případně jako směrování změny konfigurace dynamicky každých pět sekund. V závislosti na tom, ke kterému koncovému bodu službu Směrování je nakonfigurován pro odesílání zpráv do existují různé výstupy v okně konzoly klienta.  
  
5.  Pokračujte stisknutím klávesy ENTER opakovaně přes více než pět sekund a sledovat změnu ve výsledcích ze služby.  
  
    1.  Zde je, že výstup vrácena, pokud je služba směrovače je konfigurovaná pro směrování zpráv do služby zaokrouhlení kalkulačky.  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  Toto je výstup vrácena, pokud směrování služba je nakonfigurována pro směrování zpráv ke službě regulární kalkulačky.  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  Službu kalkulačky a službu kalkulačky zaokrouhlení také vytisknout protokolu operací vyvolat do svých příslušných konzoly windows.  
  
7.  V okně konzoly klienta typu "ukončit" a stiskněte klávesu ENTER ukončíte.  
  
8.  Stisknutím klávesy ENTER v oknech konzoly služby ukončení služby.  
  
## <a name="scenario"></a>Scénář  
 Tento příklad znázorňuje směrovač, který funguje jako směrovač založená na obsahu umožňuje více typů nebo implementace služby mají být exponovány prostřednictvím jeden koncový bod.  
  
### <a name="real-world-scenario"></a>Scénář skutečných  
 Contoso chce k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes která nabízejí přístup k několika různých typů služeb. V takovém případě využívají službu směrování na základě obsahu směrování možnosti k určení, kde by měly být odeslány příchozí požadavky.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
