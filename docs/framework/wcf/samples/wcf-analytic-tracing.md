---
title: Analytické trasování WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ef636a672d9384e8e3d658f0488cfaadb8d293e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183222"
---
# <a name="wcf-analytic-tracing"></a>Analytické trasování WCF
Tato ukázka ukazuje, jak přidat vlastní trasování události do datového proudu trasování analýzy, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]které Windows Communication Foundation (WCF) zapisuje do ETW v . Analytické stopy mají usnadnit přehled o vašich službách bez placení vysoké pokuty za vysoký výkon. Tato ukázka ukazuje, <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> jak používat api k zápisu událostí, které se integrují se službami WCF.  
  
 Další informace o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> souborech <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>API naleznete v tématu .  
  
 Další informace o trasování událostí v systému Windows naleznete v [tématu Zlepšení ladění a ladění výkonu pomocí eTW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).  
  
## <a name="disposing-eventprovider"></a>Odkládání zprostředkovatele událostí  
 Tato ukázka <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> používá třídu, která implementuje <xref:System.IDisposable?displayProperty=nameWithType>. Při implementaci trasování pro službu WCF je pravděpodobné, <xref:System.Diagnostics.Eventing.EventProvider>že můžete použít prostředky služby 's po dobu životnosti služby. Z tohoto důvodu a pro čitelnost tento vzorek nikdy <xref:System.Diagnostics.Eventing.EventProvider>zlikviduje zabalené . Pokud z nějakého důvodu vaše služba má různé požadavky na trasování a je nutné nakládat s tímto prostředkem, měli byste upravit tuto ukázku v souladu s osvědčenými postupy pro likvidaci nespravovaných prostředků. Další informace o odstranění nespravovaných prostředků naleznete v [tématu Implementace metody dispose](https://docs.microsoft.com/dotnet/standard/garbage-collection/implementing-dispose).  
  
## <a name="self-hosting-vs-web-hosting"></a>Vlastní hosting vs. webhosting  
 Pro služby hostované na webu, WCF analytické trasování poskytují pole s názvem "HostReference", který se používá k identifikaci služby, která vyzařuje trasování. Rozšiřitelné trasování uživatele můžete účastnit tohoto modelu a tato ukázka ukazuje osvědčené postupy pro to. Formát odkazu na webhostingového hostitele, když se ve výsledném řetězci skutečně objeví znak "&#124;" kanálu, může být libovolný z následujících:  
  
- Pokud aplikace není v kořenovém adresáři.  
  
     \<SiteName \<>ApplicationVirtualPath>&#124;\< \<ServiceVirtualPath>&#124;ServiceName>  
  
- Pokud je aplikace v kořenovém adresáři.  
  
     \<Název_webu \<>&#124;servicevirtualpath>&#124;\<servicename>  
  
 Pro služby hostované vlastním hostitelem analytické trasování WCF nenaplňují pole HostReference. Třída `WCFUserEventProvider` v této ukázce se chová konzistentně při použití samoobslužné služby.  
  
## <a name="custom-event-details"></a>Podrobnosti o vlastní události  
 Manifest Zprostředkovatele událostí ETW WCF definuje tři události, které jsou navrženy tak, aby byly emitovány autory služby WCF z kódu služby. V následující tabulce je uveden rozpis tří událostí.  
  
|Událost|Popis|ID události|  
|-----------|-----------------|--------------|  
|Došlo k události UserDefinedInformationEvent|Vyzařujte tuto událost, když se ve vaší službě stane něco, co se stane, což není problém. Můžete například vyzařovat událost po úspěšném volání do databáze.|301|  
|Došlo k upozornění uživateleDefined|Vyzařují tuto událost, když dojde k problému, který může mít za následek selhání v budoucnu. Můžete například vyzařovat událost upozornění při volání databáze selže, ale jste byli schopni obnovit tím, že přejde zpět do redundantní úložiště dat.|302|  
|Došlo k chybě UserDefinedError.|Vyzařujte tuto událost, pokud se vaše služba nechová podle očekávání. Můžete například vyzařovat událost, pokud se nezdaří volání databáze a nelze načíst data z jiného místa.|303|  
  
#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek  
  
1. Pomocí Visual Studia 2012 otevřete soubor řešení WCFAnalyticTracingExtensibility.sln.  
  
2. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.  
  
3. Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.  
  
     Ve webovém prohlížeči klepněte na položku **Calculator.svc**. Identifikátor URI dokumentu WSDL pro službu by se měl zobrazit v prohlížeči. Zkopírujte tento identifikátor URI.  
  
