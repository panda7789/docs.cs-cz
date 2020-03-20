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
# <a name="fault-contract"></a><span data-ttu-id="8252e-102">Chyba – kontrakt</span><span class="sxs-lookup"><span data-stu-id="8252e-102">Fault Contract</span></span>
<span data-ttu-id="8252e-103">Ukázka kontraktu poruchy ukazuje, jak komunikovat informace o chybě ze služby klientovi.</span><span class="sxs-lookup"><span data-stu-id="8252e-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="8252e-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s některé další kód přidán do služby převést vnitřní výjimku na chybu.</span><span class="sxs-lookup"><span data-stu-id="8252e-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="8252e-105">Klient se pokusí provést dělení nulou vynutit chybový stav ve službě.</span><span class="sxs-lookup"><span data-stu-id="8252e-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8252e-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8252e-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8252e-107">Smlouva kalkulačky byla upravena <xref:System.ServiceModel.FaultContractAttribute> tak, aby obsahovala, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="8252e-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="8252e-108">Atribut <xref:System.ServiceModel.FaultContractAttribute> označuje, `Divide` že operace může vrátit `MathFault`chybu typu .</span><span class="sxs-lookup"><span data-stu-id="8252e-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="8252e-109">Chyba může být libovolného typu, který lze serializovat.</span><span class="sxs-lookup"><span data-stu-id="8252e-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="8252e-110">V tomto případě `MathFault` je smlouva o datech, a to takto:</span><span class="sxs-lookup"><span data-stu-id="8252e-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="8252e-111">Metoda `Divide` vyvolá výjimku, <xref:System.ServiceModel.FaultException%601> když dojde k dělení nulovou výjimkou, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="8252e-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="8252e-112">Tato výjimka má za následek chybu odesílané klientovi.</span><span class="sxs-lookup"><span data-stu-id="8252e-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="8252e-113">Kód klienta vynutí chybu vyžádáním dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="8252e-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="8252e-114">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8252e-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8252e-115">Vidíte dělení nulou, která je hlášena jako chyba.</span><span class="sxs-lookup"><span data-stu-id="8252e-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="8252e-116">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="8252e-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="8252e-117">Klient to provádí zachycením `FaultException<MathFault>` příslušné výjimky:</span><span class="sxs-lookup"><span data-stu-id="8252e-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="8252e-118">Ve výchozím nastavení nejsou klientovi odesílány podrobnosti o neočekávaných výjimkách, aby se zabránilo tomu, že podrobnosti o implementaci služby budou unikat zabezpečené hranici služby.</span><span class="sxs-lookup"><span data-stu-id="8252e-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="8252e-119">`FaultContract`poskytuje způsob, jak popsat chyby ve smlouvě a označit určité typy výjimek podle potřeby pro přenos klientovi.</span><span class="sxs-lookup"><span data-stu-id="8252e-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="8252e-120">`FaultException<T>`poskytuje mechanismus běhu pro odesílání chyb spotřebitelům.</span><span class="sxs-lookup"><span data-stu-id="8252e-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="8252e-121">Je však užitečné zobrazit vnitřní podrobnosti selhání služby při ladění.</span><span class="sxs-lookup"><span data-stu-id="8252e-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="8252e-122">Chcete-li vypnout chování zabezpečení dříve popsané, můžete označit, že podrobnosti o každé neošetřené výjimce na serveru by měly být zahrnuty do chyby, která je odeslána klientovi.</span><span class="sxs-lookup"><span data-stu-id="8252e-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="8252e-123">Toho lze dosáhnout <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> nastavením na . `true`</span><span class="sxs-lookup"><span data-stu-id="8252e-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="8252e-124">Můžete jej nastavit v kódu nebo v konfiguraci, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="8252e-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="8252e-125">Dále chování musí být přidruženy ke `behaviorConfiguration` službě nastavením atributu služby v konfiguračním souboru na "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="8252e-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="8252e-126">Chcete-li zachytit tyto chyby na <xref:System.ServiceModel.FaultException> straně klienta, musí být zachyceny neobecné.</span><span class="sxs-lookup"><span data-stu-id="8252e-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="8252e-127">Toto chování by měla být použita pouze pro účely ladění a by nikdy být povolena v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="8252e-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8252e-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8252e-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8252e-129">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8252e-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8252e-130">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8252e-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8252e-131">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8252e-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8252e-132">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="8252e-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8252e-133">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8252e-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8252e-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8252e-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8252e-135">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8252e-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
