---
title: 'Postupy: Programové přidání možností rozpoznání do klienta a služby WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: dd96bc168413eef99260a5251e74971aa1309ff4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184889"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Postupy: Programové přidání možností rozpoznání do klienta a služby WCF
Toto téma vysvětluje, jak zjistit službu WCF (Windows Communication Foundation). Je založen na vzorku [Self-Host.](https://go.microsoft.com/fwlink/?LinkId=145523)  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Konfigurace existující ukázky služby Samoobslužné služby pro zjišťování  
  
1. Otevřete řešení Self-Host v sadě Visual Studio 2012. Ukázka je umístěna v adresáři TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2. Přidejte odkaz `System.ServiceModel.Discovery.dll` na projekt servisu. Může se zobrazit chybová zpráva s nápisem "Systém.You may see an error message saying "System. ServiceModel.Discovery.dll nebo jedna z jeho závislostí vyžaduje novější verzi rozhraní .NET Framework, než je zadaná v projektu ..." Pokud se zobrazí tato zpráva, klepněte pravým tlačítkem myši na projekt v Průzkumníku řešení a zvolte **Vlastnosti**. V okně **Vlastnosti projektu** zkontrolujte, [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]zda je **cílová architektura** .  
  
3. Otevřete soubor Service.cs a `using` přidejte následující příkaz.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. V `Main()` metodě uvnitř `using` příkazu <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> přidejte instanci do hostitele služby.  
  
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
  
     Určuje, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> že služba, na kterou je použita, je zjistitelná.  
  
5. Přidejte <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> a do hostitele služby hned <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>za kód, který přidá .  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Tento kód určuje, že zprávy zjišťování by měly být odeslány do koncového bodu zjišťování standardníu UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Vytvoření klientské aplikace, která používá zjišťování k volání služby  
  
1. Přidejte novou konzolovou aplikaci do řešení s názvem `DiscoveryClientApp`.  
  
2. Přidejte odkaz `System.ServiceModel.dll` na a`System.ServiceModel.Discovery.dll`  
  
3. Zkopírujte soubory GeneratedClient.cs a App.config z existujícího klientského projektu do nového projektu DiscoveryClientApp. Chcete-li to provést, klepněte pravým tlačítkem myši na soubory v **Průzkumníku řešení**, vyberte **příkaz Kopírovat**a potom vyberte projekt **DiscoveryClientApp,** klepněte pravým tlačítkem myši a vyberte **vložit**.  
  
4. Otevřete Program.cs.  
  
5. Přidejte následující příkazy `using`.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. Přidejte statickou `FindCalculatorServiceAddress()` metodu volanou do `Program` třídy.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Tato metoda používá zjišťování `CalculatorService` k vyhledání služby.  
  
7. Uvnitř `FindCalculatorServiceAddress` metody vytvořte <xref:System.ServiceModel.Discovery.DiscoveryClient> novou instanci, která předává <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> konstruktoru.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     To říká WCF, že <xref:System.ServiceModel.Discovery.DiscoveryClient> třída by měla používat koncový bod zjišťování standardní UDP k odesílání a přijímání zpráv zjišťování.  
  
8. Na dalším řádku zavolejte <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu <xref:System.ServiceModel.Discovery.FindCriteria> a zadejte instanci, která obsahuje servisní smlouvu, kterou chcete vyhledat. V tomto případě `ICalculator`zadejte .  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po volání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, zkontrolujte, zda existuje alespoň jedna odpovídající <xref:System.ServiceModel.EndpointAddress> služby a vrátit první odpovídající služby. V `null`opačném případě vrátíte .  
  
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
  
10. Přidejte statickou `InvokeCalculatorService` metodu s názvem do `Program` třídy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Tato metoda používá adresu koncového bodu vrácenou z `FindCalculatorServiceAddress` k volání služby kalkulačky.  
  
11. Uvnitř `InvokeCalculatorService` metody vytvořte instanci třídy. `CalculatorServiceClient` Tato třída je definována ukázkou [vlastního hostitele.](https://go.microsoft.com/fwlink/?LinkId=145523) To bylo generováno pomocí Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Na dalším řádku nastavte adresu koncového bodu klienta na `FindCalculatorServiceAddress()`adresu koncového bodu vrácenou z .  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Bezprostředně po kódu pro předchozí krok volejte metody vystavené službou kalkulačky.  
  
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
  
14. Přidejte kód `Main()` do `Program` metody ve `FindCalculatorServiceAddress`třídě, kterou chcete volat .  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Na dalším řádku volejte `InvokeCalculatorService()` a předat adresu koncového `FindCalculatorServiceAddress()`bodu vrácenou z .  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a>Testování aplikace  
  
1. Otevřete příkazový řádek se zvýšenými oprávněními a spusťte soubor Service.exe.  
  
2. Otevřete příkazový řádek a spusťte soubor Discoveryclientapp.exe.  
  
3. Výstup z service.exe by měl vypadat jako následující výstup.  
  
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
  
4. Výstup z Discoveryclientapp.exe by měl vypadat jako následující výstup.  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Příklad  
 Následuje seznam kódu pro tuto ukázku. Vzhledem k tomu, že tento kód je založen na [ukázce vlastního hostitele,](https://go.microsoft.com/fwlink/?LinkId=145523) jsou uvedeny pouze ty soubory, které jsou změněny. Další informace o ukázce vlastního hostitele naleznete v [tématu Pokyny k instalaci](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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

- [Přehled zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [Objektový model zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
