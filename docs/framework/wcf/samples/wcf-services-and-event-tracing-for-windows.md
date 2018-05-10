---
title: Služby WCF a Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Služby WCF a Trasování událostí pro Windows
Tento příklad znázorňuje způsob použití analytické trasování ve Windows Communication Foundation (WCF) pro vydávání událostí v události trasování pro Windows (ETW). Analytické trasování jsou události vygenerované v klíčových bodů v zásobníku WCF, které umožňují řešení potíží s služby WCF v provozním prostředí.  
  
 Analytické trasování ve službách WCF je trasování, který lze zapnout v produkčním prostředí s minimálním dopadem na výkon. Toto trasování jsou vydávány jako události relaci trasování událostí pro Windows.  
  
 Tato ukázka obsahuje základní služby WCF, ve kterém jsou události vygenerované ze služby do protokolu událostí, který lze zobrazit pomocí prohlížeče událostí. Je také možné spustit relaci vyhrazené trasování událostí pro Windows, která naslouchá události ze služby WCF. Ukázka zahrnuje skript pro vytvoření vyhrazené relace trasování událostí pro Windows, která ukládá události v binární soubor, který lze číst pomocí prohlížeče událostí.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení EtwAnalyticTraceSample.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
     Ve webovém prohlížeči, klikněte na tlačítko **Calculator.svc**. Identifikátor URI dokumentu WSDL služby by se zobrazit v prohlížeči. Zkopírujte tento identifikátor URI.  
  
     Ve výchozím nastavení, služba začne naslouchat požadavkům na portu 1378 (http://localhost:1378/Calculator.svc).  
  
4.  Spuštění testovacího klienta WCF (WcfTestClient.exe).  
  
     Testovacího klienta WCF (WcfTestClient.exe) se nachází v \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] nainstalovat Dir > \Common7\IDE\ WcfTestClient.exe (výchozí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir instalace je C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  V rámci testovacího klienta WCF, přidejte službu tak, že vyberete **soubor**a potom **přidat službu**.  
  
     Přidáte adresa koncového bodu do vstupního pole. Výchozí hodnota je http://localhost:1378/Calculator.svc.  
  
6.  Otevřete Prohlížeč událostí aplikace.  
  
     Před vyvoláním služby, spusťte Prohlížeč událostí a zkontrolujte, zda protokol událostí naslouchá pro sledování události vygenerované ze služby WCF.  
  
7.  Z **spustit** nabídce vyberte možnost **nástroje pro správu**a potom **Prohlížeč událostí**.  Povolit **analytické** a **ladění** protokoly.  
  
8.  Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom **Serveru aplikace – aplikace**. Klikněte pravým tlačítkem na **serveru aplikace – aplikace**, vyberte **zobrazení**a potom **zobrazit protokoly pro ladění a**.  
  
     Ujistěte se, že **zobrazit protokoly pro ladění a** zaškrtnutá možnost.  
  
9. Povolit **analytické** protokolu.  
  
     Ve stromovém zobrazení v prohlížeči událostí, přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom **Serveru aplikace – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **povolit protokol**.  
  
#### <a name="to-test-the-service"></a>K testování služby  
  
1.  Přepněte zpět na testovacího klienta WCF a dvakrát klikněte na `Divide` a ponechte výchozí hodnoty, které určují jmenovatel 0.  
  
     Pokud jmenovatel hodnotu 0, služba vyvolá chybu.  
  
2.  Pozorovat, jaké události vygenerované ze služby.  
  
     Přepněte zpět do prohlížeče událostí a přejděte do **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom **Serveru aplikace – aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **aktualizovat**.  
  
     Události analytického trasování WCF se zobrazí v prohlížeči událostí. Zjistíte, že vzhledem k tomu, že byl vyvolané chybu služby, kterou chybovou událost trasování je zobrazena události prohlížeč.  
  
3.  Opakujte kroky 1 a 2, ale s platné vstupní hodnoty. Hodnota `N2` parametr může být číslo než 0.  
  
     Aktualizujte analytické kanál zobrazíte WCF události nezahrnují všechny chybové události.  
  
 Ukázka ukazuje analytického trasování události vygenerované ze služby WCF.  
  
#### <a name="to-cleanup-optional"></a>Pro čištění (volitelné)  
  
1.  Otevřete Prohlížeč událostí.  
  
2.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **zakázat protokol**.  
  
3.  Přejděte na **Prohlížeč událostí**, **protokoly aplikací a služeb**, **Microsoft**, **Windows**a potom  **Aplikace serveru aplikace**. Klikněte pravým tlačítkem na **analytické** a vyberte **vymazat protokol**.  
  
4.  Vyberte **vymazat** možnost Vymazat události.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
