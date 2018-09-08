---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 787a3d08b463980721fb207d029057e14618db5e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131882"
---
# <a name="using-performance-counters"></a>Použití čítačů výkonu
Tato ukázka předvádí, jak získat přístup k čítače výkonu Windows Communication Foundation (WCF) a jak vytvořit uživatelsky definovaným výkonem čítače. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 V této ukázce, klient volá čtyři metody `ICalculator` služby. Klient i nadále to provést, dokud je přerušeno uživatelem. Služba zůstane beze změny.  
  
 V části Diagnostika souboru Web.config pro službu, jsou povoleny čítače výkonu, jak je znázorněno v následující ukázková konfigurace.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 Tato úloha je možné provést pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Když jsou povoleny čítače výkonu, celou sadu čítače výkonu WCF je povolen pro službu. Rozhraní .NET Framework automaticky udržuje data o výkonu na třech úrovních: `ServiceModelService`, `ServiceModelEndpoint` a `ServiceModelOperation`. Každá z těchto úrovní obsahuje čítače výkonu, jako je například "Volání", "Volání za sekundu" a "Zabezpečení volání nemáte oprávnění".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Chcete-li zobrazit údaje o výkonu  
  
1.  Spustit nástroj Sledování výkonu kliknutím **Start**, **spuštění...** , zadejte `perfmon` a klikněte na tlačítko **OK,** nebo v Ovládacích panelech vyberte **nástroje pro správu** a dvakrát klikněte na panel **výkonu**.  
  
    > [!NOTE]
    >  Nelze přidat čítače, dokud vzorový kód je spuštěný.  
  
2.  Odeberte čítačů výkonu, které jsou uvedeny tak, že je vyberete a stisknutím klávesy Delete.  
  
3.  Přidání čítačů WCF kliknutím pravým tlačítkem v podokně grafu a výběr **přidat čítače**. V **přidat čítače** dialogu **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 nebo ServiceModelService 3.0.0.0** v objektu výkonu rozevírací seznam pole se seznamem. Vyberte čítače, které chcete zobrazit v seznamu.  
  
    > [!NOTE]
    >  Pokud nejsou žádné WCF služby spuštěné v počítači nejsou žádné čítače výkonu WCF pro službu.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Použití editoru konfigurace pro povolení čítačů  
  
1.  Spusťte instanci SvcConfigEditor.exe.  
  
2.  V nabídce Soubor klikněte na tlačítko **otevřít** a potom klikněte na tlačítko **konfiguračního souboru...** .  
  
3.  Přejděte do složky služby ukázkovou aplikaci a otevřete soubor Web.config.  
  
4.  Klikněte na tlačítko **diagnostiky** ve stromové struktuře konfigurace.  
  
5.  Přepnout **čítač výkonu** v **diagnostiky** okno k zobrazení "Vše".  
  
6.  Konfigurační soubor uložte a ukončete editor.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
