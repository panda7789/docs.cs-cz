---
title: Výchozí kontrakt zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: dcdeeda0d6054c9cf6fefa31ea33d720c0c0f3f7
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716584"
---
# <a name="default-message-contract"></a>Výchozí kontrakt zprávy
Výchozí ukázka kontraktu zpráv ukazuje službu, ve které se vlastní uživatelem definovaná zpráva předává do a z operací služby. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje rozhraní kalkulačky jako typovou službu. Namísto individuálních operací služby pro sčítání, odčítání, násobení a dělení použité v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md)tento příklad projde vlastní zprávu, která obsahuje operandy i operátor, a vrátí výsledek aritmetického výpočtu.  
  
 Klient je program konzoly (. exe) a knihovna služeb (. dll) je hostovaná službou Internetová informační služba (IIS). Aktivita klienta se zobrazí v okně konzoly.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 V rámci služby je definována jedna operace služby, která přijímá a vrací vlastní zprávy typu `MyMessage`. I když v této ukázce jsou zprávy žádosti a odpovědi stejného typu, můžou být v případě potřeby v případě potřeby jiné kontrakty zpráv.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Vlastní `MyMessage` zpráv je definována ve třídě s poznámkou pomocí atributů <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute>. V této ukázce je použit pouze třetí konstruktor. Použití kontraktů zpráv vám umožní plně ovládat zprávu protokolu SOAP. V této ukázce je atribut <xref:System.ServiceModel.MessageHeaderAttribute> použit k vložení `Operation` v hlavičce SOAP. Operandy `N1`, `N2` a `Result` se zobrazí v těle SOAP, protože mají použit atribut <xref:System.ServiceModel.MessageBodyMemberAttribute>.  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,   
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 Třída Implementation obsahuje kód pro operaci `Calculate` služby. Třída `CalculateService` získá operandy a operátor ze zprávy požadavku a vytvoří zprávu odpovědi, která obsahuje výsledek požadovaného výpočtu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 Vygenerovaný klientský kód pro klienta byl vytvořen pomocí nástroje Nástroj pro [DoSvcutilí metadat (ServiceModel. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) . Nástroj v případě potřeby automaticky vytvoří typy kontraktů zpráv v generovaném kódu klienta. Pro vynucení generování kontraktů zpráv je možné zadat možnost `/messageContract` příkazu.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Následující vzorový kód demonstruje klienta pomocí `MyMessage`ové zprávy.  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage() 
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 Při spuštění ukázky se výpočty zobrazí v okně konzoly klienta. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 V tomto okamžiku byly mezi klientem a operací služby předány vlastní uživatelem definované zprávy. Kontrakt zprávy definoval, že operandy a výsledky byly v těle zprávy a že byl operátor v záhlaví zprávy. Protokolování zpráv je možné nakonfigurovat tak, aby sledovalo tuto strukturu zpráv.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
