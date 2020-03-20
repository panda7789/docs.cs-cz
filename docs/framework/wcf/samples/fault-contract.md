---
title: Chyba – kontrakt
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: c8e93f73d150132c9d6750b81ba2ade944808d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183657"
---
# <a name="fault-contract"></a>Chyba – kontrakt
Ukázka kontraktu poruchy ukazuje, jak komunikovat informace o chybě ze služby klientovi. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s některé další kód přidán do služby převést vnitřní výjimku na chybu. Klient se pokusí provést dělení nulou vynutit chybový stav ve službě.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Smlouva kalkulačky byla upravena <xref:System.ServiceModel.FaultContractAttribute> tak, aby obsahovala, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Atribut <xref:System.ServiceModel.FaultContractAttribute> označuje, `Divide` že operace může vrátit `MathFault`chybu typu . Chyba může být libovolného typu, který lze serializovat. V tomto případě `MathFault` je smlouva o datech, a to takto:  
  
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
  
 Metoda `Divide` vyvolá výjimku, <xref:System.ServiceModel.FaultException%601> když dojde k dělení nulovou výjimkou, jak je znázorněno v následujícím ukázkovém kódu. Tato výjimka má za následek chybu odesílané klientovi.  
  
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
  
 Kód klienta vynutí chybu vyžádáním dělení nulou. Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Vidíte dělení nulou, která je hlášena jako chyba. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 Klient to provádí zachycením `FaultException<MathFault>` příslušné výjimky:  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 Ve výchozím nastavení nejsou klientovi odesílány podrobnosti o neočekávaných výjimkách, aby se zabránilo tomu, že podrobnosti o implementaci služby budou unikat zabezpečené hranici služby. `FaultContract`poskytuje způsob, jak popsat chyby ve smlouvě a označit určité typy výjimek podle potřeby pro přenos klientovi. `FaultException<T>`poskytuje mechanismus běhu pro odesílání chyb spotřebitelům.  
  
 Je však užitečné zobrazit vnitřní podrobnosti selhání služby při ladění. Chcete-li vypnout chování zabezpečení dříve popsané, můžete označit, že podrobnosti o každé neošetřené výjimce na serveru by měly být zahrnuty do chyby, která je odeslána klientovi. Toho lze dosáhnout <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> nastavením na . `true` Můžete jej nastavit v kódu nebo v konfiguraci, jak je znázorněno v následující ukázce.  
  
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
  
 Dále chování musí být přidruženy ke `behaviorConfiguration` službě nastavením atributu služby v konfiguračním souboru na "CalculatorServiceBehavior".  
  
 Chcete-li zachytit tyto chyby na <xref:System.ServiceModel.FaultException> straně klienta, musí být zachyceny neobecné.  
  
 Toto chování by měla být použita pouze pro účely ladění a by nikdy být povolena v produkčním prostředí.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
