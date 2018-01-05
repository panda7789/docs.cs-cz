---
title: "Postupy: Používání klienta Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF clients [WCF], using
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0330c386730c6b0436196bb5b85162bc4621c214
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="723a8-102">Postupy: Používání klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="723a8-102">How to: Use a Windows Communication Foundation Client</span></span>
<span data-ttu-id="723a8-103">Toto je poslední šesti úkoly vyžadované pro vytvoření základní [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="723a8-103">This is the last of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="723a8-104">Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="723a8-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="723a8-105">Jednou [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy serveru bylo vytvořeno a nakonfigurováno, lze vytvořit instanci klienta a klientské aplikace můžete zkompilovat a použít ke komunikaci s [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="723a8-105">Once a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] proxy has been created and configured, a client instance can be created and the client application can be compiled and used to communicate with the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="723a8-106">Toto téma popisuje postupy pro vytváření instancí a použití [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="723a8-106">This topic describes procedures for instantiating and using a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span> <span data-ttu-id="723a8-107">Tento postup provádí tři věci:</span><span class="sxs-lookup"><span data-stu-id="723a8-107">This procedure does three things:</span></span>  
  
1.  <span data-ttu-id="723a8-108">Vytvoří [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="723a8-108">Instantiates a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] client.</span></span>  
  
2.  <span data-ttu-id="723a8-109">Volání operace služby ze vygenerovaný proxy server.</span><span class="sxs-lookup"><span data-stu-id="723a8-109">Calls the service operations from the generated proxy.</span></span>  
  
3.  <span data-ttu-id="723a8-110">Po dokončení volání operace se ukončí klienta.</span><span class="sxs-lookup"><span data-stu-id="723a8-110">Closes the client once the operation call is completed.</span></span>  
  
### <a name="to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="723a8-111">Chcete-li použít klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="723a8-111">To use a Windows Communication Foundation client</span></span>  
  
1.  <span data-ttu-id="723a8-112">Otevřete soubor Program.cs nebo soubor Program.vb z projektu GettingStartedClient a existujícího kódu nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="723a8-112">Open the Program.cs or Program.vb file from the GettingStartedClient project and replace the existing code with the following code:</span></span>  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using GettingStartedClient.ServiceReference1;  
  
    namespace GettingStartedClient  
    {  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                //Step 1: Create an instance of the WCF proxy.  
                CalculatorClient client = new CalculatorClient();  
  
                // Step 2: Call the service operations.  
                // Call the Add service operation.  
                double value1 = 100.00D;  
                double value2 = 15.99D;  
                double result = client.Add(value1, value2);  
                Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Subtract service operation.  
                value1 = 145.00D;  
                value2 = 76.54D;  
                result = client.Subtract(value1, value2);  
                Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Multiply service operation.  
                value1 = 9.00D;  
                value2 = 81.25D;  
                result = client.Multiply(value1, value2);  
                Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
                // Call the Divide service operation.  
                value1 = 22.00D;  
                value2 = 7.00D;  
                result = client.Divide(value1, value2);  
                Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
                //Step 3: Closing the client gracefully closes the connection and cleans up resources.  
                client.Close();  
            }  
        }  
    }  
    ```  
  
    ```  
    Imports System  
    Imports System.Collections.Generic  
    Imports System.Text  
    Imports System.ServiceModel  
    Imports GettingStartedClientVB2.ServiceReference1  
  
    Module Module1  
  
        Sub Main()  
            ' Step 1: Create an instance of the WCF proxy  
            Dim Client As New CalculatorClient()  
  
            'Step 2: Call the service operations.  
            'Call the Add service operation.  
            Dim value1 As Double = 100D  
            Dim value2 As Double = 15.99D  
            Dim result As Double = Client.Add(value1, value2)  
            Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Subtract service operation.  
            value1 = 145D  
            value2 = 76.54D  
            result = Client.Subtract(value1, value2)  
            Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Multiply service operation.  
            value1 = 9D  
            value2 = 81.25D  
            result = Client.Multiply(value1, value2)  
            Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)  
  
            'Call the Divide service operation.  
            value1 = 22D  
            value2 = 7D  
            result = Client.Divide(value1, value2)  
            Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)  
  
            ' Step 3: Closing the client gracefully closes the connection and cleans up resources.  
            Client.Close()  
  
            Console.WriteLine()  
            Console.WriteLine("Press <ENTER> to terminate client.")  
            Console.ReadLine()  
  
        End Sub  
  
    End Module  
    ```  
  
     <span data-ttu-id="723a8-113">Všimněte si pomocí nebo importuje příkaz, který importuje GettingStartedClient.ServiceReference1.</span><span class="sxs-lookup"><span data-stu-id="723a8-113">Notice the using or imports statement that imports the GettingStartedClient.ServiceReference1.</span></span> <span data-ttu-id="723a8-114">To importuje kód vygenerovaný přidat odkaz na službu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="723a8-114">This imports the code generated by Add Service Reference in Visual Studio.</span></span> <span data-ttu-id="723a8-115">Kód vytvoří WCF proxy a potom volá všechny operace služby, které jsou vystavené službu kalkulačky, zavře proxy serveru a ukončí.</span><span class="sxs-lookup"><span data-stu-id="723a8-115">The code instantiates the WCF proxy and then calls each of the service operations exposed by the calculator service, closes the proxy and terminates.</span></span>  
  
 <span data-ttu-id="723a8-116">Teď jste dokončili kurz.</span><span class="sxs-lookup"><span data-stu-id="723a8-116">You have now completed the tutorial.</span></span> <span data-ttu-id="723a8-117">Definované kontraktu služby, implementována kontrakt služby, generuje proxy server WCF, nakonfigurovat klientskou aplikaci WCF a pak použít proxy server k volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="723a8-117">You defined a service contract, implemented the service contract, generated a WCF proxy, configured a WCF client application, and then used the proxy to call service operations.</span></span> <span data-ttu-id="723a8-118">K otestování aplikace nejprve spusťte GettingStartedHost spusťte službu a pak spusťte GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="723a8-118">To test out the application first run GettingStartedHost to start the service and then run GettingStartedClient.</span></span> <span data-ttu-id="723a8-119">Výstup z GettingStartedHost by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="723a8-119">The output from GettingStartedHost should look like this:</span></span>  
  
```Output  
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714  
```  
  
 <span data-ttu-id="723a8-120">Výstup z GettingStartedClient by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="723a8-120">The output from GettingStartedClient should look like this:</span></span>  
  
```Output  
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.  
```  
  
## <a name="see-also"></a><span data-ttu-id="723a8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="723a8-121">See Also</span></span>  
 [<span data-ttu-id="723a8-122">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="723a8-122">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)  
 [<span data-ttu-id="723a8-123">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="723a8-123">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 [<span data-ttu-id="723a8-124">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="723a8-124">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)  
 [<span data-ttu-id="723a8-125">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="723a8-125">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)  
 [<span data-ttu-id="723a8-126">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="723a8-126">How to: Create a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)  
 [<span data-ttu-id="723a8-127">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="723a8-127">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)  
 [<span data-ttu-id="723a8-128">Začínáme</span><span class="sxs-lookup"><span data-stu-id="723a8-128">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="723a8-129">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="723a8-129">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
