---
title: 'Postupy: Paralelní provádění více webových požadavků s použitím modifikátoru Async a operátoru Await (C#)'
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 06b70f5f3b2e1f3e7e423b16463f0b6b613f62c2
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168381"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a>Postupy: Paralelní provádění více webových požadavků s použitím modifikátoru Async a operátoru Await (C#)
V asynchronní metodě jsou úlohy spouštěny při jejich vytvoření. Operátor [await](../../../language-reference/operators/await.md) se aplikuje na úkol v místě v metodě, kde zpracování nemůže pokračovat, dokud se úloha nedokončí. Úkol se často očekává ihned po vytvoření, jak ukazuje následující příklad.  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 Můžete ale oddělit vytvoření úlohy z čekání na úkol, pokud má program další práci, která nezávisí na dokončení úkolu.  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 Mezi zahájením úlohy a čekáním na ni můžete spustit další úlohy. Další úkoly jsou implicitně spouštěny paralelně, ale nejsou vytvořeny žádné další podprocesy.  
  
 Následující program spustí tři asynchronní webové stahování a pak je očekává v pořadí, ve kterém jsou volány. Všimněte si, že při spuštění programu nejsou úlohy vždy dokončeny v pořadí, ve kterém byly vytvořeny a očekávány. Spouštějí se při jejich vytvoření a jedna nebo více úkolů může skončit předtím, než metoda dosáhne výrazů await.  
  
> [!NOTE]
> Chcete-li dokončit tento projekt, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo vyšší a .NET Framework 4,5 nebo novější.  
  
 Další příklad, který spouští více úloh současně, naleznete v tématu [How to: Pomocí Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)rozšíříte asynchronní návod.  
  
 Kód pro tento příklad si můžete stáhnout z [ukázek kódu pro vývojáře](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).  
  
### <a name="to-set-up-the-project"></a>Vytvoření projektu  
  
1. Chcete-li nastavit aplikaci WPF, proveďte následující kroky. Podrobné pokyny k těmto krokům najdete v [návodu: Přístup k webu pomocí modifikátoru Async a operátoru](./walkthrough-accessing-the-web-by-using-async-and-await.md)await (C#).  
  
    - Vytvořte aplikaci WPF, která obsahuje textové pole a tlačítko. Pojmenujte `startButton`tlačítko a pojmenujte textové `resultsTextBox`pole.  
  
    - Přidejte odkaz pro <xref:System.Net.Http>.  
  
    - Do souboru MainWindow.XAML.cs přidejte `using` direktivu pro. `System.Net.Http`  
  
### <a name="to-add-the-code"></a>Přidání kódu  
  
1. V okně návrh MainWindow. XAML dvakrát klikněte na tlačítko a vytvořte `startButton_Click` obslužnou rutinu události v MainWindow.XAML.cs.  
  
2. Zkopírujte následující kód a vložte ho do textu `startButton_Click` v MainWindow.XAML.cs.  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     Kód volá asynchronní metodu `CreateMultipleTasksAsync`, která aplikaci zařídí.  
  
3. Do projektu přidejte následující metody podpory:  
  
    - `ProcessURLAsync`<xref:System.Net.Http.HttpClient> používá metodu ke stažení obsahu webu jako bajtového pole. Metoda `ProcessURLAsync` podpory pak zobrazí a vrátí délku pole.  
  
    - `DisplayResults`zobrazí počet bajtů v bajtovém poli pro každou adresu URL. Toto zobrazení ukazuje, kdy se každý úkol dokončí stahováním.  
  
     Zkopírujte následující metody a vložte je po `startButton_Click` obslužné rutině události v MainWindow.XAML.cs.  
  
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
  
4. Nakonec definujte metodu `CreateMultipleTasksAsync`, která provede následující kroky.  
  
    - Metoda deklaruje `HttpClient` objekt, který je zapotřebí pro přístup k metodě <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> v `ProcessURLAsync`.  
  
    - Metoda vytvoří a spustí tři úkoly typu <xref:System.Threading.Tasks.Task%601>, kde `TResult` je celé číslo. Po dokončení každé úlohy se `DisplayResults` zobrazí adresa URL úlohy a délka staženého obsahu. Vzhledem k tomu, že úlohy jsou spuštěny asynchronně, pořadí, ve kterém se výsledky zobrazují, se může lišit od pořadí, ve kterém byly deklarovány.  
  
    - Metoda čeká na dokončení každého úkolu. Každý `await` operátor pozastaví provádění, `CreateMultipleTasksAsync` dokud není dokončen očekávaný úkol. Operátor také Načte návratovou hodnotu z volání `ProcessURLAsync` z každé dokončené úlohy.  
  
    - Po dokončení úloh a načtení celočíselných hodnot metoda sečte délky webů a zobrazí výsledek.  
  
     Zkopírujte následující metodu a vložte ji do svého řešení.  
  
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
  
5. Zvolte klávesu F5 ke spuštění programu a pak klikněte na tlačítko **Start** .  
  
     Spusťte program několikrát, abyste ověřili, že tři úkoly nejsou vždy dokončeny ve stejném pořadí a že pořadí, ve kterém jsou dokončeny, nemusí být nutně pořadí, ve kterém byly vytvořeny a očekávány.  
  
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

- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./index.md)
- [Postupy: Rozšíříte asynchronní návod pomocí Task. WhenAll (C#).](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
