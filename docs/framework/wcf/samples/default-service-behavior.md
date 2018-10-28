---
title: Výchozí chování služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: 2c49c28d99bb3d300fd4589a088b2f086bdfd45d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184475"
---
# <a name="default-service-behavior"></a><span data-ttu-id="bad4c-102">Výchozí chování služby</span><span class="sxs-lookup"><span data-stu-id="bad4c-102">Default Service Behavior</span></span>
<span data-ttu-id="bad4c-103">Tato ukázka předvádí, jak lze konfigurovat nastavení chování služby.</span><span class="sxs-lookup"><span data-stu-id="bad4c-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="bad4c-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="bad4c-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="bad4c-105">Tato ukázka explicitně definuje chování služby a operace chování pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="bad4c-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="bad4c-106">Chování můžete nakonfigurovat v konfiguračních souborech nebo imperativně v kódu (jako v této ukázce).</span><span class="sxs-lookup"><span data-stu-id="bad4c-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="bad4c-107">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="bad4c-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bad4c-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="bad4c-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="bad4c-109">Určuje chování s třídu služby <xref:System.ServiceModel.ServiceBehaviorAttribute> a <xref:System.ServiceModel.OperationBehaviorAttribute> jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="bad4c-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="bad4c-110">Všechny zadané hodnoty jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bad4c-110">All values specified are the defaults.</span></span>  
  
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
  
 <span data-ttu-id="bad4c-111">Chování služby se zadaným <xref:System.ServiceModel.ServiceBehaviorAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="bad4c-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="bad4c-112">Následující tabulka popisuje některé z těchto projevů.</span><span class="sxs-lookup"><span data-stu-id="bad4c-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="bad4c-113">Chování služby</span><span class="sxs-lookup"><span data-stu-id="bad4c-113">Service behavior</span></span>|<span data-ttu-id="bad4c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bad4c-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="bad4c-115">Automaticky ukončí relaci v požadavku klienta.</span><span class="sxs-lookup"><span data-stu-id="bad4c-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="bad4c-116">Určuje režim pro každou repliku služby.</span><span class="sxs-lookup"><span data-stu-id="bad4c-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="bad4c-117">Určuje režim kontextu instance.</span><span class="sxs-lookup"><span data-stu-id="bad4c-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="bad4c-118">Určuje, zda použít kontext synchronizace zadaná, je-li nastavena.</span><span class="sxs-lookup"><span data-stu-id="bad4c-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="bad4c-119">Použijte ho, když chcete řídit, jestli se má použít `WindowsFormsSynchronizationContext` v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bad4c-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="bad4c-120">Určuje, zda mají být převedeny do jsou obecné zpracování neošetřené výjimky `Fault<string>` a odeslána jako zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="bad4c-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="bad4c-121">Určuje úroveň izolace transakce.</span><span class="sxs-lookup"><span data-stu-id="bad4c-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="bad4c-122">Určuje, zda záhlaví neočekávaná zpráva způsobí chybovou podmínku.</span><span class="sxs-lookup"><span data-stu-id="bad4c-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="bad4c-123">Operace chování je určené vlastností <xref:System.ServiceModel.OperationBehaviorAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="bad4c-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="bad4c-124">Následující tabulka popisuje některé z těchto projevů.</span><span class="sxs-lookup"><span data-stu-id="bad4c-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="bad4c-125">Chování operace</span><span class="sxs-lookup"><span data-stu-id="bad4c-125">Operation Behavior</span></span>|<span data-ttu-id="bad4c-126">Popis</span><span class="sxs-lookup"><span data-stu-id="bad4c-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="bad4c-127">Určuje, zda služba dokončení operace potvrzení aktuální transakce.</span><span class="sxs-lookup"><span data-stu-id="bad4c-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="bad4c-128">Určuje, zda operace služby využívá v rámci klienta plynoucí transakce.</span><span class="sxs-lookup"><span data-stu-id="bad4c-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="bad4c-129">Určuje, zda operace služby zosobňuje identitu volajícího.</span><span class="sxs-lookup"><span data-stu-id="bad4c-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="bad4c-130">Určuje, zda instance služby recyklován na začátku nebo konci volání operace služby.</span><span class="sxs-lookup"><span data-stu-id="bad4c-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="bad4c-131">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="bad4c-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="bad4c-132">Zpoždění mezi volání je výsledkem volání `System.Threading.Thread.Sleep()` provedených operací služby.</span><span class="sxs-lookup"><span data-stu-id="bad4c-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="bad4c-133">Zbývající část ukázky chování vysvětlit těchto projevů podrobněji.</span><span class="sxs-lookup"><span data-stu-id="bad4c-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="bad4c-134">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="bad4c-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bad4c-135">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="bad4c-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bad4c-136">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bad4c-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="bad4c-137">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bad4c-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="bad4c-138">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bad4c-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bad4c-139">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="bad4c-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bad4c-140">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bad4c-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bad4c-141">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bad4c-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bad4c-142">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bad4c-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
  
## <a name="see-also"></a><span data-ttu-id="bad4c-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="bad4c-143">See Also</span></span>
