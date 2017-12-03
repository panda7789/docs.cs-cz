---
title: "Chyba – kontrakt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3ab1213b5821233e28f36089039145d5874dd3a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="fault-contract"></a><span data-ttu-id="f1a31-102">Chyba – kontrakt</span><span class="sxs-lookup"><span data-stu-id="f1a31-102">Fault Contract</span></span>
<span data-ttu-id="f1a31-103">Chyba – kontrakt příklad znázorňuje způsob ke sdělování informací chyby ze služby klienta.</span><span class="sxs-lookup"><span data-stu-id="f1a31-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="f1a31-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s další kód přidat ke službě převést výjimku vnitřní chybu.</span><span class="sxs-lookup"><span data-stu-id="f1a31-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="f1a31-105">Klient se pokusí provést dělení nulou vynutit chybový stav služby.</span><span class="sxs-lookup"><span data-stu-id="f1a31-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f1a31-106">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f1a31-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f1a31-107">Kontrakt kalkulačky změnila zahrnout <xref:System.ServiceModel.FaultContractAttribute> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="f1a31-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="f1a31-108"><xref:System.ServiceModel.FaultContractAttribute> Atribut znamená, že `Divide` operace může vrátit chybu typu `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="f1a31-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="f1a31-109">Chybu může být jakéhokoli typu, který lze serializovat.</span><span class="sxs-lookup"><span data-stu-id="f1a31-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="f1a31-110">V takovém případě `MathFault` kontraktu dat je následující:</span><span class="sxs-lookup"><span data-stu-id="f1a31-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="f1a31-111">`Divide` Metoda vrátí <xref:System.ServiceModel.FaultException%601> došlo k výjimce při Rozděl nulové výjimkou jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="f1a31-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="f1a31-112">Tato výjimka za následek chybu odesílány do klienta.</span><span class="sxs-lookup"><span data-stu-id="f1a31-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="f1a31-113">Kód klienta vynutí chybu tím, že požádá dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="f1a31-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="f1a31-114">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="f1a31-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f1a31-115">Zobrazí dělení nulou nehlásí jako chybu.</span><span class="sxs-lookup"><span data-stu-id="f1a31-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="f1a31-116">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="f1a31-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="f1a31-117">Klient dosahuje tím, že zachytávání odpovídající `FaultException<MathFault>` výjimka:</span><span class="sxs-lookup"><span data-stu-id="f1a31-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="f1a31-118">Ve výchozím nastavení podrobnosti o neočekávané výjimky neodešlou do klienta aby podrobnosti o implementaci služby z uvozovací znaky hranice zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="f1a31-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="f1a31-119">`FaultContract`poskytuje způsob, jak popisuje chyb v kontraktu a označit určité typy výjimek podle potřeby pro přenos do klienta.</span><span class="sxs-lookup"><span data-stu-id="f1a31-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="f1a31-120">`FaultException<T>`poskytuje mechanismus běhu pro odesílání chyb k příjemce.</span><span class="sxs-lookup"><span data-stu-id="f1a31-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="f1a31-121">Je však užitečné při ladění, najdete v části interní podrobnosti o selhání služby.</span><span class="sxs-lookup"><span data-stu-id="f1a31-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="f1a31-122">Chcete-li vypnout zabezpečené chování výše popsané, můžete určit, že podrobnosti o každé neošetřených výjimek na serveru by měl být součástí chybu, která je odeslána do klienta.</span><span class="sxs-lookup"><span data-stu-id="f1a31-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="f1a31-123">To se provádí nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="f1a31-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="f1a31-124">Můžete buď ho nastavit v kódu nebo v konfiguraci, jak znázorňuje následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="f1a31-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="f1a31-125">Navíc chování musí být přidružen službu nastavením `behaviorConfiguration` atribut služby v konfiguračním souboru na "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="f1a31-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="f1a31-126">K zachycení takové chyby u klienta, neobecnou <xref:System.ServiceModel.FaultException> musí být zachycena.</span><span class="sxs-lookup"><span data-stu-id="f1a31-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="f1a31-127">Toto chování lze používat pouze pro účely ladění a nikdy by měla být povolená v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="f1a31-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f1a31-128">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="f1a31-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="f1a31-129">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1a31-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f1a31-130">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1a31-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="f1a31-131">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f1a31-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f1a31-132">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="f1a31-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1a31-133">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="f1a31-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f1a31-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="f1a31-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1a31-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f1a31-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="f1a31-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1a31-136">See Also</span></span>
