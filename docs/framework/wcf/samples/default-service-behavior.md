---
title: Výchozí chování služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 4da3deff69930dba7249e0651f820b448b837862
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84592447"
---
# <a name="default-service-behavior"></a><span data-ttu-id="9ae21-102">Výchozí chování služby</span><span class="sxs-lookup"><span data-stu-id="9ae21-102">Default Service Behavior</span></span>
<span data-ttu-id="9ae21-103">Tato ukázka předvádí, jak lze nakonfigurovat nastavení chování služby.</span><span class="sxs-lookup"><span data-stu-id="9ae21-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="9ae21-104">Ukázka je založena na [Začínáme](getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="9ae21-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="9ae21-105">Tato ukázka explicitně definuje chování služby a chování operace pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> atributů a <xref:System.ServiceModel.OperationBehaviorAttribute> .</span><span class="sxs-lookup"><span data-stu-id="9ae21-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="9ae21-106">Chování můžete nakonfigurovat v konfiguračních souborech nebo imperativně v kódu (jak ukazuje tento příklad).</span><span class="sxs-lookup"><span data-stu-id="9ae21-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="9ae21-107">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="9ae21-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ae21-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9ae21-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9ae21-109">Třída služby určuje chování pomocí a, <xref:System.ServiceModel.ServiceBehaviorAttribute> jak je <xref:System.ServiceModel.OperationBehaviorAttribute> znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="9ae21-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="9ae21-110">Všechny zadané hodnoty jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9ae21-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="9ae21-111">Chování služby je určeno <xref:System.ServiceModel.ServiceBehaviorAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="9ae21-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="9ae21-112">Některé z těchto chování jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9ae21-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="9ae21-113">Chování služby</span><span class="sxs-lookup"><span data-stu-id="9ae21-113">Service behavior</span></span>|<span data-ttu-id="9ae21-114">Popis</span><span class="sxs-lookup"><span data-stu-id="9ae21-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="9ae21-115">Automaticky vypne relaci v žádosti klienta.</span><span class="sxs-lookup"><span data-stu-id="9ae21-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="9ae21-116">Určuje režim souběžnosti pro každou instanci služby.</span><span class="sxs-lookup"><span data-stu-id="9ae21-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="9ae21-117">Určuje kontextový režim instance.</span><span class="sxs-lookup"><span data-stu-id="9ae21-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="9ae21-118">Určuje, zda se má použít poskytnutý kontext synchronizace, pokud je nastaven.</span><span class="sxs-lookup"><span data-stu-id="9ae21-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="9ae21-119">Tuto možnost použijte, pokud chcete určit, jestli se má používat `WindowsFormsSynchronizationContext` v model Windows Formsch aplikacích.</span><span class="sxs-lookup"><span data-stu-id="9ae21-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="9ae21-120">Určuje, zda mají být obecné neošetřené výjimky provádění převedeny do `Fault<string>` a odeslány jako chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="9ae21-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="9ae21-121">Určuje úroveň izolace pro transakce.</span><span class="sxs-lookup"><span data-stu-id="9ae21-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="9ae21-122">Určuje, zda neočekávaná záhlaví zprávy způsobují chybový stav.</span><span class="sxs-lookup"><span data-stu-id="9ae21-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="9ae21-123">Chování operace jsou určena pomocí <xref:System.ServiceModel.OperationBehaviorAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="9ae21-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="9ae21-124">Některé z těchto chování jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9ae21-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="9ae21-125">Chování operace</span><span class="sxs-lookup"><span data-stu-id="9ae21-125">Operation Behavior</span></span>|<span data-ttu-id="9ae21-126">Popis</span><span class="sxs-lookup"><span data-stu-id="9ae21-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="9ae21-127">Určuje, zda dokončení operace služby potvrdí aktuální transakci.</span><span class="sxs-lookup"><span data-stu-id="9ae21-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="9ae21-128">Určuje, zda operace služby zařadí transakce v transakci toku klienta.</span><span class="sxs-lookup"><span data-stu-id="9ae21-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="9ae21-129">Určuje, zda operace služby zosobňuje identitu volajícího.</span><span class="sxs-lookup"><span data-stu-id="9ae21-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="9ae21-130">Určuje, zda se instance služby recyklují na začátku nebo konci volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="9ae21-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="9ae21-131">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9ae21-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9ae21-132">Zpoždění mezi voláními je výsledkem volání, která se mají `System.Threading.Thread.Sleep()` provést v operacích služby.</span><span class="sxs-lookup"><span data-stu-id="9ae21-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="9ae21-133">Zbytek ukázek chování Vysvětlete toto chování podrobněji.</span><span class="sxs-lookup"><span data-stu-id="9ae21-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="9ae21-134">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="9ae21-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9ae21-135">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="9ae21-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9ae21-136">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ae21-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9ae21-137">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ae21-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9ae21-138">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9ae21-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9ae21-139">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="9ae21-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ae21-140">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="9ae21-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9ae21-141">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="9ae21-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ae21-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9ae21-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
