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
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Kurz: Použití klienta Windows Communication Foundation

Tento kurz popisuje poslední z pěti úkolů potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled výukových programů najdete v [tématu Výuka: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Po vytvoření a konfiguraci proxy windows communication foundation (WCF) vytvoříte instanci klienta a zkompilovat klientskou aplikaci. Potom jej použít ke komunikaci se službou WCF.

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte kód pro použití klienta WCF.
> - Otestujte klienta WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Přidání kódu pro použití klienta WCF

Kód klienta provede následující kroky:

- Konitekal a konkretizovat klienta WCF.
- Volá operace služby z generovaného proxy serveru.
- Zavře klienta po dokončení volání operace.

Otevřete soubor **Program.cs** nebo **Module1.vb** z projektu **GettingStartedClient** a nahraďte jeho kód následujícím kódem:

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

Všimněte `using` si příkazu (pro visual c#) `Imports` nebo `GettingStartedClient.ServiceReference1`(pro jazyk Visual Basic), který importuje . Tento příkaz importuje kód, který Visual Studio vygenerovalpomocí funkce **Přidat odkaz na službu.** Kód inkonkaluje wcf proxy a volá každý operace služby, které služba kalkulačky zveřejňuje. Potom zavře proxy a ukončí program.

## <a name="test-the-wcf-client"></a>Testování klienta WCF

### <a name="test-the-application-from-visual-studio"></a>Testování aplikace z aplikace Visual Studio

1. Uložte a sestavte řešení.

2. V místní nabídce vyberte složku **GettingStartedLib** a pak vyberte **Nastavit jako spouštěcí projekt.**

3. V **rozevíracím seznamu V rozevíracím**seznamu vyberte možnost **GettingStartedLib** a pak vyberte **Spustit** nebo stiskněte **klávesu F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Testování aplikace z příkazového řádku

1. Otevřete příkazový řádek jako správce a přejděte do adresáře řešení sady Visual Studio.

2. Spuštění služby: Zadejte *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. Spuštění klienta: Otevřete jiný příkazový řádek, přejděte do adresáře řešení sady Visual Studio a zadejte *příkaz GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *GettingStartedHost.exe* vytváří následující výstup:

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

   *GettingStartedClient.exe* vytváří následující výstup:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Další kroky

Nyní jste dokončili všechny úkoly v kurzu WCF začínáme. V tomto kurzu jste se naučili:

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte kód pro použití klienta WCF.
> - Otestujte klienta WCF.

Pokud máte problémy nebo chyby v některém z kroků, postupujte podle pokynů v článku pro řešení potíží a opravte je.

> [!div class="nextstepaction"]
> [Poradce při potížích s kurzy WCF](troubleshooting-the-getting-started-tutorial.md)
