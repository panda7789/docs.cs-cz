---
title: "Postupy: implementace kontraktu služby Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF], implementing
ms.assetid: d5ab51ba-61ae-403e-b3c8-e2669e326806
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4bf590b2f508cc6661b5acb045a7d66b38ed169c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-windows-communication-foundation-service-contract"></a><span data-ttu-id="9afa0-102">Postupy: implementace kontraktu služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="9afa0-102">How to: Implement a Windows Communication Foundation Service Contract</span></span>
<span data-ttu-id="9afa0-103">Toto je druhý šesti úkoly vyžadované pro vytvoření základní [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby a klienta, který můžete volat službu.</span><span class="sxs-lookup"><span data-stu-id="9afa0-103">This is the second of six tasks required to create a basic [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service and a client that can call the service.</span></span> <span data-ttu-id="9afa0-104">Přehled všech šest úloh najdete v tématu [kurzu Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="9afa0-104">For an overview of all six tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="9afa0-105">Dalším krokem při vytváření aplikace WCF je implementace rozhraní služby.</span><span class="sxs-lookup"><span data-stu-id="9afa0-105">The next step in creating a WCF application is to implement the service interface.</span></span> <span data-ttu-id="9afa0-106">To zahrnuje vytvoření třídy s názvem `CalculatorService` , která implementuje uživatelsky definované `ICalculator` rozhraní...</span><span class="sxs-lookup"><span data-stu-id="9afa0-106">This involves creating a class called `CalculatorService` that implements the user-defined `ICalculator` interface..</span></span>  
  
### <a name="to-implement-a-wcf-service-contract"></a><span data-ttu-id="9afa0-107">K implementaci kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="9afa0-107">To implement a WCF service contract</span></span>  
  
1.  <span data-ttu-id="9afa0-108">Otevřete soubor Service1.cs nebo Service1.vb a přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="9afa0-108">Open the Service1.cs or Service1.vb file and add the following code:</span></span>  
  
    ```csharp  
    //Service1.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Runtime.Serialization;  
    using System.ServiceModel;  
    using System.Text;  
  
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
    ‘Service1.vb  
    Imports System  
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
  
     <span data-ttu-id="9afa0-109">Každá metoda implementuje operaci kalkulačky a zapíše text do konzoly nástroje Testování usnadnit.</span><span class="sxs-lookup"><span data-stu-id="9afa0-109">Each method implements the calculator operation and writes some text to the console to make testing easier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9afa0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9afa0-110">Example</span></span>  
 <span data-ttu-id="9afa0-111">Následující kód ukazuje, jak rozhraní, které definuje kontrakt a implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9afa0-111">The following code shows both the interface that defines the contract and the implementation of the interface.</span></span>  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
‘IService.vb  
Imports System  
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
Imports System  
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
  
 <span data-ttu-id="9afa0-112">Kontrakt služby je teď vytvořená a implementovat.</span><span class="sxs-lookup"><span data-stu-id="9afa0-112">Now the service contract is created and implemented.</span></span> <span data-ttu-id="9afa0-113">Sestavte řešení, abyste zajistili zde nejsou žádné chyby kompilace a pak pokračujte [postupy: hostování a spuštění základní služby](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md) službu spustit.</span><span class="sxs-lookup"><span data-stu-id="9afa0-113">Build the solution to ensure there are no compilation errors and then proceed to [How to: Host and Run a Basic Service](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md) to run the service.</span></span> <span data-ttu-id="9afa0-114">Informace o odstraňování potíží, najdete v části [řešení potíží s kurzu Začínáme](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="9afa0-114">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9afa0-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9afa0-115">Compiling the Code</span></span>  
 <span data-ttu-id="9afa0-116">Pokud používáte Visual Studio, v nabídce sestavení klikněte na tlačítko Sestavit řešení (nebo stiskněte klávesu CTRL + SHIFT + B).</span><span class="sxs-lookup"><span data-stu-id="9afa0-116">If you are using Visual Studio, on the Build menu click Build Solution (or press CTRL+SHIFT+B).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9afa0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9afa0-117">See Also</span></span>  
 [<span data-ttu-id="9afa0-118">Začínáme</span><span class="sxs-lookup"><span data-stu-id="9afa0-118">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="9afa0-119">Vlastní hostování</span><span class="sxs-lookup"><span data-stu-id="9afa0-119">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
