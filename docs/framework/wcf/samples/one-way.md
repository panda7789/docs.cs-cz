---
title: Jednosměrný
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 5cb3619d56720333f23d933a8f356e8b0268c4d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="one-way"></a>Jednosměrný
Tento příklad znázorňuje služby kontaktu s operací jednosměrné služby. Klient není počkejte na dokončení stejně jako v případě s operací obousměrné služby operací služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a používá `wsHttpBinding` vazby. Služba v této ukázce je vlastním hostováním konzolové aplikace, které vám umožňují sledovat službu, která přijímá a zpracovává požadavky. Klient je také konzolové aplikace.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 K vytvoření kontraktu jednosměrné služby, zadejte své smlouvy, použít <xref:System.ServiceModel.OperationContractAttribute> na každou operaci a nastavit <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> k `true` jak je znázorněno v následujícím ukázkovém kódu:  
  
```  
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
  
 K prokázání, že klient čekat na dokončení operací služby, implementuje kódu služby v této ukázce pěti sekund zpoždění, jak je znázorněno v následujícím ukázkovém kódu:  
  
```  
/ This service class implements the service contract.  
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
  
 Při spuštění ukázky činnosti klienta a služby se zobrazí v oknech konzoly služby a klienta. Uvidíte služby přijmout zprávy z klienta. Stisknutím klávesy ENTER v každé okna konzoly vypněte službu a klienta.  
  
 Klient dokončí před službu, demonstraci toho, že klient čekat na dokončení operací jednosměrné služby. Výstup klienta vypadá takto:  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 Tento výstup služby se zobrazí:  
  
```  
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
>  HTTP je podle definice požadavků a odpovědí protokolu; Když je žádosti se vrátí odpověď. To platí i pro operaci jednosměrné služby, který je zveřejněný prostřednictvím protokolu HTTP. Při volání operace služby vrátí kód stavu HTTP 202, předtím, než se spustí operace služby. Tento kód stavu znamená, že žádost byla přijata pro zpracování, ale zpracování dosud nebyl dokončen. Klient, který volal operaci bloky, dokud neobdrží 202 odpověď ze služby. To může způsobit některé neočekávanému chování při odesílání více jednosměrný zpráv pomocí vazby, který je nakonfigurován pro použití relací. `wsHttpBinding` Vazba použitá v této ukázce je nakonfigurovaný na použití relací ve výchozím nastavení k vytvoření kontextu zabezpečení. Ve výchozím nastavení jsou zaručené doručení v pořadí, v níž jsou odesílány zprávy v relaci. Z toho důvodu je odeslání o druhou zprávu v relaci není dokud zpracovala první zprávu zpracovat. Důsledkem je, klient až do dokončení zpracování v předchozí zprávě neobdrží 202 odpovědi na zprávy. Klient proto pravděpodobně bloku při každém volání další operace. Chcete-li tomu zabránit, nakonfiguruje této ukázky modulu runtime odesílání zpráv souběžně na různých instancí pro zpracování. Ukázka sady <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> k `PerCall` tak, aby každá zpráva může zpracovat jiné instance. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> je nastavena na `Multiple` umožňuje více než jedno vlákno k odesílání zpráv v čase.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Spusťte službu před spuštěním klienta a vypnout klienta před ukončením služby. Tím je zabráněno výjimka klienta, pokud nelze klienta ukončení relace zabezpečení ještě jednou, protože služba není pryč.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a>Viz také
