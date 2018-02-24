---
title: "Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 509f9e690a5157c2d80ba9726354ce57a9d7ff26
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Postupy: paralelní provádění vícenásobných webových dotazů pomocí modifikátoru async a operátoru await (C#)
V asynchronní metody když vytváří se spustí úlohy. [Await](../../../../csharp/language-reference/keywords/await.md) operátor se použije pro úlohu v okamžiku v metodě kde zpracování nemůže pokračovat, dokud na dokončení úlohy. Úloha je často očekáváno, jakmile je vytvořen, jako ukazuje následující příklad.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Můžete však oddělit, vytvoření úlohy z čeká na úlohy, pokud má jinou práci provedete program, který nezávisí na dokončení úlohy.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Mezi počáteční úlohu a čeká na jeho, můžete spustit další úlohy. Další úlohy implicitně paralelní spuštění, ale jsou vytvořeny žádné další vlákna.  
  
 Následující program spustí tři asynchronní webové stahování a pak je čeká v pořadí, ve kterém jsou volány. Všimněte si, při spuštění programu, který úlohy není vždy dokončit v pořadí, ve kterém byly vytvořeny nebo očekáváno. Spuštění spustit, když vytvoříte a jeden nebo více úkolů může dokončit před metodu dosáhne await výrazy.  
  
> [!NOTE]
>  K dokončení tohoto projektu, musíte mít Visual Studio 2012 nebo vyšší a rozhraní .NET Framework 4.5 nebo vyšší v počítači nainstalována.  
  
 Další příklad, která se spouští ve stejnou dobu více úloh, najdete v části [postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Si můžete stáhnout kód v tomto příkladu z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Vytvoření projektu  
  
1.  Pokud chcete nastavit aplikaci WPF, proveďte následující kroky. Najdete podrobné pokyny pro tyto kroky v [návod: přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko. Název tlačítka `startButton`a název textového pole `resultsTextBox`.  
  
    -   Přidat odkaz pro <xref:System.Net.Http>.  
  
    -   V souboru MainWindow.xaml.cs přidat `using` direktivy pro `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Přidání kódu  
  
1.  V okně návrhu MainWindow.xaml, dvakrát klikněte na tlačítko vytvořit `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs.  
  
2.  Zkopírujte následující kód a vložte jej do textu `startButton_Click` v MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kód volá asynchronní metodu, `CreateMultipleTasksAsync`, jednotky, které se aplikace.  
  
3.  Do projektu přidejte následující metody podpory:  
  
    -   `ProcessURLAsync` používá <xref:System.Net.Http.HttpClient> metoda pro stažení obsahu webu, jako bajtové pole. V případě metody podporu `ProcessURLAsync` pak zobrazí a vrátí délku pole.  
  
    -   `DisplayResults` Zobrazí počet bajtů v bajtové pole pro každou adresu URL. Toto zobrazení zobrazí, když každý úkol dokončí stahování.  
  
     Zkopírujte následující metody a vložte je po `startButton_Click` obslužné rutiny událostí v MainWindow.xaml.cs.  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "http://".  
        var displayURL = url.Replace("http://", "");  
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
    }  
    ```  
  
4.  Nakonec zadejte metoda `CreateMultipleTasksAsync`, který provede následující kroky.  
  
    -   Deklaruje metodu `HttpClient` objekt, který potřebujete přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.  
  
    -   Metoda vytvoří a spustí tři úlohy typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo. Když každý úkol dokončí, `DisplayResults` zobrazí adresa URL úkolu a délka stažený obsah. Vzhledem k tomu, že úlohy běží asynchronně, pořadí, ve kterém se zobrazí výsledky se může lišit od pořadí, ve kterém bylo deklarováno.  
  
    -   Metoda čeká na dokončení každé úlohy. Každý `await` operátor pozastaví spuštění `CreateMultipleTasksAsync` dokončení awaited úloh. Operátor také načte návratová hodnota z volání `ProcessURLAsync` z každé dokončené úlohy.  
  
    -   Když byly dokončeny úlohy a byly získány celočíselné hodnoty, metoda sečte délek weby a zobrazí výsledek.  
  
     Zkopírujte následující metodu a vložte jej do řešení.  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults   
        // displays its length.  
        Task<int> download1 =   
            ProcessURLAsync("http://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text +=  
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
    }  
    ```  
  
5.  Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
     Spusťte program pro ověření, že tři úlohy není vždy dokončit ve stejném pořadí a pořadí, ve kterém dokončit není nutně pořadí, ve které jste vytvořili a očekávaná několikrát.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje kompletní příklad.  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults   
            // displays its length.  
            Task<int> download1 =   
                ProcessURLAsync("http://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text +=  
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);  
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "http://".  
            var displayURL = url.Replace("http://", "");  
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Postupy: rozšíření asynchronní návod podle pomocí metody Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
