---
title: Jednosměrný
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: e82034a79610ea7956b3ef07508295578461de1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008030"
---
# <a name="one-way"></a>Jednosměrný
Tato ukázka předvádí, služba kontaktovat s operací jednosměrné služby. Klient nečeká servisní operace dokončit, protože v případě obousměrné servisní operace. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a používá `wsHttpBinding` vazby. Služby v této ukázce je aplikace v místním prostředí konzoly, která vám umožní sledovat službu, která přijímá a zpracovává požadavky. Klient je také konzolovou aplikaci.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Vytvoření kontraktu služby jednosměrné, definování váš kontraktu služby, použije <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou operaci a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> k `true` jak je znázorněno v následujícím ukázkovém kódu:  
  
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
  
 Abychom si předvedli, že klient nečeká na dokončení operací služby, implementuje kódu služby v této ukázce zpoždění pěti sekund, jak je znázorněno v následujícím ukázkovém kódu:  
  
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
  
 Když klient zavolá službu, volání se vrátí bez čekání na dokončení operace služby.  
  
 Při spuštění ukázky činnosti klienta a služby se zobrazují v oknech konzoly služby a klienta. Můžete zobrazit přijetí zprávy služby z klienta. Stisknutím klávesy ENTER v okně konzoly se každý vypnout službu a klienta.  
  
 Klient dokončí náskok před službu, představením toho, že klient nečeká na dokončení operací jednosměrné služby. Výstup klienta vypadá takto:  
  
```console  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Se zobrazí následující výstup služby:  
  
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
>  HTTP je podle definice požadavků/odpovědí protokolu; Po provedení požadavku se vrátí odpověď. To platí i pro operaci jednosměrné služby, která je přístupná přes protokol HTTP. Při volání operace služby vrátí stavový kód HTTP 202 předtím, než se spustí operace služby. Tímto stavovým kódem znamená, že požadavek přijal ke zpracování, ale zpracování nebyla dosud dokončena. Klient, který volá operace blokuje až do obdržení odpovědi 202 ze služby. Při více jednosměrné zprávy odesílat pomocí vazby, který je nakonfigurován pro použití relací to může způsobit nějaké neočekávané chování. `wsHttpBinding` Vazba používané v tomto příkladu je nakonfigurována pro použití relací ve výchozím nastavení k vytvoření kontextu zabezpečení. Ve výchozím nastavení je zaručena doručeny v pořadí, ve kterém jsou odesílány zprávy v relaci. Z tohoto důvodu odeslání druhé zprávy v relaci není dokud byla zpracována na první zprávu zpracovat. Výsledek tohoto je, že klient neobdrží odpovědi 202 zprávy dokud se nedokončí zpracování předchozí zprávu. Klient se proto zobrazí do bloku na každé následné operace volání. Chcete-li toto chování vyhnout, tento vzorovým kódem se nakonfiguruje runtime k odeslání zpráv souběžně, což umožňuje jedinečných instancí pro zpracování. Ukázka sady <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> k `PerCall` tak, aby každá zpráva mohou být zpracovány do jiné instance. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavena na `Multiple` umožňuje více než jedno vlákno k odeslání zprávy v čase.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Spusťte službu, před spuštěním klienta a vypnout klienta před ukončením služby. Tím předejdete výjimka klienta, pokud nelze klienta ukončete relaci zabezpečení přímo, protože tato služba je pryč.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
