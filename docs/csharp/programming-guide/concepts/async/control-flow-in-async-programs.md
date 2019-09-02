---
title: Řízení toku v asynchronních programechC#()
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204439"
---
# <a name="control-flow-in-async-programs-c"></a>Řízení toku v asynchronních programechC#()

Pomocí `async` klíčových slov a `await` můžete snadno psát a spravovat asynchronní programy. Pokud ale nerozumíte tomu, jak program funguje, může se stát, že se výsledky neočekávaně neznají. Toto téma sleduje tok řízení pomocí jednoduchého asynchronního programu, který vám ukáže, kdy se ovládací prvek přesouvá z jedné metody na jinou a jaké informace se přenášejí pokaždé.

Obecně je třeba označit metody, které obsahují asynchronní kód, pomocí modifikátoru [Async (C#)](../../../language-reference/keywords/async.md) . V metodě, která je označena modifikátorem Async, můžete použít operátor [await (C#)](../../../language-reference/operators/await.md) k určení, kde metoda pozastaví čekání na dokončení volaného asynchronního procesu. Další informace naleznete v tématu [asynchronní programování s Async a await (C#)](./index.md).

Následující příklad používá asynchronní metody ke stažení obsahu zadaného webu jako řetězce a k zobrazení délky řetězce. Příklad obsahuje následující dvě metody.

- `startButton_Click`, který volá `AccessTheWebAsync` a zobrazí výsledek.

- `AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce. `AccessTheWebAsync`k stažení obsahu <xref:System.Net.Http.HttpClient> používá asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>metodu.

Číslované zobrazené řádky se zobrazí ve strategických bodech v rámci programu, které vám pomůžou pochopit, jak se program spouští, a vysvětlit, co se stane v každém označeném místě. Zobrazované řádky jsou označeny "ONE" až "šest". Popisky znázorňují pořadí, ve kterém program dosáhne těchto řádků kódu.

Následující kód ukazuje osnovu programu.

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

Každé z označených umístění, "jedna" až "šest", zobrazí informace o aktuálním stavu programu. Vytvoří se následující výstup:

```output
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

## <a name="set-up-the-program"></a>Nastavení programu

Můžete si stáhnout kód, který toto téma používá z MSDN, nebo si ho můžete vytvořit sami.

> [!NOTE]
> Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

### <a name="download-the-program"></a>Stažení programu

Aplikaci pro toto téma si můžete stáhnout z [Async Sample: Řízení toku v asynchronních](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)programech. Následující kroky otevřete a spusťte v programu.

1. Rozbalte stažený soubor a potom spusťte Visual Studio.

2. Na panelu nabídek vyberte **soubor** > **otevřít** > **projekt/řešení**.

3. Přejděte do složky, která obsahuje vzorový kód Get, otevřete soubor řešení (. sln) a pak zvolte klávesu **F5** pro sestavení a spuštění projektu.

### <a name="create-the-program-yourself"></a>Vytvoření programu sami

Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.

Chcete-li spustit projekt, proveďte následující kroky:

1. Spusťte Visual Studio.

2. V panelu nabídky zvolte **souboru** > **nový** > **projektu**.

     **Nový projekt** zobrazí se dialogové okno.

3. Zvolte kategorii **nainstalovaného** > **vizuálu C#**   >  **desktopu Windows** a pak v seznamu šablon projektů vyberte možnost **aplikace WPF** .

4. Jako `AsyncTracer` název projektu zadejte a pak klikněte na tlačítko **OK** .

     Nový projekt se zobrazí v **Průzkumník řešení**.

5. V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .

     Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.

6. V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.

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

     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.

7. Přidejte odkaz pro <xref:System.Net.Http>.

8. V **Průzkumník řešení**otevřete místní nabídku pro MainWindow.XAML.cs a pak zvolte **Zobrazit kód**.

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

10. Zvolte klávesu **F5** ke spuštění programu a pak klikněte na tlačítko **Start** .

    Zobrazí se následující výstup:

    ```output
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

První dva zobrazené řádky `startButton_Click` sledují cestu jako volání `AccessTheWebAsync`a `AccessTheWebAsync` volají asynchronní <xref:System.Net.Http.HttpClient> metodu <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>. Následující obrázek znázorňuje volání metody z metody do metody.

![Kroky 1 a 2](./media/asynctrace-onetwo.png "AsyncTrace – ONETWO")

Návratový typ obojí `AccessTheWebAsync` a `client.GetStringAsync` je <xref:System.Threading.Tasks.Task%601>. Pro `AccessTheWebAsync`TResult je celé číslo. V `GetStringAsync`případě je TResult řetězec. Další informace o návratových typech asynchronní metody naleznete v tématu [Async Return TypesC#()](./async-return-types.md).

Asynchronní metoda vracející úlohu vrátí instanci úlohy, pokud se ovládací prvek posune zpět na volajícího. Řízení se vrátí z asynchronní metody volajícímu buď v případě `await` , že je v volané metodě zjištěn operátor nebo když volaná metoda končí. V této části procesu jsou zobrazené řádky s označením "tři" až "šest".

### <a name="step-three"></a>Krok 3

V `AccessTheWebAsync`systému je volána asynchronní <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> metoda pro stažení obsahu cílové webové stránky. Ovládací prvek vrátí `client.GetStringAsync` z `AccessTheWebAsync` na `client.GetStringAsync` hodnotu when.

 Metoda vrátí úlohu řetězce, který je přiřazen `getStringTask` proměnné v `AccessTheWebAsync`. `client.GetStringAsync` Následující řádek v ukázkovém programu zobrazuje volání `client.GetStringAsync` a přiřazení.

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 Úkol si můžete představit jako příslib tím, že `client.GetStringAsync` budete chtít vytvořit skutečný řetězec nakonec. Pokud `AccessTheWebAsync` v tuto chvíli funguje práce, která nezávisí na přislíbeném řetězci z `client.GetStringAsync`, může tato práce pokračovat během `client.GetStringAsync` čekání. V příkladu představují následující řádky výstupu, které jsou označeny "tři", možnost provést nezávislou práci.

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Následující příkaz pozastaví průběh v `AccessTheWebAsync` případě, kdy `getStringTask` je očekáván.

```csharp
string urlContents = await getStringTask;
```

 Následující obrázek ukazuje tok řízení od `client.GetStringAsync` k přiřazení do `getStringTask` `getStringTask` a od vytvoření k aplikaci operátoru await.

 ![Krok 3](./media/asynctrace-three.png "AsyncTrace – tři")

 Výraz Await se pozastaví `AccessTheWebAsync` , `client.GetStringAsync` dokud se nevrátí. Mezitím se ovládací prvek vrátí volajícímu `AccessTheWebAsync`,. `startButton_Click`

> [!NOTE]
> Obvykle očekáváte okamžité volání asynchronní metody. Například následující přiřazení může nahradit předchozí kód, který vytvoří a následně očekává `getStringTask`:`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> V tomto tématu se použije operátor await později, aby se vešel na výstupní řádky, které označují tok řízení přes program.

### <a name="step-four"></a>Krok 4

Deklarovaný návratový typ `AccessTheWebAsync` je `Task<int>`. Proto když `AccessTheWebAsync` je pozastaveno, vrátí úlohu typu Integer na `startButton_Click`. Měli byste pochopit, že vrácená úloha není `getStringTask`. Vrácený úkol je nový úkol na celé číslo, který představuje to, co je potřeba udělat v pozastavené `AccessTheWebAsync`metodě. Úkol je příslib z `AccessTheWebAsync` a vytvoří celé číslo po dokončení úkolu.

Následující příkaz přiřadí tuto úlohu k `getLengthTask` proměnné.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Stejně jako `AccessTheWebAsync`v `startButton_Click` aplikaci může pokračovat v práci, která nezávisí na výsledcích asynchronní úlohy (`getLengthTask`), dokud není očekávána úloha. Následující výstupní řádky označují, že fungují.

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 Průběh je pozastaven, když `getLengthTask` je očekáváno. `startButton_Click` Následující příkaz přiřazení se pozastaví `startButton_Click` , `AccessTheWebAsync` dokud není dokončen.

```csharp
int contentLength = await getLengthTask;
```

 Na následujícím obrázku šipky ukazují tok řízení z výrazu await `AccessTheWebAsync` v pro přiřazení hodnoty k `getLengthTask`, následované normálním zpracováním v `startButton_Click` `getLengthTask` případě, že je očekáváno.

 ![Krok 4](./media/asynctrace-four.png "AsyncTrace – čtyři")

### <a name="step-five"></a>Krok 5

Když `client.GetStringAsync` signalizuje, že je dokončeno, zpracování `AccessTheWebAsync` v nástroji je uvolněno z pozastavení a může pokračovat za příkazem await. Následující řádky výstupu reprezentují pokračování zpracování.

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 Operand příkazu return, `urlContents.Length`, je uložen v úloze, která `AccessTheWebAsync` vrací. Výraz Await načte tuto hodnotu z `getLengthTask` v. `startButton_Click`

 Následující obrázek znázorňuje přenos řízení po `client.GetStringAsync` dokončení (a `getStringTask`).

 ![Krok 5](./media/asynctrace-five.png "AsyncTrace – pět")

 `AccessTheWebAsync`Spustí se k dokončení a řízení se vrátí `startButton_Click`do, což čeká na dokončení.

### <a name="step-six"></a>Krok 6

Když `AccessTheWebAsync` signalizuje, že je dokončeno, zpracování může pokračovat za příkazem await v `startButton_Async`. Ve skutečnosti program nemá nic dalšího.

Následující řádky výstupu reprezentují pokračování zpracování v `startButton_Async`:

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Výraz Await se načte z `getLengthTask` celočíselné hodnoty, která je operandem příkazu return v `AccessTheWebAsync`. Následující příkaz přiřadí tuto hodnotu k `contentLength` proměnné.

```csharp
int contentLength = await getLengthTask;
```

 Následující obrázek ukazuje vrácení ovládacího prvku z `AccessTheWebAsync` na. `startButton_Click`

 ![Krok 6](./media/asynctrace-six.png "AsyncTrace – šest")

## <a name="see-also"></a>Viz také:

- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./index.md)
- [Asynchronní návratové typyC#()](./async-return-types.md)
- [Návod: Přístup k webu pomocí modifikátoru Async a operátoru Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní Ukázka: Řízení toku v asynchronních programechC# (a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
