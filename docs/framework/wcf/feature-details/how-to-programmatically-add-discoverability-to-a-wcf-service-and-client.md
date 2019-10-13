---
title: 'Postupy: přidávání zjistitelnosti do služby a klienta WCF prostřednictvím kódu programu'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: a139eb4a15486be329bc6853ee6b3a3be06b0619
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291570"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Postupy: přidávání zjistitelnosti do služby a klienta WCF prostřednictvím kódu programu
Toto téma vysvětluje, jak nastavit službu Windows Communication Foundation (WCF) jako zjistitelnou. Je založený na ukázce [samostatného hostitele](https://go.microsoft.com/fwlink/?LinkId=145523) .  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Postup konfigurace existující ukázky služby pro samoobslužné hostování pro zjišťování  
  
1. Otevřete řešení samostatného hostitele v aplikaci Visual Studio 2012. Ukázka se nachází v adresáři TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Přidejte odkaz na `System.ServiceModel.Discovery.dll` do projektu služby. Může se zobrazit chybová zpráva oznamující, že systém. ServiceModel. Discovery. dll nebo jedna z jeho závislostí vyžaduje novější verzi .NET Framework než ta, která je zadaná v projektu... Pokud se zobrazí tato zpráva, klikněte pravým tlačítkem na projekt v Průzkumník řešení a vyberte **vlastnosti**. V okně **Vlastnosti projektu** se ujistěte, že je **Cílová architektura** [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3. Otevřete soubor Service.cs a přidejte následující příkaz `using`.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. V metodě `Main()` uvnitř příkazu `using` přidejte instanci <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> k hostiteli služby.  
  
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
  
     @No__t-0 určuje, zda je služba, na kterou je použita, zjistitelná.  
  
5. Přidejte <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> do hostitele služby hned za kód, který přidá <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Tento kód určuje, zda mají být zprávy zjišťování odesílány na standardní koncový bod zjišťování UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Vytvoření klientské aplikace používající zjišťování pro volání služby  
  
1. Do řešení s názvem `DiscoveryClientApp` přidejte novou konzolovou aplikaci.  
  
2. Přidat odkaz na `System.ServiceModel.dll` a `System.ServiceModel.Discovery.dll`  
  
3. Zkopírujte soubory GeneratedClient.cs a App. config z existujícího projektu klienta do nového projektu DiscoveryClientApp. Provedete to tak, že kliknete pravým tlačítkem na soubory v **Průzkumník řešení**, vyberete **Kopírovat**a pak vyberete projekt **DiscoveryClientApp** , kliknete pravým tlačítkem a vyberete **Vložit**.  
  
4. Otevřete Program.cs.  
  
5. Přidejte následující příkazy `using`.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Přidejte statickou metodu nazvanou `FindCalculatorServiceAddress()` do třídy `Program`.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Tato metoda používá zjišťování k vyhledání služby `CalculatorService`.  
  
7. Uvnitř metody `FindCalculatorServiceAddress` vytvořte novou instanci <xref:System.ServiceModel.Discovery.DiscoveryClient> a předejte do konstruktoru <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     To oznamuje, že třída <xref:System.ServiceModel.Discovery.DiscoveryClient> by měla používat standardní koncový bod zjišťování UDP pro odesílání a příjem zpráv zjišťování.  
  
8. Na dalším řádku volejte metodu <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> a zadejte instanci <xref:System.ServiceModel.Discovery.FindCriteria> obsahující kontrakt služby, který chcete vyhledat. V takovém případě zadejte `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po volání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Zkontrolujte, zda existuje alespoň jedna vyhovující služba a vrátí <xref:System.ServiceModel.EndpointAddress> první vyhovující služby. V opačném případě vrátí `null`.  
  
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
  
10. Přidejte statickou metodu s názvem `InvokeCalculatorService` do třídy `Program`.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Tato metoda používá adresu koncového bodu vrácenou z `FindCalculatorServiceAddress` pro volání služby kalkulačky.  
  
11. Uvnitř metody `InvokeCalculatorService` vytvořte instanci třídy `CalculatorServiceClient`. Tato třída je definována v rámci ukázky pro [vlastní hostitele](https://go.microsoft.com/fwlink/?LinkId=145523) . Byl vygenerován pomocí Svcutil. exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Na dalším řádku nastavte adresu koncového bodu klienta na adresu koncového bodu vrácenou z `FindCalculatorServiceAddress()`.  
  
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
  
14. Přidejte kód do metody `Main()` v třídě `Program` pro volání `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Na dalším řádku volejte `InvokeCalculatorService()` a předejte adresu koncového bodu vrácenou z `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Otestování aplikace  
  
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
  
## <a name="example"></a>Příklad:  
 Následující seznam obsahuje kód pro tuto ukázku. Vzhledem k tomu, že je tento kód založen na [samostatném hostiteli](https://go.microsoft.com/fwlink/?LinkId=145523) , jsou uvedeny pouze změněné soubory. Další informace o ukázce samostatného hostitele najdete v tématu [pokyny k instalaci](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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

## <a name="see-also"></a>Další informace najdete v tématech

- [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Objektový model zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
