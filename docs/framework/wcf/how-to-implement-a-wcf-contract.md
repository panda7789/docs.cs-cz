---
title: 'Kurz: Implementace kontraktu služby Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 05923dc0a2223da5e5fcda483abc1ee1dd2d643f
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928713"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="0d773-102">Kurz: Implementace kontraktu služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="0d773-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="0d773-103">Tento kurz popisuje druhý z pěti úkolů potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="0d773-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="0d773-104">Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="0d773-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="0d773-105">Dalším krokem pro vytvoření aplikace WCF je přidání kódu pro implementaci rozhraní služby WCF, které jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="0d773-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="0d773-106">V tomto kroku vytvoříte třídu s názvem `CalculatorService` , která implementuje uživatelsky definované `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0d773-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="0d773-107">Každá metoda v následujícím kódu volá operaci kalkulačky a zapisuje text do konzoly pro její otestování.</span><span class="sxs-lookup"><span data-stu-id="0d773-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="0d773-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="0d773-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0d773-109">Přidejte kód pro implementaci kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="0d773-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="0d773-110">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="0d773-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="0d773-111">Přidání kódu pro implementaci kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="0d773-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="0d773-112">V **GettingStartedLib**otevřete soubor **Service1.cs** nebo **Service1. vb** a nahraďte jeho kód následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="0d773-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="0d773-113">Upravit soubor App. config</span><span class="sxs-lookup"><span data-stu-id="0d773-113">Edit App.config</span></span>

<span data-ttu-id="0d773-114">Upravte soubor **App. config** v **GettingStartedLib** tak, aby odrážel změny, které jste provedli v kódu.</span><span class="sxs-lookup"><span data-stu-id="0d773-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>

- <span data-ttu-id="0d773-115">Pro vizuální C# projekty:</span><span class="sxs-lookup"><span data-stu-id="0d773-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="0d773-116">Změnit řádek 14 na`<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="0d773-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="0d773-117">Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="0d773-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="0d773-118">Změna řádku 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="0d773-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="0d773-119">Pro Visual Basic projekty:</span><span class="sxs-lookup"><span data-stu-id="0d773-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="0d773-120">Změnit řádek 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="0d773-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="0d773-121">Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="0d773-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="0d773-122">Změna řádku 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="0d773-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="0d773-123">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0d773-123">Compile the code</span></span>

<span data-ttu-id="0d773-124">Sestavte řešení, abyste ověřili, že nedošlo k chybám kompilace.</span><span class="sxs-lookup"><span data-stu-id="0d773-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="0d773-125">Pokud používáte aplikaci Visual Studio, v nabídce **sestavení** vyberte **sestavení řešení** (nebo stiskněte klávesy **CTRL**+**SHIFT**+**B**).</span><span class="sxs-lookup"><span data-stu-id="0d773-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="0d773-126">Další postup</span><span class="sxs-lookup"><span data-stu-id="0d773-126">Next steps</span></span>

<span data-ttu-id="0d773-127">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="0d773-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0d773-128">Přidejte kód pro implementaci kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="0d773-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="0d773-129">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="0d773-129">Build the solution.</span></span>

<span data-ttu-id="0d773-130">Přejděte k dalšímu kurzu, kde se dozvíte, jak spustit službu WCF.</span><span class="sxs-lookup"><span data-stu-id="0d773-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0d773-131">Kurz: Hostování a spuštění základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="0d773-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
