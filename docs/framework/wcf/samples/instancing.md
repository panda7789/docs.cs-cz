---
title: Vytváření instancí
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, instancing sample
- Instancing Sample [Windows Communication Foundation]
ms.assetid: c290fa54-f6ae-45a1-9186-d9504ebc6ee6
ms.openlocfilehash: 2fb48ee413c48f481b433f58352c2d0fe38f3972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="instancing"></a>Vytváření instancí
Příklad Instancing znázorňuje zřizování instancí nastavení chování, který řídí vytváření instancí třídy služby v reakci na požadavky klientů. Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby. Tento příklad definuje nové smlouvy, `ICalculatorInstance`, který dědí z `ICalculator`. Kontrakt určený `ICalculatorInstance` poskytuje tři další operace pro kontroly stavu instance služby. Změnou nastavení zřizování instancí, můžete sledovat změny v chování pomocí klienta.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 K dispozici jsou následující režimy zřizování instancí:  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>: Nové instance služby se vytvoří pro každý požadavek klienta.  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>: Novou instanci je vytvoří pro každou novou relaci klienta a udržovat po dobu jeho existence této relace (vyžaduje vazbu, která podporuje relace).  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>: Jednu instanci třídy služby zpracuje všechny žádosti klienta po dobu jeho existence aplikace.  
  
 Třída služby určuje chování zřizování instancí s `[ServiceBehavior(InstanceContextMode=<setting>)]` atributu, jak je znázorněno v ukázce kódu, který následuje dále. Změnou linky, které jsou označené jako komentář, můžete sledovat chování oba režimy instance. Mějte na paměti, znovu sestavit po změně režimu zřizování instancí služby. Nejsou žádná vytváření instancí související nastavení k určení na straně klienta.  
  
```  
// Enable one of the following instance modes to compare instancing behaviors.  
 [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
  
// PerCall creates a new instance for each operation.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerCall)]  
  
// Singleton creates a single instance for application lifetime.  
//[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class CalculatorService : ICalculatorInstance  
{  
    static Object syncObject = new object();  
    static int instanceCount;  
    int instanceId;  
    int operationCount;  
  
    public CalculatorService()  
    {  
        lock (syncObject)  
        {  
            instanceCount++;  
            instanceId = instanceCount;  
        }  
    }  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        Interlocked.Increment(ref operationCount);  
        return n1 / n2;  
    }  
  
    public string GetInstanceContextMode()  
    {   // Return the InstanceContextMode of the service  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.InstanceContextMode.ToString();  
    }  
  
    public int GetInstanceId()  
    {   // Return the id for this instance  
        return instanceId;  
    }  
  
    public int GetOperationCount()  
    {   // Return the number of ICalculator operations performed   
        // on this instance  
        lock (syncObject)  
        {  
            return operationCount;  
        }  
    }  
}  
  
static void Main()  
{  
    // Create a client.  
    CalculatorInstanceClient client = new CalculatorInstanceClient();  
    string instanceMode = client.GetInstanceContextMode();  
    Console.WriteLine("InstanceContextMode: {0}", instanceMode);  
    DoCalculations(client);  
  
    // Create a second client.  
    CalculatorInstanceClient client2 = new CalculatorInstanceClient();  
  
    DoCalculations(client2);  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Zobrazí se služba běží v režimu instance. Po každé operaci zobrazí se počet instancí ID a operace tak, aby odrážela chování v režimu zřizování instancí. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Instancing`  
  
## <a name="see-also"></a>Viz také
