---
title: Vlastní hostování
ms.date: 03/30/2017
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
ms.openlocfilehash: a38738c369db3d3f8242bd71ee04a19a669b2cf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144146"
---
# <a name="self-host"></a>Vlastní hostování
Tato ukázka ukazuje, jak implementovat samoobslužnou službu v aplikaci konzoly. Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Konfigurační soubor služby byl přejmenován z souboru Web.config na App.config a upraven tak, aby nakonfiguroval základní adresu, kterou hostitel používá. Zdrojový kód služby byl upraven `Main` tak, aby implementoval statickou funkci, která vytvoří a otevře hostitele služby, který poskytuje nakonfigurovanou základní adresu. Implementace služby byla upravena tak, aby zapisovala výstup do konzoly pro každou operaci. Klient byl nezměněn, s výjimkou konfigurace správné koncové adresy služby.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Ukázka implementuje statickou hlavní <xref:System.ServiceModel.ServiceHost> funkci `CalculatorService` k vytvoření a pro daný typ, jak je znázorněno na následujícím ukázkovém kódu.  
  
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
  
 Pokud je služba hostována v Internetové informační službě (IIS) nebo službě aktivace procesů systému Windows (WAS), základní adresa služby je poskytována hostitelským prostředím. V případě vlastní hostované, musíte zadat základní adresu sami. To se provádí `add` pomocí elementu, podřízeného [ \<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [ \<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [ \<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) jak je znázorněno v následující ukázce né konfiguraci.  
  
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
  
 Při spuštění ukázky jsou požadavky na operaci a odpovědi zobrazeny v systému Windows služby i klientské konzole. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu a klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a>Viz také

- [Ukázky hostování a perzistence appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
