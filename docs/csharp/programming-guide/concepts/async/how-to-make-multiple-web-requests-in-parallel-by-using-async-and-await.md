---
title: 'Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru async a operátoru await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 3ea41c1fa0fce3a35635e069061f1953c6395406
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335417"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Postupy: Paralelní provádění vícenásobných webových pomocí modifikátoru async a operátoru await (C#)
V asynchronní metodě jsou úlohy spuštěny při jejich vytvoření. [Await](../../../../csharp/language-reference/keywords/await.md) operátor je použít pro úlohu v okamžiku v metodě, kdy zpracování nemůže pokračovat, dokud neskončí úloha. Úloha je často očekávaná ihned, jakmile se vytvoří, jak ukazuje následující příklad.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Však můžete oddělit vytvoření úkolu od čekání na úkol, pokud má váš program provádět jinou práci, která nezávisí na dokončení úkolu.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Mezi spuštěním úlohy a čekáním na ni, můžete spustit další úkoly. Další úkoly jsou implicitně spuštěny paralelně, ale žádná další vlákna nejsou vytvořena.  
  
 Následující program spustí tři asynchronní webové soubory ke stažení a pak je čeká v pořadí, ve kterém jsou volány. Všimněte si, když spustíte program, která nejsou úlohy vždy dokončeny v pořadí, ve kterém byly vytvořeny a očekávány. Spuštění spustit, když jste vytvořili, a jeden nebo více úkolů může skončit dříve, než metoda dosáhne výrazů await.  
  
> [!NOTE]
>  Abyste mohli absolvovat tento projekt, musíte mít Visual Studio 2012 nebo novějším a rozhraní .NET Framework 4.5 nebo vyšší v počítači nainstalována.  
  
 Další příklad spuštění více úloh současně, najdete v části [jak: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Můžete stáhnout kód pro tento příklad z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Vytvoření projektu  
  
1. Chcete-li nastavit aplikaci WPF, proveďte následující kroky. Můžete najít podrobné pokyny k těmto krokům uvádí [názorný postup: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Vytvoření aplikace WPF, která obsahuje textové pole a tlačítko. Pojmenujte tlačítko `startButton`a pojmenujte textového pole `resultsTextBox`.  
  
    -   Přidat odkaz pro <xref:System.Net.Http>.  
  
    -   V souboru MainWindow.xaml.cs přidejte `using` směrnice pro `System.Net.Http`.  
  
### <a name="to-add-the-code"></a>Přidání kódu  
  
1. V okně návrhu, MainWindow.xaml, dvakrát klikněte na tlačítko vytvořit `startButton_Click` obslužné rutině událostí ve MainWindow.xaml.cs.  
  
2. Zkopírujte následující kód a vložte ho do těla `startButton_Click` v MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kód volá asynchronní metodu, `CreateMultipleTasksAsync`, která řídí aplikaci.  
  
3. Do projektu přidejte následující metody podpory:  
  
    -   `ProcessURLAsync` používá <xref:System.Net.Http.HttpClient> metodu pro stažení obsahu webu jako bajtové pole. Podpůrná metoda `ProcessURLAsync` potom zobrazí a vrátí délku pole.  
  
    -   `DisplayResults` Zobrazí počet bajtů pro každou adresu URL v bajtovém poli. Toto zobrazení se ukazuje po dokončení stahování jednotlivých úkolů.  
  
     Následující metody zkopírujte a vložte je za `startButton_Click` obslužné rutině událostí ve MainWindow.xaml.cs.  
  
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
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. Nakonec definujte metodu `CreateMultipleTasksAsync`, který provede následující kroky.  
  
    -   Deklaruje metodu `HttpClient` objekt, který potřebuje získat přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.  
  
    -   Metoda vytvoří a spustí tři úkoly typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo. Když každý úkol dokončí, `DisplayResults` zobrazí adresu URL úkolu a délku staženého obsahu. Vzhledem k tomu, že úkoly jsou spouštěny asynchronně, pořadí, ve kterém se zobrazí výsledky mohou lišit od pořadí, ve kterém byly deklarovány.  
  
    -   Metoda čeká na ukončení každého úkolu. Každý `await` operátor pozastaví provádění `CreateMultipleTasksAsync` dokud nebude dokončena očekávaná úloha. Operátor také použije vrácenou hodnotu z volání `ProcessURLAsync` z každého dokončeného úkolu.  
  
    -   Když byly úlohy dokončeny a celočíselné hodnoty byly načteny, metoda sečte délky webových stránek a zobrazí výsledek.  
  
     Následující metodu zkopírujte a vložte ho do vašeho řešení.  
  
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
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. Stisknutím klávesy F5 spusťte program a klikněte na tlačítko **Start** tlačítko.  
  
     Spusťte program několikrát a ověřte, že ve stejném pořadí nejsou vždy dokončeny tři úkoly a pořadí, ve kterém jsou dokončeny není nutně pořadí, ve kterém byly vytvořeny a očekávány.  
  
## <a name="example"></a>Příklad  
 Následující kód obsahuje úplný příklad.  
  
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
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
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
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a>Viz také:

- [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Postupy: Rozšíření návodu úloh pomocí metody Task.whenall asynchronních (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
