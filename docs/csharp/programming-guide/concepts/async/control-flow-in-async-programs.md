---
title: "Řízení toku v asynchronních programech (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7a13763b2eeec93e7db7ca770c4d52b4a2ba768c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="control-flow-in-async-programs-c"></a>Řízení toku v asynchronních programech (C#)
Můžete napsat a udržovat asynchronní programy snadněji pomocí `async` a `await` klíčová slova. Ale výsledky může ať vás překvapí Pokud nevíte, jak funguje vašeho programu. Toto téma trasování, které toku řízení prostřednictvím programu jednoduché asynchronní tak, aby zobrazovalo při řízení přechází z jedné metody na jiný a jaké informace se přenáší pokaždé, když.  
  
> [!NOTE]
>  Klíčová slova `async` a `await` byla zavedena v sadě Visual Studio 2012.  
  
 Obecně platí, označit metody, které obsahují asynchronní kódu pomocí [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifikátor. Metoda, která je označena modifikátorem async, můžete použít [await (C#)](../../../../csharp/language-reference/keywords/await.md) operátor na dobu, kdy metodu pro čekání na dokončení procesu volané asynchronní. Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
 Následující příklad používá asynchronní metody pro stažení obsahu webu, zadaný jako řetězec a zobrazíte délka řetězce. V příkladu obsahuje následující dvě metody.  
  
-   `startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.  
  
-   `AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce. `AccessTheWebAsync`používá asynchronní <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, pro stažení obsahu.  
  
 Číslované zobrazení řádky se zobrazí v strategické body v rámci programu, které vám pomohou pochopit, jak program se spustí a vysvětlit, co se stane, že v každém bodu, který je označen. Zobrazení řádků, které jsou označeny "Jeden"pomocí "šest." Popisky jasné, v pořadí, ve kterém program dosáhne tyto řádky kódu.  
  
 Následující kód ukazuje přehled programu.  
  
```csharp  
public partial class MainWindow : Window  
{  
    // . . .  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    {  
        // ONE  
        Task<int> getLengthTask = AccessTheWebAsync();  
  
        // FOUR  
        int contentLength = await getLengthTask;  
  
        // SIX  
        resultsTextBox.Text +=  
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
    }  
  
    async Task<int> AccessTheWebAsync()  
    {  
        // TWO  
        HttpClient client = new HttpClient();  
        Task<string> getStringTask =  
            client.GetStringAsync("http://msdn.microsoft.com");  
  
        // THREE                   
        string urlContents = await getStringTask;  
  
        // FIVE  
        return urlContents.Length;  
    }  
}  
```  
  
 Každý místa s popiskem, "Jeden"pomocí "PŮL," zobrazí informace o aktuální stav programu. Následující výsledek.  
  
```  
ONE:   Entering startButton_Click.  
           Calling AccessTheWebAsync.  
  
TWO:   Entering AccessTheWebAsync.  
           Calling HttpClient.GetStringAsync.  
  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
  
Length of the downloaded string: 33946.  
```  
  
## <a name="set-up-the-program"></a>Vytvoření programu  
 Kód, který používá v tomto tématu můžete stáhnout z webu MSDN nebo je možné ho vytvořit sami.  
  
> [!NOTE]
>  Pokud chcete spustit v příkladu, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalovaná ve vašem počítači.  
  
### <a name="download-the-program"></a>Stažení programu  
 Si můžete stáhnout aplikaci pro toto téma z [asynchronní ukázka: řízení toku v asynchronních programech](http://go.microsoft.com/fwlink/?LinkId=255285). Následující kroky otevřete a spusťte program.  
  
1.  Rozbalte stažený soubor a pak spusťte Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **otevřete**, **projekt nebo řešení**.  
  
3.  Přejděte do složky, která obsahuje rozbalené ukázkový kód, otevřete soubor řešení (.sln) a potom vyberte klávesy F5 sestavení a spuštění projektu.  
  
### <a name="build-the-program-yourself"></a>Vytvoření programu vlastními silami  
 Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.  
  
 Pokud chcete spustit projekt, proveďte následující kroky:  
  
1.  Spuštění sady Visual Studio.  
  
2.  Na řádku nabídek zvolte **soubor**, **nový**, **projektu**.  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **nainstalovaných šablonách** podokně vyberte **Visual C#**a potom zvolte **aplikaci WPF** ze seznamu typy projektů.  
  
4.  Zadejte `AsyncTracer` jako název projektu a klikněte **OK** tlačítko.  
  
     Nový projekt se zobrazí v **Průzkumníku řešení**.  
  
5.  V editoru Visual Studio Code, vyberte **MainWindow.xaml** kartě.  
  
     Pokud na kartě není zobrazena, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a potom zvolte **kód zobrazení**.  
  
6.  V **XAML** zobrazení MainWindow.xaml, nahraďte kód následujícím kódem.  
  
    ```csharp  
    <Window  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"  
            Title="Control Flow Trace" Height="350" Width="592">  
        <Grid>  
            <Button x:Name="startButton" Content="Start  
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>  
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>  
        </Grid>  
    </Window>  
    ```  
  
     Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhu** zobrazení MainWindow.xaml.  
  
7.  Přidat odkaz pro <xref:System.Net.Http>.  
  
8.  V **Průzkumníku řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a potom zvolte **kód zobrazení**.  
  
9. V MainWindow.xaml.cs nahraďte kód následujícím kódem.  
  
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
  
    // Add a using directive and a reference for System.Net.Http;  
    using System.Net.Http;  
  
    namespace AsyncTracer  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void startButton_Click(object sender, RoutedEventArgs e)  
            {  
                // The display lines in the example lead you through the control shifts.  
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +  
                    "           Calling AccessTheWebAsync.\r\n";  
  
                Task<int> getLengthTask = AccessTheWebAsync();  
  
                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +  
                    "           Task getLengthTask is started.\r\n" +  
                    "           About to await getLengthTask -- no caller to return to.\r\n";  
  
                int contentLength = await getLengthTask;  
  
                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +  
                    "           Task getLengthTask is finished.\r\n" +  
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +  
                    "           About to display contentLength and exit.\r\n";  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
  
            async Task<int> AccessTheWebAsync()  
            {  
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";  
  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";  
  
                // GetStringAsync returns a Task<string>.   
                Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +  
                    "           Task getStringTask is started.";  
  
                // AccessTheWebAsync can continue to work until getStringTask is awaited.  
  
                resultsTextBox.Text +=  
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";  
  
                // Retrieve the website contents when task is complete.  
                string urlContents = await getStringTask;  
  
                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +  
                    "\r\n           Task getStringTask is complete." +  
                    "\r\n           Processing the return statement." +  
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";  
  
                return urlContents.Length;  
            }  
        }  
    }  
    ```  
  
10. Zvolte klávesy F5 spusťte program a potom vyberte **spustit** tlačítko.  
  
     By se zobrazit následující výstup.  
  
    ```  
    ONE:   Entering startButton_Click.  
               Calling AccessTheWebAsync.  
  
    TWO:   Entering AccessTheWebAsync.  
               Calling HttpClient.GetStringAsync.  
  
    THREE: Back in AccessTheWebAsync.  
               Task getStringTask is started.  
               About to await getStringTask & return a Task<int> to startButton_Click.  
  
    FOUR:  Back in startButton_Click.  
               Task getLengthTask is started.  
               About to await getLengthTask -- no caller to return to.  
  
    FIVE:  Back in AccessTheWebAsync.  
               Task getStringTask is complete.  
               Processing the return statement.  
               Exiting from AccessTheWebAsync.  
  
    SIX:   Back in startButton_Click.  
               Task getLengthTask is finished.  
               Result from AccessTheWebAsync is stored in contentLength.  
               About to display contentLength and exit.  
  
    Length of the downloaded string: 33946.  
    ```  
  
## <a name="trace-the-program"></a>Trasování programu  
  
### <a name="steps-one-and-two"></a>Kroky 1 a 2  
 Zobrazení první dva řádky trasování cesty k `startButton_Click` volání `AccessTheWebAsync`, a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Následující obrázek znázorňuje volání z metoda.  
  
 ![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")  
  
 Návratový typ i `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>. Pro `AccessTheWebAsync`, TResult je celé číslo. Pro `GetStringAsync`, TResult je řetězec. Další informace o asynchronní metoda návratové typy najdete v tématu [vrátit typy Async (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
 Asynchronní metody vrácení úkolů vrátí instance úlohy při řízení posune zpět k volajícímu. Vrátí ovládací prvek z asynchronní metody jeho volajícího buď když `await` operátor se vyskytuje v volané metody nebo při ukončení zavolat metodu. Zobrazení řádků, které jsou označeny "Tři"pomocí "PŮL" trasování tuto část procesu.  
  
### <a name="step-three"></a>Krok 3  
 V `AccessTheWebAsync`, asynchronní metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> je volána pro stažení obsahu cílové webové stránky. Vrátí ovládací prvek z `client.GetStringAsync` k `AccessTheWebAsync` při `client.GetStringAsync` vrátí.  
  
 `client.GetStringAsync` Metoda vrátí úlohu, řetězce, který je přiřazen k `getStringTask` proměnné v `AccessTheWebAsync`. Následující řádek v programu příklad ukazuje volání `client.GetStringAsync` a přiřazení.  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 Úlohy si můžete představit jako promise podle `client.GetStringAsync` k vytvoření nakonec konkrétní řetězec. Do té doby Pokud `AccessTheWebAsync` má práce uděláte, které nezávisí na přislíbeném řetězec z `client.GetStringAsync`, že můžete pokračovat v práci při `client.GetStringAsync` čeká. V příkladu představují následující řádky výstupu, které jsou označeny "3", tento krok provést nezávislou práci  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 Následující příkaz pozastaví průběh `AccessTheWebAsync` při `getStringTask` je očekáváno.  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 Následující obrázek zobrazuje tok řízení z `client.GetStringAsync` k přiřazení `getStringTask` a od vytvoření `getStringTask` do aplikace operátoru await.  
  
 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace tři")  
  
 Výraz await pozastaví `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí. Do té doby, vrátí ovládací prvek do volajícího `AccessTheWebAsync`, `startButton_Click`.  
  
> [!NOTE]
>  Obvykle můžete await volání asynchronní metodu okamžitě. Například následující přiřazení může nahradit předchozí kód, který vytvoří a pak čeká `getStringTask`:`string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`  
>   
>  V tomto tématu platí operátoru await pro umístění výstupní řádky, které označit toku řízení prostřednictvím programu později.  
  
### <a name="step-four"></a>Krok 4  
 Deklarovaný návratový typ `AccessTheWebAsync` je `Task<int>`. Proto když `AccessTheWebAsync` je pozastavený, vrátí úlohu celého `startButton_Click`. Byste měli vědět, že vrácený úloh není `getStringTask`. Vrácená úloha je novou úlohu celé číslo, které představuje, co je ještě provést v metodě pozastavenou `AccessTheWebAsync`. Tato úloha je promise z `AccessTheWebAsync` k vytvoření celé po dokončení úlohy.  
  
 Následující příkaz přiřadí této úlohy můžete `getLengthTask` proměnné.  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 Jako v `AccessTheWebAsync`, `startButton_Click` můžete pokračovat v práci, kterou nezávisí na výsledky asynchronní úlohy (`getLengthTask`) dokud úloha je očekáváno. Následující výstup řádky představují svou práci.  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 V průběhu `startButton_Click` je pozastaven, když `getLengthTask` je očekáváno. Následující příkaz přiřazení pozastaví `startButton_Click` dokud `AccessTheWebAsync` dokončení.  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 Na následujícím obrázku, šipky zobrazují toku řízení z výrazu await v `AccessTheWebAsync` přiřazení hodnoty k `getLengthTask`, za nímž následují normálním zpracování v `startButton_Click` dokud `getLengthTask` je očekáváno.  
  
 ![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace ČTYŘMI")  
  
### <a name="step-five"></a>Krok 5  
 Když `client.GetStringAsync` signalizuje, že se jedná o dokončení zpracování v `AccessTheWebAsync` vydání z pozastavení a můžete pokračovat přes příkaz await. Následující řádky výstupu představují obnovení zpracování.  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 Operand příkaz return `urlContents.Length`, je uložen v úloze, `AccessTheWebAsync` vrátí. Výraz await načte tuto hodnotu z `getLengthTask` v `startButton_Click`.  
  
 Následující obrázek ukazuje ovládání po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.  
  
 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace PĚT")  
  
 `AccessTheWebAsync`používá pro dokončení a řízení vrátí do `startButton_Click`, která čeká na dokončení.  
  
### <a name="step-six"></a>Krok 6  
 Když `AccessTheWebAsync` signály, které je dokončená, zpracování, můžete pokračovat přes příkaz await v `startButton_Async`. Ve skutečnosti program nijak nesouvisí Další.  
  
 Následující řádky výstupu představují obnovení zpracování v `startButton_Async`:  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 Výraz await načte z `getLengthTask` celočíselná hodnota, která je operand příkaz return v `AccessTheWebAsync`. Tuto hodnotu přiřadí do následujícího příkazu `contentLength` proměnné.  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 Následující obrázek ukazuje návratový řízení z `AccessTheWebAsync` k `startButton_Click`.  
  
 ![Krok 6](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace šest")  
  
## <a name="see-also"></a>Viz také  
 [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)  
 [Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [Ukázka asynchronního: Řízení toku v asynchronních programech (C# a Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)
