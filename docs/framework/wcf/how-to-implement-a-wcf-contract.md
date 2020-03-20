---
title: 'Kurz: Implementace smlouvy o poskytování služeb windows communication foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: debdeeac7064f5bae21622b2d9de84a4d8a0e66f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184069"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="d64e7-102">Kurz: Implementace smlouvy o poskytování služeb windows communication foundation</span><span class="sxs-lookup"><span data-stu-id="d64e7-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="d64e7-103">Tento kurz popisuje druhý z pěti úkolů potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d64e7-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="d64e7-104">Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="d64e7-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="d64e7-105">Dalším krokem pro vytvoření aplikace WCF je přidat kód pro implementaci rozhraní služby WCF, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="d64e7-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="d64e7-106">V tomto kroku vytvoříte `CalculatorService` třídu s názvem, `ICalculator` která implementuje uživatelem definované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d64e7-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="d64e7-107">Každá metoda v následujícím kódu volá operaci kalkulačky a zapíše text do konzoly k jeho testování.</span><span class="sxs-lookup"><span data-stu-id="d64e7-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="d64e7-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="d64e7-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d64e7-109">Přidejte kód k implementaci smlouvy o poskytování služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="d64e7-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="d64e7-110">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="d64e7-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="d64e7-111">Přidání kódu k implementaci smlouvy o poskytování služeb WCF</span><span class="sxs-lookup"><span data-stu-id="d64e7-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="d64e7-112">V **části GettingStartedLib**otevřete soubor **Service1.cs** nebo **Service1.vb** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="d64e7-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
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

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

## <a name="edit-appconfig"></a><span data-ttu-id="d64e7-113">Upravit soubor App.config</span><span class="sxs-lookup"><span data-stu-id="d64e7-113">Edit App.config</span></span>

<span data-ttu-id="d64e7-114">Upravte **soubor App.config** v **aplikaci GettingStartedLib** tak, aby odrážela změny provedené v kódu.</span><span class="sxs-lookup"><span data-stu-id="d64e7-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="d64e7-115">Pro projekty Visual C#:</span><span class="sxs-lookup"><span data-stu-id="d64e7-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="d64e7-116">Změnit řádek 14 na`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="d64e7-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="d64e7-117">Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="d64e7-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="d64e7-118">Změnit řádek 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="d64e7-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="d64e7-119">Pro projekty jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="d64e7-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="d64e7-120">Změnit řádek 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="d64e7-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="d64e7-121">Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="d64e7-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="d64e7-122">Změnit řádek 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="d64e7-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="d64e7-123">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d64e7-123">Compile the code</span></span>

<span data-ttu-id="d64e7-124">Vytvořte řešení a ověřte, že neexistují žádné chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="d64e7-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="d64e7-125">Pokud používáte Visual Studio, v nabídce **Sestavení** vyberte **Build Solution** (nebo stiskněte **Ctrl**+**Shift**+**B**).</span><span class="sxs-lookup"><span data-stu-id="d64e7-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d64e7-126">Další kroky</span><span class="sxs-lookup"><span data-stu-id="d64e7-126">Next steps</span></span>

<span data-ttu-id="d64e7-127">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="d64e7-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="d64e7-128">Přidejte kód k implementaci smlouvy o poskytování služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="d64e7-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="d64e7-129">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="d64e7-129">Build the solution.</span></span>

<span data-ttu-id="d64e7-130">Přejdete k dalšímu kurzu, kde se dozvíte, jak spustit službu WCF.</span><span class="sxs-lookup"><span data-stu-id="d64e7-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d64e7-131">Kurz: Hostování a spuštění základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="d64e7-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
