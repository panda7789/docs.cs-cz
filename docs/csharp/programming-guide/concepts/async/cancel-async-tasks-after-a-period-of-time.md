---
title: Zrušení asynchronních úloh po určitou dobu (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: b95b87e1e93a9c8f8c74680a917a128d45172ed5
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2018
ms.locfileid: "47027840"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zrušení asynchronních úloh po určitou dobu (C#)

Můžete zrušit asynchronní operaci po určité době pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metody, pokud nechcete čekat na dokončení operace. Tato metoda plánuje zrušení všech přidružených úkolů, které nejsou dokončeny v časovém období, které je určeno `CancelAfter` výrazu.

V tomto příkladu přidá do kódu, který je napsán v jazyce [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) ke stažení seznamu webů a zobrazení délky obsahu jednotlivých webů.

> [!NOTE]
> Chcete-li spustit příklady, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

## <a name="download-the-example"></a>Stáhnout příklad

Můžete si stáhnout kompletní projekt Windows Presentation Foundation (WPF) z [asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.

1.  Dekomprimujte soubor, který jste stáhli a poté spusťte Visual Studio.

2.  V panelu nabídky zvolte **souboru** > **otevřít** > **projekt či řešení**.

3.  V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovali a potom otevřete soubor řešení (.sln) pro AsyncFineTuningCS.

4.  V **Průzkumníka řešení**, otevřete místní nabídku **CancelAfterTime** projektu a klikněte na tlačítko **nastavit jako spouštěný projekt**.

5.  Zvolte **F5** spusťte projekt. (Nebo stiskněte klávesu **Ctrl**+**F5** ke spuštění projektu bez ladění).

6.  Chcete-li ověřit, zda výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé webové servery spusťte program několikrát.

Pokud nechcete stáhnout projekt, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.

## <a name="build-the-example"></a>Sestavení příkladu

V příkladu v tomto tématu se přidá do projektu, který je napsán v jazyce [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) zrušení seznamu úloh. V příkladu se používá stejné uživatelské rozhraní, i když **zrušit** tlačítko není použito explicitně.

Chcete-li vytvořit příklad sami krok za krokem, postupujte podle pokynů v oddíle "Stahování příkladu", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**. Přidejte změny v tomto tématu do daného projektu.

Pokud chcete zadat maximální dobu, než jsou úkoly označeny jako zrušená, přidejte volání do `CancelAfter` k `startButton_Click`, jak ukazuje následující příklad. Přidání je označeno hvězdičkami.

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

 Chcete-li ověřit, zda výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé webové servery spusťte program několikrát. Následující výstup je vzorový.

```
Length of the downloaded string: 35990.

Length of the downloaded string: 407399.

Length of the downloaded string: 226091.

Downloads canceled.
```

## <a name="complete-example"></a>Kompletní příklad

Následující kód je celý text souboru MainWindow.xaml.cs pro příklad. Hvězdičky označují prvky, které byly přidány pro účely tohoto příkladu.

Všimněte si, že musíte přidat odkaz pro <xref:System.Net.Http>.

Stáhnete projekt z [asynchronní vzorek: jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).

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
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "http://msdn.microsoft.com",
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "http://msdn.microsoft.com/library/hh290136.aspx",
                "http://msdn.microsoft.com/library/ee256749.aspx",
                "http://msdn.microsoft.com/library/ms404677.aspx",
                "http://msdn.microsoft.com/library/ff730837.aspx"
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

## <a name="see-also"></a>Viz také:

- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)
- [Doladění aplikace s modifikátorem Async (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [Asynchronní vzorek: Jemné ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
