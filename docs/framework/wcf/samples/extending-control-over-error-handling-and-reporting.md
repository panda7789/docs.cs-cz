---
title: Rozšíření kontroly nad zpracováním a vykazováním chyb
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 09216d8b0ff58ac90a0fd6183f43fd2ccf82ad52
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039683"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="38d3d-102">Rozšíření kontroly nad zpracováním a vykazováním chyb</span><span class="sxs-lookup"><span data-stu-id="38d3d-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="38d3d-103">Tato ukázka demonstruje, jak lze v rámci služby Windows Communication Foundation (WCF) pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní nastavovat kontrolu nad zpracováním chyb a zasílání zpráv o chybách.</span><span class="sxs-lookup"><span data-stu-id="38d3d-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="38d3d-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) s nějakým dalším kódem přidaným do služby za účelem zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="38d3d-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="38d3d-105">Klient vynutí několik chybových podmínek.</span><span class="sxs-lookup"><span data-stu-id="38d3d-105">The client forces several error conditions.</span></span> <span data-ttu-id="38d3d-106">Služba zachycuje chyby a zapisuje je do souboru.</span><span class="sxs-lookup"><span data-stu-id="38d3d-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38d3d-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="38d3d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="38d3d-108">Služby mohou zachytit chyby, provádět zpracování a ovlivnit způsob hlášení chyb pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38d3d-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="38d3d-109">Rozhraní má dvě metody, které lze implementovat: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> a. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A></span><span class="sxs-lookup"><span data-stu-id="38d3d-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="38d3d-110"><xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metoda umožňuje přidat, upravit nebo potlačit chybovou zprávu, která je generována v reakci na výjimku.</span><span class="sxs-lookup"><span data-stu-id="38d3d-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="38d3d-111"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda umožňuje zpracování chyb v případě chyby a určuje, zda lze spustit další zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="38d3d-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="38d3d-112">V této ukázce `CalculatorErrorHandler` typ <xref:System.ServiceModel.Dispatcher.IErrorHandler> implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="38d3d-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="38d3d-113">V části</span><span class="sxs-lookup"><span data-stu-id="38d3d-113">In the</span></span>  
  
 <span data-ttu-id="38d3d-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>`CalculatorErrorHandler` Metoda zapisuje protokol chyby do textového souboru Error. txt v c:\Logs.</span><span class="sxs-lookup"><span data-stu-id="38d3d-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="38d3d-115">Všimněte si, že ukázka zaznamená chybu a potlačí ji, což umožňuje, aby se vrátila klientovi.</span><span class="sxs-lookup"><span data-stu-id="38d3d-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
```  
public class CalculatorErrorHandler : IErrorHandler  
{  
        // Provide a fault. The Message fault parameter can be replaced, or set to  
        // null to suppress reporting a fault.  
  
        public void ProvideFault(Exception error, MessageVersion version, ref Message fault)  
        {  
        }  
  
        // HandleError. Log an error, then allow the error to be handled as usual.  
        // Return true if the error is considered as already handled  
  
        public bool HandleError(Exception error)  
        {  
            using (TextWriter tw = File.AppendText(@"c:\logs\error.txt"))  
            {  
                if (error != null)  
                {  
                    tw.WriteLine("Exception: " + error.GetType().Name + " - " + error.Message);  
                }  
                tw.Close();  
            }  
            return true;  
        }  
    }  
```  
  
 <span data-ttu-id="38d3d-116">`ErrorBehaviorAttribute` Existuje jako mechanismus pro registraci obslužné rutiny chyb u služby.</span><span class="sxs-lookup"><span data-stu-id="38d3d-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="38d3d-117">Tento atribut přijímá jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="38d3d-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="38d3d-118">Tento typ by měl implementovat <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní a měl by mít veřejný prázdný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="38d3d-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="38d3d-119">Atribut poté vytvoří instanci instance této obslužné rutiny chyb a nainstaluje ji do služby.</span><span class="sxs-lookup"><span data-stu-id="38d3d-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="38d3d-120">Provede to implementací <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní a následným <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> použitím metody pro přidání instancí obslužné rutiny chyby do služby.</span><span class="sxs-lookup"><span data-stu-id="38d3d-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
