---
title: Hello World se směrovací službou
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 881636097cf342de09164804c6df6acfbcd97c45
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="hello-world-with-the-routing-service"></a>Hello World se směrovací službou
Tento příklad znázorňuje směrovací služby Windows Communication Foundation (WCF). Služba Směrování je součást WCF, který usnadňuje do aplikace zahrnout směrovač podle obsahu. Tato ukázka přizpůsobuje standardní ukázka kalkulačku WCF na komunikaci pomocí služby směrování. V této ukázce kalkulačky klient je nakonfigurován pro odesílání zpráv pro koncový bod vystavené směrovači. Směrovací služby je nakonfigurován tak, aby přijímal všechny zprávy do něj odeslané a předávat je koncový bod, který odpovídá službu kalkulačky. Proto jsou zpráv odeslaných z klienta přijatých směrovači a přesměrovala ke službě skutečné kalkulačky. Zprávy ze služby kalkulačky jsou odesílány zpět na směrovač, který je pak předá zpět do klienta kalkulačky.  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete HelloRoutingService.sln.  
  
2.  Stisknutím klávesy F5 nebo CTRL + SHIFT + B.  
  
    > [!NOTE]
    >  Pokud stisknete klávesu F5, kalkulačky klienta se automaticky spustí. Pokud stisknete klávesu CTRL + SHIFT + B (sestavení), musíte spustit následující aplikace sami.  
    >   
    >  1.  Klient kalkulačky (./CalculatorClient/bin/client.exe  
    > 2.  Službu kalkulačky (. / CalculatorService/bin/service.exe)  
    > 3.  Směrovací služba provádí (. / RoutingService/bin/RoutingService.exe)  
  
3.  Stiskněte klávesu ENTER a spusťte službu klienta.  
  
     Byste měli vidět následující výstup:  
  
     Add(100,15.99) = 115.99  
  
     SUBTRACT(145,76.54) = 68.46  
  
     MULTIPLY(9,81.25) = 731.25  
  
     Divide(22,7) = 3.14285714285714  
  
## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo App.Config  
 Ukázka lodě, umožňují použít soubor App.config k definování chování směrovače. Můžete taky změnit název souboru App.config na jinou tak, aby nebyla rozpoznána a zrušte komentář u volání metody ConfigureRouterViaCode(). Buď metoda výsledkem stejné chování z směrovači.  
  
### <a name="scenario"></a>Scénář  
 Tento příklad znázorňuje směrovač, který funguje jako základní zprávy odeslané. Směrovací služba funguje jako uzel transparentní proxy server nakonfigurovaný tak, aby předat zprávy přímo do předkonfigurované sadu cílové koncové body.  
  
### <a name="real-world-scenario"></a>Scénář skutečných  
 Contoso chce zvýšíte flexibilitu, který má v pojmenování, adresy, konfigurace a zabezpečení svých služeb. K tomu, že umístit základní zprávy odeslané před jejich služby tak, aby fungoval jako veřejný koncový bod přístupných. To umožňuje umístit další bezpečnostní před jejich skutečné služby, a usnadňují implementaci škálovat na více systémů verze služby nebo řešení později.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
