---
title: 'Kurz: implementace kontraktu služby Windows Communication Foundation'
description: Naučte se, jak přidat kód pro implementaci rozhraní služby WCF jako součást série článků, které vám pomůžou začít vytvářet aplikace WCF.
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 89f97610cccd42c2a5d298baa667327d077fd472
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244644"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="da72f-103">Kurz: implementace kontraktu služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="da72f-103">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="da72f-104">Tento kurz popisuje druhý z pěti úkolů potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="da72f-104">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="da72f-105">Přehled kurzů najdete v tématu [kurz: Začínáme s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="da72f-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="da72f-106">Dalším krokem pro vytvoření aplikace WCF je přidání kódu pro implementaci rozhraní služby WCF, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="da72f-106">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="da72f-107">V tomto kroku vytvoříte třídu s názvem `CalculatorService` , která implementuje uživatelsky definované `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="da72f-107">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="da72f-108">Každá metoda v následujícím kódu volá operaci kalkulačky a zapisuje text do konzoly pro její otestování.</span><span class="sxs-lookup"><span data-stu-id="da72f-108">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span>

<span data-ttu-id="da72f-109">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="da72f-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="da72f-110">Přidejte kód pro implementaci kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="da72f-110">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="da72f-111">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="da72f-111">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="da72f-112">Přidání kódu pro implementaci kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="da72f-112">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="da72f-113">V **GettingStartedLib**otevřete soubor **Service1.cs** nebo **Service1. vb** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="da72f-113">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="da72f-114">Upravit App.config</span><span class="sxs-lookup"><span data-stu-id="da72f-114">Edit App.config</span></span>

<span data-ttu-id="da72f-115">Upravte **App.config** v **GettingStartedLib** tak, aby odrážely změny, které jste provedli v kódu.</span><span class="sxs-lookup"><span data-stu-id="da72f-115">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="da72f-116">Pro projekty v jazyce Visual C#:</span><span class="sxs-lookup"><span data-stu-id="da72f-116">For Visual C# projects:</span></span>
  - <span data-ttu-id="da72f-117">Změnit řádek 14 na`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="da72f-117">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="da72f-118">Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="da72f-118">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="da72f-119">Změna řádku 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="da72f-119">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="da72f-120">Pro Visual Basic projekty:</span><span class="sxs-lookup"><span data-stu-id="da72f-120">For Visual Basic projects:</span></span>
  - <span data-ttu-id="da72f-121">Změnit řádek 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="da72f-121">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="da72f-122">Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="da72f-122">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="da72f-123">Změna řádku 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="da72f-123">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="da72f-124">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="da72f-124">Compile the code</span></span>

<span data-ttu-id="da72f-125">Sestavte řešení, abyste ověřili, že nedošlo k chybám kompilace.</span><span class="sxs-lookup"><span data-stu-id="da72f-125">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="da72f-126">Pokud používáte aplikaci Visual Studio, v nabídce **sestavení** vyberte **sestavení řešení** (nebo stiskněte klávesy **CTRL** + **SHIFT** + **B**).</span><span class="sxs-lookup"><span data-stu-id="da72f-126">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="da72f-127">Další kroky</span><span class="sxs-lookup"><span data-stu-id="da72f-127">Next steps</span></span>

<span data-ttu-id="da72f-128">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="da72f-128">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="da72f-129">Přidejte kód pro implementaci kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="da72f-129">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="da72f-130">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="da72f-130">Build the solution.</span></span>

<span data-ttu-id="da72f-131">Přejděte k dalšímu kurzu, kde se dozvíte, jak spustit službu WCF.</span><span class="sxs-lookup"><span data-stu-id="da72f-131">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="da72f-132">Kurz: hostování a spuštění základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="da72f-132">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
