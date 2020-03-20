---
title: Hostitel služby Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 83b40f467af933b5da69b859d990fbe4ba005928
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143522"
---
# <a name="windows-service-host"></a>Hostitel služby Windows
Tato ukázka ukazuje službu WCF (Windows Communication Foundation) hostovanou ve spravované službě Systému Windows. Služby systému Windows jsou řízeny pomocí apletu služby v **Ovládacích panelech** a lze je nakonfigurovat tak, aby se po restartování systému automaticky spouštěly. Ukázka se skládá z klientského programu a servisního programu systému Windows. Služba je implementována jako program .exe a obsahuje vlastní hostingový kód. V jiných hostitelských prostředích, jako je například služba aktivace procesů systému Windows (WAS) nebo Internetová informační služba (IIS), není nutné psát kód hostingu.

> [!NOTE]
> Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po vytvoření této služby musí být nainstalována pomocí nástroje Installutil.exe jako jakákoli jiná služba systému Windows. Pokud se chystáte provést změny ve službě, musíte `installutil /u`ji nejprve odinstalovat pomocí aplikace . Soubory Setup.bat a Cleanup.bat obsažené v této ukázce jsou příkazy k instalaci a spuštění služby Systému Windows a k vypnutí a odinstalaci služby systému Windows. Služba WCF může reagovat pouze klientům, pokud je spuštěna služba systému Windows. Pokud službu systému Windows zastavíte pomocí apletu služby <xref:System.ServiceModel.EndpointNotFoundException> z **ovládacího panelu** a spustíte klienta, dojde k výjimce, když se klient pokusí o přístup ke službě. Pokud restartujete službu systému Windows a znovu spustíte klienta, komunikace proběhne úspěšně.  
  
 Kód služby obsahuje třídu instalačního programu, třídu implementace služby WCF, která implementuje smlouvu ICalculator, a třídu služby systému Windows, která funguje jako hostitel za běhu. Třída instalačního programu, která <xref:System.Configuration.Install.Installer>dědí z aplikace , umožňuje instalaci programu jako služby NT nástrojem Installutil.exe. Třída implementace služby , `WcfCalculatorService`je služba WCF, která implementuje základní servisní smlouvu. Tato služba WCF je hostována `WindowsCalculatorService`uvnitř třídy služby systému Windows s názvem . Chcete-li se kvalifikovat jako služba <xref:System.ServiceProcess.ServiceBase> systému <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> Windows, třída dědí z a implementuje metody a. <xref:System.ServiceProcess.ServiceBase.OnStop> V <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>aplikaci <xref:System.ServiceModel.ServiceHost> `WcfCalculatorService` je pro daný typ vytvořen objekt a otevřen. V <xref:System.ServiceProcess.ServiceBase.OnStop>, ServiceHost je uzavřen <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> voláním <xref:System.ServiceModel.ServiceHost> metody objektu. Základní adresa hostitele je konfigurována pomocí elementu [ \<add>,](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) který je podřízeným prvkem [ \<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), který je podřízeným prvkem [ \<hostitelského>,](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) který je podřízeným prvkem [ \<služby>.](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
 Definovaný koncový bod používá základní adresu a [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Následující ukázka ukazuje konfiguraci základní adresy, jakož i koncový bod, který zveřejňuje CalculatorService.  
  
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
  
 Při spuštění ukázky jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po spuštění řešení spusťte soubor Setup.bat z příkazového řádku sady Visual Studio 2012 a nainstalujte službu Windows pomocí nástroje Installutil.exe. Služba by se měla zobrazit ve službách.  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také

- [Ukázky hostování a perzistence appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
