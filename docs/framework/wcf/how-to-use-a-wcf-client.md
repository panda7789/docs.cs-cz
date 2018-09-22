---
title: 'Postupy: Používání klienta Windows Communication Foundation'
ms.date: 09/14/2018
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 12e911fb899cb85121c129b762828cdda01e64f1
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580210"
---
# <a name="how-to-use-a-windows-communication-foundation-client"></a><span data-ttu-id="1a4a4-102">Postupy: Používání klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1a4a4-102">How to: Use a Windows Communication Foundation Client</span></span>

<span data-ttu-id="1a4a4-103">Toto je poslední z šesti úkolů, muset vytvořit základní aplikaci Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1a4a4-103">This is the last of six tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="1a4a4-104">Přehled všech šesti úkoly, naleznete v tématu [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="1a4a4-105">Jakmile se proxy server služby Windows Communication Foundation (WCF) bylo vytvořeno a nakonfigurováno, lze vytvořit instanci klienta a klientská aplikace může být sestaven a používaný ke komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-105">Once a Windows Communication Foundation (WCF) proxy has been created and configured, a client instance can be created and the client application can be compiled and used to communicate with the WCF service.</span></span> <span data-ttu-id="1a4a4-106">Toto téma popisuje postupy pro vytvoření instance a pomocí klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-106">This topic describes procedures for instantiating and using a WCF client.</span></span> <span data-ttu-id="1a4a4-107">Tato procedura dělá tři věci:</span><span class="sxs-lookup"><span data-stu-id="1a4a4-107">This procedure does three things:</span></span>

1.  <span data-ttu-id="1a4a4-108">Vytvoří instanci klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-108">Instantiates a WCF client.</span></span>

2.  <span data-ttu-id="1a4a4-109">Volání operace služby od vygenerovaný proxy server.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-109">Calls the service operations from the generated proxy.</span></span>

3.  <span data-ttu-id="1a4a4-110">Klient se zavře po dokončení volání operace.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-110">Closes the client once the operation call is completed.</span></span>

## <a name="use-a-windows-communication-foundation-client"></a><span data-ttu-id="1a4a4-111">Používání klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="1a4a4-111">Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="1a4a4-112">Otevřete soubor Program.cs nebo soubor Program.vb z projektu GettingStartedClient a nahraďte existující kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="1a4a4-112">Open the Program.cs or Program.vb file from the GettingStartedClient project and replace the existing code with the following code:</span></span>

```csharp
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

```vb
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

<span data-ttu-id="1a4a4-113">Všimněte si, že `using` nebo `Imports` příkaz, který importuje `GettingStartedClient.ServiceReference1`.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-113">Notice the `using` or `Imports` statement that imports the `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="1a4a4-114">Tento postup importuje kód vygenerovaný **přidat odkaz na službu** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-114">This imports the code generated by **Add Service Reference** in Visual Studio.</span></span> <span data-ttu-id="1a4a4-115">Kód vytvoří instanci WCF proxy a pak volá všechny operace služby, vystavený službou kalkulačky, zavře server proxy a ukončí.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-115">The code instantiates the WCF proxy and then calls each of the service operations exposed by the calculator service, closes the proxy, and terminates.</span></span>

<span data-ttu-id="1a4a4-116">Teď jste dokončili kurz.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-116">You have now completed the tutorial.</span></span> <span data-ttu-id="1a4a4-117">Definice kontraktu služby, implementovat kontrakt služby, vygeneruje WCF proxy, nakonfigurovat klientskou aplikaci WCF a poté použít proxy server k volání operací služby.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-117">You defined a service contract, implemented the service contract, generated a WCF proxy, configured a WCF client application, and then used the proxy to call service operations.</span></span> <span data-ttu-id="1a4a4-118">K otestování aplikace, nejprve spusťte GettingStartedHost spusťte službu a pak spusťte GettingStartedClient.</span><span class="sxs-lookup"><span data-stu-id="1a4a4-118">To test out the application, first run GettingStartedHost to start the service and then run GettingStartedClient.</span></span>

<span data-ttu-id="1a4a4-119">Výstup z GettingStartedHost by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1a4a4-119">The output from GettingStartedHost should look like this:</span></span>

```text
The service is ready.Press <ENTER> to terminate service.Received Add(100,15.99)Return: 115.99Received Subtract(145,76.54)Return: 68.46Received Multiply(9,81.25)Return: 731.25Received Divide(22,7)Return: 3.14285714285714
```

<span data-ttu-id="1a4a4-120">Výstup z GettingStartedClient by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="1a4a4-120">The output from GettingStartedClient should look like this:</span></span>

```text
Add(100,15.99) = 115.99Subtract(145,76.54) = 68.46Multiply(9,81.25) = 731.25Divide(22,7) = 3.14285714285714Press <ENTER> to terminate client.
```

## <a name="see-also"></a><span data-ttu-id="1a4a4-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a4a4-121">See also</span></span>

- [<span data-ttu-id="1a4a4-122">Sestavování klientů</span><span class="sxs-lookup"><span data-stu-id="1a4a4-122">Building Clients</span></span>](../../../docs/framework/wcf/building-clients.md)
- [<span data-ttu-id="1a4a4-123">Postupy: Vytvoření klienta</span><span class="sxs-lookup"><span data-stu-id="1a4a4-123">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="1a4a4-124">Kurz Začínáme</span><span class="sxs-lookup"><span data-stu-id="1a4a4-124">Getting Started Tutorial</span></span>](../../../docs/framework/wcf/getting-started-tutorial.md)
- [<span data-ttu-id="1a4a4-125">Základní programování WCF</span><span class="sxs-lookup"><span data-stu-id="1a4a4-125">Basic WCF Programming</span></span>](../../../docs/framework/wcf/basic-wcf-programming.md)
- [<span data-ttu-id="1a4a4-126">Postupy: Vytvoření duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="1a4a4-126">How to: Create a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [<span data-ttu-id="1a4a4-127">Postupy: Přístup ke službám pomocí duplexního kontraktu</span><span class="sxs-lookup"><span data-stu-id="1a4a4-127">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="1a4a4-128">Začínáme</span><span class="sxs-lookup"><span data-stu-id="1a4a4-128">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="1a4a4-129">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="1a4a4-129">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)