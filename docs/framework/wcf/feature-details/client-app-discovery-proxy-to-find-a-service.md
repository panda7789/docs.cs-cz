---
title: 'Postupy: Implementace klientské aplikace používající zjišťování proxy k vyhledání služby'
ms.date: 03/30/2017
ms.assetid: 62b41a75-cf40-4c52-a842-a5f1c70e247f
ms.openlocfilehash: 12b3fa03a1f259df8ee8c970463fa9ccee7267fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320993"
---
# <a name="how-to-implement-a-client-application-that-uses-the-discovery-proxy-to-find-a-service"></a><span data-ttu-id="7244c-102">Postupy: Implementace klientské aplikace používající zjišťování proxy k vyhledání služby</span><span class="sxs-lookup"><span data-stu-id="7244c-102">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>
<span data-ttu-id="7244c-103">Toto téma je třetí webinář tři témat, která popisuje, jak implementace zjišťování proxy.</span><span class="sxs-lookup"><span data-stu-id="7244c-103">This topic is the third of three topics that discusses how to implement a discovery proxy.</span></span> <span data-ttu-id="7244c-104">V předchozím tématu [jak: Implementace zjistitelné služby, která se registruje pomocí Proxy zjišťování](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md), implementovat službu WCF, která se zaregistruje pomocí proxy zjišťování.</span><span class="sxs-lookup"><span data-stu-id="7244c-104">In the previous topic, [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md), you implemented a WCF service that registers itself with the discovery proxy.</span></span> <span data-ttu-id="7244c-105">V tomto tématu vytvořte klienta WCF používající zjišťování proxy k vyhledání služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="7244c-105">In this topic you create a WCF client that uses the discovery proxy to find the WCF service.</span></span>  
  
### <a name="implement-the-client"></a><span data-ttu-id="7244c-106">Implementace klienta</span><span class="sxs-lookup"><span data-stu-id="7244c-106">Implement the client</span></span>  
  
1. <span data-ttu-id="7244c-107">Přidat nový projekt konzolové aplikace na `DiscoveryProxyExample` řešení `Client`.</span><span class="sxs-lookup"><span data-stu-id="7244c-107">Add a new console application project to the `DiscoveryProxyExample` solution called `Client`.</span></span>  
  
2. <span data-ttu-id="7244c-108">Přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="7244c-108">Add references to the following assemblies:</span></span>  
  
    1.  <span data-ttu-id="7244c-109">System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7244c-109">System.ServiceModel</span></span>  
  
    2.  <span data-ttu-id="7244c-110">System.ServiceModel.Discovery</span><span class="sxs-lookup"><span data-stu-id="7244c-110">System.ServiceModel.Discovery</span></span>  
  
3. <span data-ttu-id="7244c-111">Přidáte GeneratedClient.cs nalezen na konci tohoto tématu do projektu.</span><span class="sxs-lookup"><span data-stu-id="7244c-111">Add the GeneratedClient.cs found at the bottom of this topic to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7244c-112">Tento soubor je obvykle vytvořen pomocí nástroje, jako je například Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="7244c-112">This file is usually generated using a tool such as Svcutil.exe.</span></span> <span data-ttu-id="7244c-113">Je zadaná v tomto tématu můžete zjednodušit úlohy.</span><span class="sxs-lookup"><span data-stu-id="7244c-113">It is provided in this topic to simplify the task.</span></span>  
  
4. <span data-ttu-id="7244c-114">Otevřete soubor Program.cs a přidejte následující metodu.</span><span class="sxs-lookup"><span data-stu-id="7244c-114">Open the Program.cs file and add the following method.</span></span> <span data-ttu-id="7244c-115">Tato metoda přebírá adresu koncového bodu a použije ho k inicializaci služby klienta (proxy).</span><span class="sxs-lookup"><span data-stu-id="7244c-115">This method takes an endpoint address and uses it to initialize the service client (proxy).</span></span>  
  
    ```csharp  
    static void InvokeCalculatorService(EndpointAddress endpointAddress)  
    {  
        // Create a client  
        CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
        Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
        Console.WriteLine();  

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

        // Closing the client gracefully closes the connection and cleans up resources  
        client.Close();  
    }  
    ```  
  
