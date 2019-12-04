---
title: Vlastní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: 9077f2b00c97ae2a2106a50780cfd2cd9596c1ec
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716324"
---
# <a name="self-host"></a>Vlastní hostování
Tato ukázka předvádí, jak implementovat samoobslužnou službu v konzolové aplikaci. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Konfigurační soubor služby byl přejmenován ze souboru Web. config do App. config a upraven tak, aby nakonfiguroval základní adresu, kterou hostitel používá. Zdrojový kód služby byl změněn tak, aby implementoval statickou `Main` funkci, která vytváří a otevírá hostitele služby, který poskytuje nakonfigurovanou základní adresu. Implementace služby byla upravena pro zápis výstupu do konzoly pro každou operaci. Klient se nezměnil, s výjimkou konfigurace správné adresy koncového bodu služby.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka implementuje statickou hlavní funkci pro vytvoření <xref:System.ServiceModel.ServiceHost> pro daný typ `CalculatorService`, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 Když je služba hostovaná ve službě Internetová informační služba (IIS) nebo aktivační služba procesů systému Windows (WAS), poskytuje hostující prostředí základní adresu služby. V případě samostatného hostitele je nutné zadat základní adresu sami. To se provádí pomocí `add` elementu, podřízeného prvku [\<adres baseaddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), podřízenosti [\<ho hostitele >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), podřízeného\<> [služby](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) , jak je znázorněno v následující ukázkové konfiguraci.  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 Při spuštění ukázky se požadavky na operace a odpovědi zobrazí v oknech služba i klientská konzola. V každém okně konzoly stiskněte klávesu ENTER a ukončete službu a klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Viz také:

- [Hostování technologie AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
