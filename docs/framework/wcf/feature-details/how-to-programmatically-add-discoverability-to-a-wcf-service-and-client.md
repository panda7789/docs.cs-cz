---
title: 'Postupy: Programové přidání možností rozpoznání do klienta a služby WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: 0685694db8f67ed690cf2a8002bf70a05695a192
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495480"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Postupy: Programové přidání možností rozpoznání do klienta a služby WCF
Toto téma vysvětluje, jak zjistitelnost služby Windows Communication Foundation (WCF). Je založena na [hostování na vlastním](http://go.microsoft.com/fwlink/?LinkId=145523) ukázka.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Konfigurace existující ukázka hostování na vlastním serveru služby pro zjišťování  
  
1.  Otevřete řešení hostování na vlastním serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]. Tato ukázka se nachází v adresáři TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2.  Přidat odkaz na `System.ServiceModel.Discovery.dll` do projektu služby. Mohou se zobrazit chybová zpráva s oznámením "systém. ServiceModel.Discovery.dll nebo jeden z jeho závislých vyžaduje novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] než verze zadaná v projektu... " Pokud se zobrazí tato zpráva, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a zvolte **vlastnosti**. V **vlastnosti projektu** okna, ujistěte se, že **cílové rozhraní** je [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3.  Otevřete soubor Service.cs a přidejte následující `using` příkaz.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  V `Main()` metoda, uvnitř `using` příkazu Přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance hostitele služby.  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a ServiceHost for the CalculatorService type.  
        using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
        {  
            // Add a ServiceDiscoveryBehavior  
            serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());                  
  
            // ...  
        }  
    }  
    ```  
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Určuje, že je tato služba je zjistitelný.  
  
5.  Přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> k hostiteli služby hned po kód, který přidá <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Tento kód určuje zjišťování by měl být odesílání zpráv do standardní koncový bod zjišťování UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Chcete-li vytvořit klienta aplikace, která používá zjišťování pro volání služby  
  
1.  Přidat novou konzolovou aplikaci k řešení názvem `DiscoveryClientApp`.  
  
2.  Přidat odkaz na `System.ServiceModel.dll` a `System.ServiceModel.Discovery.dll`  
  
3.  Zkopírujte soubory GeneratedClient.cs a App.config z existujícího projektu klienta do nového projektu DiscoveryClientApp. K tomu, klikněte pravým tlačítkem na soubory v **Průzkumníku řešení**, vyberte **kopie**a pak vyberte **DiscoveryClientApp** projektu klikněte pravým tlačítkem a vyberte **Vložení**.  
  
4.  Otevření souboru Program.cs.  
  
5.  Přidejte následující `using` příkazy.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  Přidat statickou metodu s názvem `FindCalculatorServiceAddress()` k `Program` třídy.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Tato metoda zjišťování používá pro vyhledávání `CalculatorService` služby.  
  
7.  Uvnitř `FindCalculatorServiceAddress` metoda, vytvořte novou <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, předávání v <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> konstruktoru.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     Sdělí WCF, který <xref:System.ServiceModel.Discovery.DiscoveryClient> třída by měl použít standardní koncový bod zjišťování UDP odesílat a přijímat zprávy zjišťování.  
  
8.  Na další řádek volání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda a zadejte <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která obsahuje kontrakt služby, kterou chcete vyhledat. V takovém případě zadejte `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po zavolání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, zkontrolujte, zda existuje alespoň jedna služba odpovídající a vrátit <xref:System.ServiceModel.EndpointAddress> první odpovídající služby. V opačném případě vrátí `null`.  
  
    ```csharp  
    if (findResponse.Endpoints.Count > 0)  
    {  
        return findResponse.Endpoints[0].Address;  
    }  
    else  
    {  
        return null;  
    }  
    ```  
  
10. Přidat statickou metodu s názvem `InvokeCalculatorService` k `Program` třídy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Tato metoda používá adresa koncového bodu, kterou vrátil `FindCalculatorServiceAddress` volat službu kalkulačky.  
  
11. Uvnitř `InvokeCalculatorService` metody vytvoření instance `CalculatorServiceClient` třídy. Tato třída je definována [hostování na vlastním](http://go.microsoft.com/fwlink/?LinkId=145523) ukázka. Byly vygenerovány pomocí Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Na další řádek nastavena adresa koncového bodu klienta adresa koncového bodu vrácená z `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Ihned po kód v předchozím kroku volání metod vystavené službu kalkulačky.  
  
    ```csharp  
    Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
  
    // Call the Add service operation.  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
    Console.WriteLine();  
  
    //Closing the client gracefully closes the connection and cleans up resources  
    client.Close();  
    ```  
  
14. Přidejte kód, který `Main()` metoda v `Program` třída volat `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Na další řádek volání `InvokeCalculatorService()` a předat adresa koncového bodu vrácená z `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Testování aplikace  
  
1.  Otevřete příkazový řádek se zvýšenými oprávněními a spusťte Service.exe.  
  
2.  Otevřete příkazový řádek a spusťte Discoveryclientapp.exe.  
  
3.  Výstup z service.exe by měl vypadat jako následující výstup.  
  
    ```Output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4.  Výstup z Discoveryclientapp.exe by měl vypadat jako následující výstup.  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Příklad  
 Následuje seznam kód pro tuto ukázku. Vzhledem k tomu, že je na základě tohoto kódu [hostování na vlastním](http://go.microsoft.com/fwlink/?LinkId=145523) ukázku, jsou uvedeny pouze soubory, které se změnily. Další informace o ukázka hostování na vlastním serveru najdete v tématu [pokyny k instalaci](http://go.microsoft.com/fwlink/?LinkId=145522).  
  
```csharp  
// Service.cs  
using System;  
using System.Configuration;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.ServiceModel.Samples  
{  
    // See SelfHost sample for service contract and implementation  
    // ...  
  
        // Host the service within this EXE console application.  
        public static void Main()  
        {  
            // Create a ServiceHost for the CalculatorService type.  
            using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService)))  
            {  
                // Add the ServiceDiscoveryBehavior to make the service discoverable  
                serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
                serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
  
                // Open the ServiceHost to create listeners and start listening for messages.  
                serviceHost.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
            }  
        }  
    }  
}  
```  
  
```csharp  
// Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
using Microsoft.ServiceModel.Samples;  
using System.Text;  
  
namespace DiscoveryClientApp  
{  
    class Program  
    {  
        static EndpointAddress FindCalculatorServiceAddress()  
        {  
            // Create DiscoveryClient  
            DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
            // Find ICalculatorService endpoints              
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
  
            if (findResponse.Endpoints.Count > 0)  
            {  
                return findResponse.Endpoints[0].Address;  
            }  
            else  
            {  
                return null;  
            }  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorClient client = new CalculatorClient();  
  
            // Connect to the discovered service endpoint  
            client.Endpoint.Address = endpointAddress;  
  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress);  
  
            double value1 = 100.00D;  
            double value2 = 15.99D;  
  
            // Call the Add service operation.  
            double result = client.Add(value1, value2);  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Subtract service operation.  
            result = client.Subtract(value1, value2);  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Multiply service operation.  
            result = client.Multiply(value1, value2);  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
            // Call the Divide service operation.  
            result = client.Divide(value1, value2);  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
            Console.WriteLine();  
  
            //Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
        static void Main(string[] args)  
        {  
            EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
  
            if (endpointAddress != null)  
            {  
                InvokeCalculatorService(endpointAddress);  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
  
        }  
    }  
}  
```  

## <a name="see-also"></a>Viz také  
 [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [Objektový model zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
