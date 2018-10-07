---
title: 'Postupy: Programové přidání možností rozpoznání do klienta a služby WCF'
ms.date: 03/30/2017
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
ms.openlocfilehash: 407777b1545fb12eb3ed1787fdba86991c894fdb
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838452"
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a>Postupy: Programové přidání možností rozpoznání do klienta a služby WCF
Toto téma vysvětluje, jak zjistitelnost služby Windows Communication Foundation (WCF). Je založen na [hostování na vlastním serveru](https://go.microsoft.com/fwlink/?LinkId=145523) vzorku.  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a>Ke konfiguraci existující ukázka hostování na vlastním serveru služby pro zjišťování  
  
1.  Otevřete řešení hostování na vlastním serveru v sadě Visual Studio 2012. Tato ukázka se nachází v adresáři TechnologySamples\Basic\Service\Hosting\SelfHost.  
  
2.  Přidejte odkaz na `System.ServiceModel.Discovery.dll` do projektu služby. Může se zobrazit chybová zpráva s oznámením "systém. ServiceModel.Discovery.dll nebo některá z jeho závislostí, vyžaduje novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] než verze zadaná v projektu... " Pokud se zobrazí tato zpráva, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a zvolte **vlastnosti**. V **vlastnosti projektu** okno, ujistěte se, že **Cílová architektura** je [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
3.  Otevřete soubor Service.cs a přidejte následující `using` příkazu.  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  V `Main()` metody, uvnitř `using` příkaz, přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance hostitele služby.  
  
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
  
     <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Určuje, jestli je služba, použije se na zjistitelné.  
  
5.  Přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> k hostiteli služby přímo po kódu, který se přidá <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     Tento kód určuje, že zjišťování zpráv odesílaných do standardní koncový bod zjišťování UDP.  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a>Vytvoření klientské aplikace používající zjišťování k vyvolání služby  
  
1.  Přidání nových konzolovou aplikaci pro řešení, nazývá `DiscoveryClientApp`.  
  
2.  Přidejte odkaz na `System.ServiceModel.dll` a `System.ServiceModel.Discovery.dll`  
  
3.  Zkopírujte soubory GeneratedClient.cs a App.config z existujícího projektu klienta do nového projektu DiscoveryClientApp. Chcete-li to provést, klikněte pravým tlačítkem na soubory v **Průzkumníka řešení**vyberte **kopírování**a pak vyberte **DiscoveryClientApp** projektu, klikněte pravým tlačítkem a vyberte **Vložit**.  
  
4.  Otevřete soubor Program.cs.  
  
5.  Přidejte následující `using` příkazy.  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  Přidat volána statická metoda `FindCalculatorServiceAddress()` k `Program` třídy.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     Tato metoda používá zjišťování k vyhledání `CalculatorService` služby.  
  
7.  Uvnitř `FindCalculatorServiceAddress` metoda, vytvořte nový <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, předejte <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> konstruktoru.  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     To říká WCF, který <xref:System.ServiceModel.Discovery.DiscoveryClient> třída by měla použít standardní koncový bod zjišťování UDP k odesílání a příjem zpráv zjišťování.  
  
8.  Na dalším řádku, volání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda a zadejte <xref:System.ServiceModel.Discovery.FindCriteria> instance, která obsahuje kontrakt služby, kterou chcete vyhledat. V tomto případě `ICalculator`.  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. Po volání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, zkontrolujte, jestli je aspoň jednu odpovídající službu a vrátit <xref:System.ServiceModel.EndpointAddress> první odpovídající služby. V opačném případě vrátí `null`.  
  
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
  
10. Přidat statickou metodu pojmenovanou `InvokeCalculatorService` k `Program` třídy.  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     Tato metoda používá adresu koncového bodu vrácená `FindCalculatorServiceAddress` volat službu kalkulačky.  
  
11. Uvnitř `InvokeCalculatorService` metody vytvoření instance `CalculatorServiceClient` třídy. Tato třída je definována [hostování na vlastním serveru](https://go.microsoft.com/fwlink/?LinkId=145523) vzorku. Byl vytvořen pomocí Svcutil.exe.  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. Na dalším řádku nastavte adresu koncového bodu klienta vrácenou z adresu koncového bodu `FindCalculatorServiceAddress()`.  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. Ihned za kódem na předchozí krok voláním metody vystavené objektem službu kalkulačky.  
  
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
  
14. Přidejte kód, který `Main()` metoda ve `Program` třídy volání `FindCalculatorServiceAddress`.  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. Na dalším řádku, zavolejte `InvokeCalculatorService()` a předat adresu koncového bodu vrácená `FindCalculatorServiceAddress()`.  
  
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
  
3.  Výstup z service.exe by měl vypadat podobně jako následující výstup.  
  
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
  
4.  Výstup z Discoveryclientapp.exe by měl vypadat podobně jako následující výstup.  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a>Příklad  
 Následuje seznam kód pro tuto ukázku. Vzhledem k tomu, že tento kód je založený na [hostování na vlastním serveru](https://go.microsoft.com/fwlink/?LinkId=145523) ukázku, jsou uvedeny pouze soubory, které byly změněny. Další informace týkající se ukázky hostování na vlastním serveru najdete v tématu [pokyny k instalaci](https://go.microsoft.com/fwlink/?LinkId=145522).  
  
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
