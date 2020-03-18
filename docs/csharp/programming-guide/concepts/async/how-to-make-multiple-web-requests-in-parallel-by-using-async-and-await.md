---
title: Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 9f7420113d4af83d7d057b772af307bd8d4bcc00
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169946"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Jak vytvořit více webových požadavků paralelně pomocí async a await (C#)
V asynchronní metodě jsou úlohy spuštěny při jejich vytvoření. Operátor [await](../../../language-reference/operators/await.md) je použit na úlohu v bodě metody, kde zpracování nemůže pokračovat, dokud úkol neskončí. Často je úkol očekáván, jakmile je vytvořen, jak ukazuje následující příklad.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Pokud však program má k dokončení jiné práce, která nezávisí na dokončení úkolu, můžete vytvořit úlohu od čekání na úkol.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Mezi zahájením úkolu a čekáním na něj můžete spustit další úkoly. Další úlohy implicitně spustit paralelně, ale jsou vytvořeny žádné další podprocesy.  
  
 Následující program spustí tři asynchronní webové soubory ke stažení a pak je čeká v pořadí, ve kterém jsou volány. Všimněte si, při spuštění programu, že úkoly nejsou vždy dokončeny v pořadí, ve kterém jsou vytvořeny a čekal. Začnou běžet, když jsou vytvořeny a jeden nebo více úkolů může být dokončena dříve, než metoda dosáhne await výrazy.  
  
> [!NOTE]
> K dokončení tohoto projektu musíte mít v počítači nainstalovanou visual studio 2012 nebo vyšší a rozhraní .NET Framework 4.5 nebo vyšší.  
  
 Další příklad, který spouští více úkolů současně, naleznete v [tématu Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).
  
 Kód pro tento příklad si můžete stáhnout z [ukázky kódu vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Vytvoření projektu  
  
1. Chcete-li nastavit aplikaci WPF, proveďte následující kroky. Podrobné pokyny k těmto krokům najdete v [návodu: Přístup k webu pomocí asynchronní a await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    - Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko. Pojmenujte `startButton`tlačítko a pojmenujte textové pole `resultsTextBox`.  
  
    - Přidejte odkaz <xref:System.Net.Http>pro .  
  
    - V souboru MainWindow.xaml.cs `using` přidejte `System.Net.Http`direktivu pro .  
  
### <a name="to-add-the-code"></a>Přidání kódu  
  
1. V okně návrhu MainWindow.xaml poklepejte na `startButton_Click` tlačítko a vytvořte obslužnou rutinu události v MainWindow.xaml.cs.  
  
2. Zkopírujte následující kód a vložte `startButton_Click` jej do těla v MainWindow.xaml.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kód volá asynchronní metodu `CreateMultipleTasksAsync`, která řídí aplikaci.  
  
3. Do projektu přidejte následující metody podpory:  
  
    - `ProcessURLAsync`používá <xref:System.Net.Http.HttpClient> metodu ke stažení obsahu webu jako bajtové pole. Metoda podpory `ProcessURLAsync` pak zobrazí a vrátí délku pole.  
  
    - `DisplayResults`zobrazí počet bajtů v bajtovém poli pro každou adresu URL. Tento displej se zobrazí po dokončení stahování jednotlivých úkolů.  
  
     Zkopírujte následující metody a vložte je za obslužnou rutinu `startButton_Click` události v MainWindow.xaml.cs.  
  
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
  
4. Nakonec definujte `CreateMultipleTasksAsync`metodu , která provádí následující kroky.  
  
    - Metoda deklaruje `HttpClient` objekt,který je <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> `ProcessURLAsync`třeba získat přístup k metodě v aplikaci .  
  
    - Metoda vytvoří a spustí tři <xref:System.Threading.Tasks.Task%601>úkoly typu , kde `TResult` je celé číslo. Po dokončení každého `DisplayResults` úkolu se zobrazí adresa URL úkolu a délka staženého obsahu. Vzhledem k tomu, že úlohy jsou spuštěny asynchronně, pořadí, ve kterém se zobrazí výsledky se může lišit od pořadí, ve kterém byly deklarovány.  
  
    - Metoda čeká na dokončení každého úkolu. Každý `await` operátor pozastaví `CreateMultipleTasksAsync` provádění, dokud není dokončena očekávaná úloha. Operátor také načte vrácenou hodnotu `ProcessURLAsync` z volání z každého dokončeného úkolu.  
  
    - Po dokončení úkolů a byly načteny celé hodnoty, metoda sečte délky webových stránek a zobrazí výsledek.  
  
     Zkopírujte následující metodu a vložte ji do řešení.  
  
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
  
5. Zvolte klávesu F5 pro spuštění programu a pak zvolte tlačítko **Start.**  
  
     Spusťte program několikrát ověřit, že tři úkoly nejsou vždy dokončeny ve stejném pořadí a že pořadí, ve kterém dokončení není nutně pořadí, ve kterém jsou vytvořeny a čekal.  
  
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
  
## <a name="see-also"></a>Viz také

- [Návod: Přístup k webu pomocí asynchronní a čeká (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování s asynchronní a await (C#)](./index.md)
- [Jak rozšířit asynchronní návod pomocí Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
