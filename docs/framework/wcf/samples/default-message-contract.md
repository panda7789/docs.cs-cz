---
title: Výchozí kontrakt zprávy
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 267cdffdc532aaa2b31de835c31d23e93aca8c54
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59315514"
---
# <a name="default-message-contract"></a><span data-ttu-id="c0286-102">Výchozí kontrakt zprávy</span><span class="sxs-lookup"><span data-stu-id="c0286-102">Default Message Contract</span></span>
<span data-ttu-id="c0286-103">Výchozí kontrakt zprávy ukázce služby, kde je předán vlastní uživatelsky definovanou zprávu do a z operací služby.</span><span class="sxs-lookup"><span data-stu-id="c0286-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="c0286-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , který implementuje rozhraní kalkulačku jako služba typu.</span><span class="sxs-lookup"><span data-stu-id="c0286-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="c0286-105">Místo operace jednotlivé služby pro sčítání, odčítání, násobení a dělení používané [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), tento příklad předává vlastní zprávu, která obsahuje operandy a operátor a vrátí výsledek aritmetické výpočtu.</span><span class="sxs-lookup"><span data-stu-id="c0286-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="c0286-106">Klient je program konzoly (.exe) a služby knihovny (.dll) je hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="c0286-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="c0286-107">Činnost klienta je vidět v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="c0286-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0286-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c0286-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c0286-109">Ve službě, je definován operaci jedinou službou, která přijímá a vrací vlastní zprávy typu `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="c0286-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="c0286-110">I když v této ukázce jsou zprávy požadavků a odpovědí stejného typu, jsou samozřejmě možné jiná zpráva smluv v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="c0286-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="c0286-111">Vlastní zpráva `MyMessage` je definován ve třídě opatřen poznámkou <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="c0286-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="c0286-112">Třetí konstruktor se používá v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="c0286-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="c0286-113">Použití kontraktů zpráv umožňuje vykonávat plnou kontrolu nad zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="c0286-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="c0286-114">V této ukázce <xref:System.ServiceModel.MessageHeaderAttribute> atribut se používá pro umístění `Operation` v záhlaví SOAP.</span><span class="sxs-lookup"><span data-stu-id="c0286-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="c0286-115">Operandy `N1`, `N2` a `Result` být použit v těle SOAP, protože mají <xref:System.ServiceModel.MessageBodyMemberAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="c0286-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="c0286-116">Implementace třídy obsahuje kód `Calculate` operace služby.</span><span class="sxs-lookup"><span data-stu-id="c0286-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="c0286-117">`CalculateService` Třídy získá operandy a operátor ze zprávy požadavku a vytvoří zprávu odpovědi, který obsahuje výsledek výpočtu požadovaný, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c0286-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="c0286-118">Byl vytvořen kód klienta vygenerovaný pro klienta [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="c0286-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="c0286-119">Nástroj automaticky vytváří typy kontraktů zpráv v kódu generovaného klienta v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="c0286-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="c0286-120">`/messageContract` Příkazu lze zadat pro vynucení generování kontraktů zpráv.</span><span class="sxs-lookup"><span data-stu-id="c0286-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="c0286-121">Následující ukázkový kód ukazuje klienta pomocí `MyMessage` zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0286-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
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
  
 <span data-ttu-id="c0286-122">Při spuštění ukázky výpočty jsou zobrazeny v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="c0286-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="c0286-123">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="c0286-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="c0286-124">V tomto okamžiku vlastní uživatelem definované zprávy prošly mezi klientem a operace služby.</span><span class="sxs-lookup"><span data-stu-id="c0286-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="c0286-125">Kontrakt zprávy definován, že v textu zprávy byly operandy a výsledky a že operátor, který byl v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0286-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="c0286-126">Protokolování zpráv je možné nakonfigurovat dodržovat tato struktura zprávy.</span><span class="sxs-lookup"><span data-stu-id="c0286-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c0286-127">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="c0286-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c0286-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0286-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c0286-129">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0286-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="c0286-130">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c0286-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c0286-131">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="c0286-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c0286-132">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="c0286-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c0286-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c0286-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c0286-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c0286-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
