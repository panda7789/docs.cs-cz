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
# <a name="default-message-contract"></a><span data-ttu-id="e48b5-102">Výchozí kontrakt zprávy</span><span class="sxs-lookup"><span data-stu-id="e48b5-102">Default Message Contract</span></span>
<span data-ttu-id="e48b5-103">Ukázka výchozí zprávy kontrakt udává službu, kde je vlastní uživatelem definovaná zpráva předána a z operací služby.</span><span class="sxs-lookup"><span data-stu-id="e48b5-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="e48b5-104">Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje rozhraní kalkulačky jako zadali služby.</span><span class="sxs-lookup"><span data-stu-id="e48b5-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="e48b5-105">Namísto jednotlivých operací služby pro sčítání, odčítání, násobení a dělení použité v [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), tato ukázka předá vlastní zprávu, která obsahuje operandy i operátor a vrátí výsledek výpočtu aritmetiky.</span><span class="sxs-lookup"><span data-stu-id="e48b5-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="e48b5-106">Klient je konzolový program (.exe) a knihovna služeb (.dll) je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="e48b5-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="e48b5-107">Aktivita klienta je viditelná v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="e48b5-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e48b5-108">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e48b5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e48b5-109">Ve službě je definována jedna operace služby, která `MyMessage`přijímá a vrací vlastní zprávy typu .</span><span class="sxs-lookup"><span data-stu-id="e48b5-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="e48b5-110">I když v této ukázce jsou zprávy požadavků a odpovědí stejného typu, mohou být samozřejmě různé zprávy smlouvy v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="e48b5-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="e48b5-111">Vlastní zpráva `MyMessage` je definována ve třídě <xref:System.ServiceModel.MessageContractAttribute>s <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> poznámkou a atributy .</span><span class="sxs-lookup"><span data-stu-id="e48b5-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="e48b5-112">V této ukázce se používá pouze třetí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e48b5-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="e48b5-113">Pomocí smlouvy zprávy umožňuje vykonávat plnou kontrolu nad zprávou SOAP.</span><span class="sxs-lookup"><span data-stu-id="e48b5-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="e48b5-114">V této ukázce <xref:System.ServiceModel.MessageHeaderAttribute> se `Operation` atribut používá k vložení do hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="e48b5-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="e48b5-115">Operandy `N1` `N2` a `Result` zobrazí se v těle SOAP, <xref:System.ServiceModel.MessageBodyMemberAttribute> protože mají atribut použit.</span><span class="sxs-lookup"><span data-stu-id="e48b5-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="e48b5-116">Třída implementace obsahuje kód `Calculate` pro operaci služby.</span><span class="sxs-lookup"><span data-stu-id="e48b5-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="e48b5-117">Třída `CalculateService` získá operandy a operátor ze zprávy požadavku a vytvoří zprávu odpovědi, která obsahuje výsledek požadovaného výpočtu, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="e48b5-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="e48b5-118">Generovaný kód klienta pro klienta byl vytvořen pomocí nástroje [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="e48b5-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="e48b5-119">Nástroj v případě potřeby automaticky vytvoří typy smluv zpráv v generovaném kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="e48b5-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="e48b5-120">Možnost `/messageContract` příkazu může být zadán a vynutit generování zpráv smluv.</span><span class="sxs-lookup"><span data-stu-id="e48b5-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="e48b5-121">Následující ukázkový kód ukazuje klienta pomocí `MyMessage` zprávy.</span><span class="sxs-lookup"><span data-stu-id="e48b5-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
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
  
 <span data-ttu-id="e48b5-122">Při spuštění ukázky jsou výpočty zobrazeny v okně klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="e48b5-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="e48b5-123">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="e48b5-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e48b5-124">V tomto okamžiku vlastní uživatelem definované zprávy prošly mezi klientem a operace služby.</span><span class="sxs-lookup"><span data-stu-id="e48b5-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="e48b5-125">Kontrakt zprávy definoval, že operandy a výsledky byly v textu zprávy a že operátor byl v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="e48b5-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="e48b5-126">Protokolování zpráv lze nakonfigurovat tak, aby sledovalo tuto strukturu zpráv.</span><span class="sxs-lookup"><span data-stu-id="e48b5-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e48b5-127">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="e48b5-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e48b5-128">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e48b5-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e48b5-129">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e48b5-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e48b5-130">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e48b5-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e48b5-131">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="e48b5-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e48b5-132">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="e48b5-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e48b5-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e48b5-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e48b5-134">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e48b5-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
