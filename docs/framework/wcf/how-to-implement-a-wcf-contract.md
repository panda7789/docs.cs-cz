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
# <a name="tutorial-implement-a-windows-communication-foundation-service-contract"></a>Kurz: Implementace smlouvy o poskytování služeb windows communication foundation

Tento kurz popisuje druhý z pěti úkolů potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Dalším krokem pro vytvoření aplikace WCF je přidat kód pro implementaci rozhraní služby WCF, které jste vytvořili v předchozím kroku. V tomto kroku vytvoříte `CalculatorService` třídu s názvem, `ICalculator` která implementuje uživatelem definované rozhraní. Každá metoda v následujícím kódu volá operaci kalkulačky a zapíše text do konzoly k jeho testování.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte kód k implementaci smlouvy o poskytování služeb WCF.
> - Sestavte řešení.

## <a name="add-code-to-implement-the-wcf-service-contract"></a>Přidání kódu k implementaci smlouvy o poskytování služeb WCF

V **části GettingStartedLib**otevřete soubor **Service1.cs** nebo **Service1.vb** a nahraďte jeho kód následujícím kódem:

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

## <a name="edit-appconfig"></a>Upravit soubor App.config

Upravte **soubor App.config** v **aplikaci GettingStartedLib** tak, aby odrážela změny provedené v kódu.

- Pro projekty Visual C#:
  - Změnit řádek 14 na`<service name="GettingStartedLib.CalculatorService">`
  - Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Změnit řádek 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

- Pro projekty jazyka Visual Basic:
  - Změnit řádek 14 na`<service name="GettingStartedLib.GettingStartedLib.CalculatorService">`
  - Změnit řádek 17 na`<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
  - Změnit řádek 22 na`<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.GettingStartedLib.ICalculator">`

## <a name="compile-the-code"></a>Kompilace kódu

Vytvořte řešení a ověřte, že neexistují žádné chyby kompilace. Pokud používáte Visual Studio, v nabídce **Sestavení** vyberte **Build Solution** (nebo stiskněte **Ctrl**+**Shift**+**B**).

## <a name="next-steps"></a>Další kroky

V tomto kurzu jste se naučili:
> [!div class="checklist"]
>
> - Přidejte kód k implementaci smlouvy o poskytování služeb WCF.
> - Sestavte řešení.

Přejdete k dalšímu kurzu, kde se dozvíte, jak spustit službu WCF.

> [!div class="nextstepaction"]
> [Kurz: Hostování a spuštění základní služby WCF](how-to-host-and-run-a-basic-wcf-service.md)
