---
title: "Rozšíření kontroly nad zpracováním a vykazováním chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4284f07a21a9bb176a78a8a2abefe7c7c7c6b66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozšíření kontroly nad zpracováním a vykazováním chyb
Tento příklad ukazuje, jak rozšířit řídit zpracování chyb a zpráv o chybách v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) s další kód přidat ke službě se budou zpracovávat chyby. Klient vynutí několik chybové stavy. Služba zachytí chyby a zaznamenává je do souboru.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Služby mohou zachytávat chyby, proveďte zpracování a mít vliv na způsob hlášení chyb pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. Rozhraní se dvě metody, které se dají implementovat: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> a <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metoda umožňuje přidávat, upravovat nebo potlačit zprávu o chybě, generovaný v reakci na výjimku. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda umožňuje chyba zpracování proběhla v případě chybu a ovládací prvky, zda můžete spustit zpracování dalších chyb.  
  
 V této ukázce `CalculatorErrorHandler` zadejte implementuje <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. V  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>Metoda, `CalculatorErrorHandler` zapisuje do textového souboru Error.txt v c:\logs protokolu chyba. Upozorňujeme, že ukázku zaznamená chybu a nepotlačuje, díky kterému jej hlášené zpět klientovi.  
  
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
  
 `ErrorBehaviorAttribute` Existuje jako mechanismus pro registraci obslužná rutina se službou. Tento atribut přebírá jediný parametr typu. Aby typ měli implementovat <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní a musí mít konstruktor veřejné, prázdný. Atribut pak vytvoří instanci daného typu Chyba obslužné rutiny a nainstaluje do služby. Dělá to pomocí implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní a pak pomocí <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> metoda přidání instancí obslužná rutina chyb do služby.  
  
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
  
 Ukázka implementuje službu kalkulačky. Klient úmyslně způsobí, že dochází k výskytu na službu a poskytovat parametry neplatné hodnoty dvou chyb. `CalculatorErrorHandler` Používá <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní k protokolování chyb do místního souboru a pak je třeba ohlásit zpět klientovi umožňuje. Klient vynutí Rozděl nula a podmínku argument-out-of-range.  
  
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
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Zobrazí dělení nula a podmínky argument-out-of-range nehlásí jako chyby. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
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
  
 C:\logs\errors.txt soubor obsahuje informace o chybách, přihlášení pomocí služby. Všimněte si, že pro službu, kterou chcete zapisovat do adresáře, ujistěte se, pod kterým běží služba, proces (obvykle ASP.NET nebo síťová služba), má oprávnění k zápisu do adresáře.  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Zkontrolujte, zda že jste vytvořili c:\logs adresář pro soubor error.txt. Nebo změňte název souboru použitý v `CalculatorErrorHandler.HandleError`.  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a>Viz také
