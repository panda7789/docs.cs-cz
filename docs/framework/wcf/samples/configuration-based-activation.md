---
title: Aktivace podle konfigurace
ms.date: 03/30/2017
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
ms.openlocfilehash: e016dffdaf93b222c1fd2380bfa175256b009068
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43742313"
---
# <a name="configuration-based-activation"></a>Aktivace podle konfigurace
Tato ukázka předvádí postup aktivace služby Windows Communication Foundation (WCF) bez nutnosti souboru SVC.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce testovací klient WCF je klient a služba je hostována ve službě IIS.  
  
> [!NOTE]
>  Instalační program a sestavení pokyny pro tuto ukázku se nachází na konci tohoto tématu.  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a>Aktivace služby, bez nutnosti souboru SVC  
 V [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], byl soubor SVC požadované pro aktivaci služby. Důvodem další režie, protože je potřeba nasadit a udržovat spolu s aplikace další soubor. S vydáním [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], aktivačních komponent lze konfigurovat pomocí konfiguračního souboru aplikace.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] zavádí nový element konfigurace (<xref:System.ServiceModel.Configuration.ServiceActivationElement>) v <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> konfiguračního souboru aplikace. <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> Kolekce přijímá kolekce služeb, které chcete aktivovat, jak je znázorněno v následujícím příkladu kódu.  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 Sledování, aby je že konfigurace vypadá podobně jako konfigurace hledání souborů .svc. Další atribut, který byl představen `relativeAddress` , který obsahuje adresu služby. Relativní adresa je také virtuální cestu pro službu. Hostitel načítá soubor ze souboru Web.config `virtualPath` umístění, pokud je k dispozici; jinak prohledá hostitele své nadřazené složky rekurzivně.  
  
> [!NOTE]
>  Tato ukázka vyžaduje hostování ve službě IIS na funkci.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor Service.csproj.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Spuštěním WCFTestClient.exe otestování služby.  
  
4.  Pomocí [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], přejděte do složky %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE.  
  
5.  Spusťte WcfTestClient.exe.  
  
6.  Nastavte adresu MEX služby.  
  
7.  Stiskněte kombinaci kláves CTRL + SHIFT + A Chcete-li nastavit adresu služby.  
  
8.  Nastavena adresa http://localhost/ServiceModelSamples/Calculator.svc.  
  
9. Provést `Add` operace. Nastavte hodnotu na `n1` parametr na hodnotu 10 a nastavené na `n2` parametr do 15.  
  
10. Stisknutím klávesy **vyvolat**.  
  
     Očekávaný výsledek je 25.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po řešení je sestavený Build, spusťte Setup.bat nastavení ServiceModelSamples aplikace ve službě IIS. Adresář ServiceModelSamples by se měl objevit jako aplikace služby IIS.  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
