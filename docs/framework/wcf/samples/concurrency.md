---
title: Souběžnost
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 17cad01dfd0474c2c0520987ba45445a256f72b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="concurrency"></a>Souběžnost
Ukázka souběžnosti ukazuje, jak pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute> s <xref:System.ServiceModel.ConcurrencyMode> výčtu, který určuje, zda instance služby zpracovává zprávy postupně nebo souběžně. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby. Tento příklad definuje nové smlouvy, `ICalculatorConcurrency`, který dědí z `ICalculator`, poskytuje dva další operace pro zkontrolujte stav služby souběžnosti. Změnou nastavení souběžnosti, můžete sledovat změny v chování pomocí klienta.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Nejsou k dispozici tři režimy souběžnosti:  
  
-   `Single`: Každá instance služby zpracovává jednu zprávu najednou. Toto je výchozí režim souběžnosti.  
  
-   `Multiple`: Každá instance služby zpracovává více zpráv současně. Implementace služby musí být vláken pro použití tohoto režimu souběžnosti.  
  
-   `Reentrant`: Každá instance služby zpracovává jednu zprávu najednou, ale přijímá znovu zadaná volání. Když se volají, služba přijímá pouze těchto volání. Vícenásobně přístupné ukazují [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) ukázka.  
  
 Použití souběžného zpracování se týká zřizování instancí režimu. V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí, souběžnosti není relevantní, protože každá zpráva se zpracuje nové instance služby. V <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí buď <xref:System.ServiceModel.ConcurrencyMode.Single> nebo <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti je relevantní, v závislosti na tom, jestli jediné instance zpracovává zprávy postupně nebo souběžně. V <xref:System.ServiceModel.InstanceContextMode.PerSession> vytváření instancí, žádný z režimů souběžnosti nemusí být relevantní.  
  
 Třída služby určuje chování souběžnosti s `[ServiceBehavior(ConcurrencyMode=<setting>)]` atributu, jak je znázorněno v ukázce kódu, který následuje dále. Změnou linky, které jsou označené jako komentář můžete vyzkoušet `Single` a `Multiple` režimy souběžnosti. Mějte na paměti, znovu sestavit službu po změně souběžný režim.  
  
```  
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
  
 Příklad používá <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti s <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí ve výchozím nastavení. Kód klienta se změnilo používat asynchronní proxy server. To umožňuje klientům provádět několik volání do služby bez čekání na odezvu mezi každé volání. Rozdíl v chování souběžný režim služby můžete sledovat.  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Souběžný režim, který služba běží pod se zobrazí, se nazývá každé operace a pak se zobrazí počet operací. Všimněte si, že pokud je režim souběžnosti `Multiple`, budou vráceny výsledky v jiném pořadí než jak měla volat, protože služba zpracovává více zpráv současně. Změnou souběžný režim `Single`, budou vráceny výsledky v pořadí se měla volat, protože služba zpracovává každou zprávu postupně. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud používáte Svcutil.exe ke generování proxy serveru klienta, ujistěte se, jestli jste zahrnuli `/async` možnost.  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a>Viz také
