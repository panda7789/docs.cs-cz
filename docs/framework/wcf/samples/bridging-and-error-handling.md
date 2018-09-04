---
title: Přemostění a zpracování chyb
ms.date: 03/30/2017
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
ms.openlocfilehash: 6afaddc75855b7e95ad708b2179cabb9aee35001
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514539"
---
# <a name="bridging-and-error-handling"></a>Přemostění a zpracování chyb
Tato ukázka demonstruje použití směrovací službou Windows Communication Foundation (WCF) přemostění komunikace mezi klientem a službu, která pomocí různých vazby. Tento příklad také ukazuje, jak pomocí služby zálohování pro scénáře převzetí služeb při selhání. Směrovací služba je komponenta WCF, který umožňuje snadno do aplikace zahrnout směrovač založené na obsahu. Tato ukázka se přizpůsobí standardní kalkulačky Ukázky WCF na komunikaci pomocí směrovací službou.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce je Kalkulačka klient nakonfigurovaný pro odesílání zpráv do koncového bodu určeného směrovače. Směrovací služba je nakonfigurovaná tak, aby přijímal všechny zprávy odeslané do ní a předávají do koncového bodu, který odpovídá službu kalkulačky. Následující body popisují konfiguraci primární službu kalkulačky, službu kalkulačky zálohování a Kalkulačka klienta a jak probíhá komunikace mezi klientem a službou pomocí směrování služby:  
  
-   Kalkulačka klienta konfigurován pro použití tříd BasicHttpBinding při Kalkulačka služba je nakonfigurována pro použití NetTcpBinding. Směrovací služba automaticky převede zprávy podle potřeby před jejich odesláním do služby kalkulačky a také převádí odpovědi, aby klient Kalkulačka přístup.  
  
-   Směrovací služba ví o dvě služby Kalkulačka: primární Kalkulačka službu a službu kalkulačky zálohování. Směrovací služby se nejprve pokusí komunikovat s primární koncový bod služby kalkulačku. Pokud tento pokus selže z důvodu koncový bod je mimo provoz, směrovací služba potom se pokusí o komunikaci s koncovým bodem zálohování Kalkulačka služby.  
  
 Proto zpráv odeslaných z klienta jsou přijímány směrovače a jsou přesměrovány do aktuální Kalkulačka služby. Pokud koncový bod služby kalkulačky je vypnutý, směrovací službou směruje zprávy do koncového bodu Kalkulačka služby zálohování. Zprávy ze služby zálohování Kalkulačka odesílají zpět do služby směrovač, který je zase předá zpět do klienta kalkulačky.  
  
> [!NOTE]
>  Seznam zálohování může mít více než jeden koncový bod definovaný. V tomto případě pokud koncový bod služby zálohování je mimo provoz, směrovací služba pokusí připojit k další zálohování koncový bod v seznamu dokud neproběhne úspěšné připojení.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete RouterBridgingAndErrorHandling.sln.  
  
2.  V sadě Visual Studio stiskněte klávesu F5 nebo CTRL + SHIFT + B  
  
    1.  Pokud chcete automaticky spouštět nezbytné projektů při stisknutí klávesy F5, klikněte pravým tlačítkem na řešení, vyberte možnost **vlastnosti**a **spouštěný projekt** pod uzlem **společné vlastnosti**vyberte **více projektů po spuštění**a nastavte všechny projekty **Start**.  
  
    2.  Při vytváření projektu pomocí kombinace kláves CTRL + SHIFT + B, spusťte následující aplikace:  
  
        1.  Kalkulačka klienta (. / CalculatorClient/bin/client.exe)  
  
        2.  Kalkulačka služby (. / CalculatorService/bin/service.exe)  
  
        3.  Služba směrování (. / RoutingService/bin/RoutingService.exe)  
  
3.  V klientovi kalkulačky stisknutím klávesy ENTER klienta.  
  
     Byste měli vidět následující výstup:  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo souboru App.config  
 Ukázka lodí umožňují definovat chování ve směrovači použít soubor App.config. Můžete také změnit název souboru App.config na něco jiného, tak, aby nebyl rozpoznán a zrušte komentář u volání metod, které `ConfigureRouterViaCode()`. Některé z metod má za následek stejné chování směrovače.  
  
### <a name="scenario"></a>Scénář  
 Tato ukázka předvádí, směrovač služeb funguje jako popisovač most a Chyba protokolu. V tomto scénáři žádné směrování na základě obsahu dojde k; směrovací služba funguje jako uzel transparentní proxy server nakonfigurovaný tak, aby předávání zpráv přímo do předkonfigurovaného sadu cílové koncové body. Směrovací služba provádí také transparentně zpracování chyb vzniklých se ho pokusí odeslat ke koncovým bodům, že je nakonfigurován pro komunikaci s další kroky. Služba směrování podle funguje jako most protokol, umožňuje uživateli definovat jeden protokol pro externí komunikaci a druhý k interní komunikace.  
  
### <a name="real-world-scenario"></a>Reálné scénáře  
 Contoso chce poskytovat interoperabilní služby koncového bodu na světě, a optimalizace výkonu interně. Proto zpřístupňuje jeho služeb na celém světě prostřednictvím koncového bodu pomocí BasicHttpBinding, zatímco interně pomocí směrovací službou přemostění toto připojení ke koncovému bodu pomocí NetTcpBinding, které využívají jeho služby. Kromě toho Contoso chce, aby se jeho služba bude odolný vůči chybám dočasných výpadků ve všech svých produkčních služeb a proto Virtualizuje několik koncových bodů za služby na směrovač pomocí uživatele chyba možnosti automatické převzetí služeb při selhání zpracování zálohování koncových bodů v případě potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
