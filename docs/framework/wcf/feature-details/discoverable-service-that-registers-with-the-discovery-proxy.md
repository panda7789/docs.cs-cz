---
title: 'Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování'
ms.date: 03/30/2017
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
ms.openlocfilehash: 31c89aeed2577c5dd11ae59ee4a4d692210e5f37
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856489"
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a><span data-ttu-id="9392a-102">Postupy: Implementace zjistitelné služby, která se registruje pomocí proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="9392a-102">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>
<span data-ttu-id="9392a-103">Toto téma je druhý čtyři témat, která popisuje, jak implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="9392a-103">This topic is the second of four topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="9392a-104">V předchozím tématu [jak: Implementace zjišťování Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), jste implementovali proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="9392a-104">In the previous topic, [How to: Implement a Discovery Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), you implemented a discovery proxy.</span></span> <span data-ttu-id="9392a-105">V tomto tématu vytvoříte službu WCF, která odesílá zprávy oznámení (`Hello` a `Bye`) na server proxy zjišťování by ji chcete registrovat a deregistrovat pomocí proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="9392a-105">In this topic, you create a WCF service that sends announcement messages (`Hello` and `Bye`) to the discovery proxy, causing it to register and unregister itself with the discovery proxy.</span></span>

### <a name="to-define-the-service-contract"></a><span data-ttu-id="9392a-106">K definování kontraktu služby</span><span class="sxs-lookup"><span data-stu-id="9392a-106">To define the service contract</span></span>

1. <span data-ttu-id="9392a-107">Přidat nový projekt konzolové aplikace na `DiscoveryProxyExample` řešení `Service`.</span><span class="sxs-lookup"><span data-stu-id="9392a-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Service`.</span></span>

2. <span data-ttu-id="9392a-108">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="9392a-108">Add references to the following assemblies:</span></span>

    1. <span data-ttu-id="9392a-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9392a-109">System.ServiceModel</span></span>

    2. <span data-ttu-id="9392a-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="9392a-110">System.ServiceModel.Discovery</span></span>

3. <span data-ttu-id="9392a-111">Přidejte novou třídu projektu s názvem `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="9392a-111">Add a new class to the project called `CalculatorService`.</span></span>

4. <span data-ttu-id="9392a-112">Přidejte následující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="9392a-112">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    ```

5. <span data-ttu-id="9392a-113">V rámci CalculatorService.cs definování kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="9392a-113">Within CalculatorService.cs, define the service contract.</span></span>

    ```csharp
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }
    ```

6. <span data-ttu-id="9392a-114">Také v rámci CalculatorService.cs, implementace kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="9392a-114">Also within CalculatorService.cs, implement the service contract.</span></span>

    ```csharp
    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
    ```

### <a name="to-host-the-service"></a><span data-ttu-id="9392a-115">K hostování služby</span><span class="sxs-lookup"><span data-stu-id="9392a-115">To host the service</span></span>

1. <span data-ttu-id="9392a-116">Otevřete soubor Program.cs, který byl vygenerován při vytváření projektu.</span><span class="sxs-lookup"><span data-stu-id="9392a-116">Open the Program.cs file that was generated when you created the project.</span></span>

2. <span data-ttu-id="9392a-117">Přidejte následující příkazy using.</span><span class="sxs-lookup"><span data-stu-id="9392a-117">Add the following using statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="9392a-118">V rámci `Main()` metodu, přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9392a-118">Within the `Main()` method, add the following code:</span></span>

    ```csharp
    // Define the base address of the service
    Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
    // Define the endpoint address where announcement messages will be sent
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Create the service host
    ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
    try
    {
        // Add a service endpoint
        ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
            new NetTcpBinding(), string.Empty);

        // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
            new EndpointAddress(announcementEndpointAddress));

        // Create a ServiceDiscoveryBehavior and add the announcement endpoint
        ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
        serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

        // Add the ServiceDiscoveryBehavior to the service host to make the service discoverable
        serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

        // Start listening for messages
        serviceHost.Open();

        Console.WriteLine("Calculator Service started at {0}", baseAddress);
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        serviceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (serviceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        serviceHost.Abort();
    }
    ```

<span data-ttu-id="9392a-119">Dokončili jste implementace zjistitelné služby.</span><span class="sxs-lookup"><span data-stu-id="9392a-119">You have completed implementing a discoverable service.</span></span> <span data-ttu-id="9392a-120">Pokračovat k [jak: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="9392a-120">Continue on to [How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).</span></span>

## <a name="example"></a><span data-ttu-id="9392a-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="9392a-121">Example</span></span>
 <span data-ttu-id="9392a-122">Toto je úplný přehled kód použitý v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="9392a-122">This is the full listing of the code used in this topic.</span></span>

```csharp
// CalculatorService.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;

namespace Microsoft.Samples.Discovery
{
    // Define a service contract.
    [ServiceContract(Namespace = "http://Microsoft.Samples.Discovery")]
    public interface ICalculatorService
    {
        [OperationContract]
        double Add(double n1, double n2);
        [OperationContract]
        double Subtract(double n1, double n2);
        [OperationContract]
        double Multiply(double n1, double n2);
        [OperationContract]
        double Divide(double n1, double n2);
    }

    // Service class which implements the service contract.
    public class CalculatorService : ICalculatorService
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
  
        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

```csharp
// Program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Description;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri baseAddress = new Uri("net.tcp://localhost:9002/CalculatorService/" + Guid.NewGuid().ToString());
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress);
            try
            {
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService),
                    new NetTcpBinding(), string.Empty);

                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(),
                    new EndpointAddress(announcementEndpointAddress));

                ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
                serviceDiscoveryBehavior.AnnouncementEndpoints.Add(announcementEndpoint);

                // Make the service discoverable
                serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);

                serviceHost.Open();

                Console.WriteLine("Calculator Service started at {0}", baseAddress);
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                serviceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (serviceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                serviceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="9392a-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9392a-123">See also</span></span>

- [<span data-ttu-id="9392a-124">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="9392a-124">WCF Discovery</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [<span data-ttu-id="9392a-125">Postupy: Implementace Proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="9392a-125">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="9392a-126">Postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="9392a-126">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
