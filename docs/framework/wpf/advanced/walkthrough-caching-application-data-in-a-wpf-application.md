---
title: 'Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
ms.openlocfilehash: 2609a54ce8ba2076c35567fe5bc1d9961f6fef3f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942063"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF
Ukládání do mezipaměti umožňuje ukládat data v paměti pro rychlý přístup. Po opětovném přístup k datům mohou aplikace získat data z mezipaměti, nikoli načíst je z původního zdroje. To může zvýšit výkon a škálovatelnost. Ukládání do mezipaměti navíc zpřístupňuje data v případě, že zdroj dat není dočasně k dispozici.

 .NET Framework poskytuje třídy, které umožňují používat ukládání do mezipaměti v aplikacích .NET Framework. Tyto třídy jsou umístěny v <xref:System.Runtime.Caching> oboru názvů.

> [!NOTE]
> <xref:System.Runtime.Caching> Obor názvů je v .NET Framework 4 nový. Tento obor názvů zpřístupňuje ukládání do mezipaměti pro všechny .NET Framework aplikace. V předchozích verzích .NET Framework bylo ukládání do mezipaměti k dispozici pouze v <xref:System.Web> oboru názvů, a proto je vyžadována závislost na třídách ASP.NET.

 V tomto návodu se dozvíte, jak používat funkce ukládání do mezipaměti, které jsou k dispozici v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] .NET Framework jako součást aplikace. V tomto návodu ukládáte obsah textového souboru do mezipaměti.

 Tento návod obsahuje následující úlohy:

- Vytvoření projektu aplikace WPF.

- Přidání odkazu na .NET Framework 4.

- Inicializuje se mezipaměť.

- Přidání položky mezipaměti, která obsahuje obsah textového souboru.

- Poskytnutí zásad vyřazení pro položku mezipaměti.

- Monitorování cesty k souboru uloženého v mezipaměti a oznamování instance mezipaměti o změnách monitorované položky.

## <a name="prerequisites"></a>Požadavky
 Aby bylo možné dokončit tento návod, budete potřebovat:

- Microsoft Visual Studio 2010.

- Textový soubor, který obsahuje malé množství textu. (Obsah textového souboru se zobrazí v okně se zprávou.) Kód, který je znázorněn v návodu, předpokládá, že pracujete s následujícím souborem:

     `c:\cache\cacheText.txt`

     V tomto návodu ale můžete použít libovolný textový soubor a udělat drobné změny kódu.

## <a name="creating-a-wpf-application-project"></a>Vytvoření projektu aplikace WPF
 Začnete vytvořením projektu aplikace WPF.

#### <a name="to-create-a-wpf-application"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. V nabídce **soubor** klikněte na příkaz **Nový**a potom klikněte na **Nový projekt**.

     **Nový projekt** se zobrazí dialogové okno.

