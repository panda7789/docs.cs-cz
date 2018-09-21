---
title: 'Postupy: implementace kontraktu služby Windows Communication Foundation'
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
ms.openlocfilehash: 569de6f49b56b46ccfeb22e9f0bd25bcf339b7e0
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46493198"
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="dfcfa-102">Postupy: implementace kontraktu služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="dfcfa-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>

<span data-ttu-id="dfcfa-103">Toto je druhá z šesti úkolů, muset vytvořit základní služby Windows Communication Foundation (WCF) a klienta, která může volat službu.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-103">This is the second of six tasks required to create a basic Windows Communication Foundation (WCF) service and a client that can call the service.</span></span> <span data-ttu-id="dfcfa-104">Přehled o všech šesti úkolů, najdete v článku [kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="dfcfa-105">Dalším krokem při vytváření aplikace WCF je implementace rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="dfcfa-106">To zahrnuje vytvoření třídu s názvem `CalculatorService` , která implementuje uživatelsky definované `ICalculator` rozhraní...</span><span class="sxs-lookup"><span data-stu-id="dfcfa-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>

## <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="dfcfa-107">Implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="dfcfa-107">To implement a WCF service contract</span></span>

<span data-ttu-id="dfcfa-108">Otevřete soubor Service1.cs nebo Service1.vb a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="dfcfa-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>

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

<span data-ttu-id="dfcfa-109">Každá metoda implementuje operace kalkulačky a zapíše text do konzole testování usnadnit.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>

## <a name="example"></a><span data-ttu-id="dfcfa-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="dfcfa-110">Example</span></span>

<span data-ttu-id="dfcfa-111">Následující kód ukazuje obě rozhraní, který definuje kontrakt a implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
    public interface ICalculator
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
}
```

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

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
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

## <a name="compile-the-code"></a><span data-ttu-id="dfcfa-112">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dfcfa-112">Compile the code</span></span>

<span data-ttu-id="dfcfa-113">Sestavte řešení, aby zajistil, že neexistují žádné chyby během kompilace.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-113">Build the solution to ensure there are no compilation errors.</span></span> <span data-ttu-id="dfcfa-114">Pokud používáte Visual Studio na **sestavení** nabídky vyberte možnost **sestavit řešení** (nebo stiskněte klávesu **Ctrl**+**Shift** + **B**).</span><span class="sxs-lookup"><span data-stu-id="dfcfa-114">If you're using Visual Studio, on the **Build** menu select **Build Solution** (or press **Ctrl**+**Shift**+**B**).</span></span>

## <a name="next-steps"></a><span data-ttu-id="dfcfa-115">Další kroky</span><span class="sxs-lookup"><span data-stu-id="dfcfa-115">Next steps</span></span>

<span data-ttu-id="dfcfa-116">Kontrakt služby je teď vytvořená a implementovat.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-116">Now the service contract is created and implemented.</span></span> <span data-ttu-id="dfcfa-117">V dalším kroku spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="dfcfa-117">In the next step, you run the service.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dfcfa-118">Postupy: Hostování a spuštění základní služby</span><span class="sxs-lookup"><span data-stu-id="dfcfa-118">How to: Host and Run a Basic Service</span></span>](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

<span data-ttu-id="dfcfa-119">Informace o odstraňování potíží naleznete v tématu [řešení potíží s kurzu Začínáme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="dfcfa-119">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfcfa-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfcfa-120">See also</span></span>

- [<span data-ttu-id="dfcfa-121">Začínáme</span><span class="sxs-lookup"><span data-stu-id="dfcfa-121">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="dfcfa-122">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="dfcfa-122">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)