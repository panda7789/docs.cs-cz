---
title: 'Postupy: Programové přidání možností rozpoznání do klienta a služby WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: c28815d1d208d3e91785a13d95e03c09c0f02ed9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596991"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Postupy: Programové přidání možností rozpoznání do klienta a služby WCF
Toto téma vysvětluje, jak nastavit službu Windows Communication Foundation (WCF) jako zjistitelnou. Je založený na ukázce [samostatného hostitele](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) .  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Postup konfigurace existující ukázky služby pro samoobslužné hostování pro zjišťování  
  
1. Otevřete řešení samostatného hostitele v aplikaci Visual Studio 2012. Ukázka se nachází v adresáři TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Přidejte odkaz na `System.ServiceModel.Discovery.dll` projekt služby. Může se zobrazit chybová zpráva oznamující, že systém. ServiceModel. Discovery. dll nebo jedna z jeho závislostí vyžaduje novější verzi .NET Framework než ta, která je zadaná v projektu... Pokud se zobrazí tato zpráva, klikněte pravým tlačítkem na projekt v Průzkumník řešení a vyberte **vlastnosti**. V okně **Vlastnosti projektu** se ujistěte, že je **Cílová architektura** [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .  
  
3. Otevřete soubor Service.cs a přidejte následující `using` příkaz.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. V `Main()` metodě uvnitř `using` příkazu přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instanci do hostitele služby.  
  
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
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Určuje, zda je služba, na kterou je použita, zjistitelná.  
  
5. Přidejte <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> k hostiteli služby hned za kódem, který přidá <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Tento kód určuje, zda mají být zprávy zjišťování odesílány na standardní koncový bod zjišťování UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Vytvoření klientské aplikace používající zjišťování pro volání služby  
  
1. Přidejte novou konzolovou aplikaci do řešení s názvem `DiscoveryClientApp` .  
  
2. Přidat odkaz na `System.ServiceModel.dll` a`System.ServiceModel.Discovery.dll`  
  
3. Zkopírujte soubory GeneratedClient.cs a App. config z existujícího projektu klienta do nového projektu DiscoveryClientApp. Provedete to tak, že kliknete pravým tlačítkem na soubory v **Průzkumník řešení**, vyberete **Kopírovat**a pak vyberete projekt **DiscoveryClientApp** , kliknete pravým tlačítkem a vyberete **Vložit**.  
  
4. Otevřete Program.cs.  
  
5. Přidejte následující příkazy `using`.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Přidejte do třídy statickou metodu s názvem `FindCalculatorServiceAddress()` `Program` .  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Tato metoda používá zjišťování k hledání `CalculatorService` služby.  
  
7. Uvnitř `FindCalculatorServiceAddress` metody vytvořte novou <xref:System.ServiceModel.Discovery.DiscoveryClient> instanci s předáním do <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> konstruktoru.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     To oznamuje, že <xref:System.ServiceModel.Discovery.DiscoveryClient> třída by měla používat standardní koncový bod zjišťování UDP pro odesílání a příjem zpráv zjišťování.  
  
8. Na dalším řádku volejte <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu a určete <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která obsahuje kontrakt služby, který chcete vyhledat. V takovém případě zadejte `ICalculator` .  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po volání metody <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Zkontrolujte, zda existuje alespoň jedna vyhovující služba a vrátí <xref:System.ServiceModel.EndpointAddress> první vyhovující službu. Jinak vraťte `null` .  
  
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
  
10. Přidejte statickou metodu s názvem `InvokeCalculatorService` do `Program` třídy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Tato metoda používá adresu koncového bodu vrácenou z `FindCalculatorServiceAddress` pro volání služby kalkulačky.  
  
11. Uvnitř `InvokeCalculatorService` metody vytvořte instanci `CalculatorServiceClient` třídy. Tato třída je definována v rámci ukázky pro [vlastní hostitele](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) . Byl vygenerován pomocí Svcutil. exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Na dalším řádku nastavte adresu koncového bodu klienta na adresu koncového bodu vrácenou z `FindCalculatorServiceAddress()` .  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Hned za kód pro předchozí krok volejte metody vystavené službou Kalkulačka.  
  
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
  
14. Přidejte kód do `Main()` metody ve `Program` třídě, která se má volat `FindCalculatorServiceAddress` .  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Na dalším řádku zavolejte `InvokeCalculatorService()` a předejte adresu koncového bodu vrácenou z `FindCalculatorServiceAddress()` .  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Testování aplikace  
  
1. Otevřete příkazový řádek se zvýšenými oprávněními a spusťte Service. exe.  
  
2. Otevřete příkazový řádek a spusťte DiscoveryClientApp. exe.  
  
3. Výstup souboru Service. exe by měl vypadat jako následující výstup.  
  
    ```output  
    Received Add(100,15.99)  
    Return: 115.99  
    Received Subtract(100,15.99)  
    Return: 84.01  
    Received Multiply(100,15.99)  
    Return: 1599  
    Received Divide(100,15.99)  
    Return: 6.25390869293308  
    ```  
  
4. Výstup z DiscoveryClientApp. exe by měl vypadat jako následující výstup.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Příklad  
 Následující seznam obsahuje kód pro tuto ukázku. Vzhledem k tomu, že je tento kód založen na [samostatném hostiteli](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) , jsou uvedeny pouze změněné soubory. Další informace o ukázce samostatného hostitele najdete v tématu [pokyny k instalaci](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).  
  
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

- [Přehled zjišťování WCF](wcf-discovery-overview.md)
- [Objektový model zjišťování WCF](wcf-discovery-object-model.md)
