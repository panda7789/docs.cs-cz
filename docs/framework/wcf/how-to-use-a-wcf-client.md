---
title: 'Kurz: Používání klienta Windows Communication Foundation'
ms.date: 03/19/2019
helpviewer_keywords:
- WCF clients [WCF], using
dev_langs:
- CSharp
- VB
ms.assetid: 190349fc-0573-49c7-bb85-8e316df7f31f
ms.openlocfilehash: fa9aa3612a8dc72623fc4ea4b1ea337ac773fa26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61928840"
---
# <a name="tutorial-use-a-windows-communication-foundation-client"></a>Kurz: Používání klienta Windows Communication Foundation

Tento kurz popisuje posledních pět úloh potřebných k vytvoření základní aplikace Windows Communication Foundation (WCF). Přehled v kurzech, naleznete v tématu [kurzu: Začínáme s aplikacemi Windows Communication Foundation](getting-started-tutorial.md).

Jakmile máte vytvořený a nakonfigurovaný proxy server služby Windows Communication Foundation (WCF), vytvoříte instanci klienta a kompilace aplikace klienta. Pak použijete ho ke komunikaci se službou WCF. 

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Přidejte kód pro použití klienta WCF.
> - Testovací klient WCF.

## <a name="add-code-to-use-the-wcf-client"></a>Přidejte kód, který pomocí klienta WCF

Klientský kód provede následující kroky:
- Vytvoří instanci klienta WCF.
- Volání operace služby od vygenerovaný proxy server.
- Klient se zavře po dokončení volání operace.

Otevřít **Program.cs** nebo **Module1.vb** soubor **GettingStartedClient** projektu a nahraďte jeho kód následujícím kódem:

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

Všimněte si, že `using` (pro vizuál C#) nebo `Imports` (pro jazyk Visual Basic), který importuje `GettingStartedClient.ServiceReference1`. Tento příkaz importuje kód, který generuje sada Visual Studio s použitím **přidat odkaz na službu** funkce. Kód vytvoří instanci WCF proxy a volá všechny operace služby, které zpřístupňuje službu kalkulačky. Potom zavře proxy serveru a ukončení programu.

## <a name="test-the-wcf-client"></a>Testovací klient WCF

### <a name="test-the-application-from-visual-studio"></a>Testování aplikace ze sady Visual Studio

1. Uložit a sestavit řešení.

2. Vyberte **GettingStartedLib** složku a pak vyberte **nastavit jako spouštěný projekt** z místní nabídky.

3. Z **projektů po spuštění**vyberte **GettingStartedLib** z rozevíracího seznamu vyberte **spustit** nebo stiskněte klávesu **F5**.

### <a name="test-the-application-from-a-command-prompt"></a>Testování aplikace z příkazového řádku

1. Otevřete příkazový řádek jako správce a pak přejděte do adresáře řešení sady Visual Studio. 

2. Chcete-li spustit službu: Zadejte *GettingStartedHost\bin\Debug\GettingStartedHost.exe*.

3. Chcete spustit klienta: Otevřete další příkazový řádek, přejděte do adresáře řešení sady Visual Studio a pak zadejte *GettingStartedClient\bin\Debug\GettingStartedClient.exe*.

   *GettingStartedHost.exe* vytvoří následující výstup:

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

   *GettingStartedClient.exe* vytvoří následující výstup:

   ```text
   Add(100,15.99) = 115.99
   Subtract(145,76.54) = 68.46
   Multiply(9,81.25) = 731.25
   Divide(22,7) = 3.14285714285714

   Press <Enter> to terminate the client.
   ```

## <a name="next-steps"></a>Další kroky

Právě jste dokončili všechny úkoly v tomto kurzu Začínáme get WCF. V tomto kurzu jste se naučili:

V tomto kurzu se naučíte:
> [!div class="checklist"]
> - Přidejte kód pro použití klienta WCF.
> - Testovací klient WCF.

Pokud máte problémy nebo chyby v žádném z kroků, postupujte podle kroků v článku s řešením potíží a opravte je.

> [!div class="nextstepaction"]
> [Řešení potíží s Get začít kurzy WCF](troubleshooting-the-getting-started-tutorial.md)
