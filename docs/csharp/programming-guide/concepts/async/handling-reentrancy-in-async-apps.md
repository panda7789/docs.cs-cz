---
title: Zpracování Vícenásobný přístup v asynchronních aplikacíchC#()
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 67fbbd294ffe6219b58065f974543b2dd483a92c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451860"
---
# <a name="handling-reentrancy-in-async-apps-c"></a>Zpracování Vícenásobný přístup v asynchronních aplikacíchC#()

Při zahrnutí asynchronního kódu do aplikace byste měli zvážit a případně zabránit Vícenásobný přístup, která označuje, že se má znovu zadat asynchronní operace předtím, než se dokončí. Pokud neidentifikujete a nezpracováváte možnosti pro Vícenásobný přístup, může dojít k neočekávaným výsledkům.

**V tomto tématu**

- [Rozpoznávání Vícenásobný přístup](#BKMK_RecognizingReentrancy)

- [Zpracování Vícenásobný přístup](#BKMK_HandlingReentrancy)

  - [Zakázání tlačítka Start](#BKMK_DisableTheStartButton)

  - [Zrušení a restartování operace](#BKMK_CancelAndRestart)

  - [Spuštění více operací a zařazení výstupu do fronty](#BKMK_RunMultipleOperations)

- [Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample)

> [!NOTE]
> Chcete-li spustit příklad, musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

> [!NOTE]
> Protokol TLS (Transport Layer Security) verze 1,2 je teď minimální verzí, která se má použít při vývoji aplikací. Pokud se vaše aplikace zaměřuje na verzi .NET Framework starší než 4,7, přečtěte si následující článek o [osvědčených postupech TLS (Transport Layer Security) s .NET Framework](../../../../framework/network-programming/tls.md).

## <a name="BKMK_RecognizingReentrancy"></a>Rozpoznávání Vícenásobný přístup

V příkladu v tomto tématu uživatelé zvolí tlačítko **Spustit** pro zahájení asynchronní aplikace, která stáhne řadu webů a vypočítá celkový počet stažených bajtů. Synchronní verze příkladu by reagovala stejným způsobem bez ohledu na to, kolikrát uživatel vybere tlačítko, protože po prvním spuštění vlákno UI tyto události ignoruje, dokud se aplikace nedokončí. V asynchronní aplikaci ale vlákno uživatelského rozhraní nadále reaguje a před dokončením můžete znovu zadat asynchronní operaci.

Následující příklad ukazuje očekávaný výstup, pokud uživatel klikne na tlačítko **Start** pouze jednou. Seznam stažených webů se zobrazí v bajtech v bajtech každé lokality. Celkový počet bajtů se zobrazí na konci.

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Pokud však uživatel zvolí tlačítko více než jednou, obslužná rutina události je vyvolána opakovaně a proces stahování je znovu zadán pokaždé. Výsledkem je, že několik asynchronních operací je současně spuštěno, výstup vynechává výsledky a celkový počet bajtů je matoucí.

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Můžete zkontrolovat kód, který vytváří tento výstup posouváním na konec tohoto tématu. Můžete experimentovat s kódem stažením řešení do místního počítače a následným spuštěním projektu WebsiteDownload nebo pomocí kódu na konci tohoto tématu k vytvoření vlastního projektu. Další informace a pokyny najdete v tématu [Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample).

## <a name="BKMK_HandlingReentrancy"></a>Zpracování Vícenásobný přístup

V závislosti na tom, co má vaše aplikace dělat, můžete Vícenásobný přístup zpracovávat různými způsoby. Toto téma nabízí následující příklady:

- [Zakázání tlačítka Start](#BKMK_DisableTheStartButton)

  Zakáže tlačítko **Start** , když je operace spuštěná, aby ji uživatel nemohl přerušit.

- [Zrušení a restartování operace](#BKMK_CancelAndRestart)

  Zrušte všechny operace, které pořád běží, když uživatel znovu zvolí tlačítko **Start** , a pak nechte poslední vyžadovanou operaci pokračovat.

- [Spuštění více operací a zařazení výstupu do fronty](#BKMK_RunMultipleOperations)

  Povolí asynchronní spouštění všech požadovaných operací, ale koordinuje zobrazení výstupu, aby se výsledky jednotlivých operací zobrazovaly společně a v daném pořadí.

### <a name="BKMK_DisableTheStartButton"></a>Zakázání tlačítka Start

Tlačítko **Start** lze zablokovat, když je operace spuštěna, zakázáním tlačítka v horní části obslužné rutiny události `StartButton_Click`. Pak můžete znovu povolit tlačítko v rámci `finally` bloku po dokončení operace, aby uživatelé mohli aplikaci znovu spustit.

Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [části Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample). Dokončenou aplikaci si také můžete stáhnout z části [Async Samples: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název projektu je DisableStartButton.

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Text = "";

    // ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = false;

    try
    {
        await AccessTheWebAsync();
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
    // ***Enable the Start button in case you want to run the program again.
    finally
    {
        StartButton.IsEnabled = true;
    }
}
```

V důsledku změn tlačítko nereaguje, když `AccessTheWebAsync` stahuje weby, takže se tento proces nedá znovu zadat.

### <a name="BKMK_CancelAndRestart"></a>Zrušení a restartování operace

Místo zakázání tlačítka **Start** můžete ponechat tlačítko aktivní, ale pokud uživatel toto tlačítko zvolí znovu, zrušte operaci, která už je spuštěná, a nechejte operaci naposledy spuštěnou.

Další informace o zrušení najdete v tématu [jemné ladění asynchronní aplikaceC#()](./fine-tuning-your-async-application.md).

Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [části Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample). Dokončenou aplikaci si také můžete stáhnout z části [Async Samples: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název projektu je CancelAndRestart.

1. Deklarujte <xref:System.Threading.CancellationTokenSource> proměnnou `cts`, která je v oboru pro všechny metody.

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. V `StartButton_Click`určete, zda již operace probíhá. Pokud je hodnota `cts` null, žádná operace již není aktivní. Pokud hodnota není null, operace, která je již spuštěna, je zrušena.

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. Nastavte `cts` na jinou hodnotu, která představuje aktuální proces.

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. Na konci `StartButton_Click`je aktuální proces dokončený, takže nastavte hodnotu `cts` zpátky na null.

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

Následující kód ukazuje všechny změny v `StartButton_Click`. Přidané položky jsou označeny hvězdičkami.

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Clear();

    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }

    // *** Now set cts to cancel the current process if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;

    try
    {
        // ***Send cts.Token to carry the message if there is a cancellation request.
        await AccessTheWebAsync(cts.Token);

    }
    // *** Catch cancellations separately.
    catch (OperationCanceledException)
    {
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }
    // *** When the process is complete, signal that another process can proceed.
    if (cts == newCTS)
        cts = null;
}
```

V `AccessTheWebAsync`proveďte následující změny.

- Přidejte parametr pro přijetí tokenu zrušení z `StartButton_Click`.

- Použijte metodu <xref:System.Net.Http.HttpClient.GetAsync%2A> ke stažení webů, protože `GetAsync` přijímá argument <xref:System.Threading.CancellationToken>.

- Před voláním `DisplayResults` pro zobrazení výsledků každého staženého webu zkontrolujte `ct` a ověřte, zda aktuální operace nebyla zrušena.

Následující kód zobrazuje tyto změny, které jsou označeny hvězdičkami.

```csharp
// *** Provide a parameter for the CancellationToken from StartButton_Click.
async Task AccessTheWebAsync(CancellationToken ct)
{
    // Declare an HttpClient object.
    HttpClient client = new HttpClient();

    // Make a list of web addresses.
    List<string> urlList = SetUpURLList();

    var total = 0;
    var position = 0;

    foreach (var url in urlList)
    {
        // *** Use the HttpClient.GetAsync method because it accepts a
        // cancellation token.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // *** Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // *** Check for cancellations before displaying information about the
        // latest site.
        ct.ThrowIfCancellationRequested();

        DisplayResults(url, urlContents, ++position);

        // Update the total.
        total += urlContents.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

Pokud při spuštění této aplikace několikrát kliknete na tlačítko **Start** , mělo by se jednat o výsledky, které se podobají následujícímu výstupu.

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

Chcete-li odstranit částečné seznamy, odkomentujte první řádek kódu v `StartButton_Click` k vymazání textového pole pokaždé, když uživatel operaci restartuje.

### <a name="BKMK_RunMultipleOperations"></a>Spuštění více operací a zařazení výstupu do fronty

Tento třetí příklad je nejsložitější v tom, že aplikace spouští další asynchronní operace pokaždé, když uživatel zvolí tlačítko **Start** , a všechny operace, které se spouštějí k dokončení. Všechny požadované operace stahují weby ze seznamu asynchronně, ale výstup z operací je prezentován sekvenčně. To znamená, že se aktuální aktivita stahování prochází, protože se zobrazuje výstup v [rozpoznávání Vícenásobný přístup](#BKMK_RecognizingReentrancy) , ale seznam výsledků pro každou skupinu se zobrazí samostatně.

Operace sdílí globální <xref:System.Threading.Tasks.Task>, `pendingWork`, která slouží jako server gatekeeper pro proces zobrazení.

Chcete-li nastavit tento scénář, proveďte následující změny základního kódu, který je k dispozici v [části Kontrola a spuštění ukázkové aplikace](#BKMD_SettingUpTheExample). Dokončenou aplikaci si také můžete stáhnout z části [Async Samples: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06). Název projektu je QueueResults.

Následující výstup ukazuje výsledek, pokud uživatel zvolí tlačítko **Start** pouze jednou. Označení písmenem (a) označuje, že výsledek je od první zvolené tlačítko **Start** . Čísla zobrazují pořadí adres URL v seznamu cílů stahování.

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

Pokud uživatel třikrát zvolí tlačítko **Start** , aplikace vytvoří výstup podobný následujícímu řádku. Informační řádky, které začínají znakem křížku (#) sledují průběh aplikace.

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

Skupiny B a C se spustí před dokončením skupiny A, ale výstup pro každou skupinu se zobrazí samostatně. Nejprve se zobrazí celý výstup pro skupinu A následovaný celým výstupem pro skupinu B a pak všechny výstupy pro skupinu C. Aplikace vždy zobrazuje skupiny v pořadí a pro každou skupinu vždy zobrazuje informace o jednotlivých webech v pořadí, v jakém se adresy URL zobrazují v seznamu adres URL.

Nemůžete ale předpovědět pořadí, ve kterém ke stažení skutečně dojde. Po spuštění více skupin jsou všechny úlohy stahování, které generují, všechny aktivní. Nemůžete předpokládat, že A-1 se stáhne před B-1 a nemůžete předpokládat, že A-1 se stáhne před A-2.

#### <a name="global-definitions"></a>Globální definice

Vzorový kód obsahuje následující dvě globální deklarace, které jsou viditelné ze všech metod.

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

Proměnná `Task`, `pendingWork`, dohlíží na proces zobrazení a zabraňuje všem skupinám v přerušení operace zobrazení jiné skupiny. Proměnná znaku `group`, označí výstup z různých skupin a ověří tak, že se výsledky zobrazí v očekávaném pořadí.

#### <a name="the-click-event-handler"></a>Obslužná rutina události kliknutí

Obslužná rutina události `StartButton_Click`zvyšuje písmeno skupiny pokaždé, když uživatel klikne na tlačítko **Start** . Obslužná rutina pak zavolá `AccessTheWebAsync` ke spuštění operace stahování.

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // ***Verify that each group's results are displayed together, and that
    // the groups display in order, by marking each group with a letter.
    group = (char)(group + 1);
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";

    try
    {
        // *** Pass the group value to AccessTheWebAsync.
        char finishedGroup = await AccessTheWebAsync(group);

        // The following line verifies a successful return from the download and
        // display procedures.
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
}
```

#### <a name="the-accessthewebasync-method"></a>Metoda AccessTheWebAsync

Tento příklad rozdělí `AccessTheWebAsync` do dvou metod. První metoda, `AccessTheWebAsync`, spustí všechny úlohy stažení pro skupinu a nastaví `pendingWork` pro řízení procesu zobrazení. Metoda používá dotaz integrovaný v jazyce (dotaz LINQ) a <xref:System.Linq.Enumerable.ToArray%2A> ke spuštění všech úloh stažení současně.

`AccessTheWebAsync` pak zavolá `FinishOneGroupAsync`, aby čekal na dokončení jednotlivých stažení a zobrazila jeho délku.

`FinishOneGroupAsync` vrátí úkol, který je přiřazen `pendingWork` v `AccessTheWebAsync`. Tato hodnota brání přerušení jinou operací před dokončením úkolu.

```csharp
private async Task<char> AccessTheWebAsync(char grp)
{
    HttpClient client = new HttpClient();

    // Make a list of the web addresses to download.
    List<string> urlList = SetUpURLList();

    // ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();

    // ***Call the method that awaits the downloads and displays the results.
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);

    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";

    // ***This task is complete when a group has finished downloading and displaying.
    await pendingWork;

    // You can do other work here or just return.
    return grp;
}
```

#### <a name="the-finishonegroupasync-method"></a>Metoda FinishOneGroupAsync

Tato metoda cyklicky projde úlohy stahování ve skupině, které čekají na každé z nich, zobrazuje délku staženého webu a přidává délku k celkovému součtu.

První příkaz v `FinishOneGroupAsync` používá `pendingWork`, aby se zajistilo, že vstup do metody nekoliduje s operací, která je již v procesu zobrazení, nebo už čeká. Pokud taková operace probíhá, musí operace zadání počkat na její zapnutí.

```csharp
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)
{
    // ***Wait for the previous group to finish displaying results.
    if (pendingWork != null) await pendingWork;

    int total = 0;

    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    for (int i = 0; i < contentTasks.Length; i++)
    {
        // Await the download of a particular URL, and then display the URL and
        // its length.
        byte[] content = await contentTasks[i];
        DisplayResults(urls[i], content, i, grp);
        total += content.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

#### <a name="points-of-interest"></a>Body zájmu

Informační řádky, které začínají znakem křížku (#) ve výstupu objasňují, jak tento příklad funguje.

Výstup ukazuje následující vzory.

- Skupinu lze spustit, když se v předchozí skupině zobrazuje výstup, ale zobrazení výstupu předchozí skupiny není přerušeno.

    ```output
    #Starting group A.
    #Task assigned for group A. Download tasks are active.

    A-1. msdn.microsoft.com/library/hh191443.aspx                87389
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260

    #Starting group B.
    #Task assigned for group B. Download tasks are active.

    A-6. msdn.microsoft.com/library/ms404677.aspx               199186
    A-7. msdn.microsoft.com                                            53078
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915919

    B-1. msdn.microsoft.com/library/hh191443.aspx                87388
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870

    #Group A is complete.

    B-4. msdn.microsoft.com/library/hh290140.aspx               119027
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186
    B-7. msdn.microsoft.com                                            53078
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915908
    ```

- Úloha `pendingWork` má hodnotu null na začátku `FinishOneGroupAsync` pouze pro skupinu A, která začala jako první. Skupina A ještě nedokončila výraz await, když dosáhne `FinishOneGroupAsync`. Proto ovládací prvek nebyl vrácen do `AccessTheWebAsync`a první přiřazení, které `pendingWork`, neproběhlo.

- Ve výstupu se vždy zobrazí následující dva řádky společně. Kód se nikdy nepřerušil mezi zahájením operace skupiny v `StartButton_Click` a přiřazením úkolu, který `pendingWork`skupina.

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    Až skupina vstoupí `StartButton_Click`, operace nekončí výraz await, dokud operace nevstoupí do `FinishOneGroupAsync`. Proto žádná jiná operace nemůže získat řízení během tohoto segmentu kódu.

## <a name="BKMD_SettingUpTheExample"></a>Kontrola a spuštění ukázkové aplikace

Abyste lépe pochopili ukázkovou aplikaci, můžete si ji stáhnout, sestavit sami nebo si projít kód na konci tohoto tématu bez implementace aplikace.

> [!NOTE]
> Chcete-li spustit příklad jako desktopovou aplikaci Windows Presentation Foundation (WPF), musíte mít v počítači nainstalován systém Visual Studio 2012 nebo novější a .NET Framework 4,5 nebo novější.

### <a name="BKMK_DownloadingTheApp"></a>Stahování aplikace

1. Stáhněte si komprimovaný soubor z [Async Samples: Vícenásobný přístup v desktopových aplikacích .NET](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).

2. Dekomprimovat soubor, který jste stáhli, a potom spusťte Visual Studio.

3. Na panelu nabídek vyberte možnosti **soubor**, **otevřít**, **projekt/řešení**.

4. Přejděte do složky, která obsahuje dekomprimovaný ukázkový kód, a poté otevřete soubor řešení (. sln).

5. V **Průzkumník řešení**otevřete místní nabídku pro projekt, který chcete spustit, a pak zvolte **nastavit jako StartUpProject**.

6. Kliknutím na klávesy CTRL + F5 Sestavte a spusťte projekt.

### <a name="BKMK_BuildingTheApp"></a>Sestavování aplikace

Následující část poskytuje kód pro sestavení příkladu jako aplikace WPF.

##### <a name="to-build-a-wpf-app"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. Na panelu nabídek vyberte položku **soubor**, **Nový**, **projekt**.

     Otevře se dialogové okno **Nový projekt** .

3. V podokně **Nainstalované šablony** rozbalte položku **Visual C#** a potom rozbalte **okna**.

4. V seznamu typů projektů vyberte možnost **aplikace WPF**.

5. Pojmenujte projekt `WebsiteDownloadWPF`, zvolte .NET Framework verze 4,6 nebo vyšší a pak klikněte na tlačítko **OK** .

     Nový projekt se zobrazí v **Průzkumník řešení**.

6. V editoru Visual Studio Code klikněte na kartu **MainWindow. XAML** .

     Pokud karta není viditelná, otevřete místní nabídku pro MainWindow. XAML v **Průzkumník řešení**a pak zvolte **Zobrazit kód**.

7. V zobrazení **XAML** souboru MainWindow. xaml nahraďte kód následujícím kódem.

    ```csharp
    <Window x:Class="WebsiteDownloadWPF.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     Jednoduché okno obsahující textové pole a tlačítko se zobrazí v zobrazení **Návrh** souboru MainWindow. XAML.

8. V **Průzkumník řešení**klikněte pravým tlačítkem na **odkazy** a vyberte **Přidat odkaz**.

     Přidejte odkaz pro <xref:System.Net.Http>, pokud již není vybrán.

9. V **Průzkumník řešení**otevřete místní nabídku pro MainWindow.XAML.cs a pak zvolte **Zobrazit kód**.

10. V MainWindow.xaml.cs nahraďte kód následujícím kódem.

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

    // Add the following using directives, and add a reference for System.Net.Http.
    using System.Net.Http;
    using System.Threading;

    namespace WebsiteDownloadWPF
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
                InitializeComponent();
            }

            private async void StartButton_Click(object sender, RoutedEventArgs e)
            {
                // This line is commented out to make the results clearer in the output.
                //ResultsTextBox.Text = "";

                try
                {
                    await AccessTheWebAsync();
                }
                catch (Exception)
                {
                    ResultsTextBox.Text += "\r\nDownloads failed.";
                }
            }

            private async Task AccessTheWebAsync()
            {
                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                // Make a list of web addresses.
                List<string> urlList = SetUpURLList();

                var total = 0;
                var position = 0;

                foreach (var url in urlList)
                {
                    // GetByteArrayAsync returns a task. At completion, the task
                    // produces a byte array.
                    byte[] urlContents = await client.GetByteArrayAsync(url);

                    DisplayResults(url, urlContents, ++position);

                    // Update the total.
                    total += urlContents.Length;
                }

                // Display the total count for all of the websites.
                ResultsTextBox.Text +=
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
            }

            private List<string> SetUpURLList()
            {
                List<string> urls = new List<string>
                {
                    "https://msdn.microsoft.com/library/hh191443.aspx",
                    "https://msdn.microsoft.com/library/aa578028.aspx",
                    "https://msdn.microsoft.com/library/jj155761.aspx",
                    "https://msdn.microsoft.com/library/hh290140.aspx",
                    "https://msdn.microsoft.com/library/hh524395.aspx",
                    "https://msdn.microsoft.com/library/ms404677.aspx",
                    "https://msdn.microsoft.com",
                    "https://msdn.microsoft.com/library/ff730837.aspx"
                };
                return urls;
            }

            private void DisplayResults(string url, byte[] content, int pos)
            {
                // Display the length of each website. The string format is designed
                // to be used with a monospaced font, such as Lucida Console or
                // Global Monospace.

                // Strip off the "https://".
                var displayURL = url.Replace("https://", "");
                // Display position in the URL list, the URL, and the number of bytes.
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }
        }
    }
    ```

11. Stiskněte klávesy CTRL + F5 ke spuštění programu a pak několikrát zvolte tlačítko **Start** .

12. Proveďte změny z [zakázání tlačítka Start](#BKMK_DisableTheStartButton), [zrušte a restartujte operaci](#BKMK_CancelAndRestart)nebo [Spusťte více operací a](#BKMK_RunMultipleOperations) zaznamenejte výstup pro zpracování Vícenásobný přístup.

## <a name="see-also"></a>Viz také

- [Návod: přístup k webu pomocí modifikátoru Async a operátoru Await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Asynchronní programování s modifikátorem Async aC#operátoru Await ()](./index.md)
