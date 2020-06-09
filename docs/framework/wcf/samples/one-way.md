---
title: Jednosměrný
ms.date: 03/30/2017
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
ms.openlocfilehash: 07fc4ecf981acbad577758c943aa22405f528a52
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84575249"
---
# <a name="one-way"></a>Jednosměrný
Tato ukázka demonstruje kontakt služby pomocí jednosměrných operací služby. Klient nečeká na dokončení operací služby, protože se jedná o případ s obousměrnou operací služby. Tato ukázka je založena na [Začínáme](getting-started-sample.md) a používá `wsHttpBinding` vazbu. Služba v této ukázce je samoobslužná Konzolová aplikace, která vám umožní sledovat službu, která přijímá a zpracovává požadavky. Klient je také Konzolová aplikace.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Chcete-li vytvořit jednosměrný kontrakt služby, definujte kontrakt služby, použijte <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci třídu a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> na `true` jak je znázorněno v následujícím ukázkovém kódu:  
  
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
  
 Chcete-li předvést, že klient nečeká na dokončení operací služby, kód služby v této ukázce implementuje zpoždění pět sekund, jak je znázorněno v následujícím ukázkovém kódu:  
  
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
  
 Když klient volá službu, volání se vrátí bez čekání na dokončení operace služby.  
  
 Když spustíte ukázku, aktivity klienta a služby se zobrazí v oknech konzoly služby i klienta. Můžete vidět, že služba přijímá zprávy z klienta. V každém okně konzoly stiskněte klávesu ENTER a ukončete tak službu i klienta.  
  
 Klient se dokončí před službou a demonstruje, že klient nečeká na dokončení jednosměrných operací služby. Výstup klienta je následující:  
  
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
> HTTP je, podle definice, protokolu požadavků a odpovědí. po podání žádosti se vrátí odpověď. To platí i pro jednosměrnou operaci služby, která je vystavená přes protokol HTTP. Při volání operace vrátí služba stavový kód HTTP 202 před provedením operace služby. Tento stavový kód znamená, že žádost byla přijata ke zpracování, ale zpracování ještě nebylo dokončeno. Klient, který se nazývá operace, zablokuje, dokud nepřijme odpověď 202 od služby. To může způsobit neočekávané chování při posílání více jednosměrných zpráv pomocí vazby, která je nakonfigurována pro použití relací. `wsHttpBinding`Vazba použitá v této ukázce je nakonfigurována tak, aby ve výchozím nastavení používala relace pro vytvoření kontextu zabezpečení. Ve výchozím nastavení jsou zprávy v relaci zaručeny k doručení v pořadí, ve kterém jsou odesílány. Z tohoto důvodu se při odeslání druhé zprávy v relaci nezpracovává, dokud se nezpracuje první zpráva. Výsledkem je, že klient neobdrží odpověď 202 pro zprávu, dokud nebude dokončeno zpracování předchozí zprávy. Klient se proto zobrazí při každém následném volání operace. Chcete-li se tomuto chování vyhnout, Tato ukázka nakonfiguruje modul runtime tak, aby odesílal zprávy souběžně na samostatné instance pro zpracování. Ukázka nastaví <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> na `PerCall` tak, aby každá zpráva mohla být zpracována jinou instancí. <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>je nastaveno na `Multiple` , aby bylo možné odesílat zprávy najednou více než jedno vlákno.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!NOTE]
> Před ukončením služby spusťte službu před spuštěním klienta nástroje a vypněte klienta. Tím se zabrání výjimka klienta, pokud klient nemůže relaci zabezpečení vyčistit, protože služba zmizela.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
