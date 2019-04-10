---
title: Hostitel služby Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 85d089813a455784fde679e9200a9b29b956af8e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59338693"
---
# <a name="windows-service-host"></a>Hostitel služby Windows
V této ukázce hostovaný ve spravované službě Windows služby Windows Communication Foundation (WCF). Windows Services jsou řízeny pomocí apletu služby v **ovládací panely** a dá se spustit automaticky po restartu systému. Ukázka se skládá z programu klienta a aplikace služby Windows. Služba je implementovaný jako .exe program a obsahuje vlastní kód hostování. V jiných prostředích hostingu, jako je například Windows procesu aktivační služby (WAS) nebo internetové informační služby (IIS), není nutné pro vás bude psaní hostování kódu.

> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po vytvoření této služby, musí být nainstalován nástroj Installutil.exe stejně jako jakoukoli jinou službu Windows. Pokud se chystáte provést změny ve službě, musíte nejprve odinstalovat pomocí `installutil /u`. Setup.bat a Cleanup.bat soubory zahrnuté v této ukázce jsou příkazy pro instalaci a spuštění služby Windows a vypne a odinstalujte službu Windows. Služby WCF můžete reagovat jen na klienty, pokud je služba Windows spuštěná. Pokud zastavíte službu Windows pomocí apletu služby z **ovládací panely** a spusťte tak klienta <xref:System.ServiceModel.EndpointNotFoundException> dojde k výjimce, když se klient pokusí o přístup ke službě. Pokud službu Windows restartovat a znovu spusťte klienta, komunikace bude úspěšná.  
  
 Kód služby obsahuje instalační třídu, implementace třídy služby WCF, která implementuje ICalculator kontraktu a služby Windows třídu, která slouží jako hostitel za běhu. Instalační třída, která dědí z <xref:System.Configuration.Install.Installer>, umožňuje program, který se nainstaluje jako služby NT nástrojem Installutil.exe. Třída implementace služby `WcfCalculatorService`, je služba WCF, který implementuje kontrakt služby na úrovni basic. Tato služba WCF je umístěn uvnitř třídu služby Windows s názvem `WindowsCalculatorService`. K získání způsobilosti jako služba Windows, třída dědí z <xref:System.ServiceProcess.ServiceBase> a implementuje <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> a <xref:System.ServiceProcess.ServiceBase.OnStop> metody. V <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> pro vytvoření objektu `WcfCalculatorService` zadejte a otevřít. V <xref:System.ServiceProcess.ServiceBase.OnStop>, zavření hostitele ServiceHost voláním <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> metodu <xref:System.ServiceModel.ServiceHost> objektu. Základní adresa hostitele je nakonfigurovaný nástrojem [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, který je podřízeným prvkem z [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), který je podřízeným prvkem [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element, který je podřízeným prvkem z [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) elementu.  
  
 Koncový bod, který je definován používá základní adresu a [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Následující příklad ukazuje základní adresa, stejně jako koncový bod, který zpřístupňuje CalculatorService konfigurace.  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okno konzoly pro vypnutí klienta a služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po řešení je sestavený Build, spusťte z příkazového řádku se zvýšenými oprávněními Visual Studio 2012 pro instalaci služby Windows pomocí Installutil.exe nástroje Setup.bat. Služba by se zobrazit v služeb.  
  
4. Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také:

- [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
