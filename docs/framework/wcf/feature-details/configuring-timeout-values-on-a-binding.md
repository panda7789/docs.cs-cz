---
title: Konfigurace hodnot časových limitů u vazby
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: f323dfff338f8a3ba24caab6df3b3916d3ae0d13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779324"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurace hodnot časových limitů u vazby
Nejsou k dispozici v vazby WCF několik nastavení časového limitu. Nastavení těchto časový limit nastavení správně může zlepšit nejen vaše služba výkon, ale také play roli v oblasti použitelnosti a zabezpečení vaší služby. Následující časové limity jsou k dispozici na vazby WCF:  
  
1. openTimeout  
  
2. closeTimeout  
  
3. SendTimeout  
  
4. receiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Vypršení časového limitu pro vazby WCF  
 Každé nastavení popsané v tomto tématu jsou provedeny ve vazbě, buď v kódu nebo konfigurace. Následující kód ukazuje, jak prostřednictvím kódu programu nastavit vypršení časových limitů u vazby WCF v kontextu služby v místním prostředí.  
  
```csharp  
public static void Main()
{
    Uri baseAddress = new Uri("http://localhost/MyServer/MyService");
    
    try
    {
        ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService));
        
        WSHttpBinding binding = new WSHttpBinding();
        binding.OpenTimeout = new TimeSpan(0, 10, 0);
        binding.CloseTimeout = new TimeSpan(0, 10, 0);
        binding.SendTimeout = new TimeSpan(0, 10, 0);
        binding.ReceiveTimeout = new TimeSpan(0, 10, 0);
        
        serviceHost.AddServiceEndpoint("ICalculator", binding, baseAddress);
        serviceHost.Open();
        
        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();
    }
    catch (CommunicationException ex)
    {
        // Handle exception ...
    }
}
```  
  
 Následující příklad ukazuje, jak nakonfigurovat vypršení časových limitů u vazby v konfiguračním souboru.  
  
```xml  
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding openTimeout="00:10:00" 
                 closeTimeout="00:10:00" 
                 sendTimeout="00:10:00" 
                 receiveTimeout="00:10:00">
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
 Další informace o těchto nastaveních najdete v dokumentaci k <xref:System.ServiceModel.Channels.Binding> třídy.  
  
### <a name="client-side-timeouts"></a>Vypršení časového limitu na straně klienta  
 Na straně klienta:  
  
1. SendTimeout – použitý k inicializaci OperationTimeout, jimiž se řídí celý proces odesílání zprávy, včetně příjem zprávy odpovědi pro operaci služby požadavku/odpovědi. Tento časový limit platí i při odesílání zprávy odpovědi z metody zpětného volání kontraktu.  
  
2. OpenTimeout – při otevírání kanály, pokud není zadána žádná hodnota explicitní vypršení časového limitu.  
  
3. CloseTimeout – při zavírání kanály, pokud není zadána žádná hodnota explicitní vypršení časového limitu.  
  
4. ReceiveTimeout – se nepoužívá.  
  
### <a name="service-side-timeouts"></a>Vypršení časových limitů straně služby  
 Na straně služby:  
  
1. SendTimeout, OpenTimeout, CloseTimeout jsou stejné jako na straně klienta.  
  
2. ReceiveTimeout – vrstva služby rozhraní Framework použitý k inicializaci časového limitu nečinnosti relace, které řídí, jak dlouho může být relace nečinná, než vyprší časový limit.