4. Spusťte testovacího klienta WCF (WcfTestClient.exe).  
  
     Testovací klient WCF (WcfTestClient.exe) `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`je umístěn na adrese . Výchozí instalační dir sady Visual Studio `C:\Program Files\Microsoft Visual Studio 10.0`2012 je .  
  
5. V rámci testovacího klienta WCF přidejte službu výběrem **položky Soubor**a potom **přidejte službu**.  
  
     Přidejte adresu koncového bodu do vstupního pole.  
  
6. Klepnutím na **tlačítko OK** zavřete dialogové okno.  
  
     Služba ICalculator je přidána do levého podokna v části **Projekty služeb**.  
  
7. Otevřete aplikaci Prohlížeč událostí.  
  
     Před vyvoláním služby spusťte Prohlížeč událostí a ujistěte se, že protokol událostí naslouchá sledování událostí vyzařovaných ze služby WCF.  
  
8. V nabídce **Start** vyberte **Nástroje pro správu**a potom **prohlížeč událostí**. Povolte protokoly **Analytic a** **Ladění.**  
  
9. Ve stromovém zobrazení v Prohlížeči událostí přejděte do **prohlížeče událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikace aplikačního serveru**. Klepněte pravým tlačítkem myši na **položku Aplikační server-Aplikace**, vyberte příkaz **Zobrazit**a potom **zobrazit protokoly analýzy a ladění**.  
  
     Ujistěte se, že je zaškrtnuta možnost **Zobrazit protokoly analýzy a ladění.** Povolte protokol **Analytická.**  
  
     Ve stromovém zobrazení v Prohlížeči událostí přejděte do **prohlížeče událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**, **Application Server-Applications**a potom **na Analytické**. Klepněte pravým tlačítkem myši na **službu Analytick** a vyberte **příkaz Povolit protokol**.  
  
10. Otestujte službu pomocí testovacího klienta WCF.  
  
    1. V testovacím klientovi WCF poklepejte na **add()** pod uzětem služby ICalculator.  
  
         Metoda **Add()** se zobrazí v pravém podokně se dvěma parametry.  
  
    2. Zadejte 2 pro první parametr a 3 pro druhý parametr.  
  
    3. Chcete-li metodu vyvolat, klepněte na tlačítko **Vyvolat.**  
  
11. Přejděte do okna **Prohlížeče událostí,** které jste již otevřeli. Přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, **microsoft**, **windows**, **aplikační server-aplikace .**  
  
12. Klikněte pravým tlačítkem myši na uzel **Analytická** a vyberte **aktualizovat**.  
  
     Události se zobrazí v pravém podokně.  
  
13. Vyhledejte událost s ID 303 a poklepáním ji otevřete a zkontrolujte její obsah.  
  
     Tato událost byla vyzařována `Add()` metodou služby ICalculator a má datovou část rovnající se "2+3=5".  
  
#### <a name="to-clean-up-optional"></a>Vyčištění (volitelné)  
  
1. Otevřete **Prohlížeč událostí**.  
  
2. Přejděte do **prohlížeče událostí**, **protokolů aplikací a služeb**, společnosti **Microsoft**, **Systému Windows**a **následných aplikací aplikačního serveru**. Klepněte pravým tlačítkem myši na **službu Analytická** a vyberte **příkaz Zakázat protokol**.  
  
3. Přejděte do **prohlížeče událostí**, protokolů aplikací a služeb , **microsoftu**, **systému Windows**, aplikací a **aplikací**a poté do **služby** **Analytic .** Klepněte pravým tlačítkem myši na **položku Analytická** a vyberte příkaz **Vymazat protokol**.  
  
4. Chcete-li události vymazat, klepněte na tlačítko **Vymazat.**  
  
## <a name="known-issue"></a>Známý problém  
 V **Prohlížeči událostí** je známý problém, kdy se může selhat dekódování událostí ETW. Může se zobrazit chybová zpráva, která říká: \<"Popis ID události id> ze zdroje Microsoft-Windows-Aplikační server-aplikace nelze nalézt. Součást, která vyvolává tuto událost, není nainstalována v místním počítači nebo je instalace poškozena. Součást můžete nainstalovat nebo opravit v místním počítači." Pokud narazíte na tuto chybu, vyberte **aktualizovat** z nabídky **Akce.** Událost by pak měla dekódovat správně.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
