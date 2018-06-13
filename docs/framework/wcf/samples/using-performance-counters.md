---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 8784b4a481b8313d370aad1d8f265dcb44ab3ed6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807316"
---
# <a name="using-performance-counters"></a>Použití čítačů výkonu
Tento příklad znázorňuje, jak získat přístup k čítače výkonu systému Windows Communication Foundation (WCF) a postup vytvoření čítače výkonu definovaný uživatelem. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 V této ukázce klienta volá čtyři metody `ICalculator` služby. Klient i nadále to provést, dokud přerušení uživatelem. Služba zůstává beze změny.  
  
 V části Diagnostika souboru Web.config pro službu, jsou povoleny čítače výkonu, jak je znázorněno v následující ukázka konfigurace.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Tuto úlohu lze provést pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Když jsou povoleny čítače výkonu, povolí se celá sada čítače výkonu WCF pro službu. Rozhraní .NET Framework automaticky udržuje údaje o výkonu na třech úrovních: `ServiceModelService`, `ServiceModelEndpoint` a `ServiceModelOperation`. Každý z těchto úrovní má čítače výkonu, jako je například "Volání", "Volání za sekundu" a "Zabezpečení volání není oprávněn".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Zobrazení dat výkonu  
  
1.  Spusťte nástroj Sledování výkonu kliknutím **spustit**, **spustit...** , zadejte `perfmon` a klikněte na tlačítko **OK,** nebo z ovládacích panelů, vyberte **nástroje pro správu** a dvakrát klikněte na **výkonu**.  
  
    > [!NOTE]
    >  Čítače nelze přidat, dokud ukázkový kód běží.  
  
2.  Odeberte čítače výkonu, které jsou uvedeny tak, že je vyberete a stisknutím klávesy Delete.  
  
3.  Přidání čítačů WCF tak, že kliknete pravým tlačítkem v podokně grafu a výběr **přidat čítače**. V **přidat čítače** dialogové okno, vyberte **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 nebo ServiceModelService 3.0.0.0** v objektu výkonu rozevírací seznam. Vyberte čítače, které chcete zobrazit v seznamu.  
  
    > [!NOTE]
    >  Neexistují žádné čítače výkonu WCF pro služby, pokud neexistují žádné služby WCF na tomto počítači spuštěna.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Povolení čítačů pomocí editoru konfigurace  
  
1.  Otevřete instanci SvcConfigEditor.exe.  
  
2.  V nabídce Soubor klikněte na tlačítko **otevřete** a pak klikněte na tlačítko **konfiguračního souboru...** .  
  
3.  Přejděte do složky služby ukázkovou aplikaci a otevřete soubor Web.config.  
  
4.  Klikněte na tlačítko **diagnostiky** ve stromové struktuře konfigurace.  
  
5.  Přepnutí **čítače výkonu** v **diagnostiky** okno a zobrazit všechny'.  
  
6.  Uložit konfigurační soubor a ukončete editor.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
