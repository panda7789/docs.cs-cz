---
title: Služby WCF a Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 945daa305db9fe6785e1624e2dbb2e975cd8e94b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119571"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Služby WCF a Trasování událostí pro Windows
Tento příklad ukazuje, jak pomocí analytického trasování ve Windows Communication Foundation (WCF) vysílat události do Event Tracing for Windows (ETW). Analytické trasování jsou události, protože ho na klíčových místech v zásobníku WCF, které umožňují Poradce při potížích pro služby WCF v produkčním prostředí.

 Analytické trasování ve službách WCF je trasování, který je možné zapnout v produkčním prostředí s minimálním dopadem na výkon. Trasování jsou emitovány jako události do relace trasování událostí pro Windows.

 Tato ukázka obsahuje základní služby WCF, ve které události se vysílají ze služby do protokolu událostí, které můžete zobrazit pomocí prohlížeče událostí. Také je možné spustit relaci vyhrazené trasování událostí pro Windows, který naslouchá událostem ze služby WCF. Ukázka zahrnuje skript k vytvoření vyhrazených relace trasování událostí pro Windows, který uchovává události v binárním souboru, který může číst pomocí prohlížeče událostí.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1.  Pomocí sady Visual Studio 2012, otevřete soubor řešení EtwAnalyticTraceSample.sln.

2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

3.  Abyste mohli spustit řešení, stiskněte CTRL + F5.

     Ve webovém prohlížeči, klikněte na tlačítko **Calculator.svc**. Identifikátor URI dokumentu WSDL pro službu by se zobrazit v prohlížeči. Zkopírujte tento identifikátor URI.

     Ve výchozím nastavení, služba začne naslouchat požadavkům na portu 1378 `http://localhost:1378/Calculator.svc`.

4.  Spustíte klienta testu WCF (WcfTestClient.exe).

     Testovací klient WCF (WcfTestClient.exe) se nachází na `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Je adresář instalace sady Visual Studio 2012 výchozí `C:\Program Files\Microsoft Visual Studio 10.0`.

5.  V rámci testovacího klienta WCF, přidání služby tak, že vyberete **souboru**a potom **přidat službu**.

     Přidáte adresu koncového bodu do vstupního pole. Výchozí hodnota je `http://localhost:1378/Calculator.svc`.

6.  Otevřete Prohlížeč událostí aplikace.

     Před vyvoláním služby, spusťte Prohlížeč událostí a ujistěte se, že je pro sledování události ze služby WCF, protože ho naslouchání v protokolu událostí.

7.  Z **Start** nabídce vyberte možnost **nástroje pro správu**a potom **Prohlížeč událostí**.  Povolit **analytické** a **ladění** protokoly.

8.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak **Aplikace Server-**. Klikněte pravým tlačítkem na **aplikace Server-** vyberte **zobrazení**a potom **zobrazit protokoly ladění a analýzu**.

     Ujistěte se, **zobrazit protokoly ladění a analýzu** zaškrtnutá možnost.

9. Povolit **analytické** protokolu.

     Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak **Aplikace Server-**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.

#### <a name="to-test-the-service"></a>K otestování služby

1.  Přepněte zpět do klienta testu WCF a dvakrát klikněte na panel `Divide` a ponechte výchozí hodnoty, které určují jmenovatelem 0.

     Je-li jmenovatelem 0, služba vyvolá chybu.

2.  Sledujte události generované ze služby.

     Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a pak **Aplikace Server-**. Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**.

     Události analytického trasování WCF se zobrazí v prohlížeči událostí. Zjistíte, že protože způsobil chybu na službu, kterou událost trasování chyby je zobrazena v události prohlížeč.

3.  Opakujte kroky 1 a 2, ale s platné vstupy. Hodnota `N2` parametr může být cokoli jiného než 0.

     Aktualizovat analytického kanálu zobrazíte WCF událostí neobsahují všechny chybové události.

 Ukázce události analytického trasování ze služby WCF, protože ho.

#### <a name="to-cleanup-optional"></a>Vyčistit (volitelné)

1.  Otevřete Prohlížeč událostí.

2.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.

3.  Přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.

4.  Zvolte **vymazat** možnost pro vymazání událostí.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
