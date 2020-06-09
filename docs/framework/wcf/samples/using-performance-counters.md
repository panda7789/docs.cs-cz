---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 0b63cdc145ff8806c26b255500bcb2a132e9ef9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596497"
---
# <a name="using-performance-counters"></a>Použití čítačů výkonu
Tato ukázka předvádí, jak získat přístup k čítačům výkonu služby Windows Communication Foundation (WCF) a jak vytvořit uživatelsky definované čítače výkonu. Tato ukázka je založena na [Začínáme](getting-started-sample.md).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 V této ukázce klient volá čtyři metody `ICalculator` služby. Klient to bude pokračovat, dokud ho uživatel nepřerušil. Služba zůstane beze změny.  
  
 Čítače výkonu jsou povoleny v části Diagnostika v souboru Web. config pro službu, jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 Tuto úlohu lze provést také pomocí [nástroje Configuration Editor (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).  
  
 Pokud jsou povoleny čítače výkonu, je pro službu povolena celá sada čítačů výkonu služby WCF. .NET Framework automaticky udržuje údaje o výkonu na třech úrovních: `ServiceModelService` `ServiceModelEndpoint` a `ServiceModelOperation` . Každá z těchto úrovní má čítače výkonu, jako jsou volání "hovory", "hovory za sekundu" a "volání zabezpečení nejsou autorizována".  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
### <a name="to-view-performance-data"></a>Zobrazení údajů o výkonu  
  
1. Spusťte nástroj sledování výkonu kliknutím na tlačítko **Start**, **Spustit...**, zadejte `perfmon` a klikněte na tlačítko **OK** nebo v Ovládacích panelech vyberte možnost **Nástroje pro správu** a dvakrát klikněte na položku **výkon**.  
  
    > [!NOTE]
    > Čítače nelze přidat, dokud není spuštěn vzorový kód.  
  
2. Odeberte čítače výkonu, které jsou uvedeny výběrem a stisknutím klávesy DELETE.  
  
3. Přidejte čítače WCF kliknutím pravým tlačítkem myši na Podokno grafu a výběrem možnosti **Přidat čítače**. V dialogovém okně **Přidat čítače** vyberte v rozevíracím seznamu objekt výkonu možnost **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 nebo ServiceModelService 3.0.0.0** . V seznamu vyberte čítače, které chcete zobrazit.  
  
    > [!NOTE]
    > Nejsou-li v počítači žádné služby WCF spuštěné, neexistují žádné čítače výkonu WCF pro službu.  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a>Použití editoru konfigurace k povolení čítačů  
  
1. Otevřete instanci SvcConfigEditor. exe.  
  
2. V nabídce soubor klikněte na **otevřít** a pak klikněte na **konfigurační soubor...**.  
  
3. Přejděte do složky služby ukázkové aplikace a otevřete soubor Web. config.  
  
4. Ve stromové struktuře konfigurace klikněte na **Diagnostika** .  
  
5. Přepnutím **čítače výkonu** v okně **diagnostiky** zobrazíte možnost vše.  
  
6. Uložte konfigurační soubor a ukončete Editor.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a>Viz také

- [Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
