---
title: 'Kurz: Použití klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c280933c81ef54ba58181e3005e30775b9b8e42
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928890"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="ec273-102">Kurz: Použití klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ec273-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="ec273-103">Tento kurz popisuje posledních pět úloh potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ec273-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="ec273-104">Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="ec273-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="ec273-105">Poté, co vytvoříte a nakonfigurujete proxy server Windows Communication Foundation (WCF), vytvoříte instanci klienta a zkompilujete klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec273-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="ec273-106">Pak ho použijete ke komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="ec273-106">You then use it to communicate with the WCF service.</span></span> 

<span data-ttu-id="ec273-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="ec273-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ec273-108">Přidejte kód pro použití klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="ec273-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="ec273-109">Otestujte klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="ec273-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="ec273-110">Přidání kódu pro použití klienta WCF</span><span class="sxs-lookup"><span data-stu-id="ec273-110">Add code to use the WCF client</span></span>

<span data-ttu-id="ec273-111">Klientský kód provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="ec273-111">The client code does the following steps:</span></span>

- <span data-ttu-id="ec273-112">Vytvoří instanci klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="ec273-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="ec273-113">Zavolá operace služby z vygenerovaného proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="ec273-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="ec273-114">Ukončí klienta po dokončení volání operace.</span><span class="sxs-lookup"><span data-stu-id="ec273-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="ec273-115">Otevřete soubor **program.cs** nebo **Module1. vb** z projektu **GettingStartedClient** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="ec273-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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

            // Step 3: Close the client to gracefully close the connection and clean up resources.
            Console.WriteLine("\nPress <Enter> to terminate the client.");
            Console.ReadLine();
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
Imports GettingStartedClient.ServiceReference1

Module Module1

    Sub Main()
        ' Step 1: Create an instance of the WCF proxy.
        Dim Client As New CalculatorClient()

        ' Step 2: Call the service operations.
        ' Call the Add service operation.
        Dim value1 As Double = 100D
        Dim value2 As Double = 15.99D
        Dim result As Double = Client.Add(value1, value2)
        Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

        ' Call the Subtract service operation.
        value1 = 145D
        value2 = 76.54D
        result = Client.Subtract(value1, value2)
        Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

        ' Call the Multiply service operation.
        value1 = 9D
        value2 = 81.25D
        result = Client.Multiply(value1, value2)
        Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

        ' Call the Divide service operation.
        value1 = 22D
        value2 = 7D
        result = Client.Divide(value1, value2)
        Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

        ' Step 3: Close the client to gracefully close the connection and clean up resources.
        Console.WriteLine()
        Console.WriteLine("Press <Enter> to terminate the client.")
        Console.ReadLine()
        Client.Close()

    End Sub

End Module
```

<span data-ttu-id="ec273-116">Všimněte si příkazu C# `Imports` `GettingStartedClient.ServiceReference1`(for Visual) nebo (for Visual Basic), který importuje. `using`</span><span class="sxs-lookup"><span data-stu-id="ec273-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="ec273-117">Tento příkaz importuje kód, který aplikace Visual Studio vygenerovala pomocí funkce **Přidat odkaz na službu** .</span><span class="sxs-lookup"><span data-stu-id="ec273-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="ec273-118">Kód vytvoří instanci proxy serveru WCF a zavolá každou operaci služby, kterou služba kalkulačky zpřístupňuje.</span><span class="sxs-lookup"><span data-stu-id="ec273-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="ec273-119">Pak zavře proxy a ukončí program.</span><span class="sxs-lookup"><span data-stu-id="ec273-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="ec273-120">Testování klienta WCF</span><span class="sxs-lookup"><span data-stu-id="ec273-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="ec273-121">Testování aplikace ze sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ec273-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="ec273-122">Uložte a sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="ec273-122">Save and build the solution.</span></span>

2. <span data-ttu-id="ec273-123">Vyberte složku **GettingStartedLib** a pak v místní nabídce vyberte **nastavit jako spouštěný projekt** .</span><span class="sxs-lookup"><span data-stu-id="ec273-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="ec273-124">Z nabídky **projekty po spuštění**vyberte v rozevíracím seznamu položku **GettingStartedLib** a pak vyberte **Spustit** nebo stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="ec273-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="ec273-125">Otestování aplikace z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ec273-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="ec273-126">Otevřete příkazový řádek jako správce a pak přejděte do adresáře řešení Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ec273-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span> 

2. <span data-ttu-id="ec273-127">Spuštění služby: Zadejte *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span><span class="sxs-lookup"><span data-stu-id="ec273-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="ec273-128">Spuštění klienta: Otevřete jiný příkazový řádek, přejděte do adresáře řešení Visual Studio a pak zadejte *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="ec273-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="ec273-129">*GettingStartedHost. exe* vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ec273-129">*GettingStartedHost.exe* produces the following output:</span></span>

   ```text
   The service is ready.
   Press <Enter> to terminate the service.

   Received Add(100,15.99)
   Return: 115.99
   Received Subtract(145,76.54)
   Return: 68.46
   Received Multiply(9,81.25)
   Return: 731.25
   Received Divide(22,7)
   Return: 3.14285714285714
   ```

   <span data-ttu-id="ec273-130">*GettingStartedClient. exe* vytvoří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="ec273-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="ec273-131">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ec273-131">Next steps</span></span>

<span data-ttu-id="ec273-132">Nyní jste dokončili všechny úkoly v kurzu Začínáme WCF.</span><span class="sxs-lookup"><span data-stu-id="ec273-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="ec273-133">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="ec273-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="ec273-134">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="ec273-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="ec273-135">Přidejte kód pro použití klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="ec273-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="ec273-136">Otestujte klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="ec273-136">Test the WCF client.</span></span>

<span data-ttu-id="ec273-137">Pokud máte v některém z kroků problémy nebo chyby, opravte je podle kroků v článku věnovaném řešení potíží.</span><span class="sxs-lookup"><span data-stu-id="ec273-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ec273-138">Řešení potíží s kurzy Začínáme s WCF</span><span class="sxs-lookup"><span data-stu-id="ec273-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
