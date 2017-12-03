---
title: "Postupy: implementace zjistitelný služba, která zaregistruje se zjišťování Proxy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb275bc1-535b-44c8-b9f3-0b75e9aa473b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ffe4a94328d2728ca936425a58d4d641922356a0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-implement-a-discoverable-service-that-registers-with-the-discovery-proxy"></a>Postupy: implementace zjistitelný služba, která zaregistruje se zjišťování Proxy
Toto téma je druhý čtyři témata, která popisuje, jak implementace zjišťování proxy. V předchozích tématu [postupy: Implementace zjišťování Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md), implementována zjišťování proxy. V tomto tématu můžete vytvořit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba, která odesílá zprávy oznámení (`Hello` a `Bye`) na server proxy zjišťování způsobuje jeho registrace a zrušení registrace s proxy serverem zjišťování.  
  
### <a name="to-define-the-service-contract"></a>K definování kontraktu služby  
  
1.  Přidat nový projekt konzolové aplikace na `DiscoveryProxyExample` řešení volat `Service`.  
  
2.  Přidejte odkazy na následující sestavení:  
  
    1.  System.ServiceModel  
  
    2.  System.ServiceModel.Discovery  
  
3.  Přidejte novou třídu do projektu názvem `CalculatorService`.  
  
4.  Přidejte následující příkazy using.  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
5.  V rámci CalculatorService.cs definování kontraktu služby.  
  
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
  
6.  Také v rámci CalculatorService.cs, implementujte kontrakt služby.  
  
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
  
### <a name="to-host-the-service"></a>K hostování služby  
  
1.  Otevřete soubor Program.cs, který byl vygenerován při vytváření projektu.  
  
2.  Přidejte následující příkazy using.  
  
    ```csharp 
    using System;  
    using System.ServiceModel;  
    using System.ServiceModel.Description;  
    using System.ServiceModel.Discovery;  
    ```  
  
3.  V rámci `Main()` metoda, přidejte následující kód:  
  
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
       ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), string.Empty);                
  
       // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.  
       AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));  
  
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
  
 Dokončili jste implementace zjistitelný služby. Pokračujte na [postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md).  
  
## <a name="example"></a>Příklad  
 Toto je úplný seznam kód použitý v tomto tématu.  
  
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
                ServiceEndpoint netTcpEndpoint = serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new NetTcpBinding(), string.Empty);                
  
                // Create an announcement endpoint, which points to the Announcement Endpoint hosted by the proxy service.  
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));  
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

## <a name="see-also"></a>Viz také  
 [Zjišťování WCF](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)  
 [Postupy: Implementace zjišťování Proxy](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 [Postupy: Implementace klientské aplikace používající zjišťování Proxy k vyhledání služby](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)
