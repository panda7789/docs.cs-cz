---
title: Chyba – kontrakt
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 37b977feffd7ce46d2f4bc7b8a4e5dc89d21b137
ms.sourcegitcommit: fd8d4587cc26e53f0e27e230d6e27d828ef4306b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2018
ms.locfileid: "49347767"
---
# <a name="fault-contract"></a>Chyba – kontrakt
Chyba – kontrakt ukázka ukazuje, jak komunikovat se informace o chybě ze služby klienta. Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s další kód přidat do služby k převodu výjimku interní chybu. Klient se pokusí provádět dělení nulou vynutit chybový stav služby.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Kalkulačka smlouvy se změnila zahrnout <xref:System.ServiceModel.FaultContractAttribute> jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
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
  
 <xref:System.ServiceModel.FaultContractAttribute> Atribut označuje, že `Divide` operace může vrátit chybu typu `MathFault`. Chyba může být libovolného typu, který lze serializovat. V takovém případě `MathFault` kontraktu dat, vypadá takto:  
  
```csharp
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
  
 `Divide` Vyvolá metoda výjimku <xref:System.ServiceModel.FaultException%601> dojde k výjimce při dělení nulovou výjimky, jak je znázorněno v následujícím ukázkovém kódu. Tato výjimka za následek selhání odesílané do klienta.  
  
```csharp
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
  
 Klientský kód způsobí chybu vyžádáním dělení nulou. Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Zobrazí dělení nulou uváděny jako chyba. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Klient k tomu zachytávání odpovídající `FaultException<MathFault>` výjimka:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Ve výchozím nastavení podrobnosti neočekávané výjimky neodešlou do klienta zabránit podrobnosti o implementaci služby z uvození hranici zabezpečení služby. `FaultContract` poskytuje způsob, jak popisují chyby v kontraktu a označit určité typy výjimek podle potřeby pro přenos do klienta. `FaultException<T>` poskytuje mechanismus za běhu pro odesílání chyb spotřebitelům.  
  
 Je však užitečné při ladění, naleznete v tématu interních detailů selhání služby. Chcete-li vypnout zabezpečené chování výše popsaný, můžete určit, že podrobnosti o každé neošetřená výjimka na serveru součástí by měly být chyby, která je odeslána do klienta. To lze provést nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> k `true`. Můžete buď nastavit ji v kódu nebo v konfiguraci, jak je znázorněno v následujícím příkladu.  
  
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
  
 Dále chování musí být přidružené služby tak, že nastavíte `behaviorConfiguration` atribut služby v konfiguračním souboru na "CalculatorServiceBehavior".  
  
 K zachytávání těchto chyb na straně klienta, který není obecný <xref:System.ServiceModel.FaultException> musí být zachycena.  
  
 Toto chování by měla sloužit pouze pro účely ladění a nikdy by měl být povoleno v produkčním prostředí.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a>Viz také
