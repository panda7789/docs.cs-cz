---
title: "Hello World se směrovací službou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f1d068894c9ad28d786c7b433c56b6d0fd79acc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hello-world-with-the-routing-service"></a>Hello World se směrovací službou
Tento příklad ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrovací služby. Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje směrovač na základě obsahu do aplikace zahrnout. Tato ukázka přizpůsobuje standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázka kalkulačku na komunikaci pomocí služby směrování. V této ukázce kalkulačky klient je nakonfigurován pro odesílání zpráv pro koncový bod vystavené směrovači. Směrovací služby je nakonfigurován tak, aby přijímal všechny zprávy do něj odeslané a předávat je koncový bod, který odpovídá službu kalkulačky. Proto jsou zpráv odeslaných z klienta přijatých směrovači a přesměrovala ke službě skutečné kalkulačky. Zprávy ze služby kalkulačky jsou odesílány zpět na směrovač, který je pak předá zpět do klienta kalkulačky.  
  
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
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
