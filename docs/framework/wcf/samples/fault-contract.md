---
title: Chyba – kontrakt
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 5081284075ffa31c947a0e63f915a721ea5983c0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600500"
---
# <a name="fault-contract"></a><span data-ttu-id="5ae84-102">Chyba – kontrakt</span><span class="sxs-lookup"><span data-stu-id="5ae84-102">Fault Contract</span></span>
<span data-ttu-id="5ae84-103">Ukázka smlouvy o selhání ukazuje, jak sdělit informace o chybě ze služby klientovi.</span><span class="sxs-lookup"><span data-stu-id="5ae84-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="5ae84-104">Ukázka je založena na [Začínáme](getting-started-sample.md)s nějakým dalším kódem přidaným do služby pro převod vnitřní výjimky na chybu.</span><span class="sxs-lookup"><span data-stu-id="5ae84-104">The sample is based on the [Getting Started](getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="5ae84-105">Klient se pokusí provést dělení nulou, aby vynutil chybový stav služby.</span><span class="sxs-lookup"><span data-stu-id="5ae84-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ae84-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5ae84-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5ae84-107">Smlouva kalkulačky byla upravena tak, aby obsahovala, <xref:System.ServiceModel.FaultContractAttribute> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5ae84-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="5ae84-108"><xref:System.ServiceModel.FaultContractAttribute>Atribut označuje, že `Divide` operace může vracet chybu typu `MathFault` .</span><span class="sxs-lookup"><span data-stu-id="5ae84-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="5ae84-109">Chyba může být libovolného typu, který lze serializovat.</span><span class="sxs-lookup"><span data-stu-id="5ae84-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="5ae84-110">V tomto případě je to `MathFault` kontrakt dat, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="5ae84-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="5ae84-111">`Divide`Metoda vyvolá <xref:System.ServiceModel.FaultException%601> výjimku, pokud dojde k výjimce nulou, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="5ae84-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="5ae84-112">Tato výjimka vede k odeslání chyby klientovi.</span><span class="sxs-lookup"><span data-stu-id="5ae84-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="5ae84-113">Kód klienta vynutí chybu tím, že si vyžádá dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="5ae84-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="5ae84-114">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5ae84-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5ae84-115">Uvidíte, že dělení nulou se hlásí jako chyba.</span><span class="sxs-lookup"><span data-stu-id="5ae84-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="5ae84-116">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="5ae84-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="5ae84-117">Klient to provede zachycením příslušné `FaultException<MathFault>` výjimky:</span><span class="sxs-lookup"><span data-stu-id="5ae84-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="5ae84-118">Ve výchozím nastavení se klientovi neodesílají podrobnosti o neočekávaných výjimkách, aby se předešlo podrobnostem implementace služby z řídicího panelu zabezpečené hranice služby.</span><span class="sxs-lookup"><span data-stu-id="5ae84-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="5ae84-119">`FaultContract`poskytuje způsob, jak popsat chyby ve smlouvě a označovat určité typy výjimek, které jsou vhodné pro přenos klientovi.</span><span class="sxs-lookup"><span data-stu-id="5ae84-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="5ae84-120">`FaultException<T>`poskytuje mechanizmus běhu pro posílání chyb příjemcům.</span><span class="sxs-lookup"><span data-stu-id="5ae84-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="5ae84-121">Je však vhodné zobrazit interní podrobnosti o selhání služby při ladění.</span><span class="sxs-lookup"><span data-stu-id="5ae84-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="5ae84-122">Chcete-li vypnout zabezpečené chování popsané výše, můžete určit, že podrobnosti o každé neošetřené výjimce na serveru by měly být zahrnuty do chyby, která je odeslána klientovi.</span><span class="sxs-lookup"><span data-stu-id="5ae84-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="5ae84-123">To je provedeno nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> na `true` .</span><span class="sxs-lookup"><span data-stu-id="5ae84-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="5ae84-124">Můžete ho buď nastavit v kódu, nebo v konfiguraci, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="5ae84-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="5ae84-125">Kromě toho musí být chování přidruženo ke službě nastavením `behaviorConfiguration` atributu služby v konfiguračním souboru na hodnotu "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="5ae84-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="5ae84-126">Chcete-li zachytit taková selhání klienta, <xref:System.ServiceModel.FaultException> musí být zachycena neobecná.</span><span class="sxs-lookup"><span data-stu-id="5ae84-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="5ae84-127">Toto chování by se mělo používat jenom pro účely ladění a nikdy by nemělo být povolené v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="5ae84-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5ae84-128">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5ae84-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5ae84-129">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ae84-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5ae84-130">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ae84-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5ae84-131">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5ae84-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5ae84-132">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="5ae84-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5ae84-133">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5ae84-133">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5ae84-134">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="5ae84-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5ae84-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5ae84-135">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
