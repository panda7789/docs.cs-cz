---
title: Tok řízení v asynchronních programech (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204439"
---
# <a name="control-flow-in-async-programs-c"></a>Řízení toku v asynchronních programech (C#)

Asynchronní programy můžete snadněji psát a `async` udržovat `await` pomocí klíčových slov a. Výsledky vás však mohou překvapit, pokud nerozumíte tomu, jak váš program funguje. Toto téma sleduje tok řízení prostřednictvím jednoduchého asynchronního programu, který vám ukáže, kdy se ovládací prvek přesune z jedné metody do druhé a jaké informace se přenesou pokaždé.

Obecně lze označit metody, které obsahují asynchronní kód s [asynchronní (C#)](../../../language-reference/keywords/async.md) modifikátor. V metodě, která je označena asynchronním modifikátorem, můžete použít operátor [await (C#)](../../../language-reference/operators/await.md) k určení, kde se metoda pozastaví a čeká se na dokončení takzvaného asynchronního procesu. Další informace naleznete [v tématu Asynchronní programování s asynchronní a await (C#)](./index.md).

Následující příklad používá asynchronní metody ke stažení obsahu zadaného webu jako řetězec a zobrazení délky řetězce. Příklad obsahuje následující dvě metody.

- `startButton_Click`, který `AccessTheWebAsync` volá a zobrazuje výsledek.

- `AccessTheWebAsync`, který stáhne obsah webu jako řetězec a vrátí délku řetězce. `AccessTheWebAsync`používá asynchronní <xref:System.Net.Http.HttpClient> metodu <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, ke stažení obsahu.

Číslované řádky zobrazení se zobrazují ve strategických bodech v celém programu, aby vám pomohly pochopit, jak program běží, a vysvětlit, co se děje v každém označeném bodě. Řádky zobrazení jsou označeny jako "ONE" až "SIX". Popisky představují pořadí, ve kterém program dosáhne těchto řádků kódu.

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

Každé z označených umístění,"ONE" až "SIX", zobrazuje informace o aktuálním stavu programu. Vytvoří se následující výstup:

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

Můžete si stáhnout kód, který toto téma používá z MSDN, nebo si můžete vytvořit sami.

> [!NOTE]
> Chcete-li spustit příklad, musíte mít Visual Studio 2012 nebo novější a rozhraní .NET Framework 4.5 nebo novější nainstalován v počítači.

### <a name="download-the-program"></a>Stáhněte si program

Aplikaci pro toto téma si můžete stáhnout z aplikace [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0). Otevřete následující kroky a spusťte program.

1. Rozbalte stažený soubor a spusťte visual studio.

2. Na řádku nabídek zvolte **Soubor** > **otevřít** > **projekt/řešení**.

3. Přejděte do složky, která obsahuje rozbalený ukázkový kód, otevřete soubor řešení (.sln) a pak zvolte klávesu **F5** pro sestavení a spuštění projektu.

### <a name="create-the-program-yourself"></a>Vytvořte si program sami

Následující projekt Windows Presentation Foundation (WPF) obsahuje příklad kódu pro toto téma.

Chcete-li projekt spustit, proveďte následující kroky:

1. Spusťte Visual Studio.

2. Na řádku nabídek zvolte **Soubor** > **nového** > **projektu**.

     Otevře se dialogové okno **Nový projekt.**

3. Zvolte **nainstalovaný** > **Visual C#** > Windows**Desktop** kategorie a pak zvolte **WPF App** ze seznamu šablon projektu.

4. Zadejte `AsyncTracer` jako název projektu a pak zvolte tlačítko **OK.**

     Nový projekt se zobrazí v **Průzkumníku řešení**.

5. V Editoru kódu Visual Studia zvolte kartu **MainWindow.xaml.**

     Pokud karta není viditelná, otevřete místní nabídku pro MainWindow.xaml v **Průzkumníku řešení**a pak zvolte **Zobrazit kód**.

6. V zobrazení **XAML** MainWindow.xaml nahraďte kód následujícím kódem.

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

     Jednoduché okno, které obsahuje textové pole a tlačítko se zobrazí v **návrhovém** zobrazení MainWindow.xaml.

7. Přidejte odkaz <xref:System.Net.Http>pro .

8. V **Průzkumníku řešení**otevřete místní nabídku pro MainWindow.xaml.cs a pak zvolte **Zobrazit kód**.

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

10. Zvolte klávesu **F5** pro spuštění programu a pak zvolte tlačítko **Start.**

    Zobrazí se výstup:

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

## <a name="trace-the-program"></a>Sledování programu

### <a name="steps-one-and-two"></a>Kroky 1 a 2

První dvě řádky zobrazení trasují cestu jako `startButton_Click` volání `AccessTheWebAsync` <xref:System.Net.Http.HttpClient> a <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> `AccessTheWebAsync` volají asynchronní metodu . Následující obrázek popisuje volání z metody na metodu.

![Kroky 1 a 2](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")

Návratový typ `AccessTheWebAsync` obou `client.GetStringAsync` <xref:System.Threading.Tasks.Task%601>a je . Pro `AccessTheWebAsync`, TResult je celé číslo. Pro `GetStringAsync`, TResult je řetězec. Další informace o návratových typech asynchronní metody naleznete [v tématu Asynchronní návratové typy (C#).](./async-return-types.md)

Asynchronní metoda vracející úlohu vrátí instanci úlohy, když se ovládací prvek přesune zpět na volajícího. Ovládací prvek vrátí z asynchronní metody `await` jeho volajícímu buď při operátoru je zjištěna v volané metody nebo při ukončení volané metody. Řádky zobrazení, které jsou označeny "TŘI" až "ŠEST" sledovat tuto část procesu.

### <a name="step-three"></a>Krok 3

V `AccessTheWebAsync`aplikaci je volána asynchronní metoda <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> ke stažení obsahu cílové webové stránky. Ovládací prvek `client.GetStringAsync` `AccessTheWebAsync` se `client.GetStringAsync` vrátí z při vrácení.

 Metoda `client.GetStringAsync` vrátí úlohu řetězce, který je `getStringTask` přiřazen `AccessTheWebAsync`proměnné v aplikaci . Následující řádek v ukázkovém programu `client.GetStringAsync` zobrazuje volání a přiřazení.

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 Úkol si můžete usuzovat `client.GetStringAsync` jako slib tím, že nakonec vytvoříte skutečný řetězec. Do té doby, `AccessTheWebAsync` pokud má práci na tom, že `client.GetStringAsync`nezávisí na slíbený řetězec od , že práce může pokračovat při `client.GetStringAsync` čekání. V příkladu následující řádky výstupu, které jsou označeny jako "TŘI", představují možnost dělat nezávislou práci

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 Následující příkaz pozastaví `AccessTheWebAsync` průběh `getStringTask` v případě, že je očekáván.

```csharp
string urlContents = await getStringTask;
```

 Následující obrázek znázorňuje `client.GetStringAsync` tok řízení `getStringTask` z přiřazení `getStringTask` do a z vytvoření do aplikace operátoru await.

 ![Třetí krok](./media/asynctrace-three.png "AsyncTrace-tři")

 Await výraz pozastaví, `AccessTheWebAsync` dokud `client.GetStringAsync` vrátí. Do té doby ovládací prvek vrátí `AccessTheWebAsync` `startButton_Click`volajícímu , .

> [!NOTE]
> Obvykle čekáte na volání asynchronní metody okamžitě. Například následující přiřazení může nahradit předchozí kód, který `getStringTask`vytvoří a pak čeká :`string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`
>
> V tomto tématu await operátor je použita později přizpůsobit výstupní řádky, které označují tok řízení prostřednictvím programu.

### <a name="step-four"></a>Krok 4

Deklarovaný `AccessTheWebAsync` návratový typ je `Task<int>`. Proto při `AccessTheWebAsync` pozastavení vrátí úkol celé číslo na `startButton_Click`. Měli byste pochopit, že vrácená úloha není `getStringTask`. Vrácený úkol je nový úkol celé číslo, který představuje co zbývá `AccessTheWebAsync`udělat v pozastavené metodě . Úkol je příslibem `AccessTheWebAsync` z vytvoření celého čísla po dokončení úkolu.

Následující příkaz přiřadí tento `getLengthTask` úkol proměnné.

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 Stejně `AccessTheWebAsync` `startButton_Click` jako v , může pokračovat v práci, která nezávisí`getLengthTask`na výsledcích asynchronní úlohy ( ), dokud nebude úkol očekáván. Následující výstupní řádky představují tuto práci.

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 Průběh `startButton_Click` v programu `getLengthTask` je pozastaven, když je očekáván. Následující příkaz přiřazení `startButton_Click` pozastaví, dokud není `AccessTheWebAsync` dokončena.

```csharp
int contentLength = await getLengthTask;
```

 Na následujícím obrázku šipky znázorňují tok `AccessTheWebAsync` ovládacího prvku z `getLengthTask`výrazu await `startButton_Click` do `getLengthTask` přiřazení hodnoty do aplikace , následované normálním zpracováním v aplikaci, dokud není očekáváno.

 ![Krok 4](./media/asynctrace-four.png "AsyncTrace-čtyři")

### <a name="step-five"></a>Krok 5

Když `client.GetStringAsync` signalizuje, že je `AccessTheWebAsync` kompletní, zpracování v je uvolněna z pozastavení a může pokračovat v minulosti await prohlášení. Následující řádky výstupu představují obnovení zpracování.

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 Operand příkazu return `urlContents.Length`, je uložen v `AccessTheWebAsync` úloze, která vrátí. Await výraz načte tuto `getLengthTask` `startButton_Click`hodnotu z v .

 Následující obrázek znázorňuje `client.GetStringAsync` přenos `getStringTask`ovládacího prvku po (a ) jsou kompletní.

 ![Krok 5](./media/asynctrace-five.png "AsyncTrace-pět")

 `AccessTheWebAsync`spustí do dokončení a `startButton_Click`řízení se vrátí do , který čeká na dokončení.

### <a name="step-six"></a>Krok 6

Když `AccessTheWebAsync` signalizuje, že je kompletní, zpracování může `startButton_Async`pokračovat za příkaz učekání v . Ve skutečnosti, program nemá nic víc dělat.

Následující řádky výstupu představují obnovení zpracování `startButton_Async`v :

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 Await výraz načte `getLengthTask` z celé hodnoty, která je operand příkazu return v `AccessTheWebAsync`. Následující příkaz přiřadí tuto `contentLength` hodnotu proměnné.

```csharp
int contentLength = await getLengthTask;
```

 Následující obrázek znázorňuje `AccessTheWebAsync` návrat `startButton_Click`ovládacího prvku z do .

 ![Krok 6](./media/asynctrace-six.png "AsyncTrace-ŠEST")

## <a name="see-also"></a>Viz také

- [Asynchronní programování s asynchronní a await (C#)](./index.md)
- [Asynchronní návratové typy (C#)](./async-return-types.md)
- [Návod: Přístup k webu pomocí asynchronní a čeká (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Ukázka asynchronního řízení: Tok řízení v asynchronních programech (C# a Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
