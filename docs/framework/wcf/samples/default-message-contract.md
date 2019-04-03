---
title: Výchozí kontrakt zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: c65004189c43e4838c9131f61aaa09a41191b702
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817289"
---
# <a name="default-message-contract"></a>Výchozí kontrakt zprávy
Výchozí kontrakt zprávy ukázce služby, kde je předán vlastní uživatelsky definovanou zprávu do a z operací služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , který implementuje rozhraní kalkulačku jako služba typu. Místo operace jednotlivé služby pro sčítání, odčítání, násobení a dělení používané [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), tento příklad předává vlastní zprávu, která obsahuje operandy a operátor a vrátí výsledek aritmetické výpočtu.  
  
 Klient je program konzoly (.exe) a služby knihovny (.dll) je hostované v Internetové informační služby (IIS). Činnost klienta je vidět v okně konzoly.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Ve službě, je definován operaci jedinou službou, která přijímá a vrací vlastní zprávy typu `MyMessage`. I když v této ukázce jsou zprávy požadavků a odpovědí stejného typu, jsou samozřejmě možné jiná zpráva smluv v případě potřeby.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 Vlastní zpráva `MyMessage` je definován ve třídě opatřen poznámkou <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy. Třetí konstruktor se používá v této ukázce. Použití kontraktů zpráv umožňuje vykonávat plnou kontrolu nad zprávu protokolu SOAP. V této ukázce <xref:System.ServiceModel.MessageHeaderAttribute> atribut se používá pro umístění `Operation` v záhlaví SOAP. Operandy `N1`, `N2` a `Result` být použit v těle SOAP, protože mají <xref:System.ServiceModel.MessageBodyMemberAttribute> atribut.  
  
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
  
 Implementace třídy obsahuje kód `Calculate` operace služby. `CalculateService` Třídy získá operandy a operátor ze zprávy požadavku a vytvoří zprávu odpovědi, který obsahuje výsledek výpočtu požadovaný, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Byl vytvořen kód klienta vygenerovaný pro klienta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj. Nástroj automaticky vytváří typy kontraktů zpráv v kódu generovaného klienta v případě potřeby. `/messageContract` Příkazu lze zadat pro vynucení generování kontraktů zpráv.  
  
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
  
 Při spuštění ukázky výpočty jsou zobrazeny v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 V tomto okamžiku vlastní uživatelem definované zprávy prošly mezi klientem a operace služby. Kontrakt zprávy definován, že v textu zprávy byly operandy a výsledky a že operátor, který byl v záhlaví zprávy. Protokolování zpráv je možné nakonfigurovat dodržovat tato struktura zprávy.  
  
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
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
