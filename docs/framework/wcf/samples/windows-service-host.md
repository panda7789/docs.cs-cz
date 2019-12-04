---
title: Hostitel služby Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 4d5e29f51ab49c142beb97060b719f26b050e767
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715019"
---
# <a name="windows-service-host"></a>Hostitel služby Windows
Tato ukázka předvádí službu Windows Communication Foundation (WCF) hostovanou ve spravované službě systému Windows. Služby systému Windows jsou ovládány pomocí apletu služby v **Ovládacích panelech** a lze je nakonfigurovat tak, aby se automaticky spouštěly po restartování systému. Ukázka se skládá z klientského programu a programu služby systému Windows. Služba je implementována jako program. exe a obsahuje svůj vlastní hostitelský kód. V jiných hostitelských prostředích, jako jsou služby Aktivace procesů systému Windows (WAS) nebo Internetová informační služba (IIS), není nutné psát hostující kód.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po vytvoření této služby je nutné ji nainstalovat pomocí nástroje Installutil. exe, stejně jako jakékoli jiné služby systému Windows. Pokud budete chtít změnit službu, musíte ji nejdřív odinstalovat pomocí `installutil /u`. Soubory Setup. bat a Cleanup. bat, které jsou součástí této ukázky, jsou příkazy pro instalaci a spuštění služby systému Windows a pro vypnutí a odinstalaci služby systému Windows. Služba WCF může reagovat jenom na klienty, pokud je spuštěná služba systému Windows. Pokud zastavíte službu systému Windows pomocí apletu služby v **Ovládacích panelech** a spustíte klienta, dojde k výjimce <xref:System.ServiceModel.EndpointNotFoundException>, když se klient pokusí o přístup ke službě. Pokud službu systému Windows restartujete a znovu spustíte klienta, komunikace bude úspěšná.  
  
 Kód služby zahrnuje instalační třídu, třídu implementace služby WCF, která implementuje kontrakt ICalculator, a třídu služby systému Windows, která funguje jako hostitel v době běhu. Instalační třída, která dědí z <xref:System.Configuration.Install.Installer>, umožňuje programu instalovat program jako službu NT pomocí nástroje Installutil. exe. Třída implementace služby, `WcfCalculatorService`, je služba WCF, která implementuje základní kontrakt služby. Tato služba WCF je hostována v rámci třídy služby systému Windows s názvem `WindowsCalculatorService`. Pro zařazení jako služba systému Windows dědí třída z <xref:System.ServiceProcess.ServiceBase> a implementuje metody <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> a <xref:System.ServiceProcess.ServiceBase.OnStop>. V <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>je vytvořen <xref:System.ServiceModel.ServiceHost> objekt pro `WcfCalculatorService` typ a otevřen. V <xref:System.ServiceProcess.ServiceBase.OnStop>je Třída ServiceHost zavřena voláním metody <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> objektu <xref:System.ServiceModel.ServiceHost>. Základní adresa hostitele je nakonfigurována pomocí [\<přidat >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, který je podřízeným objektem [\<adres BaseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), který je podřízeným prvku\<[hostitele](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) >, který je podřízeným prvkem\<> [služby](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) .  
  
 Koncový bod, který je definován, používá základní adresu a [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). Následující ukázka znázorňuje konfiguraci základní adresy i koncového bodu, který zpřístupňuje CalculatorService.  
  
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
  
 Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Po sestavení řešení spusťte soubor Setup. bat z příkazového řádku se zvýšenými oprávněními sady Visual Studio 2012 a nainstalujte službu systému Windows pomocí nástroje Installutil. exe. Služba by se měla zobrazit v části služby.  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také:

- [Hostování technologie AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
