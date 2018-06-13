---
title: Analytické trasování WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: e13aa0f7d0dbc48bedad0a9c639695ed038b9303
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807095"
---
# <a name="wcf-analytic-tracing"></a>Analytické trasování WCF
Tento příklad ukazuje, jak přidat vlastní trasování událostí do datového proudu analytické trasování, které Windows Communication Foundation (WCF) zapisuje do trasování událostí pro Windows v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Analytické trasování jsou určené můžete snadno získat viditelnost do služeb bez placení snížení výkonu vysoké. Tento příklad ukazuje způsob použití <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> rozhraní API zápisu události, které se integrují se službou WCF.  
  
 Další informace o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> rozhraní API, najdete v části <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Další informace o trasování událostí v systému Windows, najdete v části [vylepšení ladění a optimalizace výkonu s ETW](http://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Uvolnění EventProvider  
 V tomto příkladu <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> třídy, které implementuje <xref:System.IDisposable?displayProperty=nameWithType>. Při implementaci trasování pro služby WCF, je pravděpodobné, že můžete používat <xref:System.Diagnostics.Eventing.EventProvider>na prostředky po dobu jeho existence služby. Z tohoto důvodu a čitelnější, tato ukázka nikdy uvolní zabalenou <xref:System.Diagnostics.Eventing.EventProvider>. Pokud z nějakého důvodu vaše služba má jiné požadavky pro trasování a vy musíte dispose tohoto prostředku a potom upravte tuto ukázku v souladu s doporučené postupy pro uvolnění nespravovaných prostředků. Další informace o uvolnění nespravovaných prostředků najdete v tématu [implementace metody Dispose](http://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Vlastní hostování vs. Hostování webů  
 Analytické trasování WCF na hostované webové služby, zadejte pole, s názvem "HostReference", který se používá k identifikaci služby, který je generování trasování. Trasování rozšiřitelnými uživatelskými mohl účastnit tohoto modelu a tento příklad znázorňuje osvědčené postupy, jak to udělat. Formát webového hostitele odkazovat při kanálu '&#124;' znak zobrazí se ve skutečnosti ve výsledné řetězec může být jakýkoli z následujících akcí:  
  
-   Pokud aplikace není v kořenovém adresáři.  
  
     \<Název_lokality >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   Pokud aplikace je v kořenovém adresáři.  
  
     \<Název_lokality >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 Pro samoobslužné hostované služby analytické trasování WCF je není vyplňte pole "HostReference". `WCFUserEventProvider` – Třída v této ukázce chová konzistentně při použití s vlastním hostováním služby.  
  
## <a name="custom-event-details"></a>Podrobnosti o vlastní události  
 Manifest zprostředkovatele události trasování událostí pro Windows na WCF definuje tři události, které mají být vysílaných autorům služby WCF v kódu služby. Následující tabulka ukazuje rozpis ze tří událostí.  
  
|Událost|Popis|ID události|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Emitování tuto událost, pokud ve službě, která se nejedná o problém se stane něco Poznámka. Událost může například emitování po úspěšném provedení volání do databáze.|301|  
|UserDefinedWarningOccurred|Emitování Tato událost, když dojde k potížím, které může vést k selhání v budoucnu. Například může vysílat upozorňovací událost, pokud selže volání databáze, ale bylo možné obnovit tím, že probíhá návrat k úložišti dat redundantní.|302|  
|UserDefinedErrorOccurred|Emitování tuto událost, pokud vaše služba nepodaří chovat podle očekávání. Může například emitování událost, pokud selže volání databáze a nelze načíst data z jiného místa.|303|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení WCFAnalyticTracingExtensibility.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
     Ve webovém prohlížeči, klikněte na tlačítko **Calculator.svc**. Identifikátor URI dokumentu WSDL služby by se zobrazit v prohlížeči. Zkopírujte tento identifikátor URI.  
  
4.  Spuštění testovacího klienta WCF (WcfTestClient.exe).  
  
     Testovacího klienta WCF (WcfTestClient.exe) se nachází v \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] nainstalovat Dir > \Common7\IDE\ WcfTestClient.exe (výchozí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir instalace je C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  V rámci testovacího klienta WCF, přidejte službu tak, že vyberete **soubor**a potom **přidat službu**.  
  
     Přidáte adresa koncového bodu do vstupního pole.  
  
6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
     Přidání služby ICalculator v levém podokně v části **Moje projekty služeb**.  
  
7.  Otevřete Prohlížeč událostí aplikace.  
  
     Před vyvoláním služby, spusťte Prohlížeč událostí a zkontrolujte, zda protokol událostí naslouchá pro sledování události vygenerované ze služby WCF.  
  
8.  Z **spustit** nabídce vyberte možnost **nástroje pro správu**a potom **Prohlížeč událostí**. Povolit **analytické** a **ladění** protokoly.  
  
9. Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom **Serveru aplikace – aplikace**. Klikněte pravým tlačítkem na **serveru aplikace – aplikace**, vyberte **zobrazení**a potom **zobrazit protokoly pro ladění a**.  
  
     Ujistěte se, že **zobrazit protokoly pro ladění a** zaškrtnutá možnost. Povolit **analytické** protokolu.  
  
     Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru – aplikace**a potom **analytické**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.  
  
10. Testování služby pomocí testovacího klienta WCF.  
  
    1.  V testu klienta WCF, klikněte dvakrát na **Add()** pod uzlem služby ICalculator.  
  
         **Add()** metoda se zobrazí v pravém podokně se dva parametry.  
  
    2.  Zadejte pro první parametr 2 a 3 pro druhý parametr.  
  
    3.  Klikněte na tlačítko **Invoke** k vyvolání metody.  
  
11. Přejděte na **Prohlížeč událostí** okno, které už máte otevřený. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**.  
  
12. Klikněte pravým tlačítkem myši **analytické** uzel a vyberte možnost **aktualizovat**.  
  
     V pravém podokně se zobrazí události.  
  
13. Vyhledejte událost s ID 303 a dvojím kliknutím ho otevřít a zkontrolovat její obsah.  
  
     Tato událost byla vysílaných `Add()` metoda služby ICalculator a má datovou část rovno "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Vyčistěte (volitelné)  
  
1.  Otevřete **Prohlížeč událostí**.  
  
2.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.  
  
3.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru aplikace**a potom **analytické**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.  
  
4.  Klikněte na tlačítko **vymazat** vymazat události.  
  
## <a name="known-issue"></a>Známý problém  
 Je známý problém nástroje **Prohlížeč událostí** kde může dojít k selhání dekódovat události trasování událostí. Mohou se zobrazit chybová zpráva s upozorněním: "popis k ID události \<id > ze zdroje aplikaci Microsoft Windows Server – aplikace nebyla nalezena. Buď není nainstalována součást, který vyvolává tuto událost v místním počítači nebo je poškozená instalace. Můžete nainstalovat nebo opravit součásti v místním počítači." Pokud dojde k této chybě, vyberte **aktualizovat** z **akce** nabídky. Události by pak dekódovat správně.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
