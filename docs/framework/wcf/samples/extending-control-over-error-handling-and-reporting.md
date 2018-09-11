---
title: Rozšíření kontroly nad zpracováním a vykazováním chyb
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 6492807b55b50662790cf25807a35ddd65fbe01d
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264239"
---
# <a name="extending-control-over-error-handling-and-reporting"></a><span data-ttu-id="71d3a-102">Rozšíření kontroly nad zpracováním a vykazováním chyb</span><span class="sxs-lookup"><span data-stu-id="71d3a-102">Extending Control Over Error Handling and Reporting</span></span>
<span data-ttu-id="71d3a-103">Tato ukázka předvádí, jak rozšířit řídit zpracování chyb a zpráv o chybách pomocí služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71d3a-103">This sample demonstrates how to extend control over error handling and error reporting in a Windows Communication Foundation (WCF) service using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="71d3a-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) s další kód přidá ke službě pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="71d3a-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) with some additional code added to the service to handle errors.</span></span> <span data-ttu-id="71d3a-105">Vynutí klient několik chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="71d3a-105">The client forces several error conditions.</span></span> <span data-ttu-id="71d3a-106">Služba zachycuje chyby a zaznamenává je do souboru.</span><span class="sxs-lookup"><span data-stu-id="71d3a-106">The service intercepts the errors and logs them in a file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71d3a-107">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="71d3a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="71d3a-108">Služby můžete zachytávat chyby, provádět zpracování a mít vliv na způsob hlášení chyb pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71d3a-108">Services can intercept errors, perform processing, and affect how errors are reported using the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="71d3a-109">Rozhraní obsahuje dvě metody, které je možné implementovat: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> a <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span><span class="sxs-lookup"><span data-stu-id="71d3a-109">The interface has two methods that can be implemented: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> and <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>.</span></span> <span data-ttu-id="71d3a-110"><xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metody umožňují přidat, upravit nebo potlačit zprávu o chybě, který se vygeneruje v reakci na výjimku.</span><span class="sxs-lookup"><span data-stu-id="71d3a-110">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> method allows you to add, modify, or suppress a fault message that is generated in response to an exception.</span></span> <span data-ttu-id="71d3a-111"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda umožňuje zpracování chyb, aby proběhla v případě chybu a ovládací prvky, zda lze spustit další chyba zpracování.</span><span class="sxs-lookup"><span data-stu-id="71d3a-111">The <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method allows error processing to take place in the event of an error and controls whether additional error handling can run.</span></span>  
  
 <span data-ttu-id="71d3a-112">V této ukázce `CalculatorErrorHandler` typ implementuje <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="71d3a-112">In this sample, the `CalculatorErrorHandler` type implements the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface.</span></span> <span data-ttu-id="71d3a-113">V</span><span class="sxs-lookup"><span data-stu-id="71d3a-113">In the</span></span>  
  
 <span data-ttu-id="71d3a-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda, `CalculatorErrorHandler` zapisuje do textového souboru Error.txt v c:\logs protokolu chyby.</span><span class="sxs-lookup"><span data-stu-id="71d3a-114"><xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> method, the `CalculatorErrorHandler` writes a log of the error to an Error.txt text file in c:\logs.</span></span> <span data-ttu-id="71d3a-115">Mějte na paměti, že ukázky protokoluje chyby a nepotlačuje, díky kterému jej předá zpátky do klienta.</span><span class="sxs-lookup"><span data-stu-id="71d3a-115">Note that the sample logs the fault and does not suppress it, allowing it to be reported back to the client.</span></span>  
  
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
  
 <span data-ttu-id="71d3a-116">`ErrorBehaviorAttribute` Existuje jako mechanismus pro obslužnou rutinu chyby zaregistrovat služby.</span><span class="sxs-lookup"><span data-stu-id="71d3a-116">The `ErrorBehaviorAttribute` exists as a mechanism to register an error handler with a service.</span></span> <span data-ttu-id="71d3a-117">Tento atribut přebírá jediný parametr typu.</span><span class="sxs-lookup"><span data-stu-id="71d3a-117">This attribute takes a single type parameter.</span></span> <span data-ttu-id="71d3a-118">Typu by měly implementovat <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní a musí mít prázdný veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="71d3a-118">That type should implement the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface and should have a public, empty constructor.</span></span> <span data-ttu-id="71d3a-119">Atribut pak vytvoří instanci tohoto typu obslužné rutiny chyb a nainstaluje ho do služby.</span><span class="sxs-lookup"><span data-stu-id="71d3a-119">The attribute then instantiates an instance of that error handler type and installs it into the service.</span></span> <span data-ttu-id="71d3a-120">Dělá to tak, že implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní a následným použitím <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> metoda doplnit dodatečné instance obslužná rutina chyb do služby.</span><span class="sxs-lookup"><span data-stu-id="71d3a-120">It does this by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface and then using the <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> method to add instances of the error handler to the service.</span></span>  
  
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
  
 <span data-ttu-id="71d3a-121">Ukázka implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="71d3a-121">The sample implements a calculator service.</span></span> <span data-ttu-id="71d3a-122">Klient záměrně způsobí, že dvě chyb ve službě poskytnutí neplatné hodnoty parametrů.</span><span class="sxs-lookup"><span data-stu-id="71d3a-122">The client deliberately causes two errors to occur on the service by providing parameters with illegal values.</span></span> <span data-ttu-id="71d3a-123">`CalculatorErrorHandler` Používá <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní k protokolování chyb do místního souboru a pak umožňuje jejich předá zpátky do klienta.</span><span class="sxs-lookup"><span data-stu-id="71d3a-123">The `CalculatorErrorHandler` uses the <xref:System.ServiceModel.Dispatcher.IErrorHandler> interface to log the errors to a local file and then allows them to be reported back to the client.</span></span> <span data-ttu-id="71d3a-124">Klient vynutí dělení nula a podmínku argumentu out z rozsahu.</span><span class="sxs-lookup"><span data-stu-id="71d3a-124">The client forces a divide by zero and an argument-out-of-range condition.</span></span>  
  
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
  
 <span data-ttu-id="71d3a-125">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="71d3a-125">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="71d3a-126">Zobrazí dělení nulou a podmínky argumentu out rozsah uváděny jako chyby.</span><span class="sxs-lookup"><span data-stu-id="71d3a-126">You see the division by zero and the argument-out-of-range conditions being reported as faults.</span></span> <span data-ttu-id="71d3a-127">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="71d3a-127">Press ENTER in the client window to shut down the client.</span></span>  
  
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
  
 <span data-ttu-id="71d3a-128">C:\logs\errors.txt soubor obsahuje informace o chybách zaznamenané službou.</span><span class="sxs-lookup"><span data-stu-id="71d3a-128">The file c:\logs\errors.txt contains the information logged about the errors by the service.</span></span> <span data-ttu-id="71d3a-129">Všimněte si, že pro službu zápisu do adresáře, že je nutné, pod kterým běží služba, proces (obvykle technologie ASP.NET nebo síťové služby), má oprávnění k zápisu do adresáře.</span><span class="sxs-lookup"><span data-stu-id="71d3a-129">Note that for the service to write to the directory you must make sure that the process under which the service is running, (typically ASP.NET or Network Service), has the permission to write to the directory.</span></span>  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="71d3a-130">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="71d3a-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="71d3a-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71d3a-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="71d3a-132">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71d3a-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="71d3a-133">Zkontrolujte, že jste vytvořili v adresáři c:\logs error.txt souboru.</span><span class="sxs-lookup"><span data-stu-id="71d3a-133">Ensure you have created the c:\logs directory for the error.txt file.</span></span> <span data-ttu-id="71d3a-134">Nebo změnit název souboru použitého v `CalculatorErrorHandler.HandleError`.</span><span class="sxs-lookup"><span data-stu-id="71d3a-134">Or modify the file name used in `CalculatorErrorHandler.HandleError`.</span></span>  
  
4.  <span data-ttu-id="71d3a-135">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="71d3a-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="71d3a-136">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="71d3a-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="71d3a-137">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="71d3a-137">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="71d3a-138">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="71d3a-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="71d3a-139">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="71d3a-139">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a><span data-ttu-id="71d3a-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="71d3a-140">See Also</span></span>
