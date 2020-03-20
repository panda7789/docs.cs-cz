---
title: Rozšíření kontroly nad zpracováním a vykazováním chyb
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 68f3381e8db9d7c0222720dda335b47e30f57ac7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183672"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozšíření kontroly nad zpracováním a vykazováním chyb
Tato ukázka ukazuje, jak rozšířit kontrolu nad zpracování chyb a zasílání zpráv <xref:System.ServiceModel.Dispatcher.IErrorHandler> o chybách ve službě WCF (Windows Communication Foundation) pomocí rozhraní. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) s některé další kód přidán do služby pro zpracování chyb. Klient vynutí několik chybových stavů. Služba zachytí chyby a zaznamená je do souboru.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Služby mohou zachytit chyby, provádět zpracování a <xref:System.ServiceModel.Dispatcher.IErrorHandler> ovlivnit způsob, jakým jsou chyby hlášeny pomocí rozhraní. Rozhraní má dvě metody, které <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>mohou být implementovány: a . Metoda <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> umožňuje přidat, upravit nebo potlačit zprávu o chybě, která je generována v reakci na výjimku. Metoda <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> umožňuje zpracování chyb probíhá v případě chyby a určuje, zda lze spustit další zpracování chyb.  
  
 V této ukázce `CalculatorErrorHandler` <xref:System.ServiceModel.Dispatcher.IErrorHandler> typ implementuje rozhraní. V  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>`CalculatorErrorHandler` zapíše protokol chyby do textového souboru Error.txt v c:\logs. Všimněte si, že ukázka protokoluje chybu a nepotlačuje ji, což umožňuje, aby byla oznámena zpět klientovi.  
  
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
  
 Existuje `ErrorBehaviorAttribute` jako mechanismus pro registraci obslužné rutiny chyb se službou. Tento atribut přebírá jeden parametr typu. Tento typ by <xref:System.ServiceModel.Dispatcher.IErrorHandler> měl implementovat rozhraní a měl by mít veřejný, prázdný konstruktor. Atribut pak instance tohoto typu obslužné rutiny chyby instanci a nainstaluje do služby. Provede to implementací <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní a <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> potom pomocí metody přidat instance obslužné rutiny chyby do služby.  
  
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
  
 Ukázka implementuje službu kalkulačky. Klient záměrně způsobí dvě chyby dojít ve službě poskytnutím parametry s neplatné hodnoty. Používá `CalculatorErrorHandler` <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní k protokolování chyb do místního souboru a pak umožňuje, aby byly hlášeny zpět klientovi. Klient vynutí dělení nulou a argument-out-of-range podmínku.  
  
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
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Zobrazí dělení nulou a argument mimo rozsah podmínky jsou hlášeny jako chyby. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
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
  
 Soubor c:\logs\errors.txt obsahuje informace zaznamenané o chybách služby. Všimněte si, že pro službu zapisovat do adresáře, musíte se ujistit, že proces, pod kterým je služba spuštěna (obvykle ASP.NET nebo síťová služba) má oprávnění k zápisu do adresáře.  
  
```txt
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Ujistěte se, že jste vytvořili adresář c:\logs pro soubor error.txt. Nebo upravte název `CalculatorErrorHandler.HandleError`souboru použitý v aplikace .  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
