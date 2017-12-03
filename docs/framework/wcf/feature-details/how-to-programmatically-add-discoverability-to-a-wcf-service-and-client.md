---
title: "Postupy: Programové přidání možností rozpoznání do klienta a služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f7ae7ab-6fc8-4769-9730-c14d43f7b9b1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 11d5b00113f9b44d1d77d00dd541bc602afcb405
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-programmatically-add-discoverability-to-a-wcf-service-and-client"></a><span data-ttu-id="a3483-102">Postupy: Programové přidání možností rozpoznání do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="a3483-102">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>
<span data-ttu-id="a3483-103">Toto téma vysvětluje, jak vytvořit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby zjistitelný.</span><span class="sxs-lookup"><span data-stu-id="a3483-103">This topic explains how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span> <span data-ttu-id="a3483-104">Je založena na [hostování na vlastním](http://go.microsoft.com/fwlink/?LinkId=145523) ukázka.</span><span class="sxs-lookup"><span data-stu-id="a3483-104">It is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span>  
  
### <a name="to-configure-the-existing-self-host-service-sample-for-discovery"></a><span data-ttu-id="a3483-105">Konfigurace existující ukázka hostování na vlastním serveru služby pro zjišťování</span><span class="sxs-lookup"><span data-stu-id="a3483-105">To configure the existing Self-Host service sample for Discovery</span></span>  
  
1.  <span data-ttu-id="a3483-106">Otevřete řešení hostování na vlastním serveru v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3483-106">Open the Self-Host solution in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="a3483-107">Tato ukázka se nachází v adresáři TechnologySamples\Basic\Service\Hosting\SelfHost.</span><span class="sxs-lookup"><span data-stu-id="a3483-107">The sample is located in the TechnologySamples\Basic\Service\Hosting\SelfHost directory.</span></span>  
  
2.  <span data-ttu-id="a3483-108">Přidat odkaz na `System.ServiceModel.Discovery.dll` do projektu služby.</span><span class="sxs-lookup"><span data-stu-id="a3483-108">Add a reference to `System.ServiceModel.Discovery.dll` to the service project.</span></span> <span data-ttu-id="a3483-109">Mohou se zobrazit chybová zpráva s oznámením "systém.</span><span class="sxs-lookup"><span data-stu-id="a3483-109">You may see an error message saying "System.</span></span> <span data-ttu-id="a3483-110">ServiceModel.Discovery.dll nebo jeden z jeho závislých vyžaduje novější verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] než verze zadaná v projektu... "</span><span class="sxs-lookup"><span data-stu-id="a3483-110">ServiceModel.Discovery.dll or one of its dependencies requires a later version of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] than the one specified in the project …"</span></span> <span data-ttu-id="a3483-111">Pokud se zobrazí tato zpráva, klikněte pravým tlačítkem na projekt v Průzkumníku řešení a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a3483-111">If you see this message, right-click the project in the Solution Explorer and choose **Properties**.</span></span> <span data-ttu-id="a3483-112">V **vlastnosti projektu** okna, ujistěte se, že **cílové rozhraní** je [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a3483-112">In the **Project Properties** window, make sure that the **Target Framework** is [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span>  
  
3.  <span data-ttu-id="a3483-113">Otevřete soubor Service.cs a přidejte následující `using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a3483-113">Open the Service.cs file and add the following `using` statement.</span></span>  
  
    ```csharp  
    using System.ServiceModel.Discovery;  
    ```  
  
4.  <span data-ttu-id="a3483-114">V `Main()` metoda, uvnitř `using` příkazu Přidat <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="a3483-114">In the `Main()` method, inside the `using` statement, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance to the service host.</span></span>  
  
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
  
     <span data-ttu-id="a3483-115"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> Určuje, že je tato služba je zjistitelný.</span><span class="sxs-lookup"><span data-stu-id="a3483-115">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> specifies that the service it is applied to is discoverable.</span></span>  
  
5.  <span data-ttu-id="a3483-116">Přidat <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> k hostiteli služby hned po kód, který přidá <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span><span class="sxs-lookup"><span data-stu-id="a3483-116">Add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the service host right after the code that adds the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span>  
  
    ```csharp  
    // Add ServiceDiscoveryBehavior  
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());  
  
    // Add a UdpDiscoveryEndpoint  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    ```  
  
     <span data-ttu-id="a3483-117">Tento kód určuje zjišťování by měl být odesílání zpráv do standardní koncový bod zjišťování UDP.</span><span class="sxs-lookup"><span data-stu-id="a3483-117">This code specifies that discovery messages should be sent to the standard UDP discovery endpoint.</span></span>  
  
