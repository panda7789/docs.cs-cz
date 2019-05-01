---
title: Vytvoření postupu kanálu
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: 0bcaa739a51d168e18c809804b7da6948ab61e9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002408"
---
# <a name="channel-factory"></a>Vytvoření postupu kanálu
Tato ukázka předvádí, jak vytvořit kanál s klientskou aplikaci <xref:System.ServiceModel.ChannelFactory> třídy namísto generovaného klienta. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Tento příklad používá <xref:System.ServiceModel.ChannelFactory%601> třídy za účelem vytvoření kanálu pro koncový bod služby. Obvykle k vytvoření kanálu pro koncový bod služby, můžete generovat typ klienta s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) a vytvořte její instanci generovaným typem. Můžete také vytvořit kanál pomocí <xref:System.ServiceModel.ChannelFactory%601> třídy, jak je uvedeno v této ukázce. Služba vytvořené následující ukázkový kód je stejný jako službu v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  Pokud tuto ukázku spustíte ve scénáři mezi počítači, je "localhost" v předchozím kódu nahradit plně kvalifikovaný název počítače, na kterém je spuštěná služba. Tato ukázka nepoužívá konfigurace nastavit adresu koncového bodu, aby to je nutné provést v kódu.  
  
 Po vytvoření kanálu můžete stejně jako u generovaného klienta vyvolat operace služby.  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 Zavřete kanál, je nutné nejprve přetypovat na <xref:System.ServiceModel.IClientChannel> rozhraní. Důvodem je, že kanál generovaná je deklarován v klientská aplikace používající `ICalculator` rozhraní, které obsahuje metody jako `Add` a `Subtract` , ale ne `Close`. `Close` Metoda pochází <xref:System.ServiceModel.ICommunicationObject> rozhraní.  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klientské aplikace.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Všimněte si, že tato ukázka není povoleno publikování metadat. Nejprve je nutné povolit publikování metadat pro tuto ukázku se znova vygenerovat typu klienta.  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-cross-machine"></a>Ke spuštění ukázky pro různé počítače  
  
1. Nahraďte plně kvalifikovaný název počítače, na kterém je spuštěná služba "localhost" v následujícím kódu.  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
