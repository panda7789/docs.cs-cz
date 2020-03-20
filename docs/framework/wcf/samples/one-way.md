---
title: Jednosměrný
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 3203762e05c794ed28b65d8fded6972fac1f5820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183446"
---
# <a name="one-way"></a>Jednosměrný
Tato ukázka ukazuje kontakt služby s operacemi jednosměrné služby. Klient nečeká na dokončení operací služby, jako je tomu v případě obousměrných operací služby. Tato ukázka je založena na `wsHttpBinding` [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a používá vazbu. Služba v této ukázce je aplikace konzoly s vlastním hostitelem, která umožňuje sledovat službu, která přijímá a zpracovává požadavky. Klient je také konzolová aplikace.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Chcete-li vytvořit jednosměrnou servisní smlouvu, definujte servisní smlouvu, použijte třídu <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> tak, jak je `true` znázorněno v následujícím ukázkovém kódu:  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Chcete-li prokázat, že klient nečeká na dokončení operací služby, kód služby v této ukázce implementuje pětisekundové zpoždění, jak je znázorněno v následujícím ukázkovém kódu:  
  
```csharp
// This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 Když klient volá službu, volání vrátí bez čekání na dokončení operace služby.  
  
 Při spuštění ukázky jsou aktivity klienta a služby zobrazeny v systému Windows služby i klientské konzole. Můžete vidět službu přijímat zprávy od klienta. Stisknutím klávesy ENTER v každém okně konzoly vypněte službu i klienta.  
  
 Klient dokončí před službou, což dokazuje, že klient nečeká na dokončení operací jednosměrné služby. Výstup klienta je následující:  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Zobrazí se následující výstup služby:  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
> HTTP je ze své podstaty protokol požadavku/odpovědi; při požadavku je vrácena odpověď. To platí i pro jednosměrné operace služby, která je vystavena přes HTTP. Při volání operace vrátí služba stavový kód HTTP 202 před spuštěním operace služby. Tento stavový kód znamená, že požadavek byl přijat ke zpracování, ale zpracování ještě nebylo dokončeno. Klient, který volal bloky operace, dokud neobdrží odpověď 202 ze služby. To může způsobit některé neočekávané chování při více jednosměrné zprávy jsou odesílány pomocí vazby, která je nakonfigurována pro použití relací. Vazba použitá `wsHttpBinding` v této ukázce je nakonfigurována tak, aby ve výchozím nastavení používala relace k vytvoření kontextu zabezpečení. Ve výchozím nastavení je zaručeno, že zprávy v relaci dorazí v pořadí, ve kterém jsou odesílány. Z tohoto důvodu při odeslání druhé zprávy v relaci není zpracována, dokud první zpráva byla zpracována. Výsledkem je, že klient neobdrží odpověď 202 pro zprávu, dokud nebude dokončeno zpracování předchozí zprávy. Klient se proto zobrazí blokovat při každém volání následující operace. Chcete-li se tomuto chování vyhnout, tato ukázka konfiguruje runtime k odeslání zpráv současně na různé instance pro zpracování. Ukázka <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> se `PerCall` nastaví tak, aby každá zpráva může být zpracována jinou instancí. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>je nastavena tak, aby `Multiple` více než jedno vlákno k odeslání zpráv najednou.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Spusťte službu před spuštěním klienta a vypněte klienta před vypnutím služby. Tím se vyhnete výjimce klienta, když klient nemůže zavřít relaci zabezpečení čistě, protože služba je pryč.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
