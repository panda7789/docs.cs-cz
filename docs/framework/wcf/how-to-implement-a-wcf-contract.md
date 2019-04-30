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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929050"
---
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Kurz: Implementace kontraktu služby Windows Communication Foundation

Tento kurz popisuje druhý pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Dalším krokem pro vytvoření aplikace WCF je přidání kódu k implementaci rozhraní služby WCF, který jste vytvořili v předchozím kroku. V tomto kroku vytvoříte třídu s názvem `CalculatorService` , která implementuje uživatelsky definované `ICalculator` rozhraní. Každá metoda v následujícím kódu volá operace kalkulačky a zapíše text do konzoly a otestovat ho. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Přidejte kód do implementace kontraktu služby WCF.
> - Sestavte řešení.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Přidejte kód do implementace kontraktu služby WCF

V **GettingStartedLib**, otevřete **Service1.cs** nebo **Service1.vb** souboru a jeho kódu nahraďte následujícím kódem:

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

## <a name="edit-appconfig"></a>Edit App.config

Upravit **App.config** v **GettingStartedLib** tak, aby odrážely změny provedené v kódu.
- Pro Vizuály C# projekty:
  - Změňte na řádek 14 `<service name="GettingStartedLib.CalculatorService">`
  - Změňte řádek 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Změňte řádek 22 na `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Pro projekty jazyka Visual Basic:
  - Změňte na řádek 14 `<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Změňte řádek 17 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Změňte řádek 22 na `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kompilace kódu

Sestavte řešení, chcete-li ověřit, že nejsou k dispozici žádné chyby kompilace. Pokud používáte Visual Studio na **sestavení** nabídky vyberte možnost **sestavit řešení** (nebo stiskněte klávesu **Ctrl**+**Shift** + **B**).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
> - Přidejte kód do implementace kontraktu služby WCF.
> - Sestavte řešení.

Přejděte k dalšímu kurzu se naučíte spustit službu WCF.

> [!div class="nextstepaction"]
> [Kurz: Hostování a spuštění základní služby WCF](how-to-host-and-run-a-basic-wcf-service.md)
