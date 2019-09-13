---
title: 'Kurz: Použití klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: 5c280933c81ef54ba58181e3005e30775b9b8e42
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928890"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Kurz: Použití klienta Windows Communication Foundation

Tento kurz popisuje posledních pět úloh potřebných k vytvoření aplikace Basic Windows Communication Foundation (WCF). Přehled kurzů najdete v tématu [kurz: Začněte s Windows Communication Foundation aplikacemi](getting-started-tutorial.md).

Poté, co vytvoříte a nakonfigurujete proxy server Windows Communication Foundation (WCF), vytvoříte instanci klienta a zkompilujete klientskou aplikaci. Pak ho použijete ke komunikaci se službou WCF. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte kód pro použití klienta WCF.
> - Otestujte klienta WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Přidání kódu pro použití klienta WCF

Klientský kód provede následující kroky:

- Vytvoří instanci klienta WCF.
- Zavolá operace služby z vygenerovaného proxy serveru.
- Ukončí klienta po dokončení volání operace.

Otevřete soubor **program.cs** nebo **Module1. vb** z projektu **GettingStartedClient** a nahraďte jeho kód následujícím kódem:

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
Imports System
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

Všimněte si příkazu C# `Imports` `GettingStartedClient.ServiceReference1`(for Visual) nebo (for Visual Basic), který importuje. `using` Tento příkaz importuje kód, který aplikace Visual Studio vygenerovala pomocí funkce **Přidat odkaz na službu** . Kód vytvoří instanci proxy serveru WCF a zavolá každou operaci služby, kterou služba kalkulačky zpřístupňuje. Pak zavře proxy a ukončí program.

## <a name="test-the-wcf-client"></a>Testování klienta WCF

### <a name="test-the-application-from-visual-studio"></a>Testování aplikace ze sady Visual Studio

1. Uložte a sestavte řešení.

2. Vyberte složku **GettingStartedLib** a pak v místní nabídce vyberte **nastavit jako spouštěný projekt** .

3. Z nabídky **projekty po spuštění**vyberte v rozevíracím seznamu položku **GettingStartedLib** a pak vyberte **Spustit** nebo stiskněte klávesu **F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Otestování aplikace z příkazového řádku

1. Otevřete příkazový řádek jako správce a pak přejděte do adresáře řešení Visual Studio. 

2. Spuštění služby: Zadejte *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. Spuštění klienta: Otevřete jiný příkazový řádek, přejděte do adresáře řešení Visual Studio a pak zadejte *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *GettingStartedHost. exe* vytvoří následující výstup:

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

   *GettingStartedClient. exe* vytvoří následující výstup:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Další kroky

Nyní jste dokončili všechny úkoly v kurzu Začínáme WCF. V tomto kurzu jste se naučili:

V tomto kurzu se naučíte:
> [!div class="checklist"]
>
> - Přidejte kód pro použití klienta WCF.
> - Otestujte klienta WCF.

Pokud máte v některém z kroků problémy nebo chyby, opravte je podle kroků v článku věnovaném řešení potíží.

> [!div class="nextstepaction"]
> [Řešení potíží s kurzy Začínáme s WCF](troubleshooting-the-getting-started-tutorial.md)
