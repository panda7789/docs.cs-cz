---
title: Relace
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 53500a256e843c33854eb3323d92a29dcb64fa55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503259"
---
# <a name="session"></a><span data-ttu-id="43eec-102">Relace</span><span class="sxs-lookup"><span data-stu-id="43eec-102">Session</span></span>
<span data-ttu-id="43eec-103">Relace příklad znázorňuje způsob implementace kontraktu, která vyžaduje relaci.</span><span class="sxs-lookup"><span data-stu-id="43eec-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="43eec-104">Relaci poskytuje kontext pro provádění více operací.</span><span class="sxs-lookup"><span data-stu-id="43eec-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="43eec-105">To umožňuje službě k přidružení stavu dané relace tak, aby následných operací můžete použít stav předchozí operace.</span><span class="sxs-lookup"><span data-stu-id="43eec-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="43eec-106">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="43eec-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="43eec-107">`ICalculator` Kontrakt změnila umožňující sadu aritmetické operace, které mají být provedeny, a zajistit přitom ochranu výsledku spuštěné.</span><span class="sxs-lookup"><span data-stu-id="43eec-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="43eec-108">Tato funkce je definována `ICalculatorSession` kontrakt.</span><span class="sxs-lookup"><span data-stu-id="43eec-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="43eec-109">Služba udržuje stavu pro klienta jako výpočet se říká víc operací služeb.</span><span class="sxs-lookup"><span data-stu-id="43eec-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="43eec-110">Klient může získat aktuální výsledek pomocí volání `Result()` a zrušte zaškrtnutí výsledek, který má nula voláním `Clear()`.</span><span class="sxs-lookup"><span data-stu-id="43eec-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="43eec-111">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="43eec-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43eec-112">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="43eec-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="43eec-113">Nastavení <xref:System.ServiceModel.SessionMode> smlouvy na `Required` zajišťuje Pokud přes konkrétní vazbu je vystavený kontrakt, vazbu podporuje relací.</span><span class="sxs-lookup"><span data-stu-id="43eec-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="43eec-114">Pokud vazba nepodporuje relace je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="43eec-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="43eec-115">`ICalculatorSession` Rozhraní je definováno tak, že je možné volat jednu nebo více operací, které upraví spuštěné výsledek, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="43eec-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="43eec-116">Používání služby <xref:System.ServiceModel.InstanceContextMode> z <xref:System.ServiceModel.InstanceContextMode.PerSession> vytvořit vazbu instance kontextu uvedená služba každý příchozí relace.</span><span class="sxs-lookup"><span data-stu-id="43eec-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="43eec-117">To umožňuje službě udržovat spuštěné výsledek pro každou relaci v místní členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="43eec-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```  
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
  
 <span data-ttu-id="43eec-118">Když spustíte ukázku, klient provede několik požadavků na server a požadavky výsledek, který potom zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="43eec-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="43eec-119">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="43eec-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43eec-120">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="43eec-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="43eec-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43eec-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="43eec-122">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43eec-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="43eec-123">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43eec-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43eec-124">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="43eec-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43eec-125">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="43eec-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43eec-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="43eec-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43eec-127">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="43eec-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
  
## <a name="see-also"></a><span data-ttu-id="43eec-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="43eec-128">See Also</span></span>
