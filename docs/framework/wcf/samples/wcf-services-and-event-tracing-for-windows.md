---
title: Služby WCF a Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 5bf965ad6a9997ec0603325f246679cf42662a52
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094810"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Služby WCF a Trasování událostí pro Windows
Tato ukázka předvádí, jak použít analytické trasování v Windows Communication Foundation (WCF) k vygenerování událostí v trasování událostí pro Windows (ETW). Analytická trasování jsou události vydávané na klíčových místech v zásobníku WCF, které umožňují řešení potíží se službami WCF v produkčním prostředí.

 Analytická trasování ve službách WCF je trasování, které je možné zapnout v produkčním prostředí s minimálním dopadem na výkon. Tato trasování jsou generována jako události v relaci trasování událostí pro Windows.

 Tato ukázka obsahuje základní službu WCF, ve které jsou události emitovány ze služby do protokolu událostí, který lze zobrazit pomocí Prohlížeč událostí. Je také možné spustit vyhrazenou relaci ETW, která naslouchá událostem ze služby WCF. Ukázka obsahuje skript pro vytvoření vyhrazené relace trasování událostí pro Windows, která ukládá události do binárního souboru, který je možné číst pomocí Prohlížeč událostí.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2012 otevřete soubor řešení EtwAnalyticTraceSample. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.

     Ve webovém prohlížeči klikněte na **Kalkulačka. svc**. V prohlížeči by se měl zobrazit identifikátor URI dokumentu WSDL pro službu. Zkopírujte tento identifikátor URI.

     Ve výchozím nastavení služba zahajuje naslouchání požadavkům na portu 1378 `http://localhost:1378/Calculator.svc`.

4. Spusťte testovacího klienta WCF (WcfTestClient. exe).

     Testovací klient služby WCF (WcfTestClient. exe) je umístěný na adrese `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Výchozí instalační adresář sady Visual Studio 2012 je `C:\Program Files\Microsoft Visual Studio 10.0`.

5. V rámci testovacího klienta WCF přidejte službu tak, že vyberete **soubor**a pak **přidáte službu**.

     Do vstupního pole přidejte adresu koncového bodu. Výchozí formát je `http://localhost:1378/Calculator.svc`.

6. Otevřete Prohlížeč událostí aplikace.

     Před vyvoláním služby spusťte Prohlížeč událostí a zajistěte, aby protokol událostí naslouchal sledování událostí vygenerovaných ze služby WCF.

7. V nabídce **Start** vyberte **Nástroje pro správu**a potom **Prohlížeč událostí**.  Povolte protokoly pro **analýzu** a **ladění** .

8. Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikační server – aplikace**. Klikněte pravým tlačítkem na **aplikační server – aplikace**, vyberte **Zobrazit**a pak **Zobrazte protokoly o analýze a ladění**.

     Zajistěte, aby byla zaškrtnuta možnost **Zobrazit protokoly o analýze a ladění** .

9. Povolte **analytický** protokol.

     Ve stromovém zobrazení v Prohlížeč událostí přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikační server – aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **Povolit protokol**.

#### <a name="to-test-the-service"></a>Testování služby

1. Přepněte zpátky na testovacího klienta WCF a dvakrát klikněte na `Divide` a ponechte výchozí hodnoty, které určují jmenovatele 0.

     Pokud je jmenovatel 0, vyvolá služba chybu.

2. Sledujte události emitované ze služby.

     Přepněte zpět na Prohlížeč událostí a přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom na **aplikační server – aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte **aktualizovat**.

     Události analytického trasování WCF se zobrazí v prohlížeči událostí. Všimněte si, že protože služba vyvolala chybu, zobrazí se v prohlížeči událostí událost trasování chyby.

3. Opakujte kroky 1 a 2, ale s platnými vstupy. Hodnota parametru `N2` může být libovolné číslo jiné než 0.

     Aktualizujte analytickou kanál, aby se zobrazily události WCF, které neobsahují žádné chybové události.

 Ukázka demonstruje události analytického trasování emitované ze služby WCF.

#### <a name="to-cleanup-optional"></a>K vyčištění (volitelné)

1. Otevřete Prohlížeč událostí.

2. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak na **aplikace-Server-aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **zakázat protokol**.

3. Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak na **aplikace-Server-aplikace**. Klikněte pravým tlačítkem na možnost **analytické** a vyberte možnost **Vymazat protokol**.

4. Kliknutím na možnost **Vymazat** vymažte události.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Viz také

- [Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
