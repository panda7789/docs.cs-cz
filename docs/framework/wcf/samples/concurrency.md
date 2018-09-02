---
title: Souběžnost
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 892def5d9788dfdf86d312aa04cf89e891323971
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388812"
---
# <a name="concurrency"></a>Souběžnost
Ukázka souběžnosti znázorňuje použití <xref:System.ServiceModel.ServiceBehaviorAttribute> s <xref:System.ServiceModel.ConcurrencyMode> výčet, který řídí, zda instance služby zpracovává zprávy postupně sekvenčně nebo současně. Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby. Tato ukázka definuje kontrakt nové `ICalculatorConcurrency`, který dědí z `ICalculator`, poskytuje dvě další operace Kontrola stavu služby souběžnosti. Změnou nastavení souběžnosti můžete sledovat změny v chování pomocí klienta.  
  
 V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 K dispozici jsou tři režimy souběžnosti:  
  
-   `Single`: Každá instance služby zpracovává jednu zprávu najednou. Toto je výchozí režim.  
  
-   `Multiple`: Každá instance služby zpracovává více zpráv souběžně. Implementace služby musí být bezpečná pro vlákno pro použití tohoto režimu souběžnosti.  
  
-   `Reentrant`: Každá instance služby zpracovává zprávy jeden po druhém, ale přijímá znovu zadaných volání. Služba přijímá pouze tato volání zavoláním navýšení kapacity. Vícenásobný jsou popsané v článku [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) vzorku.  
  
 Vytvoření instance režimu se týká použití souběžnosti. V <xref:System.ServiceModel.InstanceContextMode.PerCall> vytváření instancí, souběžnost není odpovídající, protože každá zpráva se zpracuje pomocí nové instance služby. V <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí, buď <xref:System.ServiceModel.ConcurrencyMode.Single> nebo <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti je relevantní, v závislosti na tom, jestli jedna instance zpracovává zprávy postupně sekvenčně nebo současně. V <xref:System.ServiceModel.InstanceContextMode.PerSession> vytváření instancí, všechny režimy souběžnosti můžou být relevantní.  
  
 Určuje chování souběžnosti s třídu služby `[ServiceBehavior(ConcurrencyMode=<setting>)]` atributu, jak je znázorněno v ukázce kódu, který následuje. Tak, že změníte, které řádky jsou označené jako komentář, můžete experimentovat s `Single` a `Multiple` režimy souběžnosti. Nezapomeňte znovu sestavit službě po změně režimu souběžnosti.  
  
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
  
 Ukázka používá <xref:System.ServiceModel.ConcurrencyMode.Multiple> souběžnosti ovládacím prvkem <xref:System.ServiceModel.InstanceContextMode.Single> vytváření instancí ve výchozím nastavení. Klientský kód byl změněn na používání asynchronních proxy. Díky tomu se klient několik volání služby bez čekání na odpověď mezi jednotlivými voláními. Podívejte se na rozdíl v chování souběžný režim služby.  
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Režim souběžnosti, ve kterém je služba spuštěná v části se zobrazí, se nazývá každé operace a zobrazí počet operací. Všimněte si, že pokud je režim `Multiple`, výsledky jsou vráceny v jiném pořadí, než jak byly volány, protože služba zpracovává více zpráv souběžně. Změnou souběžný režim `Single`, výsledky se vrátí v pořadí jejich byly volány, protože služba každou zprávu zpracovává postupně. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Pokud pomocí Svcutil.exe lze generovat proxy serveru klienta, ujistěte se, že složku zahrnujete `/async` možnost.  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a>Viz také
