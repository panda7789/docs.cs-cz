---
title: Hostitel služby Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 06bb17ca174eef069889381460b77f6b50902f70
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="windows-service-host"></a>Hostitel služby Windows
Tento příklad znázorňuje službě Windows Communication Foundation (WCF) hostované ve spravované službě Windows. Služby systému Windows jsou řízena pomocí apletu služby v **ovládací panely** a dá se nakonfigurovat automatické spuštění po restartu systému. Ukázka se skládá z programu klienta a aplikace služby systému Windows. Služba je implementovaný jako .exe program a obsahuje vlastní kód pro hostování. V jiných hostitelských prostředích, jako jsou služby Aktivace procesů systému Windows (WAS) nebo internetové informační služby (IIS), není nutné pro vás bude psaní hostování kódu.  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po vytvoření této služby, musí být nainstalován s nástroj Installutil.exe stejně jako ostatní služby systému Windows. Pokud chcete provést změny ve službě, můžete ji nejprve odinstalovat s `installutil /u`. Setup.bat a Cleanup.bat soubory obsažené v této ukázce jsou příkazy k instalaci a spustit službu systému Windows a k vypnutí a odinstalovat službu systému Windows. Služby WCF můžete reagovat jen na klienty, pokud je spuštěná služba Windows. Pokud zastavíte službu systému Windows pomocí apletu služby z **ovládací panely** a spusťte klienta, <xref:System.ServiceModel.EndpointNotFoundException> když se klient pokusí o přístup ke službě došlo k výjimce. Je-li restartovat službu systému Windows a znovu spusťte klienta, komunikace se zdaří.  
  
 Kód služby zahrnuje instalační třídy, třída implementace služby WCF, která implementuje ICalculator kontraktu a služby systému Windows třídu, která funguje jako hostitel běhu. Instalační program třídy, která dědí z <xref:System.Configuration.Install.Installer>, umožňuje program, který má být nainstalován jako služba NT nástrojem Installutil.exe. Třídě implementace služby `WcfCalculatorService`, je služba WCF, která implementuje kontraktu služby na úrovni basic. Tato služba WCF je umístěn uvnitř třídy služba systému Windows s názvem `WindowsCalculatorService`. Aby se dosáhlo nároku jako služby systému Windows, třídy dědí z <xref:System.ServiceProcess.ServiceBase> a implementuje <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> a <xref:System.ServiceProcess.ServiceBase.OnStop> metody. V <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, <xref:System.ServiceModel.ServiceHost> pro vytvoření objektu `WcfCalculatorService` zadejte a otevřít. V <xref:System.ServiceProcess.ServiceBase.OnStop>, hostitele ServiceHost uzavřené volání <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> metodu <xref:System.ServiceModel.ServiceHost> objektu. Základní adresa hostitele je konfigurován pomocí [ \<Přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, který je podřízená z [ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), která je podřízená [ \<hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element, který je podřízená z [ \<služby >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element.  
  
 Koncový bod, který je definován používá základní adresu a [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Následující příklad ukazuje konfiguraci základní adresu, jakož i koncového bodu, který zveřejňuje CalculatorService.  
  
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
  
 Při spuštění vzorového operaci požadavky a odpovědi se zobrazují v oknech konzoly služby a klienta. Stisknutím klávesy ENTER v každé okna konzoly vypnout klienta a služby.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Po vytvoření řešení, spusťte Setup.bat ze se zvýšenými oprávněními [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazového řádku pro instalaci služby systému Windows pomocí nástroje Installutil.exe. Služba by se zobrazit v služby.  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
