---
title: Souběžnost
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: eb6140895bb922bd159f1abf536a0d0b12d4f96c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183936"
---
# <a name="concurrency"></a>Souběžnost
Ukázka souběžnosti ukazuje <xref:System.ServiceModel.ServiceBehaviorAttribute> použití <xref:System.ServiceModel.ConcurrencyMode> s výčtu, který řídí, zda instance služby zpracovává zprávy postupně nebo souběžně. Ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), `ICalculator` který implementuje servisní smlouvy. Tato ukázka definuje novou `ICalculatorConcurrency`smlouvu , `ICalculator`která dědí z , poskytuje dvě další operace pro kontrolu stavu souběžnosti služby. Změnou nastavení souběžnosti můžete sledovat změnu v chování spuštěním klienta.  
  
 V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 K dispozici jsou tři režimy souběžnosti:  
  
- `Single`: Každá instance služby zpracovává jednu zprávu najednou. Toto je výchozí režim souběžnosti.  
  
- `Multiple`: Každá instance služby zpracovává více zpráv současně. Implementace služby musí být bezpečné pro přístup z více vláken, aby bylo možné použít tento režim souběžnosti.  
  
- `Reentrant`: Každá instance služby zpracovává jednu zprávu najednou, ale přijímá reentrant volání. Služba přijímá tato volání pouze při volání. Reentrant je prokázáno v [Ukázce ConcurrencyMode.Reentrant.](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md)  
  
 Použití souběžnosti souvisí s instance režimu. V <xref:System.ServiceModel.InstanceContextMode.PerCall> instance souběžnosti není relevantní, protože každá zpráva je zpracována novou instancí služby. V <xref:System.ServiceModel.InstanceContextMode.Single> instance buď <xref:System.ServiceModel.ConcurrencyMode.Single> nebo <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnost je relevantní, v závislosti na tom, zda jedna instance zpracovává zprávy postupně nebo souběžně. V <xref:System.ServiceModel.InstanceContextMode.PerSession> instance může být relevantní kterýkoli z režimů souběžnosti.  
  
 Třída service určuje chování souběžnosti `[ServiceBehavior(ConcurrencyMode=<setting>)]` s atributem, jak je znázorněno v následujícím příkladu kódu. Změnou, které řádky jsou zakomentovány, můžete experimentovat s režimy `Single` a `Multiple` souběžnost. Nezapomeňte znovu sestavit službu po změně režimu souběžnosti.  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 Ukázka <xref:System.ServiceModel.ConcurrencyMode.Multiple> používá souběžnost s <xref:System.ServiceModel.InstanceContextMode.Single> instance ve výchozím nastavení. Kód klienta byl upraven tak, aby používal asynchronní proxy server. To umožňuje klientovi provádět více volání služby bez čekání na odpověď mezi jednotlivými volání. Můžete sledovat rozdíl v chování režimu souběžnosti služby.  
  
 Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Je zobrazen režim souběžnosti, pod kterým je služba spuštěna, každá operace je volána a poté se zobrazí počet operací. Všimněte si, že `Multiple`pokud je režim souběžnosti , výsledky jsou vráceny v jiném pořadí, než jak byly volány, protože služba zpracovává více zpráv současně. Změnou režimu souběžnosti na `Single`, jsou výsledky vráceny v pořadí, v jakém byly volány, protože služba zpracovává každou zprávu postupně. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud používáte Svcutil.exe ke generování proxy klienta, ujistěte se, že zahrnete `/async` možnost.  
  
3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
