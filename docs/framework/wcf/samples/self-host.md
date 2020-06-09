---
title: Vlastní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: f5c46bc486e03cf86ada3a565a3c282cd81db286
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599942"
---
# <a name="self-host"></a>Vlastní hostování
Tato ukázka předvádí, jak implementovat samoobslužnou službu v konzolové aplikaci. Tato ukázka je založena na [Začínáme](getting-started-sample.md). Konfigurační soubor služby byl přejmenován ze souboru Web. config do App. config a upraven tak, aby nakonfiguroval základní adresu, kterou hostitel používá. Zdrojový kód služby byl změněn tak, aby implementoval statickou `Main` funkci, která vytváří a otevírá hostitele služby, který poskytuje nakonfigurovanou základní adresu. Implementace služby byla upravena pro zápis výstupu do konzoly pro každou operaci. Klient se nezměnil, s výjimkou konfigurace správné adresy koncového bodu služby.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka implementuje statickou hlavní funkci pro vytvoření <xref:System.ServiceModel.ServiceHost> pro daný `CalculatorService` typ, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Když je služba hostovaná ve službě Internetová informační služba (IIS) nebo aktivační služba procesů systému Windows (WAS), poskytuje hostující prostředí základní adresu služby. V případě samostatného hostitele je nutné zadat základní adresu sami. To se provádí pomocí `add` elementu podřízeného prvku, podřízeného objektu [\<baseAddresses>](../../configure-apps/file-schema/wcf/baseaddresses.md) [\<host>](../../configure-apps/file-schema/wcf/host.md) , podřízeného prvku, [\<service>](../../configure-apps/file-schema/wcf/service.md) jak je znázorněno v následující ukázkové konfiguraci.  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Viz také

- [Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
