---
title: Zrušení asynchronních úloh po uplynutí časového intervalu (C#)
ms.date: 07/20/2015
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 55cf6b960752b36a1bfbd8ede25d7693225fbb20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zrušení asynchronních úloh po uplynutí časového intervalu (C#)
Asynchronní operaci po určitou dobu můžete zrušit pomocí <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> metoda, pokud nechcete čekat na dokončení operace. Tato metoda plány zrušení všechny přidružené úlohy, které nejsou v rámci časový interval, který je určen podle dokončení `CancelAfter` výraz.  
  
 Tento příklad přidá do kód, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) stáhnout seznam webů a zobrazit je délka obsahu z každé z nich.  
  
> [!NOTE]
>  Pro spuštění příkladů, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaný ve vašem počítači.  
  
## <a name="downloading-the-example"></a>Stažení příkladu  
 Stáhnete dokončený projekt Windows Presentation Foundation (WPF) z [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) a pak postupujte podle těchto kroků.  
  
1.  Dekomprimovat soubor, který jste stáhli a pak spusťte Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
3.  V **otevřít projekt** dialogové okno, otevřete složku, která obsahuje ukázkový kód, který jste dekomprimovat a pak otevřete soubor řešení (.sln) pro AsyncFineTuningCS.  
  
4.  V **Průzkumníku řešení**, otevřete místní nabídku pro **CancelAfterTime** projektu a potom vyberte **nastavit jako spouštěný projekt**.  
  
5.  Zvolte klávesu F5 a spusťte projekt.  
  
     Vyberte klíče Ctrl + F5 spusťte projekt bez ladění ho.  
  
6.  Chcete-li ověřit, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby spuste program několikrát.  
  
 Pokud nechcete, aby ke stažení projektu, můžete zkontrolovat soubor MainWindow.xaml.cs na konci tohoto tématu.  
  
## <a name="building-the-example"></a>Vytváření v příkladu  
 V příkladu v tomto tématu přidá do projektu, který je vyvinuta v [zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) zrušit seznamu úloh. Tento příklad používá stejné uživatelské rozhraní, i když **zrušit** tlačítko nepoužívá explicitně.  
  
 K sestavení v příkladu sami, krok za krokem, postupujte podle pokynů v části "příkladu se stahování", ale zvolte **CancelAListOfTasks** jako **spouštěný projekt**. Do tohoto projektu přidáte změny v tomto tématu.  
  
 Chcete-li určit maximální dobu, než úlohy jsou označeny jako zrušená, přidejte volání `CancelAfter` k `startButton_Click`, jak ukazuje následující příklad. Přidání je označena pomocí hvězdiček.  
  
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
  
 Chcete-li ověřit, že výstup může zobrazit výstup pro všechny weby, žádné weby nebo některé weby spuste program několikrát. Tento výstup je ukázka.  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kód je úplný text souboru MainWindow.xaml.cs pro tento příklad. Hvězdičky označit prvky, které byly přidány v tomto příkladu.  
  
 Všimněte si, že je nutné přidat odkaz pro <xref:System.Net.Http>.  
  
 Si můžete stáhnout z projektu [asynchronní ukázka: jemné ladění vaše aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).  
  
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
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Zrušení asynchronní úlohy nebo seznamu úloh (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)  
 [Vyladění s modifikátorem Async aplikace (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
 [Ukázka asynchronního: Jemnou ladění aplikace](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
