---
title: Tok řízení v asynchronních programech (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 6a7b8f3f41b2096e3e7524d03217bdc123f26f10
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326200"
---
# <a name="control-flow-in-async-programs-c"></a>Tok řízení v asynchronních programech (C#)

Můžete napsat a snadněji udržovat asynchronní programy pomocí `async` a `await` klíčová slova. Ale výsledků možná vás překvapí Pokud nevíte, jak program pracuje. Toto téma sleduje tok řízení prostřednictvím jednoduchého asynchronního programu k zobrazení, když se ovládací prvek přesune z jedné metody na jinou a jaké informace jsou pokaždé přeneseny.

Obecně označujete metody, které obsahují asynchronní kód s [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifikátor. V metodě, která je označena asynchronním modifikátorem, můžete použít [await (C#)](../../../../csharp/language-reference/keywords/await.md) operátor k určení, kde Metoda počká na dokončení volaného asynchronního procesu. Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).

Následující příklad používá asynchronní metody ke stahování obsahu zadaného webu jako řetězec a zobrazí délku řetězce. Tento příklad obsahuje následující dvě metody.

-   `startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.

-   `AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce. `AccessTheWebAsync` používá asynchronní <xref:System.Net.Http.HttpClient> metody <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, chcete-li stáhnout obsah.

Číslované řádky se zobrazí strategická místa v celém programu, které vám pomohou pochopit, jak program funguje a co se stane v každém bodu, který je označen jako zobrazení. Zobrazené řádky jsou označeny "Jedna"až "šest." Popisky představují pořadí, ve kterém dosáhne program tyto řádky kódu.

Následující kód ukazuje osnovu třídy program.

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
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

Každé z označených míst "Jedna"až "šest" zobrazí informace o aktuálním stavu programu. Následující výstup je vytvořen:

```text
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

Kód, který se používá v tomto tématu si můžete stáhnout z webu MSDN nebo si ho můžete vytvořit sami.

> [!NOTE]
> Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

### <a name="download-the-program"></a>Stáhnout program

Můžete stáhnout aplikaci pro toto téma z [asynchronní vzorek: Řízení toku v asynchronních programech](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Následující postup otevře a spustí program.

1. Rozbalte stažený soubor a poté spusťte Visual Studio.

2. V panelu nabídky zvolte **souboru** > **otevřít** > **projekt či řešení**.

3. Přejděte do složky obsahující dekomprimovaný ukázkový kód, otevřete soubor řešení (.sln) a klikněte na tlačítko **F5** klíče pro sestavení a spuštění projektu.

### <a name="create-the-program-yourself"></a>Vytvoření programu

Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.

Spusťte projekt, proveďte následující kroky:

1. Spusťte Visual Studio.

2. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

     **Nový projekt** zobrazí se dialogové okno.

3. Zvolte **nainstalováno** > **Visual C#** > **Windows Desktop** kategorie a klikněte na tlačítko **aplikace WPF** ze seznamu šablon projektu.

4. Zadejte `AsyncTracer` jako název projektu a klikněte na tlačítko **OK** tlačítko.

     Nový projekt se zobrazí v **Průzkumníka řešení**.

5. V editoru Visual Studio Code, vyberte **souboru MainWindow.xaml** kartu.

     Pokud karta není zobrazena, otevřete místní nabídku souboru mainwindow.XAML v **Průzkumníka řešení**a klikněte na tlačítko **zobrazit kód**.

6. V **XAML** zobrazení souboru mainwindow.XAML, nahraďte kód následujícím kódem.

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

     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v **návrhu** zobrazení souboru MainWindow.xaml.

7. Přidat odkaz pro <xref:System.Net.Http>.

8. V **Průzkumníka řešení**, otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **zobrazit kód**.

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
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

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

10. Zvolte **F5** klíče ke spuštění programu a klikněte na tlačítko **Start** tlačítko.

    Zobrazí se následující výstup:

    ```text
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

První dva zobrazené řádky sledují cestu jako `startButton_Click` volání `AccessTheWebAsync`, a `AccessTheWebAsync` volá asynchronní <xref:System.Net.Http.HttpClient> metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Následující obrázek popisuje volání z metody do metody.

![Kroky 1 a 2](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")

Návratový typ obou `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>. Pro `AccessTheWebAsync`, je TResult celé číslo. Pro `GetStringAsync`, TResult je řetězec. Další informace o asynchronních návratových typech metod naleznete v tématu [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).

Asynchronní metody vracející úlohy vrátí instance úlohy, když ovládací prvek přepne zpět do volajícího. Se řízení vrací z asynchronní metodu jeho volajícímu buď pokud `await` se střetne s operátorem ve volané metodě, nebo po ukončení volané metody. Zobrazené řádky, které jsou označeny jako "Tři"až "šest" trasují tuto část procesu.

### <a name="step-three"></a>Krok 3

V `AccessTheWebAsync`, asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> volána ke stažení obsahu cílové webové stránky. Ovládací prvek vrátí `client.GetStringAsync` k `AccessTheWebAsync` při `client.GetStringAsync` vrátí.

 `client.GetStringAsync` Metoda vrátí úlohu řetězce, který je přiřazen `getStringTask` proměnné v `AccessTheWebAsync`. Následující řádek v příkladu programu ukazuje volání do `client.GetStringAsync` a přiřazení.

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 Úlohy si můžete představit jako za příslib od `client.GetStringAsync` nakonec vytvoří vytvoření skutečného řetězce. Do té doby Pokud `AccessTheWebAsync` má pracovní postup, která není závislá na přislíbeném řetězci z `client.GetStringAsync`, této práci pokračovat během `client.GetStringAsync` čeká. V tomto příkladu představují následující řádky výstupu, které nesou označení "Tři", příležitost k nezávislé práci.

```
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Následující příkaz pozastaví průběh `AccessTheWebAsync` při `getStringTask` je očekáváno.

```csharp
string urlContents = await getStringTask;
```

 Následující obrázek znázorňuje tok řízení z `client.GetStringAsync` k přiřazení na `getStringTask` a od vytvoření `getStringTask` k použití operátoru await.

 ![Krok 3](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace tři")

 Výraz await pozastaví `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí. Do té doby se ovládací prvek vrátí volajícímu metody `AccessTheWebAsync`, `startButton_Click`.

> [!NOTE]
> Obvykle můžete očekávat volání asynchronní metody okamžitě. Například následující přiřazení může nahradit předchozí kód, který vytvoří a poté očekává `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> V tomto tématu je později použit operátor await pro výstupní řádky, které označí tok řízení programem.

### <a name="step-four"></a>Krok 4

Deklarovaný návratový typ `AccessTheWebAsync` je `Task<int>`. Proto když `AccessTheWebAsync` je pozastaven, vrátí úkol čísla do `startButton_Click`. Měli byste pochopit, že vrácená úloha není `getStringTask`. Vrácený úkol je nový úkol celého čísla, která představuje, co je ještě třeba provést v pozastavené metodě `AccessTheWebAsync`. Úkol je příslib z `AccessTheWebAsync` k vytvoření celého čísla po dokončení úkolu.

Následující příkaz přiřadí tuto úlohu `getLengthTask` proměnné.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Stejně jako v `AccessTheWebAsync`, `startButton_Click` může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`) dokud je na úkol čekáno. Následující řádky výstupu představují tuto práci.

```
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 V průběhu `startButton_Click` se pozastavuje, když `getLengthTask` je očekáváno. Přiřazovací příkaz pozastaví `startButton_Click` dokud `AccessTheWebAsync` je dokončena.

```csharp
int contentLength = await getLengthTask;
```

 Na následujícím obrázku šipky zobrazují tok řízení z výrazu await v metodě `AccessTheWebAsync` k přiřazení hodnoty ke `getLengthTask`, následované běžným zpracováním v `startButton_Click` dokud `getLengthTask` je očekáváno.

 ![Krok 4](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace čtyři")

### <a name="step-five"></a>Krok 5

Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování v `AccessTheWebAsync` je uvolněno z pozastavení a může pokračovat po příkazu await. Následující řádky výstupu představují opětovné zpracování.

```
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 Operanda příkazu return, `urlContents.Length`, je uložen v úloze, která `AccessTheWebAsync` vrátí. Výraz await získá tuto hodnotu z `getLengthTask` v `startButton_Click`.

 Následující obrázek znázorňuje přenos ovládání po `client.GetStringAsync` (a `getStringTask`) jsou dokončeny.

 ![Krok 5](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace pěti")

 `AccessTheWebAsync` spuštění a dokončení, ovládací prvek vrátí na `startButton_Click`, který čeká na dokončení.

### <a name="step-six"></a>Krok 6

Když `AccessTheWebAsync` oznamuje, že je dokončeno, zpracování může pokračovat po příkazu await v `startButton_Async`. Program ve skutečnosti nemá žádnou další akci nelze provést.

Následující řádky výstupu představují opětovné zpracování ve službě `startButton_Async`:

```
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Výraz await získá z `getLengthTask` celočíselnou hodnotu, která je operandou příkazu return v `AccessTheWebAsync`. Následující příkaz přiřadí tuto hodnotu `contentLength` proměnné.

```csharp
int contentLength = await getLengthTask;
```

 Následující obrázek znázorňuje návrat ovládacího prvku z `AccessTheWebAsync` k `startButton_Click`.

 ![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")

## <a name="see-also"></a>Viz také:

- [Asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/index.md)
- [Asynchronní návratové typy (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- [Návod: Přístup k webu pomocí modifikátoru async a operátoru await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Ukázka asynchronní metody: Řízení toku v asynchronních programech (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
