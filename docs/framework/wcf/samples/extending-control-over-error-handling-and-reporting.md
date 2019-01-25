---
title: Rozšíření kontroly nad zpracováním a vykazováním chyb
ms.date: 03/30/2017
ms.assetid: 45f996a7-fa00-45cb-9d6f-b368f5778aaa
ms.openlocfilehash: 30b36f5373563ec9faba8e655ab1e31d47b23c99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622452"
---
# <a name="extending-control-over-error-handling-and-reporting"></a>Rozšíření kontroly nad zpracováním a vykazováním chyb
Tato ukázka předvádí, jak rozšířit řídit zpracování chyb a zpráv o chybách pomocí služby Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) s další kód přidá ke službě pro zpracování chyb. Vynutí klient několik chybové stavy. Služba zachycuje chyby a zaznamenává je do souboru.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Služby můžete zachytávat chyby, provádět zpracování a mít vliv na způsob hlášení chyb pomocí <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. Rozhraní obsahuje dvě metody, které je možné implementovat: <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> a <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A>. <xref:System.ServiceModel.Dispatcher.IErrorHandler.ProvideFault%28System.Exception%2CSystem.ServiceModel.Channels.MessageVersion%2CSystem.ServiceModel.Channels.Message%40%29> Metody umožňují přidat, upravit nebo potlačit zprávu o chybě, který se vygeneruje v reakci na výjimku. <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda umožňuje zpracování chyb, aby proběhla v případě chybu a ovládací prvky, zda lze spustit další chyba zpracování.  
  
 V této ukázce `CalculatorErrorHandler` typ implementuje <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní. V  
  
 <xref:System.ServiceModel.Dispatcher.IErrorHandler.HandleError%2A> Metoda, `CalculatorErrorHandler` zapisuje do textového souboru Error.txt v c:\logs protokolu chyby. Mějte na paměti, že ukázky protokoluje chyby a nepotlačuje, díky kterému jej předá zpátky do klienta.  
  
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
  
 `ErrorBehaviorAttribute` Existuje jako mechanismus pro obslužnou rutinu chyby zaregistrovat služby. Tento atribut přebírá jediný parametr typu. Typu by měly implementovat <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní a musí mít prázdný veřejný konstruktor. Atribut pak vytvoří instanci tohoto typu obslužné rutiny chyb a nainstaluje ho do služby. Dělá to tak, že implementace <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní a následným použitím <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> metoda doplnit dodatečné instance obslužná rutina chyb do služby.  
  
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
  
 Ukázka implementuje službu kalkulačky. Klient záměrně způsobí, že dvě chyb ve službě poskytnutí neplatné hodnoty parametrů. `CalculatorErrorHandler` Používá <xref:System.ServiceModel.Dispatcher.IErrorHandler> rozhraní k protokolování chyb do místního souboru a pak umožňuje jejich předá zpátky do klienta. Klient vynutí dělení nula a podmínku argumentu out z rozsahu.  
  
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
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Zobrazí dělení nulou a podmínky argumentu out rozsah uváděny jako chyby. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
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
  
 C:\logs\errors.txt soubor obsahuje informace o chybách zaznamenané službou. Všimněte si, že pro službu zápisu do adresáře, že je nutné, pod kterým běží služba, proces (obvykle technologie ASP.NET nebo síťové služby), má oprávnění k zápisu do adresáře.  
  
```  
Fault: Reason = Invalid Argument: The second argument must not be zero.  
Fault: Reason = Invalid Argument: The argument must be greater than zero.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Zkontrolujte, že jste vytvořili v adresáři c:\logs error.txt souboru. Nebo změnit název souboru použitého v `CalculatorErrorHandler.HandleError`.  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\ErrorHandling`  
  
## <a name="see-also"></a>Viz také:
