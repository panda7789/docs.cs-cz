---
title: "Konfigurace hodnot časových limitů u vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5c825a2-b48f-444a-8659-61751ff11d34
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 458f2143021ac40bfcaddbe957113e400bd5f3c5
ms.sourcegitcommit: 5d0e069655439984862a835f400058b7e8bbadc6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2017
---
# <a name="configuring-timeout-values-on-a-binding"></a>Konfigurace hodnot časových limitů u vazby
Nejsou k dispozici v vazby WCF několik nastavení časového limitu. Nastavení těchto časový limit nastavení správně může zlepšit pouze vaší služby výkon, ale také play roli v použitelnost a zabezpečení vaší služby. Následující časové limity jsou k dispozici na vazby WCF:  
  
1.  openTimeout  
  
2.  Intervalu  
  
3.  sendTimeout  
  
4.  receiveTimeout  
  
## <a name="wcf-binding-timeouts"></a>Časové limity vazby WCF  
 Každé nastavení popsané v tomto tématu jsou probíhají vazby samostatně, buď v kódu nebo konfigurace. Následující kód ukazuje, jak programového nastavení časových limitů u vazby WCF v kontextu služba s vlastním hostováním.  
  
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
  
 Další informace o těchto nastaveních naleznete v dokumentaci k <xref:System.ServiceModel.Channels.Binding> třídy.  
  
### <a name="client-side-timeouts"></a>Časové limity straně klienta  
 Na straně klienta:  
  
1.  SendTimeout – použitý k inicializaci OperationTimeout, jimiž se řídí celý proces odesílání zprávy, včetně přijímání zprávy odpovědi pro požadavek nebo odpověď operace služby. Tento časový limit platí také při odesílání zprávy odpovědi z kontrakt metody zpětného volání.  
  
2.  OpenTimeout – použít při otevírání kanály, když není zadaná žádná hodnota explicitní vypršení časového limitu  
  
3.  Intervalu – použít při zavření kanály, když není zadaná žádná hodnota explicitní vypršení časového limitu  
  
4.  ReceiveTimeout – se nepoužívá.  
  
### <a name="service-side-timeouts"></a>Časové limity straně služby  
 Na straně služby:  
  
1.  SendTimeout, OpentTimeout, intervalu jsou stejné jako na straně klienta  
  
2.  ReceiveTimeout – vrstvou Framework služby použitý k inicializaci časový limit nečinnosti relace, který řídí, jak dlouho může být relace před vypršením časového limitu nečinnosti.
