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
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="7e6bb-102">Postupy: Programové přidání možností rozpoznání do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="7e6bb-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="7e6bb-103">Toto téma vysvětluje, jak nastavit službu Windows Communication Foundation (WCF) jako zjistitelnou.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-103">This topic explains how to make a Windows Communication Foundation (WCF) service discoverable.</span></span> <span data-ttu-id="7e6bb-104">Je založený na ukázce [samostatného hostitele](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-104">It is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="7e6bb-105">Postup konfigurace existující ukázky služby pro samoobslužné hostování pro zjišťování</span><span class="sxs-lookup"><span data-stu-id="7e6bb-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1. <span data-ttu-id="7e6bb-106">Otevřete řešení samostatného hostitele v aplikaci Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-106">Open the Self-Host solution in Visual Studio 2012.</span></span> <span data-ttu-id="7e6bb-107">Ukázka se nachází v adresáři TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2. <span data-ttu-id="7e6bb-108">Přidejte odkaz na `System.ServiceModel.Discovery.dll` projekt služby.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="7e6bb-109">Může se zobrazit chybová zpráva oznamující, že systém.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-109">You may see an error message saying "System.</span></span> <span data-ttu-id="7e6bb-110">ServiceModel. Discovery. dll nebo jedna z jeho závislostí vyžaduje novější verzi .NET Framework než ta, která je zadaná v projektu... Pokud se zobrazí tato zpráva, klikněte pravým tlačítkem na projekt v Průzkumník řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the .NET Framework than the one specified in the project …" If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="7e6bb-111">V okně **Vlastnosti projektu** se ujistěte, že je **Cílová architektura** [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-111">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3. <span data-ttu-id="7e6bb-112">Otevřete soubor Service.cs a přidejte následující `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-112">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4. <span data-ttu-id="7e6bb-113">V `Main()` metodě uvnitř `using` příkazu přidejte <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instanci do hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-113">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="7e6bb-114"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>Určuje, zda je služba, na kterou je použita, zjistitelná.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-114">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5. <span data-ttu-id="7e6bb-115">Přidejte <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> k hostiteli služby hned za kódem, který přidá <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-115">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="7e6bb-116">Tento kód určuje, zda mají být zprávy zjišťování odesílány na standardní koncový bod zjišťování UDP.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-116">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="7e6bb-117">Vytvoření klientské aplikace používající zjišťování pro volání služby</span><span class="sxs-lookup"><span data-stu-id="7e6bb-117">To create a client application that uses discovery to call the service</span></span>  
  
1. <span data-ttu-id="7e6bb-118">Přidejte novou konzolovou aplikaci do řešení s názvem `DiscoveryClientApp` .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-118">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2. <span data-ttu-id="7e6bb-119">Přidat odkaz na `System.ServiceModel.dll` a`System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="7e6bb-119">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3. <span data-ttu-id="7e6bb-120">Zkopírujte soubory GeneratedClient.cs a App. config z existujícího projektu klienta do nového projektu DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-120">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="7e6bb-121">Provedete to tak, že kliknete pravým tlačítkem na soubory v **Průzkumník řešení**, vyberete **Kopírovat**a pak vyberete projekt **DiscoveryClientApp** , kliknete pravým tlačítkem a vyberete **Vložit**.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-121">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4. <span data-ttu-id="7e6bb-122">Otevřete Program.cs.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-122">Open Program.cs.</span></span>  
  
5. <span data-ttu-id="7e6bb-123">Přidejte následující příkazy `using`.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-123">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6. <span data-ttu-id="7e6bb-124">Přidejte do třídy statickou metodu s názvem `FindCalculatorServiceAddress()` `Program` .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-124">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="7e6bb-125">Tato metoda používá zjišťování k hledání `CalculatorService` služby.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-125">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7. <span data-ttu-id="7e6bb-126">Uvnitř `FindCalculatorServiceAddress` metody vytvořte novou <xref:System.ServiceModel.Discovery.DiscoveryClient> instanci s předáním do <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-126">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="7e6bb-127">To oznamuje, že <xref:System.ServiceModel.Discovery.DiscoveryClient> třída by měla používat standardní koncový bod zjišťování UDP pro odesílání a příjem zpráv zjišťování.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-127">This tells WCF that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8. <span data-ttu-id="7e6bb-128">Na dalším řádku volejte <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metodu a určete <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která obsahuje kontrakt služby, který chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-128">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="7e6bb-129">V takovém případě zadejte `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-129">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="7e6bb-130">Po volání metody <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> Zkontrolujte, zda existuje alespoň jedna vyhovující služba a vrátí <xref:System.ServiceModel.EndpointAddress> první vyhovující službu.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-130">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="7e6bb-131">Jinak vraťte `null` .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-131">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="7e6bb-132">Přidejte statickou metodu s názvem `InvokeCalculatorService` do `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-132">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="7e6bb-133">Tato metoda používá adresu koncového bodu vrácenou z `FindCalculatorServiceAddress` pro volání služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-133">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="7e6bb-134">Uvnitř `InvokeCalculatorService` metody vytvořte instanci `CalculatorServiceClient` třídy.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-134">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="7e6bb-135">Tato třída je definována v rámci ukázky pro [vlastní hostitele](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-135">This class is defined by the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample.</span></span> <span data-ttu-id="7e6bb-136">Byl vygenerován pomocí Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-136">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="7e6bb-137">Na dalším řádku nastavte adresu koncového bodu klienta na adresu koncového bodu vrácenou z `FindCalculatorServiceAddress()` .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-137">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="7e6bb-138">Hned za kód pro předchozí krok volejte metody vystavené službou Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-138">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="7e6bb-139">Přidejte kód do `Main()` metody ve `Program` třídě, která se má volat `FindCalculatorServiceAddress` .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-139">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="7e6bb-140">Na dalším řádku zavolejte `InvokeCalculatorService()` a předejte adresu koncového bodu vrácenou z `FindCalculatorServiceAddress()` .</span><span class="sxs-lookup"><span data-stu-id="7e6bb-140">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="7e6bb-141">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="7e6bb-141">To test the application</span></span>  
  
1. <span data-ttu-id="7e6bb-142">Otevřete příkazový řádek se zvýšenými oprávněními a spusťte Service. exe.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-142">Open an elevated command prompt and run Service.exe.</span></span>  
  
2. <span data-ttu-id="7e6bb-143">Otevřete příkazový řádek a spusťte DiscoveryClientApp. exe.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-143">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3. <span data-ttu-id="7e6bb-144">Výstup souboru Service. exe by měl vypadat jako následující výstup.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-144">The output from service.exe should look like the following output.</span></span>  
  
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
  
4. <span data-ttu-id="7e6bb-145">Výstup z DiscoveryClientApp. exe by měl vypadat jako následující výstup.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-145">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="7e6bb-146">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e6bb-146">Example</span></span>  
 <span data-ttu-id="7e6bb-147">Následující seznam obsahuje kód pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-147">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="7e6bb-148">Vzhledem k tomu, že je tento kód založen na [samostatném hostiteli](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) , jsou uvedeny pouze změněné soubory.</span><span class="sxs-lookup"><span data-stu-id="7e6bb-148">Because this code is based on the [Self-Host](https://docs.microsoft.com/dotnet/framework/wcf/samples/self-host) sample, only those files that are changed are listed.</span></span> <span data-ttu-id="7e6bb-149">Další informace o ukázce samostatného hostitele najdete v tématu [pokyny k instalaci](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span><span class="sxs-lookup"><span data-stu-id="7e6bb-149">For more information about the Self-Host sample, see [Setup Instructions](https://docs.microsoft.com/dotnet/framework/wcf/samples/set-up-instructions).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="7e6bb-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e6bb-150">See also</span></span>

- [<span data-ttu-id="7e6bb-151">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="7e6bb-151">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="7e6bb-152">Objektový model zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="7e6bb-152">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)
