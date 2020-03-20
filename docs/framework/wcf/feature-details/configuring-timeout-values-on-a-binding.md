---
title: Konfigurace hodnot časových limitů u vazby
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: 968e80bbd4b50d72d089a325f8e3fe498de2eac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185289"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurace hodnot časových limitů u vazby
Existuje několik nastavení časového času k dispozici ve vazbách WCF. Správné nastavení časového času může zlepšit nejen výkon služby, ale také hrát roli v použitelnosti a zabezpečení vaší služby. Následující časové osy jsou k dispozici na WCF vazby:  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Časové osy vazby WCF  
 Každé z nastavení popsaných v tomto tématu jsou provedeny na vazbě sám, a to buď v kódu nebo konfigurace. Následující kód ukazuje, jak programově nastavit časové toky na vazbě WCF v kontextu samoobslužné služby.  
  
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
  
 Následující příklad ukazuje, jak nakonfigurovat časové toky na vazbě v konfiguračním souboru.  
  
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
  
 Další informace o těchto nastaveních naleznete <xref:System.ServiceModel.Channels.Binding> v dokumentaci pro třídu.  
  
### <a name="client-side-timeouts"></a>Časové opozí na straně klienta  
 Na straně klienta:  
  
1. SendTimeout – slouží k inicializaci OperationTimeout, který řídí celý proces odesílání zprávy, včetně přijetí odpovědi na operaci služby požadavek/odpověď. Tento časový opova platí také při odesílání odpovědí z metody smlouvy zpětného volání.  
  
2. OpenTimeout – používá se při otevírání kanálů, když není zadána žádná explicitní hodnota časového času.  
  
3. CloseTimeout – používá se při zavírání kanálů, když není zadána žádná explicitní hodnota časového času.  
  
4. ReceiveTimeout – se nepoužívá.  
  
### <a name="service-side-timeouts"></a>Časové výtažky na straně služby  
 Na straně služby:  
  
1. SendTimeout, OpenTimeout, CloseTimeout jsou stejné jako na straně klienta.  
  
2. ReceiveTimeout – používá vrstva rozhraní služby k inicializaci relace nečinnosti časový limit, který určuje, jak dlouho relace může být nečinný před vypršením časového limitu.