5. <span data-ttu-id="7244c-116">Přidejte následující kód, který `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="7244c-116">Add the following code to the `Main` method.</span></span>  
  
    ```csharp  
    public static void Main()  
    {  
        // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
        Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  

        // Create a DiscoveryClient passing in the discovery endpoint  
        DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  

        Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
        Console.WriteLine();  

        try  
        {  
            // Search for services that implement ICalculatorService              
            FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  

            Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
            Console.WriteLine();  

            // Check to see if endpoints were found, if so then invoke the service.  
            if (findResponse.Endpoints.Count > 0)  
            {  
                InvokeCalculatorService(findResponse.Endpoints[0].Address);  
            }  
        }  
        catch (TargetInvocationException)  
        {  
            Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
        }  

        Console.WriteLine("Press <ENTER> to exit.");  
        Console.ReadLine();  
    }  
    ```  
  
 <span data-ttu-id="7244c-117">Dokončili jste implementace klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="7244c-117">You have completed implementing the client application.</span></span> <span data-ttu-id="7244c-118">Pokračovat k [jak: Test Proxy zjišťování](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="7244c-118">Continue on to [How to: Test the Discovery Proxy](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7244c-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="7244c-119">Example</span></span>  
 <span data-ttu-id="7244c-120">Toto je úplný výpis pro toto téma kódu.</span><span class="sxs-lookup"><span data-stu-id="7244c-120">This is the full code listing for this topic.</span></span>  
  
```csharp  
// GeneratedClient.cs  
//----------------------------------------------------------------  
// Copyright (c) Microsoft Corporation.  All rights reserved.  
//----------------------------------------------------------------  
//------------------------------------------------------------------------------  
// <auto-generated>  
//     This code was generated by a tool.  
//     Runtime Version:2.0.50727.1434  
//  
//     Changes to this file may cause incorrect behavior and will be lost if  
//     the code is regenerated.  
// </auto-generated>  
//------------------------------------------------------------------------------  
  
namespace Microsoft.Samples.Discovery  
{  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    [System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.Samples.Discovery", ConfigurationName = "ICalculatorService")]  
    public interface ICalculatorService  
    {  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Add", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/AddResponse")]  
        double Add(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Subtract", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/SubtractResponse")]  
        double Subtract(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Multiply", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/MultiplyResponse")]  
        double Multiply(double n1, double n2);  
  
        [System.ServiceModel.OperationContractAttribute(ProtectionLevel = System.Net.Security.ProtectionLevel.EncryptAndSign, Action = "http://Microsoft.Samples.Discovery/ICalculatorService/Divide", ReplyAction = "http://Microsoft.Samples.Discovery/ICalculatorService/DivideResponse")]  
        double Divide(double n1, double n2);  
    }  
  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public interface ICalculatorServiceChannel : ICalculatorService, System.ServiceModel.IClientChannel  
    {  
    }  
  
    [System.Diagnostics.DebuggerStepThroughAttribute()]  
    [System.CodeDom.Compiler.GeneratedCodeAttribute("System.ServiceModel", "4.0.0.0")]  
    public partial class CalculatorServiceClient : System.ServiceModel.ClientBase<ICalculatorService>, ICalculatorService  
    {  
  
        public CalculatorServiceClient()  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName) :  
            base(endpointConfigurationName)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, string remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(string endpointConfigurationName, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(endpointConfigurationName, remoteAddress)  
        {  
        }  
  
        public CalculatorServiceClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress remoteAddress) :  
            base(binding, remoteAddress)  
        {  
        }  
  
        public double Add(double n1, double n2)  
        {  
            return base.Channel.Add(n1, n2);  
        }  
  
        public double Subtract(double n1, double n2)  
        {  
            return base.Channel.Subtract(n1, n2);  
        }  
  
        public double Multiply(double n1, double n2)  
        {  
            return base.Channel.Multiply(n1, n2);  
        }  
  
        public double Divide(double n1, double n2)  
        {  
            return base.Channel.Divide(n1, n2);  
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
using System.Reflection;  
using System.ServiceModel;  
using System.ServiceModel.Discovery;  
  
namespace Microsoft.Samples.Discovery  
{  
    class Client  
    {  
        public static void Main()  
        {  
            // Create a DiscoveryEndpoint that points to the DiscoveryProxy  
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");  
            DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));  
  
            DiscoveryClient discoveryClient = new DiscoveryClient(discoveryEndpoint);  
  
            Console.WriteLine("Finding ICalculatorService endpoints using the proxy at {0}", probeEndpointAddress);  
            Console.WriteLine();  
  
            try  
            {  
                // Find ICalculatorService endpoints              
                FindResponse findResponse = discoveryClient.Find(new FindCriteria(typeof(ICalculatorService)));  
  
                Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count);  
                Console.WriteLine();  
  
                // Check to see if endpoints were found, if so then invoke the service.  
                if (findResponse.Endpoints.Count > 0)  
                {  
                    InvokeCalculatorService(findResponse.Endpoints[0].Address);  
                }  
            }  
            catch (TargetInvocationException)  
            {  
                Console.WriteLine("This client was unable to connect to and query the proxy. Ensure that the proxy is up and running.");  
            }  
  
            Console.WriteLine("Press <ENTER> to exit.");  
            Console.ReadLine();  
        }  
  
        static void InvokeCalculatorService(EndpointAddress endpointAddress)  
        {  
            // Create a client  
            CalculatorServiceClient client = new CalculatorServiceClient(new NetTcpBinding(), endpointAddress);  
            Console.WriteLine("Invoking CalculatorService at {0}", endpointAddress.Uri);  
            Console.WriteLine();  
  
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
  
            // Closing the client gracefully closes the connection and cleans up resources  
            client.Close();  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7244c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7244c-121">See also</span></span>

- [<span data-ttu-id="7244c-122">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="7244c-122">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)
- [<span data-ttu-id="7244c-123">Postupy: Implementace Proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="7244c-123">How to: Implement a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)
- [<span data-ttu-id="7244c-124">Postupy: Implementace zjistitelné služby, která se registruje pomocí Proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="7244c-124">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)
