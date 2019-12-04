---
title: Relace
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: e364b539e355f669037983813f9e6d1e0371da1f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715077"
---
# <a name="session"></a><span data-ttu-id="67501-102">Relace</span><span class="sxs-lookup"><span data-stu-id="67501-102">Session</span></span>
<span data-ttu-id="67501-103">Ukázka relace ukazuje, jak implementovat kontrakt, který vyžaduje relaci.</span><span class="sxs-lookup"><span data-stu-id="67501-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="67501-104">Relace poskytuje kontext pro provádění více operací.</span><span class="sxs-lookup"><span data-stu-id="67501-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="67501-105">Díky tomu může služba přidružit stav k dané relaci, aby následné operace mohly používat stav předchozí operace.</span><span class="sxs-lookup"><span data-stu-id="67501-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="67501-106">Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="67501-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="67501-107">`ICalculator` kontrakt byl upraven, aby bylo možné provést sadu aritmetických operací a přitom zachovat běžící výsledek.</span><span class="sxs-lookup"><span data-stu-id="67501-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="67501-108">Tato funkce je definována kontraktem `ICalculatorSession`.</span><span class="sxs-lookup"><span data-stu-id="67501-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="67501-109">Služba udržuje stav pro klienta jako volání více operací služby za účelem provedení výpočtu.</span><span class="sxs-lookup"><span data-stu-id="67501-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="67501-110">Klient může načíst aktuální výsledek voláním `Result()` a vymazat výsledek na nulu voláním `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="67501-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="67501-111">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="67501-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="67501-112">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="67501-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="67501-113">Nastavení <xref:System.ServiceModel.SessionMode> kontraktu pro `Required` zajistí, že pokud se kontrakt zveřejní přes konkrétní vazbu, vazba podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="67501-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="67501-114">Pokud vazba nepodporuje relace, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="67501-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="67501-115">Rozhraní `ICalculatorSession` je definováno tak, aby bylo možné volat jednu nebo více operací, což upravuje běžící výsledek, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="67501-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="67501-116">Služba používá <xref:System.ServiceModel.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession> ke svázání daného kontextu instance služby s každou příchozí relací.</span><span class="sxs-lookup"><span data-stu-id="67501-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="67501-117">Díky tomu může služba udržovat běžící výsledek pro každou relaci v místní členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="67501-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="67501-118">Když spustíte ukázku, klient provede několik požadavků na server a požádá o výsledek, který se pak zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="67501-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="67501-119">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="67501-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="67501-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="67501-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="67501-121">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67501-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="67501-122">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67501-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="67501-123">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="67501-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="67501-124">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="67501-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="67501-125">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="67501-125">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="67501-126">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="67501-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="67501-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="67501-127">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
