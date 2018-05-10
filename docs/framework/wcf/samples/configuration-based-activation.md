---
title: Aktivace podle konfigurace
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: 3ac4edd2a51e4ed8a5c0b7e73d7d1afa31334c33
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="configuration-based-activation"></a>Aktivace podle konfigurace
Tento příklad znázorňuje postup aktivace služby Windows Communication Foundation (WCF) bez nutnosti .svc souboru.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce je klient testovacího klienta WCF a služba je hostovaná ve službě IIS.  
  
> [!NOTE]
>  Instalační program a sestavení pokyny v tomto příkladu jsou umístěné na konci tohoto tématu.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>Aktivace služby bez nutnosti soubor .svc  
 V [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], soubor .svc nebyla nutná pro aktivaci služby. Příčinou další správní režii, protože další soubor je potřeba nasadit a udržovat spolu s aplikací. S vydáním [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], aktivačních komponent lze nakonfigurovat pomocí konfiguračního souboru aplikace.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] zavádí nový element konfigurace (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) v <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> konfiguračního souboru aplikace. <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekci lze používat pouze kolekce služeb, které chcete aktivovat, jak je znázorněno v následujícím příkladu kódu.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 Pozorování, aby je, že konfigurace je velmi podobná konfigurace souborů .svc. Další atribut, který byl představen `relativeAddress` adresu služby, který poskytuje. Relativní adresa je také virtuální cestu pro službu. Hostitel načítá soubor ze souboru Web.config `virtualPath` umístění, pokud existuje; jinak hodnota hostitele Vyhledá rekurzivně jeho nadřazené složky.  
  
> [!NOTE]
>  Tato ukázka vyžaduje hostování funkce ve službě IIS.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor Service.csproj.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Testování služby spuštěním WCFTestClient.exe.  
  
4.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte do složky 10.0\Common7\IDE %SystemDrive%\Program Files\Microsoft Visual Studio.  
  
5.  Spusťte WcfTestClient.exe.  
  
6.  Nastavte adresu MEX služby.  
  
7.  Stisknutím kombinace kláves CTRL + SHIFT + A nastavit adresu služby.  
  
8.  Nastavena adresa http://localhost/ServiceModelSamples/Calculator.svc.  
  
9. Proveďte `Add` operace. Nastavit hodnotu `n1` parametr 10 a nastavte hodnotu na `n2` parametru 15.  
  
10. Stiskněte klávesu **vyvolání**.  
  
     Očekávaný výsledek je 25.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po řešení byla vytvořena, spusťte Setup.bat nastavit ServiceModelSamples aplikace ve službě IIS. Adresář ServiceModelSamples by se měla zobrazit jako aplikace služby IIS.  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
