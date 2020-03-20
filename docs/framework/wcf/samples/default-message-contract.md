---
title: Výchozí kontrakt zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 46b69697616ad7983daed16f8a180a4da7f61a16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183773"
---
# <a name="default-message-contract"></a>Výchozí kontrakt zprávy
Ukázka výchozí zprávy kontrakt udává službu, kde je vlastní uživatelem definovaná zpráva předána a z operací služby. Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje rozhraní kalkulačky jako zadali služby. Namísto jednotlivých operací služby pro sčítání, odčítání, násobení a dělení použité v [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), tato ukázka předá vlastní zprávu, která obsahuje operandy i operátor a vrátí výsledek výpočtu aritmetiky.  
  
 Klient je konzolový program (.exe) a knihovna služeb (.dll) je hostována internetovou informační službou (IIS). Aktivita klienta je viditelná v okně konzoly.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Ve službě je definována jedna operace služby, která `MyMessage`přijímá a vrací vlastní zprávy typu . I když v této ukázce jsou zprávy požadavků a odpovědí stejného typu, mohou být samozřejmě různé zprávy smlouvy v případě potřeby.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Vlastní zpráva `MyMessage` je definována ve třídě <xref:System.ServiceModel.MessageContractAttribute>s <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> poznámkou a atributy . V této ukázce se používá pouze třetí konstruktor. Pomocí smlouvy zprávy umožňuje vykonávat plnou kontrolu nad zprávou SOAP. V této ukázce <xref:System.ServiceModel.MessageHeaderAttribute> se `Operation` atribut používá k vložení do hlavičky SOAP. Operandy `N1` `N2` a `Result` zobrazí se v těle SOAP, <xref:System.ServiceModel.MessageBodyMemberAttribute> protože mají atribut použit.  
  
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
  
 Třída implementace obsahuje kód `Calculate` pro operaci služby. Třída `CalculateService` získá operandy a operátor ze zprávy požadavku a vytvoří zprávu odpovědi, která obsahuje výsledek požadovaného výpočtu, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Generovaný kód klienta pro klienta byl vytvořen pomocí nástroje [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) Nástroj v případě potřeby automaticky vytvoří typy smluv zpráv v generovaném kódu klienta. Možnost `/messageContract` příkazu může být zadán a vynutit generování zpráv smluv.  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 Následující ukázkový kód ukazuje klienta pomocí `MyMessage` zprávy.  
  
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
  
 Při spuštění ukázky jsou výpočty zobrazeny v okně klientské konzole. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 V tomto okamžiku vlastní uživatelem definované zprávy prošly mezi klientem a operace služby. Kontrakt zprávy definoval, že operandy a výsledky byly v textu zprávy a že operátor byl v záhlaví zprávy. Protokolování zpráv lze nakonfigurovat tak, aby sledovalo tuto strukturu zpráv.  
  
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
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
