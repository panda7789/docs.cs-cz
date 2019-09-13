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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Kurz: Implementace kontraktu služby Windows Communication Foundation

Tento kurz popisuje druhý z pěti úkolů potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF). Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).

Dalším krokem pro vytvoření aplikace WCF je přidání kódu pro implementaci rozhraní služby WCF, které jste vytvořili v předchozím kroku. V tomto kroku vytvoříte třídu s názvem `CalculatorService` , která implementuje uživatelsky definované `ICalculator` rozhraní. Každá metoda v následujícím kódu volá operaci kalkulačky a zapisuje text do konzoly pro její otestování. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte kód pro implementaci kontraktu služby WCF.
> - Sestavte řešení.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Přidání kódu pro implementaci kontraktu služby WCF

V **GettingStartedLib**otevřete soubor **Service1.cs** nebo **Service1. vb** a nahraďte jeho kód následujícím kódem:

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

## <a name="edit-appconfig"></a>Upravit soubor App. config

Upravte soubor **App. config** v **GettingStartedLib** tak, aby odrážel změny, které jste provedli v kódu.

- Pro vizuální C# projekty:
  - Změnit řádek 14 na`<service name="GettingStartedLib.CalculatorService">`
  - Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Změna řádku 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Pro Visual Basic projekty:
  - Změnit řádek 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Změna řádku 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kompilace kódu

Sestavte řešení, abyste ověřili, že nedošlo k chybám kompilace. Pokud používáte aplikaci Visual Studio, v nabídce **sestavení** vyberte **sestavení řešení** (nebo stiskněte klávesy **CTRL**+**SHIFT**+**B**).

## <a name="next-steps"></a>Další postup

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Přidejte kód pro implementaci kontraktu služby WCF.
> - Sestavte řešení.

Přejděte k dalšímu kurzu, kde se dozvíte, jak spustit službu WCF.

> [!div class="nextstepaction"]
> [Kurz: Hostování a spuštění základní služby WCF](how-to-host-and-run-a-basic-wcf-service.md)
