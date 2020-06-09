---
title: Vytvoření postupu kanálu
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 2aa44c4ef274fa548d490b0d8a648457a7b1e03b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600656"
---
# <a name="channel-factory"></a>Vytvoření postupu kanálu

Tato ukázka předvádí, jak může klientská aplikace vytvořit kanál s <xref:System.ServiceModel.ChannelFactory> třídou namísto vygenerovaného klienta. Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky.

> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.

Tato ukázka používá <xref:System.ServiceModel.ChannelFactory%601> třídu k vytvoření kanálu pro koncový bod služby. Chcete-li vytvořit kanál pro koncový bod služby, vygenerujete typ klienta pomocí nástroje pro tvorbu [metadat ServiceModel (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) a vytvoříte instanci generovaného typu. Kanál můžete také vytvořit pomocí <xref:System.ServiceModel.ChannelFactory%601> třídy, jak je znázorněno v této ukázce. Služba vytvořená následujícím ukázkovým kódem je shodná se službou v [Začínáme](getting-started-sample.md).

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> Pokud tuto ukázku spouštíte ve scénáři více počítačů, je nutné v předchozím kódu nahradit "localhost" úplným názvem počítače, na kterém je spuštěna služba. Tato ukázka nepoužívá konfiguraci k nastavení adresy koncového bodu, takže to je nutné provést v kódu.

Po vytvoření kanálu mohou být operace služby vyvolány stejně jako u vygenerovaného klienta.

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

Chcete-li kanál zavřít, musí být nejprve převeden na <xref:System.ServiceModel.IClientChannel> rozhraní. Důvodem je, že kanál jak je vygenerován, je deklarován v klientské aplikaci pomocí `ICalculator` rozhraní, které má metody jako `Add` a nikoli `Subtract` `Close` . `Close`Metoda pochází z <xref:System.ServiceModel.ICommunicationObject> rozhraní.

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER, aby se ukončila klientská aplikace.

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).

2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md). Všimněte si, že tato ukázka nepovoluje publikování metadat. Aby bylo možné znovu vygenerovat typ klienta, je třeba nejprve povolit publikování metadat pro tuto ukázku.

3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).

### <a name="to-run-the-sample-cross-machine"></a>Spuštění ukázkového počítače

1. Nahraďte "localhost" v následujícím kódu plně kvalifikovaným názvem počítače, na kterém je spuštěna služba.

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
