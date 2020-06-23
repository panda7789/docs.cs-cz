---
title: Konfigurace hodnot časových limitů u vazby
description: Naučte se spravovat nastavení časových limitů pro vazby WCF za účelem zvýšení výkonu, použitelnosti a zabezpečení vaší služby.
ms.date: 03/30/2017
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
ms.openlocfilehash: c41824a242d9b42290183cd70b9acf5b8ee59e6b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245112"
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurace hodnot časových limitů u vazby
V vazbách WCF je dostupných několik nastavení časového limitu. Nastavení těchto nastavení časového limitu může správně zlepšit nejen výkon služby, ale také hrát roli v oblasti použitelnosti a zabezpečení vaší služby. V vazbách WCF jsou k dispozici následující časové limity:  
  
1. OpenTimeout  
  
2. CloseTimeout  
  
3. SendTimeout  
  
4. ReceiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Vypršení časových limitů vazeb WCF  
 Každé nastavení popsané v tomto tématu se provádí na samotné vazbě, a to buď v kódu, nebo v konfiguraci. Následující kód ukazuje, jak programově nastavit vypršení časových limitů u vazby WCF v kontextu samoobslužné služby.  
  
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
  
 Následující příklad ukazuje způsob konfigurace časových limitů u vazby v konfiguračním souboru.  
  
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
  
 Další informace o těchto nastaveních najdete v dokumentaci pro <xref:System.ServiceModel.Channels.Binding> třídu.  
  
### <a name="client-side-timeouts"></a>Vypršení časových limitů na straně klienta  
 Na straně klienta:  
  
1. SendTimeout – slouží k inicializaci OperationTimeout, který řídí celý proces odeslání zprávy, včetně přijetí zprávy odpovědi pro operaci služby žádosti a odpověď. Tento časový limit platí i při posílání odpovědí na zprávy z metody kontraktu zpětného volání.  
  
2. OpenTimeout – používá se při otevírání kanálů, když není zadaná žádná explicitní hodnota časového limitu.  
  
3. CloseTimeout – používá se při zavírání kanálů, když není zadaná žádná explicitní hodnota časového limitu.  
  
4. ReceiveTimeout – se nepoužívá.  
  
### <a name="service-side-timeouts"></a>Vypršení časových limitů na straně služby  
 Na straně služby:  
  
1. SendTimeout, OpenTimeout, CloseTimeout jsou stejné jako u klienta.  
  
2. ReceiveTimeout – používá se vrstvou rozhraní služby k inicializaci časového limitu nečinnosti relace, který určuje, jak dlouho může být relace nečinná, než vyprší časový limit.