3. V části **Nainstalované šablony**vyberte programovací jazyk, který chcete použít (**Visual Basic** nebo **vizuál C#** ).

4. V dialogovém okně **Nový projekt** vyberte **aplikace WPF**.

    > [!NOTE]
    > Pokud nevidíte šablonu **aplikace WPF** , ujistěte se, že cílíte na verzi .NET Framework, která podporuje WPF. V dialogovém okně **Nový projekt** vyberte ze seznamu položku .NET Framework 4.

5. Do textového pole **název** zadejte název projektu. Můžete například zadat **WPFCaching**.

6. Zaškrtněte políčko **vytvořit adresář pro řešení** .

7. Klikněte na **OK**.

     Návrhář WPF se otevře v **návrhovém** zobrazení a zobrazí soubor MainWindow. XAML. Visual Studio vytvoří složku **moje projekt** , soubor Application. XAML a soubor MainWindow. XAML.

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Cílení na .NET Framework a přidání odkazu na sestavení pro ukládání do mezipaměti
 Ve výchozím nastavení aplikace WPF cílí na [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Chcete-li <xref:System.Runtime.Caching> použít obor názvů v aplikaci WPF, musí aplikace cílit na .NET Framework 4 (ne na [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) a musí zahrnovat odkaz na obor názvů.

 Proto je dalším krokem Změna cíle .NET Framework a přidání odkazu na <xref:System.Runtime.Caching> obor názvů.

> [!NOTE]
> Postup změny cíle .NET Framework se liší v projektu Visual Basic a ve vizuálním C# projektu.

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Změna cílového .NET Framework v Visual Basic

1. V **Průzkumníku řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **vlastnosti**.

     Zobrazí se okno Vlastnosti aplikace.

2. Klikněte na kartu **kompilovat** .

3. V dolní části okna klikněte na možnost **Pokročilé možnosti kompilace...** .

     Zobrazí se dialogové okno **Upřesnit nastavení kompilátoru** .

4. V seznamu **cílové rozhraní (všechny konfigurace)** vyberte .NET Framework 4. (Nevybírejte [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)

5. Klikněte na **OK**.

     **Změnit cílový rámec** se zobrazí dialogové okno.

6. V dialogovém okně **změnit cílovou architekturu** klikněte na tlačítko **Ano**.

     Projekt je uzavřený a pak se znovu otevřel.

7. Pomocí následujících kroků přidejte odkaz na sestavení pro ukládání do mezipaměti:

    1. V **Průzkumník řešení**klikněte pravým tlačítkem na název projektu a pak klikněte na **Přidat odkaz**.

    2. Vyberte kartu **.NET** , vyberte `System.Runtime.Caching`a pak klikněte na **OK**.

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Změna cílového .NET Framework ve vizuálním C# projektu

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na název projektu a pak klikněte na **vlastnosti**.

     Zobrazí se okno Vlastnosti aplikace.

2. Klikněte na kartu **aplikace** .

3. V seznamu **cílové rozhraní** vyberte .NET Framework 4. (Nevybírejte **.NET Framework 4 profil klienta**.)

4. Pomocí následujících kroků přidejte odkaz na sestavení pro ukládání do mezipaměti:

    1. Klikněte pravým tlačítkem na složku **odkazy** a pak klikněte na **Přidat odkaz**.

    2. Vyberte kartu **.NET** , vyberte `System.Runtime.Caching`a pak klikněte na **OK**.

## <a name="adding-a-button-to-the-wpf-window"></a>Přidání tlačítka do okna WPF
 Dále přidáte ovládací prvek tlačítko a vytvoříte obslužnou rutinu události pro `Click` událost tlačítka. Později přidáte kód, takže když kliknete na tlačítko, obsah textového souboru se uloží do mezipaměti a zobrazí se.

#### <a name="to-add-a-button-control"></a>Přidání ovládacího prvku tlačítko

1. V **Průzkumník řešení**dvakrát klikněte na soubor MainWindow. XAML a otevřete ho.

2. Z **panelu nástrojů**v části **běžné ovládací prvky WPF**přetáhněte `Button` ovládací prvek do `MainWindow` okna.

3. V okně **vlastnosti** nastavte `Content` vlastnost `Button` ovládacího prvku na **získat mezipaměť**.

## <a name="initializing-the-cache-and-caching-an-entry"></a>Inicializuje se mezipaměť a zapíše do mezipaměti záznam.
 V dalším kroku přidáte kód, který provede následující úlohy:

- Vytvořte instanci třídy cache – to znamená, že vytvoříte instanci nového <xref:System.Runtime.Caching.MemoryCache> objektu.

- Určuje, že mezipaměť používá <xref:System.Runtime.Caching.HostFileChangeMonitor> objekt k monitorování změn v textovém souboru.

- Přečtěte si textový soubor a zapíšete jeho obsah do mezipaměti jako položku mezipaměti.

- Zobrazí obsah textového souboru v mezipaměti.

#### <a name="to-create-the-cache-object"></a>Vytvoření objektu mezipaměti

1. Dvakrát klikněte na tlačítko, které jste právě přidali, aby se vytvořila obslužná rutina události v souboru MainWindow.xaml.cs nebo MainWindow. XAML. vb.

2. V horní části souboru (před deklarací třídy) přidejte následující `Imports` příkazy (Visual Basic) nebo `using` (C#):

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. V obslužné rutině události přidejte následující kód pro vytvoření instance objektu Cache:

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache> Třída je vestavěná třída, která poskytuje mezipaměť objektů v paměti.

4. Přidejte následující kód pro čtení obsahu položky mezipaměti s názvem `filecontents`:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. Přidejte následující kód, který zkontroluje, zda existuje položka mezipaměti `filecontents` s názvem:

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     Pokud zadaná položka mezipaměti neexistuje, musíte si přečíst textový soubor a přidat ho jako položku mezipaměti do mezipaměti.

6. V bloku přidejte následující kód pro vytvoření nového <xref:System.Runtime.Caching.CacheItemPolicy> objektu, který určuje, že platnost položky mezipaměti vyprší po 10 sekundách. `if/then`

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     Pokud nejsou k dispozici žádné informace o vyřazení nebo vypršení <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>platnosti, výchozí hodnota je, což znamená, že položky mezipaměti nikdy neprošly platností na základě pouze absolutního času. Místo toho vyprší platnost položek mezipaměti pouze v případě, že dojde k tlaku na paměť. V souladu s osvědčeným postupem byste vždy měli explicitně zadat absolutní nebo klouzavé vypršení platnosti.

7. `if/then` Uvnitř bloku a za kódem, který jste přidali v předchozím kroku, přidejte následující kód, který vytvoří kolekci pro cesty k souborům, které chcete monitorovat, a přidejte cestu k textovému souboru do kolekce:

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    > Pokud textový soubor, který chcete použít `c:\cache\cacheText.txt`, není, zadejte cestu, kde je textový soubor, který chcete použít.

8. Po kódu, který jste přidali v předchozím kroku, přidejte následující kód pro přidání nového <xref:System.Runtime.Caching.HostFileChangeMonitor> objektu do kolekce monitorování změn pro položku mezipaměti:

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor> Objekt sleduje cestu k textovému souboru a upozorní mezipaměť, pokud dojde k provedeným změnám. V tomto příkladu vyprší platnost položky mezipaměti, pokud dojde ke změně obsahu souboru.

9. Po kódu, který jste přidali v předchozím kroku, přidejte následující kód, který přečte obsah textového souboru:

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     Časové razítko pro datum a čas je přidané, takže budete moct zobrazit, kdy vyprší platnost položky mezipaměti.

10. Po kódu, který jste přidali v předchozím kroku, přidejte následující kód pro vložení obsahu souboru do objektu mezipaměti jako <xref:System.Runtime.Caching.CacheItem> instanci:

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     Informace o tom, jak by měla být položka mezipaměti vyřazena, zadáte <xref:System.Runtime.Caching.CacheItemPolicy> předáním objektu, který jste vytvořili dříve jako parametr.

11. `if/then` Po bloku přidejte následující kód pro zobrazení obsahu souboru uloženého v mezipaměti v okně se zprávou:

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. V nabídce **sestavení** klikněte na **sestavit WPFCaching** a sestavte projekt.

## <a name="testing-caching-in-the-wpf-application"></a>Testování ukládání do mezipaměti v aplikaci WPF
 Nyní můžete aplikaci otestovat.

#### <a name="to-test-caching-in-the-wpf-application"></a>Testování ukládání do mezipaměti v aplikaci WPF

1. Stisknutím kombinace kláves CTRL + F5 spusťte aplikaci.

     Zobrazí `MainWindow` se okno.

2. Klikněte na **získat mezipaměť**.

     Obsah uložený v mezipaměti z textového souboru se zobrazí v okně se zprávou. Všimněte si časového razítka v souboru.

3. Zavřete okno se zprávou a pak znovu klikněte na **načíst mezipaměť** .

     Časové razítko je beze změny. To znamená, že se zobrazí obsah uložený v mezipaměti.

4. Počkejte 10 sekund nebo více a pak znovu klikněte na **načíst mezipaměť** .

     Tentokrát se zobrazí nové časové razítko. To znamená, že zásada umožňuje vypršení platnosti položky mezipaměti a zobrazí se nový obsah uložený v mezipaměti.

5. V textovém editoru otevřete textový soubor, který jste vytvořili. Zatím žádné změny neprovádějte.

6. Zavřete okno se zprávou a pak znovu klikněte na **načíst mezipaměť** .

     Všimněte si časového razítka znovu.

7. Proveďte změnu v textovém souboru a pak soubor uložte.

8. Zavřete okno se zprávou a pak znovu klikněte na **načíst mezipaměť** .

     Toto okno se zprávou obsahuje aktualizovaný obsah z textového souboru a nové časové razítko. To znamená, že sledování změn v hostitelském souboru vyřadí položku mezipaměti hned po změně souboru, a to i v případě, že nevypršela absolutní doba časového limitu.

    > [!NOTE]
    > Dobu vyřazení můžete zvýšit na 20 sekund nebo více, aby bylo možné provést změnu v souboru více času.

## <a name="code-example"></a>Příklad kódu
 Po dokončení tohoto návodu se kód projektu, který jste vytvořili, podobá následujícímu příkladu.

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [Ukládání do vyrovnávací paměti v aplikacích .NET Framework](../../performance/caching-in-net-framework-applications.md)
