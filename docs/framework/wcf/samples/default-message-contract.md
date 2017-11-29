---
title: "Výchozí kontrakt zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
caps.latest.revision: "35"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 765e531530342af5cf0fccfb759626341103114a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="default-message-contract"></a><span data-ttu-id="7743f-102">Výchozí kontrakt zprávy</span><span class="sxs-lookup"><span data-stu-id="7743f-102">Default Message Contract</span></span>
<span data-ttu-id="7743f-103">Výchozí kontrakt zprávy příklad znázorňuje služby, kde je předán vlastní uživatelem definovaná zpráva do a z operací služby.</span><span class="sxs-lookup"><span data-stu-id="7743f-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="7743f-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje rozhraní kalkulačky jako typu služby.</span><span class="sxs-lookup"><span data-stu-id="7743f-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="7743f-105">Místo operací jednotlivé služby pro přidání, odčítání, násobení a dělení používány [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), tato ukázka předá vlastní zprávu, která obsahuje operandy a operátor a vrátí výsledek aritmetické výpočtu.</span><span class="sxs-lookup"><span data-stu-id="7743f-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="7743f-106">Klient je program konzoly (.exe) a služby knihovny (DLL.dll) je součást Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7743f-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7743f-107">Činnost klienta je viditelný v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="7743f-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7743f-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7743f-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7743f-109">Ve službě, je definována operace jedné služby která přijme a vrátí vlastních zpráv typu `MyMessage`.</span><span class="sxs-lookup"><span data-stu-id="7743f-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="7743f-110">I když v této ukázce zprávy požadavku a odpovědi jsou stejného typu, může samozřejmě být kontrakty jiná zpráva v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="7743f-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="7743f-111">Vlastní zprávu `MyMessage` je definována v třídě opatřen poznámkou <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="7743f-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="7743f-112">V této ukázce se používá pouze třetí konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7743f-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="7743f-113">Použití kontraktů zpráv umožňuje vykonávat plnou kontrolu nad zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7743f-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="7743f-114">V této ukázce <xref:System.ServiceModel.MessageHeaderAttribute> atribut se používá k put `Operation` v hlavičce protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7743f-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="7743f-115">Operandy `N1`, `N2` a `Result` být použit v těle protokolu SOAP, protože mají <xref:System.ServiceModel.MessageBodyMemberAttribute> atribut použitý.</span><span class="sxs-lookup"><span data-stu-id="7743f-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```  
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
  
 <span data-ttu-id="7743f-116">Obsahuje kód pro implementaci třídy `Calculate` operace služby.</span><span class="sxs-lookup"><span data-stu-id="7743f-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="7743f-117">`CalculateService` Třída získá operandy a operátor ze zprávy požadavku a vytvoří zprávu odpovědi, která obsahuje výsledek požadovaný výpočet, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="7743f-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="7743f-118">Kód klienta vygenerovaný pro klienta byla vytvořena pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="7743f-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="7743f-119">Nástroj automaticky vytvoří typy kontraktů zpráv v kódu generovaného klienta v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="7743f-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="7743f-120">`/messageContract` Účelem vynutit generování kontrakty zpráv může být určen příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="7743f-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="7743f-121">Následující vzorový kód ukazuje klienta pomocí `MyMessage` zprávy.</span><span class="sxs-lookup"><span data-stu-id="7743f-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage();  
request.N1 = 100D;  
request.N2 = 15.99D;  
request.Operation = "+";  
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="7743f-122">Při spuštění vzorového výpočty se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="7743f-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="7743f-123">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="7743f-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="7743f-124">Vlastní zprávy uživatelem definované v tomto okamžiku uplynulo mezi klientem a operace služby.</span><span class="sxs-lookup"><span data-stu-id="7743f-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="7743f-125">Kontrakt zprávy definované že operandy a výsledky byly v textu zprávy a že operátor bylo v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="7743f-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="7743f-126">Protokolování zpráv lze nakonfigurovat sledovat tuto strukturu zprávy.</span><span class="sxs-lookup"><span data-stu-id="7743f-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7743f-127">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="7743f-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7743f-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7743f-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7743f-129">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7743f-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7743f-130">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7743f-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7743f-131">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="7743f-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7743f-132">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7743f-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7743f-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7743f-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7743f-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7743f-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
  
## <a name="see-also"></a><span data-ttu-id="7743f-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="7743f-135">See Also</span></span>
