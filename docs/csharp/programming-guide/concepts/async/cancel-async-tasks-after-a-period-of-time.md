---
title: Zrušit asynchronní úkoly po časovém období (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 110c4700d0d2afc87f9144bf258cdd4991f107f4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204345"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zrušení asynchronních úloh po určité době (C#)

Asynchronní operaci můžete po určité době zrušit pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, pokud nechcete čekat na dokončení operace. Tato metoda naplánuje zrušení všech přidružených úkolů, které nejsou dokončeny v `CancelAfter` rámci časového období, které je určeno výrazem.

Tento příklad přidá ke kódu, který je vyvinut v [Zrušit asynchronní úlohu nebo Seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) ke stažení seznamu webů a zobrazit délku obsahu každého z nich.

> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

## <a name="download-the-example"></a>Stáhněte si příklad

Můžete si stáhnout celý projekt Windows Presentation Foundation (WPF) z [ukázky asynchronní: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a postupujte takto.

1. Dekomprimujte soubor, který jste stáhli, a spusťte Visual Studio.

2. Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.

3. V dialogovém okně **Otevřít projekt** otevřete složku obsahující ukázkový kód, který jste dekomprimovali, a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.

4. V **Průzkumníku řešení**otevřete místní nabídku projektu **CancelAfterTime** a pak zvolte **Nastavit jako počáteční projekt**.

5. Zvolte klávesu **F5** pro spuštění projektu. (Nebo stisknutím **klávesy Ctrl**+**F5** spusťte projekt bez ladění).

6. Spusťte program několikrát a ověřte, zda výstup může zobrazovat výstup pro všechny weby, žádné weby nebo některé webové stránky.

Pokud projekt nechcete stáhnout, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.

## <a name="build-the-example"></a>Sestavení příkladu

Příklad v tomto tématu přidá do projektu, který je vyvinut v [Zrušit asynchronní úkol nebo Seznam úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznam úkolů. Příklad používá stejné ui, i když **tlačítko Storno** není použit explicitně.

Chcete-li vytvořit příklad sami, krok za krokem postupujte podle pokynů v části "Stažení příkladu", ale zvolte **CancelAListOfTasks** jako **projekt StartUp**Project . Přidejte změny v tomto tématu do tohoto projektu.

Chcete-li určit maximální dobu, po jejíž například `CancelAfter` `startButton_Click`jsou úkoly označeny jako zrušené, přidejte volání do , jak ukazuje následující příklad. Přídavek je označen hvězdičkami.

```csharp
private async void startButton_Click(object sender, RoutedEventArgs e)
{
    // Instantiate the CancellationTokenSource.
    cts = new CancellationTokenSource();

    resultsTextBox.Clear();

    try
    {
        // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
        // can adjust the time.)
        cts.CancelAfter(2500);

        await AccessTheWebAsync(cts.Token);
        resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
    }
    catch (OperationCanceledException)
    {
        resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        resultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }

    cts = null;
}
```

 Spusťte program několikrát a ověřte, zda výstup může zobrazovat výstup pro všechny weby, žádné weby nebo některé webové stránky. Následující výstup je ukázka.

```output
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Kompletní příklad

Následující kód je úplný text MainWindow.xaml.cs souboru pro příklad. Hvězdičky označují prvky, které byly přidány pro tento příklad.

Všimněte si, že <xref:System.Net.Http>je nutné přidat odkaz pro .

Projekt si můžete stáhnout z [ukázky aplikace Async: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;

// Add a using directive and a reference for System.Net.Http.
using System.Net.Http;

// Add the following using directive.
using System.Threading;

namespace CancelAfterTime
{
    public partial class MainWindow : Window
    {
        // Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;

        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            resultsTextBox.Clear();

            try
            {
                // ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You
                // can adjust the time.)
                cts.CancelAfter(2500);

                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads succeeded.\r\n";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        // You can still include a Cancel button if you want to.
        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            // Declare an HttpClient object.
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            foreach (var url in urlList)
            {
                // GetAsync returns a Task<HttpResponseMessage>.
                // Argument ct carries the message if the Cancel button is chosen.
                // Note that the Cancel button cancels all remaining downloads.
                HttpResponseMessage response = await client.GetAsync(url, ct);

                // Retrieve the website contents from the HttpResponseMessage.
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }
    }

    // Sample Output:

    // Length of the downloaded string: 35990.

    // Length of the downloaded string: 407399.

    // Length of the downloaded string: 226091.

    // Downloads canceled.
}
```

## <a name="see-also"></a>Viz také

- [Asynchronní programování s asynchronní a await (C#)](./index.md)
- [Návod: Přístup k webu pomocí asynchronní a čeká (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zrušení asynchronní úlohy nebo seznamu úkolů (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)
- [Jemné doladění asynchronní aplikace (C#)](./fine-tuning-your-async-application.md)
- [Asynchronní ukázka: Jemné doladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
