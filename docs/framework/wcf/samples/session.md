---
title: Relace
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: 85f1034999fc4cd36075c49bd8f4631bbd283679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183367"
---
# <a name="session"></a><span data-ttu-id="4e502-102">Relace</span><span class="sxs-lookup"><span data-stu-id="4e502-102">Session</span></span>
<span data-ttu-id="4e502-103">Ukázka relace ukazuje, jak implementovat smlouvu, která vyžaduje relaci.</span><span class="sxs-lookup"><span data-stu-id="4e502-103">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="4e502-104">Relace poskytuje kontext pro provádění více operací.</span><span class="sxs-lookup"><span data-stu-id="4e502-104">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="4e502-105">To umožňuje službě přidružit stav k dané relaci, takže následné operace mohou použít stav předchozí operace.</span><span class="sxs-lookup"><span data-stu-id="4e502-105">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="4e502-106">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje kalkulačku služby.</span><span class="sxs-lookup"><span data-stu-id="4e502-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="4e502-107">Smlouva `ICalculator` byla upravena tak, aby umožňovala provádění sady aritmetických operací při zachování průběžného výsledku.</span><span class="sxs-lookup"><span data-stu-id="4e502-107">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="4e502-108">Tato funkce je definována smlouvou. `ICalculatorSession`</span><span class="sxs-lookup"><span data-stu-id="4e502-108">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="4e502-109">Služba udržuje stav pro klienta jako více operací služby jsou volány k provedení výpočtu.</span><span class="sxs-lookup"><span data-stu-id="4e502-109">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="4e502-110">Klient může načíst aktuální `Result()` výsledek voláním a vymazat `Clear()`výsledek na nulu voláním .</span><span class="sxs-lookup"><span data-stu-id="4e502-110">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="4e502-111">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="4e502-111">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4e502-112">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4e502-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4e502-113"><xref:System.ServiceModel.SessionMode> Nastavení smlouvy zajistit, `Required` že při smlouvy je vystavena přes konkrétní vazbu, vazba podporuje relace.</span><span class="sxs-lookup"><span data-stu-id="4e502-113">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="4e502-114">Pokud vazba nepodporuje relace je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="4e502-114">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="4e502-115">Rozhraní `ICalculatorSession` je definováno tak, že lze volat jednu nebo více operací, které mění průběžný výsledek, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="4e502-115">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="4e502-116">Služba používá <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> svázat kontext dané instance služby na každou příchozí relaci.</span><span class="sxs-lookup"><span data-stu-id="4e502-116">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="4e502-117">To umožňuje službě udržovat spuštěný výsledek pro každou relaci v místní členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="4e502-117">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
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
  
 <span data-ttu-id="4e502-118">Při spuštění ukázky klient provede několik požadavků na server a požaduje výsledek, který se pak zobrazí v okně klientské konzole.</span><span class="sxs-lookup"><span data-stu-id="4e502-118">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="4e502-119">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="4e502-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4e502-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="4e502-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4e502-121">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e502-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4e502-122">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e502-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4e502-123">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4e502-123">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4e502-124">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="4e502-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4e502-125">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="4e502-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4e502-126">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4e502-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4e502-127">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4e502-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