### <a name="to-create-a-client-application-that-uses-discovery-to-call-the-service"></a><span data-ttu-id="a3483-118">Chcete-li vytvořit klienta aplikace, která používá zjišťování pro volání služby</span><span class="sxs-lookup"><span data-stu-id="a3483-118">To create a client application that uses discovery to call the service</span></span>  
  
1.  <span data-ttu-id="a3483-119">Přidat novou konzolovou aplikaci k řešení názvem `DiscoveryClientApp`.</span><span class="sxs-lookup"><span data-stu-id="a3483-119">Add a new console application to the solution called `DiscoveryClientApp`.</span></span>  
  
2.  <span data-ttu-id="a3483-120">Přidat odkaz na `System.ServiceModel.dll` a`System.ServiceModel.Discovery.dll`</span><span class="sxs-lookup"><span data-stu-id="a3483-120">Add a reference to `System.ServiceModel.dll` and `System.ServiceModel.Discovery.dll`</span></span>  
  
3.  <span data-ttu-id="a3483-121">Zkopírujte soubory GeneratedClient.cs a App.config z existujícího projektu klienta do nového projektu DiscoveryClientApp.</span><span class="sxs-lookup"><span data-stu-id="a3483-121">Copy the GeneratedClient.cs and App.config files from the existing client project to the new DiscoveryClientApp project.</span></span> <span data-ttu-id="a3483-122">K tomu, klikněte pravým tlačítkem na soubory v **Průzkumníku řešení**, vyberte **kopie**a pak vyberte **DiscoveryClientApp** projektu klikněte pravým tlačítkem a vyberte **Vložení**.</span><span class="sxs-lookup"><span data-stu-id="a3483-122">To do this, right-click the files in the **Solution Explorer**, select **Copy**, and then select the **DiscoveryClientApp** project, right-click and select **Paste**.</span></span>  
  
4.  <span data-ttu-id="a3483-123">Otevření souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="a3483-123">Open Program.cs.</span></span>  
  
5.  <span data-ttu-id="a3483-124">Přidejte následující `using` příkazy.</span><span class="sxs-lookup"><span data-stu-id="a3483-124">Add the following `using` statements.</span></span>  
  
    ```csharp  
    using System.ServiceModel;  
    using System.ServiceModel.Discovery;  
    using Microsoft.ServiceModel.Samples;  
    ```  
  
6.  <span data-ttu-id="a3483-125">Přidat statickou metodu s názvem `FindCalculatorServiceAddress()` k `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="a3483-125">Add a static method called `FindCalculatorServiceAddress()` to the `Program` class.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
    }  
    ```  
  
     <span data-ttu-id="a3483-126">Tato metoda zjišťování používá pro vyhledávání `CalculatorService` služby.</span><span class="sxs-lookup"><span data-stu-id="a3483-126">This method uses discovery to search for the `CalculatorService` service.</span></span>  
  
