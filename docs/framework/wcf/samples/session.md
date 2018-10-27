---
title: Relace
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 0f6a06bfb9d1e5274df047e45a5042353515e206
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190772"
---
# <a name="session"></a><span data-ttu-id="808a1-102">Relace</span><span class="sxs-lookup"><span data-stu-id="808a1-102">Session</span></span>
<span data-ttu-id="808a1-103">Ukázková relace ukazuje, jak implementovat kontrakt, který vyžaduje relaci.</span><span class="sxs-lookup"><span data-stu-id="808a1-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="808a1-104">Relace poskytuje kontext pro provádění více operací.</span><span class="sxs-lookup"><span data-stu-id="808a1-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="808a1-105">To umožňuje službám přidružení stavu dané relace tak, aby následné operace můžete použít stav předchozí operace.</span><span class="sxs-lookup"><span data-stu-id="808a1-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="808a1-106">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje Kalkulačka služby.</span><span class="sxs-lookup"><span data-stu-id="808a1-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="808a1-107">`ICalculator` Povolit sadu aritmetické operace, které mají být provedeny, a zajistit přitom ochranu spuštěné výsledek byl změněn kontraktu.</span><span class="sxs-lookup"><span data-stu-id="808a1-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="808a1-108">Tato funkce je definována `ICalculatorSession` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="808a1-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="808a1-109">Služba zajišťuje stav na klienty, jako jsou volány více operací služby k provedení výpočtu.</span><span class="sxs-lookup"><span data-stu-id="808a1-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="808a1-110">Klient může načíst aktuální výsledek voláním `Result()` a zrušte zaškrtnutí výsledek, který má nulovou voláním `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="808a1-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="808a1-111">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="808a1-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="808a1-112">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="808a1-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="808a1-113">Nastavení <xref:System.ServiceModel.SessionMode> smlouvy na `Required` zajistí, že pokud kontrakt je přístupná přes konkrétní vazbu, vazba podporuje relací.</span><span class="sxs-lookup"><span data-stu-id="808a1-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="808a1-114">Pokud se vazba nepodporuje relace je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="808a1-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="808a1-115">`ICalculatorSession` Rozhraní je definován tak, že je možné volat jednu nebo více operací, který změní spuštěné výsledek, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="808a1-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="808a1-116">Služba používá <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.PerSession> každou příchozí relace vytvořit vazbu kontext instance dané služby.</span><span class="sxs-lookup"><span data-stu-id="808a1-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="808a1-117">To umožňuje službě udržovat výsledku spuštěný pro každou relaci v místní členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="808a1-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
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
  
 <span data-ttu-id="808a1-118">Při spuštění ukázky klient provede několik požadavků na serveru a vyžaduje výsledek, který se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="808a1-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="808a1-119">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="808a1-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="808a1-120">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="808a1-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="808a1-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="808a1-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="808a1-122">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="808a1-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="808a1-123">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="808a1-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="808a1-124">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="808a1-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="808a1-125">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="808a1-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="808a1-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="808a1-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="808a1-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="808a1-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="808a1-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="808a1-128">See Also</span></span>
