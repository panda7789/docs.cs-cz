---
title: Analytické trasování WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: a5e4b82bd28cae18f393a4143325623634d4bbaf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181654"
---
# <a name="wcf-analytic-tracing"></a>Analytické trasování WCF
Tato ukázka předvádí, jak přidat vlastní události trasování do datového proudu analytického trasování, které Windows Communication Foundation (WCF) zapisuje do trasování událostí pro Windows v [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Analytické trasování jsou určené k tomu, aby, získat přehled o vaší služby bez nutnosti platit penalizace vysoký výkon. Tento příklad ukazuje způsob použití <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> rozhraní API pro zápis událostí, které integrace se službami WCF.  
  
 Další informace o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> naleznete v tématu rozhraní API, <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Další informace o trasování událostí ve Windows najdete v tématu [vylepšení ladění a optimalizace výkonu pomocí trasování událostí pro Windows](https://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Připravuje se EventProvider  
 Tento příklad používá <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> třídy, která implementuje <xref:System.IDisposable?displayProperty=nameWithType>. Při implementaci trasování pro služby WCF, je pravděpodobné, že můžete použít <xref:System.Diagnostics.Eventing.EventProvider>od prostředků po dobu životnosti služby. Z tohoto důvodu a pro lepší čitelnost, tato ukázka nikdy uvolní zabalenou <xref:System.Diagnostics.Eventing.EventProvider>. Pokud z nějakého důvodu vaše služba má jiné požadavky při trasování a je musí odstranění tohoto prostředku, pak byste měli upravit tato ukázka podle osvědčených postupů pro uvolnění nespravovaných prostředků. Další informace o uvolnění nespravovaných prostředků najdete v tématu [Implementing a Dispose Method](https://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Hostování na vlastním vs. Hostování webů  
 Analytické trasování WCF. pro hostované webové služby, zadejte pole, s názvem "HostReference", který se používá k identifikaci služby, který generuje trasování. Trasování rozšiřitelnými uživatelskými mohl podílet na tomto modelu a v této ukázce osvědčené postupy to udělat. Formát webového hostitele odkazovat při do kanálu '&#124;"znak se objeví ve skutečnosti ve výsledné řetězce může být jedna z následujících akcí:  
  
-   Pokud aplikace není v kořenovém adresáři.  
  
     \<Název webu % >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<název_služby >  
  
-   Pokud je v kořenovém adresáři.  
  
     \<Název webu % >&#124;\<ServiceVirtualPath >&#124;\<název_služby >  
  
 V místním prostředí služby analytické trasování WCF. není vyplnění pole "HostReference". `WCFUserEventProvider` Třídy v této ukázce se chová konzistentně při použití služby v místním prostředí.  
  
## <a name="custom-event-details"></a>Podrobnosti o vlastní události  
 Manifest zprostředkovatele událostí trasování událostí pro Windows na WCF definuje tři události, které jsou navržené tak, aby byly vypuštěny autory WCF service z v rámci kódu služby. Následující tabulka uvádí rozpis tři události.  
  
|Událost|Popis|ID události|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Vygenerovat tuto událost, pokud ve své službě, která není problém se stane něco Poznámka. Například může vygenerovat událost po úspěšném provedení volání do databáze.|301|  
|UserDefinedWarningOccurred|Generování Tato událost, když dojde k potížím, které může vést k selhání v budoucnu. Například může vygenerovat událost upozornění, když selže volání databáze, ale jste byli schopni obnovit považován za redundantní úložiště.|302|  
|UserDefinedErrorOccurred|Vygenerovat tuto událost, pokud vaše služba selže chovat podle očekávání. Mohou například vysílat událost, pokud selže volání databáze a nešla načíst data z jinde.|303|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí sady Visual Studio 2012, otevřete soubor řešení WCFAnalyticTracingExtensibility.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
     Ve webovém prohlížeči, klikněte na tlačítko **Calculator.svc**. Identifikátor URI dokumentu WSDL pro službu by se zobrazit v prohlížeči. Zkopírujte tento identifikátor URI.  
  
4.  Spustíte klienta testu WCF (WcfTestClient.exe).  
  
     Testovací klient WCF (WcfTestClient.exe) se nachází na `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`. Je adresář instalace sady Visual Studio 2012 výchozí `C:\Program Files\Microsoft Visual Studio 10.0`.  
  
5.  V rámci testovacího klienta WCF, přidání služby tak, že vyberete **souboru**a potom **přidat službu**.  
  
     Přidáte adresu koncového bodu do vstupního pole.  
  
6.  Klikněte na tlačítko **OK** zavřete dialogové okno.  
  
     V levém podokně v části Přidání služby ICalculator **Moje projekty služeb**.  
  
7.  Otevřete Prohlížeč událostí aplikace.  
  
     Před vyvoláním služby, spusťte Prohlížeč událostí a ujistěte se, že je pro sledování události ze služby WCF, protože ho naslouchání v protokolu událostí.  
  
8.  Z **Start** nabídce vyberte možnost **nástroje pro správu**a potom **Prohlížeč událostí**. Povolit **analytické** a **ladění** protokoly.  
  
9. Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak **Aplikace Server-**. Klikněte pravým tlačítkem na **aplikace Server-** vyberte **zobrazení**a potom **zobrazit protokoly ladění a analýzu**.  
  
     Ujistěte se, **zobrazit protokoly ladění a analýzu** zaškrtnutá možnost. Povolit **analytické** protokolu.  
  
     Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace Server-** a potom **analytické**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.  
  
10. Test pomocí testovacího klienta WCF.  
  
    1.  Testovací klient WCF, dvakrát klikněte na panel **Add()** pod uzlem ICalculator služby.  
  
         **Add()** metoda se zobrazí v pravém podokně se dvěma parametry.  
  
    2.  Zadejte pro první parametr 2 a 3 pro druhý parametr.  
  
    3.  Klikněte na tlačítko **Invoke** k vyvolání metody.  
  
11. Přejděte **Prohlížeč událostí** okno, které jste již otevřeli. Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikace Aplikace serveru**.  
  
12. Klikněte pravým tlačítkem myši **analytické** uzel a vyberte možnost **aktualizovat**.  
  
     V pravém podokně se zobrazí události.  
  
13. Najděte událost s ID 303 a dvojím kliknutím ho otevřete a zkontrolujte jeho obsah.  
  
     Tato událost, protože ho vygeneroval `Add()` metody ICalculator služby a datové části je rovno "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Chcete-li vyčistit (volitelné)  
  
1.  Otevřít **Prohlížeč událostí**.  
  
2.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.  
  
3.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**,  **Aplikace serveru**a potom **analytické**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.  
  
4.  Klikněte na tlačítko **vymazat** vymazat události.  
  
## <a name="known-issue"></a>Známý problém  
 Existuje známý problém nástroje **Prohlížeč událostí** kde může dojít k selhání k dekódování událostí trasování událostí pro Windows. Může se zobrazit chybová zpráva s upozorněním: "Popis objektu Event ID \<id > ze zdroje aplikace Microsoft Windows Server – aplikace nebyla nalezena. Součást, která vyvolá tuto událost není nainstalována na místním počítači nebo že je poškozená instalace. Můžete nainstalovat nebo opravit součásti v místním počítači." Pokud dojde k této chybě vyberte **aktualizovat** z **akce** nabídky. Události by pak správně dekódovat.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
