---
title: 'Kurz: Implementace kontraktu služby Windows Communication Foundation'
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: fa8c5457c636d7f37215f0d4b4fdbb1c96c9481e
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463615"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="a14dc-102">Kurz: Implementace kontraktu služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a14dc-102">Tutorial: Implement a Windows Communication Foundation service contract</span></span>

<span data-ttu-id="a14dc-103">Tento kurz popisuje druhý pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a14dc-103">This tutorial describes the second of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="a14dc-104">Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="a14dc-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="a14dc-105">Dalším krokem pro vytvoření aplikace WCF je přidání kódu k implementaci rozhraní služby WCF, který jste vytvořili v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="a14dc-105">The next step for creating a WCF application is to add code to implement the WCF service interface that you created in the previous step.</span></span> <span data-ttu-id="a14dc-106">V tomto kroku vytvoříte třídu s názvem `CalculatorService` , která implementuje uživatelsky definované `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a14dc-106">In this step, you create a class named `CalculatorService` that implements the user-defined `ICalculator` interface.</span></span> <span data-ttu-id="a14dc-107">Každá metoda v následujícím kódu volá operace kalkulačky a zapíše text do konzoly a otestovat ho.</span><span class="sxs-lookup"><span data-stu-id="a14dc-107">Each method in the following code calls a calculator operation and writes text to the console to test it.</span></span> 

<span data-ttu-id="a14dc-108">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="a14dc-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="a14dc-109">Přidejte kód do implementace kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a14dc-109">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="a14dc-110">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="a14dc-110">Build the solution.</span></span>

## <a name="add-code-to-implement-the-wcf-service-contract"></a><span data-ttu-id="a14dc-111">Přidejte kód do implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="a14dc-111">Add code to implement the WCF service contract</span></span>

<span data-ttu-id="a14dc-112">V **GettingStartedLib**, otevřete **Service1.cs** nebo **Service1.vb** souboru a jeho kódu nahraďte následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="a14dc-112">In **GettingStartedLib**, open the **Service1.cs** or **Service1.vb** file and replace its code with the following code:</span></span>

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

## <a name="edit-appconfig"></a><span data-ttu-id="a14dc-113">Edit App.config</span><span class="sxs-lookup"><span data-stu-id="a14dc-113">Edit App.config</span></span>

<span data-ttu-id="a14dc-114">Upravit **App.config** v **GettingStartedLib** tak, aby odrážely změny provedené v kódu.</span><span class="sxs-lookup"><span data-stu-id="a14dc-114">Edit **App.config** in **GettingStartedLib** to reflect the changes you made to the code.</span></span>
- <span data-ttu-id="a14dc-115">Pro Vizuály C# projekty:</span><span class="sxs-lookup"><span data-stu-id="a14dc-115">For Visual C# projects:</span></span>
  - <span data-ttu-id="a14dc-116">Změňte na řádek 14 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="a14dc-116">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="a14dc-117">Změňte řádek 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="a14dc-117">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="a14dc-118">Změňte řádek 22 na `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="a14dc-118">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

- <span data-ttu-id="a14dc-119">Pro projekty jazyka Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="a14dc-119">For Visual Basic projects:</span></span>
  - <span data-ttu-id="a14dc-120">Změňte na řádek 14 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="a14dc-120">Change line 14 to `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`</span></span>
  - <span data-ttu-id="a14dc-121">Změňte řádek 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="a14dc-121">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
  - <span data-ttu-id="a14dc-122">Změňte řádek 22 na `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="a14dc-122">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="a14dc-123">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a14dc-123">Compile the code</span></span>

<span data-ttu-id="a14dc-124">Sestavte řešení, chcete-li ověřit, že nejsou k dispozici žádné chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="a14dc-124">Build the solution to verify there aren't any compilation errors.</span></span> <span data-ttu-id="a14dc-125">Pokud používáte Visual Studio na **sestavení** nabídky vyberte možnost **sestavit řešení** (nebo stiskněte klávesu **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="a14dc-125">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a14dc-126">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a14dc-126">Next steps</span></span>

<span data-ttu-id="a14dc-127">V tomto kurzu jste se naučili:</span><span class="sxs-lookup"><span data-stu-id="a14dc-127">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="a14dc-128">Přidejte kód do implementace kontraktu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a14dc-128">Add code to implement the WCF service contract.</span></span>
> - <span data-ttu-id="a14dc-129">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="a14dc-129">Build the solution.</span></span>

<span data-ttu-id="a14dc-130">Přejděte k dalšímu kurzu se naučíte spustit službu WCF.</span><span class="sxs-lookup"><span data-stu-id="a14dc-130">Advance to the next tutorial to learn how to run the WCF service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a14dc-131">Kurz: Hostování a spuštění základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="a14dc-131">Tutorial: Host and run a basic WCF service</span></span>](how-to-host-and-run-a-basic-wcf-service.md)