7.  <span data-ttu-id="a3483-127">Uvnitř `FindCalculatorServiceAddress` metoda, vytvořte novou <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, předávání v <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="a3483-127">Inside the `FindCalculatorServiceAddress` method, create a new <xref:System.ServiceModel.Discovery.DiscoveryClient> instance, passing in a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> to the constructor.</span></span>  
  
    ```csharp  
    static EndpointAddress FindCalculatorServiceAddress()  
    {  
        // Create DiscoveryClient  
        DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
    }  
    ```  
  
     <span data-ttu-id="a3483-128">Tato hodnota informuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , <xref:System.ServiceModel.Discovery.DiscoveryClient> třída by měl použít standardní koncový bod zjišťování UDP odesílat a přijímat zprávy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="a3483-128">This tells [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] that the <xref:System.ServiceModel.Discovery.DiscoveryClient> class should use the standard UDP discovery endpoint to send and receive discovery messages.</span></span>  
  
8.  <span data-ttu-id="a3483-129">Na další řádek volání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> metoda a zadejte <xref:System.ServiceModel.Discovery.FindCriteria> instanci, která obsahuje kontrakt služby, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="a3483-129">On the next line, call the <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method and specify a <xref:System.ServiceModel.Discovery.FindCriteria> instance that contains the service contract you want to search for.</span></span> <span data-ttu-id="a3483-130">V takovém případě zadejte `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="a3483-130">In this case, specify `ICalculator`.</span></span>  
  
    ```csharp  
    // Find ICalculatorService endpoints              
    FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculator)));  
    ```  
  
9. <span data-ttu-id="a3483-131">Po zavolání <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, zkontrolujte, zda existuje alespoň jedna služba odpovídající a vrátit <xref:System.ServiceModel.EndpointAddress> první odpovídající služby.</span><span class="sxs-lookup"><span data-stu-id="a3483-131">After the call to <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>, check to see if there is at least one matching service and return the <xref:System.ServiceModel.EndpointAddress> of the first matching service.</span></span> <span data-ttu-id="a3483-132">V opačném případě vrátí `null`.</span><span class="sxs-lookup"><span data-stu-id="a3483-132">Otherwise return `null`.</span></span>  
  
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
  
10. <span data-ttu-id="a3483-133">Přidat statickou metodu s názvem `InvokeCalculatorService` k `Program` třídy.</span><span class="sxs-lookup"><span data-stu-id="a3483-133">Add a static method named `InvokeCalculatorService` to the `Program` class.</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
    }  
    ```  
  
     <span data-ttu-id="a3483-134">Tato metoda používá adresa koncového bodu, kterou vrátil `FindCalculatorServiceAddress` volat službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a3483-134">This method uses the endpoint address returned from `FindCalculatorServiceAddress` to call the calculator service.</span></span>  
  
