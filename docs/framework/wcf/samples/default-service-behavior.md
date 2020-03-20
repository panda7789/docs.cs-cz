---
title: Výchozí chování služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 798231cbfddf17dd63a61f3e2a07a6490289e56f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183755"
---
# <a name="default-service-behavior"></a><span data-ttu-id="040bb-102">Výchozí chování služby</span><span class="sxs-lookup"><span data-stu-id="040bb-102">Default Service Behavior</span></span>
<span data-ttu-id="040bb-103">Tato ukázka ukazuje, jak lze konfigurovat nastavení chování služby.</span><span class="sxs-lookup"><span data-stu-id="040bb-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="040bb-104">Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` který implementuje servisní smlouvy.</span><span class="sxs-lookup"><span data-stu-id="040bb-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="040bb-105">Tato ukázka explicitně definuje chování služby <xref:System.ServiceModel.ServiceBehaviorAttribute> <xref:System.ServiceModel.OperationBehaviorAttribute> a chování operací pomocí atributů a.</span><span class="sxs-lookup"><span data-stu-id="040bb-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="040bb-106">Můžete nakonfigurovat chování v konfiguračních souborech nebo imperativně v kódu (jak ukazuje tento příklad).</span><span class="sxs-lookup"><span data-stu-id="040bb-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="040bb-107">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="040bb-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="040bb-108">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="040bb-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="040bb-109">Třída service určuje chování s <xref:System.ServiceModel.ServiceBehaviorAttribute> a, <xref:System.ServiceModel.OperationBehaviorAttribute> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="040bb-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="040bb-110">Všechny zadané hodnoty jsou výchozí.</span><span class="sxs-lookup"><span data-stu-id="040bb-110">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="040bb-111">Chování služby jsou <xref:System.ServiceModel.ServiceBehaviorAttribute> určeny s atributem.</span><span class="sxs-lookup"><span data-stu-id="040bb-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="040bb-112">Následující tabulka popisuje některé z těchto chování.</span><span class="sxs-lookup"><span data-stu-id="040bb-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="040bb-113">Chování služby</span><span class="sxs-lookup"><span data-stu-id="040bb-113">Service behavior</span></span>|<span data-ttu-id="040bb-114">Popis</span><span class="sxs-lookup"><span data-stu-id="040bb-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="040bb-115">Automaticky vypne relaci na žádost klienta.</span><span class="sxs-lookup"><span data-stu-id="040bb-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="040bb-116">Určuje režim souběžnosti pro každou instanci služby.</span><span class="sxs-lookup"><span data-stu-id="040bb-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="040bb-117">Určuje kontextový režim instance.</span><span class="sxs-lookup"><span data-stu-id="040bb-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="040bb-118">Určuje, zda se má použít kontext poskytované synchronizace, pokud je nastaven.</span><span class="sxs-lookup"><span data-stu-id="040bb-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="040bb-119">Tuto možnost použijte, pokud chcete `WindowsFormsSynchronizationContext` určit, zda chcete použít a v aplikacích windows forms.</span><span class="sxs-lookup"><span data-stu-id="040bb-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="040bb-120">Určuje, zda obecné výjimky neošetřeného spuštění `Fault<string>` mají být převedeny na a odeslané jako zpráva o chybě.</span><span class="sxs-lookup"><span data-stu-id="040bb-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="040bb-121">Určuje úroveň izolace pro transakce.</span><span class="sxs-lookup"><span data-stu-id="040bb-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="040bb-122">Určuje, zda neočekávaná záhlaví zpráv způsobí chybový stav.</span><span class="sxs-lookup"><span data-stu-id="040bb-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="040bb-123">Chování operace jsou určeny <xref:System.ServiceModel.OperationBehaviorAttribute> pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="040bb-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="040bb-124">Následující tabulka popisuje některé z těchto chování.</span><span class="sxs-lookup"><span data-stu-id="040bb-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="040bb-125">Chování operace</span><span class="sxs-lookup"><span data-stu-id="040bb-125">Operation Behavior</span></span>|<span data-ttu-id="040bb-126">Popis</span><span class="sxs-lookup"><span data-stu-id="040bb-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="040bb-127">Určuje, zda dokončení operace služby potvrdí aktuální transakci.</span><span class="sxs-lookup"><span data-stu-id="040bb-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="040bb-128">Určuje, zda operace služby zařadí do transakce toku klienta.</span><span class="sxs-lookup"><span data-stu-id="040bb-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="040bb-129">Určuje, zda operace služby zosobňuje identitu volajícího.</span><span class="sxs-lookup"><span data-stu-id="040bb-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="040bb-130">Určuje, zda jsou instance služby recyklovány na začátku nebo na konci volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="040bb-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="040bb-131">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="040bb-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="040bb-132">Zpoždění mezi volání je výsledkem volání `System.Threading.Thread.Sleep()` provedené v operacích služby.</span><span class="sxs-lookup"><span data-stu-id="040bb-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="040bb-133">Zbytek ukázky chování vysvětlit toto chování podrobněji.</span><span class="sxs-lookup"><span data-stu-id="040bb-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="040bb-134">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="040bb-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="040bb-135">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="040bb-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="040bb-136">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="040bb-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="040bb-137">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="040bb-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="040bb-138">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="040bb-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="040bb-139">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="040bb-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="040bb-140">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="040bb-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="040bb-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="040bb-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="040bb-142">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="040bb-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
