---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143574"
---
# <a name="using-performance-counters"></a>Použití čítačů výkonu
Tato ukázka ukazuje, jak získat přístup k čítačům výkonu WCF (Windows Communication Foundation) a jak vytvořit uživatelem definované čítače výkonu. Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 V této ukázce klient volá `ICalculator` čtyři metody služby. Klient pokračuje v tomto, dokud je přerušen uživatelem. Služba zůstane nezměněna.  
  
 Čítače výkonu jsou povoleny v části diagnostika souboru Web.config pro službu, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 Tuto úlohu lze provést také pomocí [nástroje Editor konfigurace (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Pokud jsou povoleny čítače výkonu, je pro službu povolena celá sada čítačů výkonu WCF. Rozhraní .NET Framework automaticky udržuje údaje `ServiceModelService`o `ServiceModelEndpoint` `ServiceModelOperation`výkonu na třech úrovních: a . Každá z těchto úrovní má čítače výkonu, například "Volání", "Volání za sekundu" a "Bezpečnostní volání nejsou autorizována".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Zobrazení dat o výkonu  
  
1. Spusťte nástroj sledování výkonu klepnutím na `perfmon` tlačítko **Start**, **Spustit...**, zadejte a klepněte na tlačítko **OK** nebo v ovládacím panelu vyberte nástroje **pro správu** a poklepejte na **položku Výkon**.  
  
    > [!NOTE]
    > Nelze přidat čítače, dokud ukázkový kód je spuštěn.  
  
2. Odeberte čítače výkonu, které jsou uvedeny, tak, že je vyberete a stisknete klávesu Delete.  
  
3. Přidejte čítače WCF tak, že kliknete pravým tlačítkem myši na podokno grafu a vyberete **přidat čítače**. V dialogovém okně **Přidat čítače** vyberte v rozevíracím seznamu Objekt výkonu položku **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0 nebo ServiceModelService 3.0.0.0.** Ze seznamu vyberte čítače, které chcete zobrazit.  
  
    > [!NOTE]
    > Neexistují žádné čítače výkonu WCF pro službu, pokud nejsou k dispozici žádné služby WCF spuštěné v počítači.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Povolení čítačů pomocí Editoru konfigurace  
  
1. Otevřete instanci souboru SvcConfigEditor.exe.  
  
2. V nabídce Soubor klepněte na tlačítko **Otevřít** a potom klepněte na **položku Konfigurační soubor...**.  
  
3. Přejděte do složky služby ukázkové aplikace a otevřete soubor Web.config.  
  
4. Ve stromu Konfigurace klikněte na **Diagnostika.**  
  
5. Přepnout **čítač výkonu** v okně **Diagnostika** zobrazíte vše.  
  
6. Uložte konfigurační soubor a ukončete editor.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