```  
// This attribute can be used to install a custom error handler for a service.  
public class ErrorBehaviorAttribute : Attribute, IServiceBehavior  
{  
    Type errorHandlerType;  
  
    public ErrorBehaviorAttribute(Type errorHandlerType)  
    {  
        this.errorHandlerType = errorHandlerType;  
    }  
  
    void IServiceBehavior.Validate(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
    }  
  
    void IServiceBehavior.AddBindingParameters(ServiceDescription description, ServiceHostBase serviceHostBase, System.Collections.ObjectModel.Collection<ServiceEndpoint> endpoints, BindingParameterCollection parameters)  
    {  
    }  
  
    void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
    {  
        IErrorHandler errorHandler;  
  
        try  
        {  
            errorHandler = (IErrorHandler)Activator.CreateInstance(errorHandlerType);  
        }  
        catch (MissingMethodException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must have a public empty constructor.", e);  
        }  
        catch (InvalidCastException e)  
        {  
            throw new ArgumentException("The errorHandlerType specified in the ErrorBehaviorAttribute constructor must implement System.ServiceModel.Dispatcher.IErrorHandler.", e);  
        }  
  
        foreach (ChannelDispatcherBase channelDispatcherBase in serviceHostBase.ChannelDispatchers)  
        {  
            ChannelDispatcher channelDispatcher = channelDispatcherBase as ChannelDispatcher;  
            channelDispatcher.ErrorHandlers.Add(errorHandler);  
        }                                                  
    }  
}  
```  
  
 <span data-ttu-id="38d3d-121">Ukázka implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="38d3d-121">The sample implements a calculator service.</span></span> <span data-ttu-id="38d3d-122">V důsledku toho může klient v rámci služby provést dvě chyby zadáním parametrů s neplatnými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="38d3d-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="38d3d-123">Rozhraní<xref:System.ServiceModel.Dispatcher.IErrorHandler>používározhraní k zaprotokolování chyb do místního souboru a pak jim umožní, aby je vrátili zpět klientovi. `CalculatorErrorHandler`</span><span class="sxs-lookup"><span data-stu-id="38d3d-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="38d3d-124">Klient vynutí dělení nulou a argument-mimo rozsah.</span><span class="sxs-lookup"><span data-stu-id="38d3d-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
```  
try  
{  
    Console.WriteLine("Forcing an error in Divide");  
    // Call the Divide service operation - trigger a divide by 0 error.  
    value1 = 22;  
    value2 = 0;  
    result = proxy.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
}  
catch (FaultException e)  
{  
    Console.WriteLine("FaultException: " + e.GetType().Name + " - " + e.Message);  
}  
catch (Exception e)  
{  
    Console.WriteLine("Exception: " + e.GetType().Name + " - " + e.Message);  
}  
```  
  
 <span data-ttu-id="38d3d-125">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="38d3d-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="38d3d-126">Zobrazí se dělení nulou a podmínky argumentu mimo rozsah hlášené jako chyby.</span><span class="sxs-lookup"><span data-stu-id="38d3d-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="38d3d-127">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="38d3d-127">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="38d3d-128">Soubor c:\logs\errors.txt obsahuje informace zaznamenané o chybách služby.</span><span class="sxs-lookup"><span data-stu-id="38d3d-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="38d3d-129">Všimněte si, že aby služba mohla zapisovat do adresáře, musíte se ujistit, že proces, pod kterým je služba spuštěná (obvykle ASP.NET nebo Network Service), má oprávnění k zápisu do adresáře.</span><span class="sxs-lookup"><span data-stu-id="38d3d-129">Note that for the service to write to the directory you must make sure that the process under which the service is running, (typically ASP.NET or Network Service), has the permission to write to the directory.</span></span>  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="38d3d-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="38d3d-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="38d3d-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38d3d-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="38d3d-132">Při sestavování řešení postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38d3d-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="38d3d-133">Ujistěte se, že jste vytvořili adresář c:\Logs. pro soubor Error. txt.</span><span class="sxs-lookup"><span data-stu-id="38d3d-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="38d3d-134">Nebo upravte název souboru, který se `CalculatorErrorHandler.HandleError`používá v nástroji.</span><span class="sxs-lookup"><span data-stu-id="38d3d-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4. <span data-ttu-id="38d3d-135">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="38d3d-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="38d3d-136">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="38d3d-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="38d3d-137">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="38d3d-137">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="38d3d-138">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="38d3d-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="38d3d-139">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="38d3d-139">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
