---
title: Rozšíření kontroly nad zpracováním a vykazováním chyb
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: c7ca8d85220d65905bc4d9d220de366c331504a4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600539"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozšíření kontroly nad zpracováním a vykazováním chyb
Tato ukázka demonstruje, jak lze v rámci služby Windows Communication Foundation (WCF) pomocí rozhraní nastavovat kontrolu nad zpracováním chyb a zasílání zpráv o chybách <xref:System.ServiceModel.Dispatcher.IErrorHandler> . Ukázka je založena na [Začínáme](getting-started-sample.md) s nějakým dalším kódem přidaným do služby za účelem zpracování chyb. Klient vynutí několik chybových podmínek. Služba zachycuje chyby a zapisuje je do souboru.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Služby mohou zachytit chyby, provádět zpracování a ovlivnit způsob hlášení chyb pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. Rozhraní má dvě metody, které lze implementovat: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> a <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> . <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29>Metoda umožňuje přidat, upravit nebo potlačit chybovou zprávu, která je generována v reakci na výjimku. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>Metoda umožňuje zpracování chyb v případě chyby a určuje, zda lze spustit další zpracování chyb.  
  
 V této ukázce `CalculatorErrorHandler` typ implementuje <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. V  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>Metoda `CalculatorErrorHandler` zapisuje protokol chyby do textového souboru Error. txt v c:\Logs. Všimněte si, že ukázka zaznamená chybu a potlačí ji, což umožňuje, aby se vrátila klientovi.  
  
```csharp
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
  
 `ErrorBehaviorAttribute`Existuje jako mechanismus pro registraci obslužné rutiny chyb u služby. Tento atribut přijímá jeden parametr typu. Tento typ by měl implementovat <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní a měl by mít veřejný prázdný konstruktor. Atribut poté vytvoří instanci instance této obslužné rutiny chyb a nainstaluje ji do služby. Provede to implementací <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní a následným použitím <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> metody pro přidání instancí obslužné rutiny chyby do služby.  
  
```csharp
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
  
 Ukázka implementuje službu kalkulačky. V důsledku toho může klient v rámci služby provést dvě chyby zadáním parametrů s neplatnými hodnotami. `CalculatorErrorHandler` <xref:System.ServiceModel.Dispatcher.IErrorHandler> Rozhraní používá rozhraní k zaprotokolování chyb do místního souboru a pak jim umožní, aby je vrátili zpět klientovi. Klient vynutí dělení nulou a argument-mimo rozsah.  
  
```csharp
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
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Zobrazí se dělení nulou a podmínky argumentu mimo rozsah hlášené jako chyby. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Forcing an error in Divide  
FaultException: FaultException - Invalid Argument: The second argument must not be zero.  
Forcing an error in Factorial  
FaultException: FaultException - Invalid Argument: The argument must be greater than zero.  
  
Press <ENTER> to terminate client.  
```  
  
 Soubor c:\logs\errors.txt obsahuje informace zaznamenané o chybách služby. Upozorňujeme, že aby služba mohla zapisovat do adresáře, musíte se ujistit, že proces, pod kterým je služba spuštěná (obvykle ASP.NET nebo Network Service), má oprávnění k zápisu do adresáře.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Ujistěte se, že jste vytvořili adresář c:\Logs. pro soubor Error. txt. Nebo upravte název souboru, který se používá v nástroji `CalculatorErrorHandler.HandleError` .  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