11. <span data-ttu-id="a3483-135">Uvnitř `InvokeCalculatorService` metody vytvoření instance `CalculatorServiceClient` třídy.</span><span class="sxs-lookup"><span data-stu-id="a3483-135">Inside the `InvokeCalculatorService` method, create an instance of the `CalculatorServiceClient` class.</span></span> <span data-ttu-id="a3483-136">Tato třída je definována [hostování na vlastním](http://go.microsoft.com/fwlink/?LinkId=145523) ukázka.</span><span class="sxs-lookup"><span data-stu-id="a3483-136">This class is defined by the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample.</span></span> <span data-ttu-id="a3483-137">Byly vygenerovány pomocí Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="a3483-137">It was generated using Svcutil.exe.</span></span>  
  
    ```csharp  
    // Create a client  
    CalculatorClient client = new CalculatorClient();  
    ```  
  
12. <span data-ttu-id="a3483-138">Na další řádek nastavena adresa koncového bodu klienta adresa koncového bodu vrácená z `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="a3483-138">On the next line, set the endpoint address of the client to the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    // Connect to the discovered service endpoint  
    client.Endpoint.Address = endpointAddress;  
    ```  
  
13. <span data-ttu-id="a3483-139">Ihned po kód v předchozím kroku volání metod vystavené službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a3483-139">Immediately after the code for the previous step, call the methods exposed by the calculator service.</span></span>  
  
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
  
14. <span data-ttu-id="a3483-140">Přidejte kód, který `Main()` metoda v `Program` třída volat `FindCalculatorServiceAddress`.</span><span class="sxs-lookup"><span data-stu-id="a3483-140">Add code to the `Main()` method in the `Program` class to call `FindCalculatorServiceAddress`.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        EndpointAddress endpointAddress = FindCalculatorServiceAddress();  
    }  
    ```  
  
15. <span data-ttu-id="a3483-141">Na další řádek volání `InvokeCalculatorService()` a předat adresa koncového bodu vrácená z `FindCalculatorServiceAddress()`.</span><span class="sxs-lookup"><span data-stu-id="a3483-141">On the next line, call the `InvokeCalculatorService()` and pass in the endpoint address returned from `FindCalculatorServiceAddress()`.</span></span>  
  
    ```csharp  
    if (endpointAddress != null)  
    {  
        InvokeCalculatorService(endpointAddress);  
    }  
  
    Console.WriteLine("Press <ENTER> to exit.");  
    Console.ReadLine();  
    ```  
  
### <a name="to-test-the-application"></a><span data-ttu-id="a3483-142">Testování aplikace</span><span class="sxs-lookup"><span data-stu-id="a3483-142">To test the application</span></span>  
  
1.  <span data-ttu-id="a3483-143">Otevřete příkazový řádek se zvýšenými oprávněními a spusťte Service.exe.</span><span class="sxs-lookup"><span data-stu-id="a3483-143">Open an elevated command prompt and run Service.exe.</span></span>  
  
2.  <span data-ttu-id="a3483-144">Otevřete příkazový řádek a spusťte Discoveryclientapp.exe.</span><span class="sxs-lookup"><span data-stu-id="a3483-144">Open a command prompt and run Discoveryclientapp.exe.</span></span>  
  
3.  <span data-ttu-id="a3483-145">Výstup z service.exe by měl vypadat jako následující výstup.</span><span class="sxs-lookup"><span data-stu-id="a3483-145">The output from service.exe should look like the following output.</span></span>  
  
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
  
4.  <span data-ttu-id="a3483-146">Výstup z Discoveryclientapp.exe by měl vypadat jako následující výstup.</span><span class="sxs-lookup"><span data-stu-id="a3483-146">The output from Discoveryclientapp.exe should look like the following output.</span></span>  
  
    ```Output  
    Invoking CalculatorService at http://localhost:8000/ServiceModelSamples/service  
    Add(100,15.99) = 115.99  
    Subtract(100,15.99) = 84.01  
    Multiply(100,15.99) = 1599  
    Divide(100,15.99) = 6.25390869293308  
  
    Press <ENTER> to exit.  
    ```  
  
## <a name="example"></a><span data-ttu-id="a3483-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3483-147">Example</span></span>  
 <span data-ttu-id="a3483-148">Následuje seznam kód pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="a3483-148">The following is a listing of the code for this sample.</span></span> <span data-ttu-id="a3483-149">Vzhledem k tomu, že je na základě tohoto kódu [hostování na vlastním](http://go.microsoft.com/fwlink/?LinkId=145523) ukázku, jsou uvedeny pouze soubory, které se změnily.</span><span class="sxs-lookup"><span data-stu-id="a3483-149">Because this code is based on the [Self-Host](http://go.microsoft.com/fwlink/?LinkId=145523) sample, only those files that are changed are listed.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="a3483-150">Ukázka hostování na vlastním serveru, najdete v části [pokyny k instalaci](http://go.microsoft.com/fwlink/?LinkId=145522).</span><span class="sxs-lookup"><span data-stu-id="a3483-150"> the Self-Host sample, see [Setup Instructions](http://go.microsoft.com/fwlink/?LinkId=145522).</span></span>  
  
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

## <a name="see-also"></a><span data-ttu-id="a3483-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3483-151">See Also</span></span>  
 [<span data-ttu-id="a3483-152">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="a3483-152">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="a3483-153">Objektový Model zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="a3483-153">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)
