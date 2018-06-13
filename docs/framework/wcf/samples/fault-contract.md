---
title: Chyba – kontrakt
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 37b9d7e3ec2135d60215232fae114baef1b54f36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504156"
---
# <a name="fault-contract"></a>Chyba – kontrakt
Chyba – kontrakt příklad znázorňuje způsob ke sdělování informací chyby ze služby klienta. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s další kód přidat ke službě převést výjimku vnitřní chybu. Klient se pokusí provést dělení nulou vynutit chybový stav služby.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Kontrakt kalkulačky změnila zahrnout <xref:System.ServiceModel.FaultContractAttribute> jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut znamená, že `Divide` operace může vrátit chybu typu `MathFault`. Chybu může být jakéhokoli typu, který lze serializovat. V takovém případě `MathFault` kontraktu dat je následující:  
  
```  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{      
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]          
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 `Divide` Metoda vrátí <xref:System.ServiceModel.FaultException%601> došlo k výjimce při Rozděl nulové výjimkou jak je znázorněno v následujícím ukázkovém kódu. Tato výjimka za následek chybu odesílány do klienta.  
  
```  
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 Kód klienta vynutí chybu tím, že požádá dělení nulou. Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Zobrazí dělení nulou nehlásí jako chybu. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Klient dosahuje tím, že zachytávání odpovídající `FaultException<MathFault>` výjimka:  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Ve výchozím nastavení podrobnosti o neočekávané výjimky neodešlou do klienta aby podrobnosti o implementaci služby z uvozovací znaky hranice zabezpečení služby. `FaultContract` poskytuje způsob, jak popisuje chyb v kontraktu a označit určité typy výjimek podle potřeby pro přenos do klienta. `FaultException<T>` poskytuje mechanismus běhu pro odesílání chyb k příjemce.  
  
 Je však užitečné při ladění, najdete v části interní podrobnosti o selhání služby. Chcete-li vypnout zabezpečené chování výše popsané, můžete určit, že podrobnosti o každé neošetřených výjimek na serveru by měl být součástí chybu, která je odeslána do klienta. To se provádí nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> k `true`. Můžete buď ho nastavit v kódu nebo v konfiguraci, jak znázorňuje následující ukázka.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Navíc chování musí být přidružen službu nastavením `behaviorConfiguration` atribut služby v konfiguračním souboru na "CalculatorServiceBehavior".  
  
 K zachycení takové chyby u klienta, neobecnou <xref:System.ServiceModel.FaultException> musí být zachycena.  
  
 Toto chování lze používat pouze pro účely ladění a nikdy by měla být povolená v produkčním prostředí.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a>Viz také
