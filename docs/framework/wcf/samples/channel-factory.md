---
title: Vytvoření postupu kanálu
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: a528cc759ad550b21845dfd351d4e7808cfb6b56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="channel-factory"></a>Vytvoření postupu kanálu
Tento příklad ukazuje, jak klientská aplikace můžete vytvořit kanál s <xref:System.ServiceModel.ChannelFactory> třída místo generovaného klienta. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 V tomto příkladu <xref:System.ServiceModel.ChannelFactory%601> třída k vytvoření kanálu pro koncový bod služby. Obvykle k vytvoření kanálu pro koncový bod služby, můžete vygenerovat typu klienta s [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) a vytvořit instanci typu generované. Můžete také vytvořit kanál pomocí <xref:System.ServiceModel.ChannelFactory%601> třídy, jak je předvedeno v této ukázce. Službu vytvořené následující vzorový kód je stejný jako do služby [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
```csharp  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  Pokud používáte této ukázky ve scénáři mezi počítači, je potřeba "localhost" v předchozí kód nahradit plně kvalifikovaný název počítače, ve kterém je spuštěna služba. Tato ukázka nepoužívá konfigurace nastavit adresa koncového bodu, musí provést v kódu.  
  
 Po vytvoření kanálu operací služby nelze vyvolat stejně jako v generovaného klienta.  
  
```csharp  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
```  
  
 Zavřete kanál, se musí nejprve přetypovat <xref:System.ServiceModel.IClientChannel> rozhraní. Důvodem je, že je v klientská aplikace používající deklarována kanál generovaná `ICalculator` rozhraní, které se má metody jako `Add` a `Subtract` ale ne `Close`. `Close` Metoda pochází <xref:System.ServiceModel.ICommunicationObject> rozhraní.  
  
```csharp  
// Close the channel.  
 ((IClientChannel)client).Close();  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klientské aplikace.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md). Všimněte si, že tato ukázka neumožňuje publikování metadat. Nejprve je nutné povolit publikování metadat pro tato ukázka se znova vygenerovat typ klienta.  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
### <a name="to-run-the-sample-cross-machine"></a>Ke spuštění ukázky pro různé počítače  
  
1.  Nahraďte plně kvalifikovaný název počítače, ve kterém je spuštěna služba "localhost" v následujícím kódu.  
  
    ```csharp  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## <a name="see-also"></a>Viz také
