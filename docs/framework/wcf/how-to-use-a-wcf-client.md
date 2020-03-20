---
title: 'Kurz: Použití klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: d2357c134aef8da204dcdb19d6c1fc93cfdc068c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184015"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a><span data-ttu-id="8bc2f-102">Kurz: Použití klienta Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="8bc2f-102">Tutorial: Use a Windows Communication Foundation client</span></span>

<span data-ttu-id="8bc2f-103">Tento kurz popisuje poslední z pěti úkolů potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8bc2f-103">This tutorial describes the last of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="8bc2f-104">Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="8bc2f-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="8bc2f-105">Po vytvoření a konfiguraci proxy windows communication foundation (WCF) vytvoříte instanci klienta a zkompilovat klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-105">After you've created and configured a Windows Communication Foundation (WCF) proxy, you create a client instance and compile the client application.</span></span> <span data-ttu-id="8bc2f-106">Potom jej použít ke komunikaci se službou WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-106">You then use it to communicate with the WCF service.</span></span>

<span data-ttu-id="8bc2f-107">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="8bc2f-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8bc2f-108">Přidejte kód pro použití klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-108">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="8bc2f-109">Otestujte klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-109">Test the WCF client.</span></span>

## <a name="add-code-to-use-the-wcf-client"></a><span data-ttu-id="8bc2f-110">Přidání kódu pro použití klienta WCF</span><span class="sxs-lookup"><span data-stu-id="8bc2f-110">Add code to use the WCF client</span></span>

<span data-ttu-id="8bc2f-111">Kód klienta provede následující kroky:</span><span class="sxs-lookup"><span data-stu-id="8bc2f-111">The client code does the following steps:</span></span>

- <span data-ttu-id="8bc2f-112">Konitekal a konkretizovat klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-112">Instantiates the WCF client.</span></span>
- <span data-ttu-id="8bc2f-113">Volá operace služby z generovaného proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-113">Calls the service operations from the generated proxy.</span></span>
- <span data-ttu-id="8bc2f-114">Zavře klienta po dokončení volání operace.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-114">Closes the client after the operation call is completed.</span></span>

<span data-ttu-id="8bc2f-115">Otevřete soubor **Program.cs** nebo **Module1.vb** z projektu **GettingStartedClient** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="8bc2f-115">Open the **Program.cs** or **Module1.vb** file from the **GettingStartedClient** project and replace its code with the following code:</span></span>

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

<span data-ttu-id="8bc2f-116">Všimněte `using` si příkazu (pro visual c#) `Imports` nebo `GettingStartedClient.ServiceReference1`(pro jazyk Visual Basic), který importuje .</span><span class="sxs-lookup"><span data-stu-id="8bc2f-116">Notice the `using` (for Visual C#) or `Imports` (for Visual Basic) statement that imports `GettingStartedClient.ServiceReference1`.</span></span> <span data-ttu-id="8bc2f-117">Tento příkaz importuje kód, který Visual Studio vygenerovalpomocí funkce **Přidat odkaz na službu.**</span><span class="sxs-lookup"><span data-stu-id="8bc2f-117">This statement imports the code that Visual Studio generated with the **Add Service Reference** function.</span></span> <span data-ttu-id="8bc2f-118">Kód inkonkaluje wcf proxy a volá každý operace služby, které služba kalkulačky zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-118">The code instantiates the WCF proxy and calls each of the service operations that the calculator service exposes.</span></span> <span data-ttu-id="8bc2f-119">Potom zavře proxy a ukončí program.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-119">It then closes the proxy and ends the program.</span></span>

## <a name="test-the-wcf-client"></a><span data-ttu-id="8bc2f-120">Testování klienta WCF</span><span class="sxs-lookup"><span data-stu-id="8bc2f-120">Test the WCF client</span></span>

### <a name="test-the-application-from-visual-studio"></a><span data-ttu-id="8bc2f-121">Testování aplikace z aplikace Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8bc2f-121">Test the application from Visual Studio</span></span>

1. <span data-ttu-id="8bc2f-122">Uložte a sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-122">Save and build the solution.</span></span>

2. <span data-ttu-id="8bc2f-123">V místní nabídce vyberte složku **GettingStartedLib** a pak vyberte **Nastavit jako spouštěcí projekt.**</span><span class="sxs-lookup"><span data-stu-id="8bc2f-123">Select the **GettingStartedLib** folder, and then select **Set as Startup Project** from the shortcut menu.</span></span>

3. <span data-ttu-id="8bc2f-124">V **rozevíracím seznamu V rozevíracím**seznamu vyberte možnost **GettingStartedLib** a pak vyberte **Spustit** nebo stiskněte **klávesu F5**.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-124">From **Startup Projects**, select **GettingStartedLib** from the drop-down list, then select **Run** or press **F5**.</span></span>

### <a name="test-the-application-from-a-command-prompt"></a><span data-ttu-id="8bc2f-125">Testování aplikace z příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="8bc2f-125">Test the application from a command prompt</span></span>

1. <span data-ttu-id="8bc2f-126">Otevřete příkazový řádek jako správce a přejděte do adresáře řešení sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-126">Open a command prompt as an administrator, and then navigate to your Visual Studio solution directory.</span></span>

2. <span data-ttu-id="8bc2f-127">Spuštění služby: Zadejte *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-127">To start the service: Enter *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.</span></span>

3. <span data-ttu-id="8bc2f-128">Spuštění klienta: Otevřete jiný příkazový řádek, přejděte do adresáře řešení sady Visual Studio a zadejte *příkaz GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-128">To start the client: Open another command prompt, navigate to your Visual Studio solution directory, then enter *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.</span></span>

   <span data-ttu-id="8bc2f-129">*GettingStartedHost.exe* vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8bc2f-129">*GettingStartedHost.exe* produces the following output:</span></span>

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

   <span data-ttu-id="8bc2f-130">*GettingStartedClient.exe* vytváří následující výstup:</span><span class="sxs-lookup"><span data-stu-id="8bc2f-130">*GettingStartedClient.exe* produces the following output:</span></span>

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a><span data-ttu-id="8bc2f-131">Další kroky</span><span class="sxs-lookup"><span data-stu-id="8bc2f-131">Next steps</span></span>

<span data-ttu-id="8bc2f-132">Nyní jste dokončili všechny úkoly v kurzu WCF začínáme.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-132">You've now completed all the tasks in the WCF get started tutorial.</span></span> <span data-ttu-id="8bc2f-133">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="8bc2f-133">In this tutorial, you learned how to:</span></span>

<span data-ttu-id="8bc2f-134">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="8bc2f-134">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8bc2f-135">Přidejte kód pro použití klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-135">Add code to use the WCF client.</span></span>
> - <span data-ttu-id="8bc2f-136">Otestujte klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-136">Test the WCF client.</span></span>

<span data-ttu-id="8bc2f-137">Pokud máte problémy nebo chyby v některém z kroků, postupujte podle pokynů v článku pro řešení potíží a opravte je.</span><span class="sxs-lookup"><span data-stu-id="8bc2f-137">If you have problems or errors in any of the steps, follow the steps in the troubleshooting article to fix them.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8bc2f-138">Poradce při potížích s kurzy WCF</span><span class="sxs-lookup"><span data-stu-id="8bc2f-138">Troubleshoot the Get started with WCF tutorials</span></span>](troubleshooting-the-getting-started-tutorial.md)
