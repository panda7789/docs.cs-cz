---
title: Analytické trasování WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ba4f1778059f7b960eebd42822048fa031e6961e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044550"
---
# <a name="wcf-analytic-tracing"></a>Analytické trasování WCF
Tento příklad ukazuje, jak přidat vlastní trasovací události do datového proudu analytických trasování, které Windows Communication Foundation (WCF) zapisuje do trasování [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]událostí pro Windows v. Analytická trasování jsou určena k tomu, aby bylo možné snadno získat přehled o službách bez placení vysokého snížení výkonu. V této ukázce se dozvíte, <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> jak pomocí rozhraní API zapisovat události, které se integrují se službami WCF.  
  
 Další informace o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> rozhraních API naleznete v <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>tématu.  
  
 Další informace o trasování událostí ve Windows najdete v tématu [vylepšení ladění a ladění výkonu pomocí ETW](https://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Disposing – EventProvider  
 Tato ukázka používá <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> třídu, která implementuje <xref:System.IDisposable?displayProperty=nameWithType>. Při implementaci trasování pro službu WCF je pravděpodobně vhodné použít <xref:System.Diagnostics.Eventing.EventProvider>prostředky pro celou dobu životnosti služby. Z tohoto důvodu a pro účely čitelnosti Tato ukázka nikdy neodstraní zabalenou <xref:System.Diagnostics.Eventing.EventProvider>. Pokud z nějakého důvodu má vaše služba různé požadavky na trasování a musíte tento prostředek odstranit, měli byste tuto ukázku upravit v souladu s osvědčenými postupy pro odstraňování nespravovaných prostředků. Další informace o odstraňování nespravovaných prostředků naleznete v tématu [implementace metody Dispose](https://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Samoobslužné hostování vs. Web Hosting  
 V případě služeb hostovaných na webu poskytuje analytická trasování WCF pole s názvem "HostReference", které slouží k identifikaci služby, která vysílá trasování. V tomto modelu se můžou zúčastnit rozšiřitelné trasování uživatelů a tato ukázka demonstruje osvědčené postupy. Formát odkazu webového hostitele v případě, že se ve výsledném řetězci skutečně zobrazuje znak kanálu&#124;, může být kterýkoli z následujících:  
  
- Pokud aplikace není v kořenovém adresáři.  
  
     \<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
- Pokud se aplikace nachází v kořenovém adresáři.  
  
     \<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName>  
  
 V případě samoobslužných služeb se pro analytická trasování WCF neplní pole HostReference. Třída `WCFUserEventProvider` v této ukázce se při použití v rámci samoobslužné služby chová konzistentně.  
  
## <a name="custom-event-details"></a>Podrobnosti o vlastní události  
 Manifest zprostředkovatele událostí ETW WCF definuje tři události, které jsou navržené tak, aby tvůrci služby WCF vygenerovali v rámci kódu služby. Následující tabulka uvádí rozpis tří událostí.  
  
|Událost|Popis|ID události|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Vygenerovat tuto událost, pokud se ve vaší službě stane něco poznámky, která není problémem. Můžete například vygenerovat událost po úspěšném provedení volání do databáze.|301|  
|UserDefinedWarningOccurred|Vygeneruje tuto událost, když dojde k problému, který může v budoucnu způsobit selhání. Například můžete vygenerovat událost upozornění, když se volání databáze nepovede, ale jste se mohli zotavit zpátky do redundantního úložiště dat.|302|  
|UserDefinedErrorOccurred|Vygeneruje tuto událost, když se služba nedokáže chovat podle očekávání. Můžete například vygenerovat událost, pokud dojde k chybě volání databáze a nemůžete načíst data jinde.|303|  
  
#### <a name="to-use-this-sample"></a>Použití této ukázky  
  
1. Pomocí sady Visual Studio 2012 otevřete soubor řešení WCFAnalyticTracingExtensibility. sln.  
  
2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.  
  
     Ve webovém prohlížeči klikněte na **Kalkulačka. svc**. V prohlížeči by se měl zobrazit identifikátor URI dokumentu WSDL pro službu. Zkopírujte tento identifikátor URI.  
  
4. Spusťte testovacího klienta WCF (WcfTestClient. exe).  
  
     Testovací klient služby WCF (WcfTestClient. exe) je umístěný na `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`adrese. Výchozí instalační adresář sady Visual Studio 2012 je `C:\Program Files\Microsoft Visual Studio 10.0`.  
  
5. V rámci testovacího klienta WCF přidejte službu tak, že vyberete **soubor**a pak **přidáte službu**.  
  
     Do vstupního pole přidejte adresu koncového bodu.  
  
6. Kliknutím na tlačítko **OK** zavřete dialogové okno.  
  
     Služba ICalculator se přidá v levém podokně v části **projekty služeb**.  
  
7. Otevřete Prohlížeč událostí aplikace.  
  
     Před vyvoláním služby spusťte Prohlížeč událostí a zajistěte, aby protokol událostí naslouchal sledování událostí vygenerovaných ze služby WCF.  
  
8. V nabídce **Start** vyberte **Nástroje pro správu**a potom **Prohlížeč událostí**. Povolte protokoly pro **analýzu** a **ladění** .  
  
9. Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikační server – aplikace**. Klikněte pravým tlačítkem na **aplikační server – aplikace**, vyberte **Zobrazit**a pak **Zobrazte protokoly o analýze a ladění**.  
  
     Zajistěte, aby byla zaškrtnuta možnost **Zobrazit protokoly o analýze a ladění** . Povolte **analytický** protokol.  
  
     Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**a pak na **analytické**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol**.  
  
10. Otestujte službu pomocí testovacího klienta WCF.  
  
    1. V testovacím klientovi WCF poklikejte na **Přidat ()** pod uzlem služby ICalculator.  
  
         Metoda **Add ()** se zobrazí v pravém podokně se dvěma parametry.  
  
    2. Zadejte 2 pro první parametr a 3 pro druhý parametr.  
  
    3. Pro vyvolání metody klikněte na **vyvolat** .  
  
11. Přejdete do okna **Prohlížeč událostí** , které jste už otevřeli. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **aplikační server – aplikace**.  
  
12. Klikněte pravým tlačítkem na uzel analýzy a vyberte **aktualizovat**.  
  
     Události se zobrazí v pravém podokně.  
  
13. Vyhledejte událost s ID 303 a poklikejte na ni, abyste ji otevřeli a zkontrolovali její obsah.  
  
     Tato událost byla vygenerována `Add()` metodou služby ICalculator a má datovou část, která se rovná "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Vyčištění (volitelné)  
  
1. Otevřete **Prohlížeč událostí**.  
  
2. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak na **aplikace-Server-aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **zakázat protokol**.  
  
3. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **Application-Server-Applications**a pak na **analytické**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **Vymazat protokol**.  
  
4. Kliknutím na tlačítko **Vymazat** události vymažete.  
  
## <a name="known-issue"></a>Známý problém  
 Došlo k známému problému **Prohlížeč událostí** , kde se nemusí podařit dekódovat události ETW. Může se zobrazit chybová zpráva, která říká: Popis události \<ID ID > ze zdrojového serveru Microsoft-Windows-Application Server – aplikace se nenašly. Buď není v místním počítači nainstalována komponenta, která vyvolává tuto událost, nebo je instalace poškozena. Součást můžete nainstalovat nebo opravit v místním počítači. " Pokud k této chybě dojde, v nabídce **Akce** vyberte **aktualizovat** . Událost by se pak měla správně dekódovat.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky monitorování technologie AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
