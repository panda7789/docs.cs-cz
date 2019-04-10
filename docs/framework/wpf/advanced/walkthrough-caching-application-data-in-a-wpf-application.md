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
ms.openlocfilehash: 1d00c222dabf446c7c102307c3b904d3f1ff4bca
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314387"
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF
Ukládání do mezipaměti umožňuje uložit data do paměti pro rychlý přístup. Když je znovu přístupu k datům, aplikacím můžete získat data z mezipaměti namísto načítání z původního zdroje. Tím lze vylepšit výkon a škálovatelnost. Navíc umožňuje ukládání dat do mezipaměti k dispozici při zdroj dat je dočasně nedostupný.

 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje třídy, které vám umožní používat ukládání do mezipaměti v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikací. Tyto třídy se nacházejí v <xref:System.Runtime.Caching> oboru názvů.

> [!NOTE]
>  <xref:System.Runtime.Caching> Obor názvů je novinkou [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Tento obor názvů umožňuje ukládání do mezipaměti je k dispozici všem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikací. V předchozích verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ukládání do mezipaměti byla k dispozici pouze ve <xref:System.Web> obor názvů a proto požadovaná závislost na třídách technologie ASP.NET.

 Tento návod ukazuje, jak používat ukládání do mezipaměti funkce, které jsou k dispozici v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jako součást [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace. V tomto návodu můžete ukládat do mezipaměti obsah textového souboru.

 Tento návod obsahuje následující úlohy:

-   Vytvoření projektu aplikace WPF.

-   Přidání odkazu na [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].

-   Inicializuje se mezipaměť.

-   Přidává se položka v mezipaměti, který obsahuje obsah textového souboru.

-   Poskytování zásadu vyřazení pro položku mezipaměti.

-   Monitorování cestu k souboru v mezipaměti a upozornit na instanci mezipaměti se změní na maximální počet monitorovaných položek.

## <a name="prerequisites"></a>Požadavky
 K dokončení tohoto návodu budete potřebovat:

-   Microsoft Visual Studio 2010.

-   Textový soubor, který obsahuje malé množství textu. (Obsah textového souboru se zobrazí v okně se zprávou.) Kód popsaných v tomto návodu se předpokládá, že pracujete s následující soubor:

     `c:\cache\cacheText.txt`

     Můžete však použít libovolný textový soubor a dělat malé změny kódu v tomto názorném postupu.

## <a name="creating-a-wpf-application-project"></a>Vytvoření projektu aplikace WPF
 Začněte vytvořením projektu aplikace WPF.

#### <a name="to-create-a-wpf-application"></a>Vytvoření aplikace WPF

1. Spusťte Visual Studio.

2. V **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **nový projekt**.

     **Nový projekt** se zobrazí dialogové okno.

3. V části **nainstalované šablony**, vyberte programovací jazyk, který chcete použít (**jazyka Visual Basic** nebo **Visual C#**).

4. V **nový projekt** dialogu **aplikace WPF**.

    > [!NOTE]
    >  Pokud se nezobrazí **aplikace WPF** šablonu, ujistěte se, zda cílíte na verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WPF, která podporuje. V **nový projekt** dialogu [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ze seznamu.

5. V **název** textové pole, zadejte název pro váš projekt. Například můžete zadat **WPFCaching**.

6. Vyberte **vytvořit adresář pro řešení** zaškrtávací políčko.

7. Klikněte na **OK**.

     Otevře se Návrhář WPF v **návrhu** zobrazení a zobrazí soubor MainWindow.xaml. Visual Studio vytvoří **Můj projekt** složka, soubor Application.xaml a souboru MainWindow.xaml.

## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Cílení na rozhraní .NET Framework a přidání odkazu na ukládání do mezipaměti sestavení
 Ve výchozím nastavení, cílové aplikace WPF [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Použít <xref:System.Runtime.Caching> oboru názvů v aplikaci WPF, aplikace musí cílit [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (není [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) a musí obsahovat odkaz na obor názvů.

 Proto, dalším krokem je změnit cílové rozhraní .NET Framework a přidejte odkaz na <xref:System.Runtime.Caching> oboru názvů.

> [!NOTE]
>  Postup pro změnu cílové rozhraní .NET Framework se liší v projektu jazyka Visual Basic a v projektu jazyka Visual C#.

#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Chcete-li změnit cílové rozhraní .NET Framework v jazyce Visual Basic

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.

     Zobrazí se okno Vlastnosti pro aplikaci.

2. Klikněte na tlačítko **kompilaci** kartu.

3. V dolní části okna klikněte na tlačítko **Upřesnit možnosti kompilace...** .

     **Pokročilé nastavení kompilátoru** se zobrazí dialogové okno.

4. V **cílového rozhraní (všechny konfigurace)** seznamu vyberte [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nesmí být zvolen [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)

5. Klikněte na **OK**.

     **Změnit cílový rámec** se zobrazí dialogové okno.

6. V **změnit cílový rámec** dialogové okno, klikněte na tlačítko **Ano**.

     Projekt je uzavřen a pak znovu otevřelo.

7. Přidáte odkaz na sestavení ukládání do mezipaměti pomocí následujících kroků:

    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **přidat odkaz**.

    2.  Vyberte **.NET** kartu, vyberte možnost `System.Runtime.Caching`a potom klikněte na tlačítko **OK**.

#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Chcete-li změnit cílové rozhraní .NET Framework v projektu jazyka Visual C#

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.

     Zobrazí se okno Vlastnosti pro aplikaci.

2. Klikněte na tlačítko **aplikace** kartu.

3. V **Cílová architektura** seznamu vyberte [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nesmí být zvolen **rozhraní .NET Framework 4 Client Profile**.)

4. Přidáte odkaz na sestavení ukládání do mezipaměti pomocí následujících kroků:

    1.  Klikněte pravým tlačítkem myši **odkazy** složku a pak klikněte na tlačítko **přidat odkaz**.

    2.  Vyberte **.NET** kartu, vyberte možnost `System.Runtime.Caching`a potom klikněte na tlačítko **OK**.

## <a name="adding-a-button-to-the-wpf-window"></a>Přidání tlačítka do okna WPF
 V dalším kroku přidáte ovládací prvek button a vytvořit obslužnou rutinu události pro tlačítka `Click` událostí. Kód, který později přidáte tak, aby po kliknutí na tlačítko, jsou uložené v mezipaměti a zobrazí obsah textového souboru.

#### <a name="to-add-a-button-control"></a>Chcete-li přidat ovládací prvek button

1. V **Průzkumníka řešení**, poklikejte na soubor MainWindow.xaml a otevřete ho.

2. Z **nástrojů**v části **běžných ovládacích prvků WPF**, přetáhněte `Button` ovládací prvek `MainWindow` okna.

3. V **vlastnosti** okno, nastaveno `Content` vlastnost `Button` mít pod kontrolou **získat mezipaměti**.

## <a name="initializing-the-cache-and-caching-an-entry"></a>Inicializace mezipaměti a ukládání do mezipaměti položku
 V dalším kroku přidáte kód k provádění následujících úloh:

-   Vytvoření instance třídy mezipaměti – to znamená, že jste se vytvořit novou instanci <xref:System.Runtime.Caching.MemoryCache> objektu.

-   Určete, že mezipaměť používá <xref:System.Runtime.Caching.HostFileChangeMonitor> objektů pro sledování změn v textovém souboru.

-   Čtení textového souboru a jeho obsah v mezipaměti jako položka v mezipaměti.

-   Zobrazte obsah v mezipaměti textového souboru.

#### <a name="to-create-the-cache-object"></a>Chcete-li vytvořit objekt mezipaměti

1. Dvakrát klikněte na tlačítko, které jste právě přidali, chcete-li vytvořit obslužnou rutinu události v souboru MainWindow.xaml.cs nebo soubor MainWindow.Xaml.vb.

2. V horní části souboru (před deklaraci třídy), přidejte následující `Imports` (Visual Basic) nebo `using` příkazy (C#):

    ```csharp
    using System.Runtime.Caching;
    using System.IO;
    ```

    ```vb
    Imports System.Runtime.Caching
    Imports System.IO
    ```

3. V obslužné rutině události přidejte následující kód k vytvoření instance objektu mezipaměti:

    ```csharp
    ObjectCache cache = MemoryCache.Default;
    ```

    ```vb
    Dim cache As ObjectCache = MemoryCache.Default
    ```

     <xref:System.Runtime.Caching.ObjectCache> Třída je integrované třídu, která poskytuje mezipaměti objektů v paměti do mezipaměti.

4. Přidejte následující kód k načtení obsahu položky mezipaměti s názvem `filecontents`:

    ```vb
    Dim fileContents As String = TryCast(cache("filecontents"), String)
    ```

    ```csharp
    string fileContents = cache["filecontents"] as string;
    ```

5. Přidejte následující kód, který zkontrolujte, zda položka mezipaměti s názvem `filecontents` existuje:

    ```vb
    If fileContents Is Nothing Then

    End If
    ```

    ```csharp
    if (fileContents == null)
    {

    }
    ```

     Určená položka mezipaměti neexistuje, musíte přečíst textový soubor a přidejte jej jako položka v mezipaměti do mezipaměti.

6. V `if/then` blokovat, přidejte následující kód k vytvoření nového <xref:System.Runtime.Caching.CacheItemPolicy> objekt, který určuje, že položka mezipaměti vyprší po 10 sekundách.

    ```vb
    Dim policy As New CacheItemPolicy()
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)
    ```

    ```csharp
    CacheItemPolicy policy = new CacheItemPolicy();
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);
    ```

     Pokud je k dispozici žádné informace o vyřazení nebo vypršení platnosti, výchozí hodnota je <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, což znamená, že položky mezipaměti nikdy nevyprší závislosti pouze na absolutním čase. Místo toho platnost položky mezipaměti pouze v případě nedostatku paměti. Jako osvědčený postup byste měli vždy explicitně poskytnout buď absolutní, nebo klouzavé vypršení platnosti.

7. Uvnitř `if/then` blokovat a následující kód, kterou jste přidali v předchozím kroku, přidejte následující kód k vytvoření kolekce pro cesty k souborům, které chcete monitorovat a přidejte cestu k souboru text do kolekce:

    ```vb
    Dim filePaths As New List(Of String)()
    filePaths.Add("c:\cache\cacheText.txt")
    ```

    ```csharp
    List<string> filePaths = new List<string>();
    filePaths.Add("c:\\cache\\cacheText.txt");
    ```

    > [!NOTE]
    >  Pokud není textový soubor, který chcete použít `c:\cache\cacheText.txt`, zadejte cestu k umístění textového souboru, kterou chcete použít.

8. Následující kód, který jste přidali v předchozím kroku, přidejte následující kód přidejte nový <xref:System.Runtime.Caching.HostFileChangeMonitor> do kolekce změnu monitoruje položky mezipaměti:

    ```vb
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))
    ```

    ```csharp
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));
    ```

     <xref:System.Runtime.Caching.HostFileChangeMonitor> Objekt cesta k souboru text sleduje a upozorní mezipaměti, pokud dojde ke změnám. V tomto příkladu položky uložené v mezipaměti vyprší, pokud se změní obsah souboru.

9. Následující kód, který jste přidali v předchozím kroku přidejte následující kód k načtení obsahu textového souboru:

    ```vb
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()
    ```

    ```csharp
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + "\n" + DateTime.Now;
    ```

     Časové razítko data a času je přidán, takže budete moci zobrazit, když vyprší platnost položky mezipaměti.

10. Následující kód, který jste přidali v předchozím kroku, přidejte následující kód k vložení obsahu souboru do objektu mezipaměti jako <xref:System.Runtime.Caching.CacheItem> instance:

    ```vb
    cache.Set("filecontents", fileContents, policy)
    ```

    ```csharp
    cache.Set("filecontents", fileContents, policy);
    ```

     Zadejte informace o tom, jak položka mezipaměti by měla být vyřazena předáním <xref:System.Runtime.Caching.CacheItemPolicy> objekt, který jste vytvořili dříve jako parametr.

11. Po `if/then` blokovat, přidejte následující kód k zobrazení obsahu v mezipaměti souborů v okně se zprávou:

    ```vb
    MessageBox.Show(fileContents)
    ```

    ```csharp
    MessageBox.Show(fileContents);
    ```

12. V **sestavení** nabídky, klikněte na tlačítko **sestavení WPFCaching** k sestavení projektu.

## <a name="testing-caching-in-the-wpf-application"></a>Testování ukládání do mezipaměti v aplikaci WPF
 Teď můžete aplikaci otestovat.

#### <a name="to-test-caching-in-the-wpf-application"></a>K testování ukládání do mezipaměti v aplikaci WPF

1. Stisknutím kláves CTRL + F5 spusťte aplikaci.

     `MainWindow` Se zobrazí okno.

2. Klikněte na tlačítko **získat mezipaměti**.

     Obsah uložený v mezipaměti z textového souboru se zobrazí v okně se zprávou. Všimněte si, že časové razítko souboru.

3. Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu.

     Časové razítko je beze změny. To znamená, že je zobrazen obsah uložený v mezipaměti.

4. Počkejte 10 sekund nebo informace a pak klikněte na tlačítko **získat mezipaměti** znovu.

     Tentokrát se zobrazí nové časové razítko. To znamená, že umožňují zásady vypršení platnosti položky mezipaměti a zobrazí se nový obsah uložený v mezipaměti.

5. V textovém editoru otevřete textový soubor, který jste vytvořili. Ještě neprovádějte žádné změny.

6. Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu.

     Všimněte si, že časové razítko znovu.

7. Proveďte změnu do textového souboru a pak soubor uložte.

8. Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu.

     Toto okno se zprávou obsahuje aktualizovaný obsah z textového souboru a nové časové razítko. To znamená, že sledování změn souboru hostitele vyřazení položka mezipaměti okamžitě při změně souboru i v případě, kdyby absolutní časový limit vypršel.

    > [!NOTE]
    >  Vám může prodloužit dobu vyřazení na 20 sekund nebo více a více času, abyste provedli změnu v souboru.

## <a name="code-example"></a>Příklad kódu
 Po dokončení tohoto návodu, kód, který jste vytvořili projekt bude vypadat podobně jako v následujícím příkladu.

 [!code-csharp[CachingWPFApplications#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Caching.MemoryCache>
- <xref:System.Runtime.Caching.ObjectCache>
- <xref:System.Runtime.Caching>
- [Ukládání do vyrovnávací paměti v aplikacích .NET Framework](../../performance/caching-in-net-framework-applications.md)
