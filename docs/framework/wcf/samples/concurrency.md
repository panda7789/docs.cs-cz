---
title: Souběžnost
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 1342e50a5dca56260f832f5e0d684f4f79d355e2
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715991"
---
# <a name="concurrency"></a>Souběžnost
Ukázka souběžnosti ukazuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> s výčtem <xref:System.ServiceModel.ConcurrencyMode>, která určuje, zda instance služby zpracovává zprávy sekvenčně nebo souběžně. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje kontrakt služby `ICalculator`. Tato ukázka definuje nový kontrakt, `ICalculatorConcurrency`, který dědí z `ICalculator`a poskytuje dvě další operace pro kontrolu stavu souběžnosti služby. Změnou nastavení souběžnosti můžete sledovat změnu v chování spuštěním klienta.  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 K dispozici jsou tři režimy souběžnosti:  
  
- `Single`: každá instance služby zpracovává vždy jednu zprávu. Toto je výchozí režim souběžnosti.  
  
- `Multiple`: každá instance služby zpracovává více zpráv souběžně. Aby bylo možné používat tento režim souběžnosti, musí být implementace služby bezpečná pro přístup z více vláken.  
  
- `Reentrant`: každá instance služby zpracovává jednu zprávu po druhém, ale přijímá znovu zadaná volání. Služba akceptuje tato volání pouze při vyvolání. Znovu se zavedlo na výběr v ukázce režimu [ConcurrencyMode. revstupujícího](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) .  
  
 Použití souběžnosti souvisí s režimem vytváření instancí. V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí není souběžnost relevantní, protože každá zpráva je zpracována novou instancí služby. V <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí je relevantní souběžnost <xref:System.ServiceModel.ConcurrencyMode.Single> nebo <xref:System.ServiceModel.ConcurrencyMode.Multiple>, v závislosti na tom, jestli jediná instance zpracovává zprávy sekvenčně nebo souběžně. V <xref:System.ServiceModel.InstanceContextMode.PerSession> vytváření instancí můžou být relevantní všechny režimy souběžnosti.  
  
 Třída služby určuje chování souběžnosti s atributem `[ServiceBehavior(ConcurrencyMode=<setting>)]`, jak je znázorněno v následujícím příkladu kódu. Změnou řádků, které jsou zakomentovány, můžete experimentovat s `Single` a `Multiple` režimy souběžnosti. Nezapomeňte znovu sestavit službu po změně režimu souběžnosti.  
  
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
  
 Ukázka používá ve výchozím nastavení <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti s <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí. Kód klienta byl změněn tak, aby používal asynchronní proxy server. Díky tomu může klient uskutečnit více volání služby bez čekání na odezvu mezi jednotlivými voláními. Můžete sledovat rozdíl v chování režimu souběžnosti služby.  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Režim souběžnosti, ve kterém je služba spuštěna, se zobrazí při každé operaci a pak se zobrazí počet operací. Všimněte si, že když je režim souběžnosti `Multiple`, výsledky se vrátí v jiném pořadí, než jak byly volány, protože služba zpracovává více zpráv souběžně. Když změníte režim souběžnosti na `Single`, výsledky se vrátí v pořadí, ve kterém byly volány, protože služba zpracovává každou zprávu sekvenčně. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud k vygenerování proxy klienta používáte Svcutil. exe, ujistěte se, že jste zahrnuli možnost `/async`.  
  
3. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
