---
title: Chyba – kontrakt
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: 5b3348f31d239d6bf7e64852ba02010115062669
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724905"
---
# <a name="fault-contract"></a><span data-ttu-id="4c701-102">Chyba – kontrakt</span><span class="sxs-lookup"><span data-stu-id="4c701-102">Fault Contract</span></span>
<span data-ttu-id="4c701-103">Chyba – kontrakt ukázka ukazuje, jak komunikovat se informace o chybě ze služby klienta.</span><span class="sxs-lookup"><span data-stu-id="4c701-103">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="4c701-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), s další kód přidat do služby k převodu výjimku interní chybu.</span><span class="sxs-lookup"><span data-stu-id="4c701-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="4c701-105">Klient se pokusí provádět dělení nulou vynutit chybový stav služby.</span><span class="sxs-lookup"><span data-stu-id="4c701-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c701-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4c701-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4c701-107">Kalkulačka smlouvy se změnila zahrnout <xref:System.ServiceModel.FaultContractAttribute> jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4c701-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="4c701-108"><xref:System.ServiceModel.FaultContractAttribute> Atribut označuje, že `Divide` operace může vrátit chybu typu `MathFault`.</span><span class="sxs-lookup"><span data-stu-id="4c701-108">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="4c701-109">Chyba může být libovolného typu, který lze serializovat.</span><span class="sxs-lookup"><span data-stu-id="4c701-109">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="4c701-110">V takovém případě `MathFault` kontraktu dat, vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="4c701-110">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
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
  
 <span data-ttu-id="4c701-111">`Divide` Vyvolá metoda výjimku <xref:System.ServiceModel.FaultException%601> dojde k výjimce při dělení nulovou výjimky, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4c701-111">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="4c701-112">Tato výjimka za následek selhání odesílané do klienta.</span><span class="sxs-lookup"><span data-stu-id="4c701-112">This exception results in a fault being sent to the client.</span></span>  
  
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
  
 <span data-ttu-id="4c701-113">Klientský kód způsobí chybu vyžádáním dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="4c701-113">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="4c701-114">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="4c701-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4c701-115">Zobrazí dělení nulou uváděny jako chyba.</span><span class="sxs-lookup"><span data-stu-id="4c701-115">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="4c701-116">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="4c701-116">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4c701-117">Klient k tomu zachytávání odpovídající `FaultException<MathFault>` výjimka:</span><span class="sxs-lookup"><span data-stu-id="4c701-117">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```  
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="4c701-118">Ve výchozím nastavení podrobnosti neočekávané výjimky neodešlou do klienta zabránit podrobnosti o implementaci služby z uvození hranici zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="4c701-118">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="4c701-119">`FaultContract` poskytuje způsob, jak popisují chyby v kontraktu a označit určité typy výjimek podle potřeby pro přenos do klienta.</span><span class="sxs-lookup"><span data-stu-id="4c701-119">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="4c701-120">`FaultException<T>` poskytuje mechanismus za běhu pro odesílání chyb spotřebitelům.</span><span class="sxs-lookup"><span data-stu-id="4c701-120">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="4c701-121">Je však užitečné při ladění, naleznete v tématu interních detailů selhání služby.</span><span class="sxs-lookup"><span data-stu-id="4c701-121">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="4c701-122">Chcete-li vypnout zabezpečené chování výše popsaný, můžete určit, že podrobnosti o každé neošetřená výjimka na serveru součástí by měly být chyby, která je odeslána do klienta.</span><span class="sxs-lookup"><span data-stu-id="4c701-122">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="4c701-123">To lze provést nastavením <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="4c701-123">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="4c701-124">Můžete buď nastavit ji v kódu nebo v konfiguraci, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4c701-124">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="4c701-125">Dále chování musí být přidružené služby tak, že nastavíte `behaviorConfiguration` atribut služby v konfiguračním souboru na "CalculatorServiceBehavior".</span><span class="sxs-lookup"><span data-stu-id="4c701-125">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="4c701-126">K zachytávání těchto chyb na straně klienta, který není obecný <xref:System.ServiceModel.FaultException> musí být zachycena.</span><span class="sxs-lookup"><span data-stu-id="4c701-126">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="4c701-127">Toto chování by měla sloužit pouze pro účely ladění a nikdy by měl být povoleno v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="4c701-127">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4c701-128">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="4c701-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4c701-129">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4c701-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4c701-130">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4c701-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4c701-131">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4c701-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4c701-132">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="4c701-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4c701-133">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4c701-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4c701-134">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4c701-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4c701-135">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4c701-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
  
## <a name="see-also"></a><span data-ttu-id="4c701-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c701-136">See Also</span></span>
