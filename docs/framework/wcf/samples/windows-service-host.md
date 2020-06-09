---
title: Hostitel služby Windows
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 9c041f6e9505d2ec5865dd512359b497a411cb40
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602281"
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
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 Po vytvoření této služby je nutné ji nainstalovat pomocí nástroje Installutil. exe, stejně jako jakékoli jiné služby systému Windows. Pokud budete chtít změnit službu, musíte ji nejprve odinstalovat pomocí nástroje `installutil /u` . Soubory Setup. bat a Cleanup. bat, které jsou součástí této ukázky, jsou příkazy pro instalaci a spuštění služby systému Windows a pro vypnutí a odinstalaci služby systému Windows. Služba WCF může reagovat jenom na klienty, pokud je spuštěná služba systému Windows. Pokud zastavíte službu systému Windows pomocí apletu služby v **Ovládacích panelech** a spustíte klienta, <xref:System.ServiceModel.EndpointNotFoundException> dojde k výjimce, když se klient pokusí o přístup ke službě. Pokud službu systému Windows restartujete a znovu spustíte klienta, komunikace bude úspěšná.  
  
 Kód služby zahrnuje instalační třídu, třídu implementace služby WCF, která implementuje kontrakt ICalculator, a třídu služby systému Windows, která funguje jako hostitel v době běhu. Instalační třída, která dědí z <xref:System.Configuration.Install.Installer> , umožňuje programu instalovat program jako službu NT pomocí nástroje Installutil. exe. Třída implementace služby, `WcfCalculatorService` je služba WCF, která implementuje základní kontrakt služby. Tato služba WCF je hostovaná ve třídě služby systému Windows s názvem `WindowsCalculatorService` . Chcete-li se kvalifikovat jako služba systému Windows, třída dědí z <xref:System.ServiceProcess.ServiceBase> a <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> implementuje <xref:System.ServiceProcess.ServiceBase.OnStop> metody a. V je <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> <xref:System.ServiceModel.ServiceHost> objekt vytvořen pro `WcfCalculatorService` typ a otevřen. V systému <xref:System.ServiceProcess.ServiceBase.OnStop> je hostitel ServiceHost uzavřen voláním <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> metody <xref:System.ServiceModel.ServiceHost> objektu. Základní adresa hostitele je nakonfigurována pomocí elementu, který je podřízeným prvkem, který je podřízenou položkou prvku, který je podřízeným elementu [\<add>](../../configure-apps/file-schema/wcf/add-of-baseaddresses.md) [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) [\<host>](../../configure-apps/file-schema/wcf/host.md) [\<service>](../../configure-apps/file-schema/wcf/service.md) .  
  
 Koncový bod, který je definován, používá základní adresu a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . Následující ukázka znázorňuje konfiguraci základní adresy i koncového bodu, který zpřístupňuje CalculatorService.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Po sestavení řešení spusťte soubor Setup. bat z příkazového řádku se zvýšenými oprávněními sady Visual Studio 2012 a nainstalujte službu systému Windows pomocí nástroje Installutil. exe. Služba by se měla zobrazit v části služby.  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
## <a name="see-also"></a>Viz také

- [Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
