---
title: "Přemostění a zpracování chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: eec60855dc8ce3c611fa0fe3c8668973b43099b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="bridging-and-error-handling"></a>Přemostění a zpracování chyb
Tento příklad ukazuje, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrování služby se používá pro přemostění komunikace mezi klientem a služba, která použít jiný vazby. Tento příklad také ukazuje, jak pomocí služby zálohování pro scénáře převzetí služeb při selhání. Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje do aplikace zahrnout směrovač podle obsahu. Tato ukázka přizpůsobuje standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázka kalkulačku komunikovat pomocí služby směrování.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce kalkulačky klient je nakonfigurován pro odesílání zpráv pro koncový bod vystavené směrovači. Směrovací služba je nakonfigurována tak, aby přijímal všechny zprávy do něj odeslané a předávat je koncový bod, který odpovídá službu kalkulačky. Následující body popisují konfiguraci primární služba kalkulačky, službu kalkulačky zálohování a kalkulačky klienta a jak se stane komunikace mezi klientem a služby pomocí služby směrování:  
  
-   Klient kalkulačky je nakonfigurován k používání BasicHttpBinding, zatímco služba kalkulačky je konfigurovaná pro použití NetTcpBinding. Služba směrování zprávy v případě potřeby automaticky převede před jejich odesláním do služby kalkulačky a také převede odpovědi, aby klient kalkulačky přístup.  
  
-   Směrovací služba ví o dvě služby kalkulačky: primární kalkulačky služba a služba zálohování kalkulačky. Služba směrování se napřed pokusí komunikovat s primární koncový bod služby kalkulačky. Pokud tento pokus selže z důvodu koncový bod se dolů, služba Směrování potom se pokusí o komunikaci s koncovým bodem kalkulačky služby zálohování.  
  
 Proto zpráv odeslaných z klienta jsou přijímány směrovači a jsou přesměrovány do aktuální kalkulačky služby. Pokud koncový bod služby kalkulačky je vypnutý, směrovací služba provádí směrování zprávy do koncového bodu služby kalkulačky zálohování. Zprávy ze služby zálohování kalkulačky jsou odesílány zpět do služby směrovač, který je pak předá zpět do klienta kalkulačky.  
  
> [!NOTE]
>  Seznam zálohování může mít více než jeden koncový bod definované. V takovém případě pokud koncový bod služby zálohování je vypnutý, směrovací služba pokusí připojit k další koncový bod zálohování v seznamu dokud nedojde k úspěšné připojení.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete RouterBridgingAndErrorHandling.sln.  
  
2.  Stisknutím klávesy F5 nebo CTRL + SHIFT + B v sadě Visual Studio  
  
    1.  Pokud chcete automaticky spouštěné projekty potřebné po stisknutí klávesy F5, klikněte pravým tlačítkem na řešení, vyberte **vlastnosti**a v **spouštěný projekt** pod uzlem **společných vlastností**, vyberte **více projektů po spuštění**a nastavte všechny projekty **spustit**.  
  
    2.  Pokud vytvoříte projekt pomocí kombinace kláves CTRL + SHIFT + B, spusťte následující aplikace:  
  
        1.  Klient kalkulačky (. / CalculatorClient/bin/client.exe)  
  
        2.  Službu kalkulačky (. / CalculatorService/bin/service.exe)  
  
        3.  Směrovací služba provádí (. / RoutingService/bin/RoutingService.exe)  
  
3.  V klientovi kalkulačky stiskněte klávesu ENTER pro spuštění klienta.  
  
     Byste měli vidět následující výstup:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo App.config  
 Ukázka lodě, umožňují použít soubor App.config k definování chování směrovače. Můžete taky změnit název souboru App.config na jinou tak, aby nebyla rozpoznána a zrušte komentář u volání metody `ConfigureRouterViaCode()`. Buď metoda výsledkem stejné chování z směrovači.  
  
### <a name="scenario"></a>Scénář  
 Tento příklad znázorňuje směrovač služeb, který funguje jako popisovač most a chyb protokolu. V tomto scénáři žádné směrování na základě obsahu dojde; směrovací služba funguje jako uzel transparentní proxy server nakonfigurovaný tak, aby předat zprávy přímo do předkonfigurované sadu cílové koncové body. Směrovací služba provádí taky transparentního zpracování chyb, které nastat, když se ho pokusí k odeslání do koncových bodů, které je nakonfigurován pro komunikaci s další kroky. Služba směrování podle funguje jako mostu, protokol, umožňuje uživatelům definovat jeden protokol pro externí komunikaci a druhý pro interní komunikaci.  
  
### <a name="real-world-scenario"></a>Scénář skutečných  
 Contoso chce poskytovat interoperabilní služby koncového bodu na světě a optimalizace výkonu interně. Proto zveřejňuje jeho služby na světě prostřednictvím koncový bod pomocí BasicHttpBinding, při interně pomocí služby směrování pro přemostění připojení ke koncovému bodu pomocí NetTcpBinding, který jeho služby používat. Kromě toho Contoso chce jeho nabídky jako odolný vůči chybám dočasných výpadků v některém z jejich produkční služeb služby a proto Virtualizuje několik koncových bodů za použití služby směrovače této funkce, které automaticky převzetí služeb při selhání na zpracování chyb Koncové body zálohování v případě potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
