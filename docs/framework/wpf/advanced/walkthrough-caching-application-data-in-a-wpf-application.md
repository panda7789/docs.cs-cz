---
title: 'Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- walkthroughs [WPF], caching
- caching [.NET Framework]
- caching [WPF]
ms.assetid: dac2c9ce-042b-4d23-91eb-28f584415cef
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a8d3fe2dbfe0b4b5fb9081d71cec080dfa54add8
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-caching-application-data-in-a-wpf-application"></a>Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF
Ukládání do mezipaměti umožňuje ukládání dat v paměti pro rychlý přístup. Když je znovu přístupu k datům, aplikací můžete získat data z mezipaměti místo toho je načítání z původního zdroje. Tím lze vylepšit výkon a škálovatelnost. Navíc díky ukládání dat do mezipaměti k dispozici při zdroj dat je dočasně nedostupný.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Poskytuje třídy, které vám umožní používat ukládání do mezipaměti v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace. Tyto třídy jsou umístěné v <xref:System.Runtime.Caching> oboru názvů.  
  
> [!NOTE]
>  <xref:System.Runtime.Caching> Je nového v oboru názvů [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. Tento obor názvů umožňuje ukládání do mezipaměti je k dispozici pro všechny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplikace. V předchozích verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ukládání do mezipaměti byla k dispozici pouze v <xref:System.Web> obor názvů a proto vyžaduje závislost na třídy technologie ASP.NET.  
  
 Tento postup vám ukáže, jak používat funkci ukládání do mezipaměti, který je k dispozici v [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] jako součást [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace. V tomto návodu mezipaměti obsahu textového souboru.  
  
 Tento návod obsahuje následující úlohy:  
  
-   Vytvoření projektu aplikace WPF.  
  
-   Přidání odkazu na [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].  
  
-   Inicializace mezipaměti.  
  
-   Přidání položky mezipaměti obsahující obsah textového souboru.  
  
-   Poskytuje zásadu vyřazení položky mezipaměti.  
  
-   Sledování cestu k souboru v mezipaměti a oznamování instance mezipaměti o změny monitorovaných položek.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu, budete potřebovat:  
  
-   Microsoft [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Textový soubor, který obsahuje malou část textu. (Obsah textového souboru se zobrazí v okně se zprávou.) Kód popsaných v tomto návodu se předpokládá, že pracujete s následující soubor:  
  
     `c:\cache\cacheText.txt`  
  
     Můžete však použít libovolný textový soubor a provést změny malý kód v tomto návodu.  
  
## <a name="creating-a-wpf-application-project"></a>Vytvoření projektu aplikace WPF  
 Začněte vytvořením projektu aplikace WPF.  
  
#### <a name="to-create-a-wpf-application"></a>Vytvoření aplikace WPF  
  
1.  Spuštění sady Visual Studio.  
  
2.  V **soubor** nabídky, klikněte na tlačítko **nový**a potom klikněte na **nový projekt**.  
  
     **Nový projekt** se zobrazí dialogové okno.  
  
3.  V části **nainstalovaných šablonách**, vyberte programovací jazyk, který chcete použít (**jazyka Visual Basic** nebo **Visual C#**).  
  
4.  V **nový projekt** dialogové okno, vyberte **aplikaci WPF**.  
  
    > [!NOTE]
    >  Pokud se nezobrazí **aplikaci WPF** šablony, ujistěte se, že jsou cílení na verzi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podporující WPF. V **nový projekt** dialogové okno, vyberte [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] ze seznamu.  
  
5.  V **název** textové pole, zadejte název pro svůj projekt. Například můžete zadat **WPFCaching**.  
  
6.  Vyberte **vytvořit adresář pro řešení** zaškrtávací políčko.  
  
7.  Click **OK**.  
  
     WPF Designer se otevře v **návrhu** zobrazení a zobrazí MainWindow.xaml soubor. Visual Studio vytvoří **Můj projekt** složka, soubor Application.xaml a soubor MainWindow.xaml.  
  
## <a name="targeting-the-net-framework-and-adding-a-reference-to-the-caching-assemblies"></a>Cílení na rozhraní .NET Framework a přidáním odkazu na ukládání do mezipaměti sestavení  
 Ve výchozím nastavení, cílové aplikace WPF [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]. Použít <xref:System.Runtime.Caching> oboru názvů v aplikaci WPF, aplikace musí mít jako cíl [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] (není [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)]) a musí obsahovat odkaz na obor názvů.  
  
 Proto je dalším krokem je změnit cíl rozhraní .NET Framework a přidat odkaz na <xref:System.Runtime.Caching> oboru názvů.  
  
> [!NOTE]
>  Postup pro změnu cílové rozhraní .NET Framework se liší v projektu jazyka Visual Basic a v projektu jazyka Visual C#.  
  
#### <a name="to-change-the-target-net-framework-in-visual-basic"></a>Chcete-li změnit cíl rozhraní .NET Framework v jazyce Visual Basic  
  
1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.  
  
     Zobrazí se okno Vlastnosti pro aplikaci.  
  
2.  Klikněte **zkompilovat** kartě.  
  
3.  V dolní části okna klikněte na tlačítko **Upřesnit možnosti kompilace...** .  
  
     **Upřesnit nastavení kompilátoru** se zobrazí dialogové okno.  
  
4.  V **cílové rozhraní (všechny konfigurace)** seznamu, vyberte [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nevybírejte [!INCLUDE[net_client_v40_long](../../../../includes/net-client-v40-long-md.md)].)  
  
5.  Click **OK**.  
  
     **Změnit cílový Framework** se zobrazí dialogové okno.  
  
6.  V **změnit cílový Framework** dialogové okno, klikněte na tlačítko **Ano**.  
  
     Projekt se zavře a pak znovu otevřete.  
  
7.  Přidáte odkaz na sestavení ukládání do mezipaměti pomocí následujících kroků:  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **přidat odkaz na**.  
  
    2.  Vyberte **.NET** vyberte `System.Runtime.Caching`a potom klikněte na **OK**.  
  
#### <a name="to-change-the-target-net-framework-in-a-visual-c-project"></a>Chcete-li změnit cíl rozhraní .NET Framework v projektu jazyka Visual C#  
  
1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na název projektu a pak klikněte na tlačítko **vlastnosti**.  
  
     Zobrazí se okno Vlastnosti pro aplikaci.  
  
2.  Klikněte **aplikace** kartě.  
  
3.  V **cílové rozhraní** seznamu, vyberte [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]. (Nevybírejte **rozhraní .NET Framework 4 Client Profile**.)  
  
4.  Přidáte odkaz na sestavení ukládání do mezipaměti pomocí následujících kroků:  
  
    1.  Klikněte pravým tlačítkem myši **odkazy** složku a pak klikněte na tlačítko **přidat odkaz na**.  
  
    2.  Vyberte **.NET** vyberte `System.Runtime.Caching`a potom klikněte na **OK**.  
  
## <a name="adding-a-button-to-the-wpf-window"></a>Přidání tlačítka do okna WPF  
 V dalším kroku přidáte ovládacího prvku tlačítko a vytvoření obslužné rutiny události pro tlačítka `Click` událostí. Kód pro později přidáte tak, aby po kliknutí na tlačítko, jsou do mezipaměti a zobrazí obsah textového souboru.  
  
#### <a name="to-add-a-button-control"></a>Přidání ovládacího prvku tlačítko  
  
1.  V **Průzkumníku**, poklikejte na soubor MainWindow.xaml ho otevřete.  
  
2.  Z **sada nástrojů**v části **běžných ovládacích prvků WPF**, přetáhněte ji `Button` řídit k `MainWindow` okno.  
  
3.  V **vlastnosti** nastavte `Content` vlastnost `Button` řídit k **získat mezipaměti**.  
  
## <a name="initializing-the-cache-and-caching-an-entry"></a>Inicializace mezipaměti a ukládání do mezipaměti položku  
 Dále přidáte kód, který provádět následující úlohy:  
  
-   Vytvoření instance třídy mezipaměti – to znamená, že vytvoříte instanci novou <xref:System.Runtime.Caching.MemoryCache> objektu.  
  
-   Zadejte, že mezipaměť používá <xref:System.Runtime.Caching.HostFileChangeMonitor> objekt, který chcete sledovat změny v textovém souboru.  
  
-   Čtení textového souboru a jeho obsah do mezipaměti jako položku mezipaměti.  
  
-   Zobrazte obsah v mezipaměti textového souboru.  
  
#### <a name="to-create-the-cache-object"></a>Chcete-li vytvořit objekt mezipaměti  
  
1.  Dvakrát klikněte na tlačítko, které jste právě přidali, aby bylo možné vytvořit obslužnou rutinu události v souboru MainWindow.xaml.cs nebo MainWindow.Xaml.vb.  
  
2.  V horní části souboru (před deklaraci třídy), přidejte následující `Imports` (Visual Basic) nebo `using` příkazy (C#):  
  
    ```csharp  
    using System.Runtime.Caching;  
    using System.IO;  
    ```  
  
    ```vb  
    Imports System.Runtime.Caching  
    Imports System.IO  
    ```  
  
3.  V obslužné rutině přidejte následující kód k vytvoření instance objektu mezipaměti:  
  
    ```csharp  
    ObjectCache cache = MemoryCache.Default;  
    ```  
  
    ```vb  
    Dim cache As ObjectCache = MemoryCache.Default  
    ```  
  
     <xref:System.Runtime.Caching.ObjectCache> Třída je předdefinovaný třídu, která poskytuje mezipaměti objektů v paměti.  
  
4.  Přidejte následující kód ke čtení obsahu položky mezipaměti s názvem `filecontents`:  
  
    ```vb  
    Dim fileContents As String = TryCast(cache("filecontents"), String)  
    ```  
  
    ```csharp  
    string fileContents = cache["filecontents"] as string;  
    ```  
  
5.  Přidejte následující kód, který zkontrolujte, zda položka mezipaměti s názvem `filecontents` existuje:  
  
    ```vb  
    If fileContents Is Nothing Then  
  
    End If  
    ```  
  
    ```csharp  
    if (fileContents == null)  
    {  
  
    }  
    ```  
  
     Pokud určená položka mezipaměti neexistuje, musíte čtení textového souboru a přidejte jej jako položku mezipaměti do mezipaměti.  
  
6.  V `if/then` blokovat, přidejte následující kód k vytvoření nové <xref:System.Runtime.Caching.CacheItemPolicy> objekt, který určuje, že položky mezipaměti vyprší po 10 sekundách.  
  
    ```vb  
    Dim policy As New CacheItemPolicy()  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0)  
    ```  
  
    ```csharp  
    CacheItemPolicy policy = new CacheItemPolicy();  
    policy.AbsoluteExpiration = DateTimeOffset.Now.AddSeconds(10.0);  
    ```  
  
     Pokud je zadaný žádné informace o vyřazení nebo vypršení platnosti, výchozí hodnota je <xref:System.Runtime.Caching.ObjectCache.InfiniteAbsoluteExpiration>, což znamená, že položky mezipaměti vyprší na základě nikdy pouze na absolutním čase. Místo toho platnost položky mezipaměti jenom v případě, že je přetížení paměti. Jako osvědčený postup je vhodné vždy explicitně zadat absolutní nebo vedlejší vypršení platnosti.  
  
7.  Uvnitř `if/then` blokovat a následující kód, který jste přidali v předchozím kroku, přidejte následující kód k vytvoření kolekce cest souborů, které chcete monitorovat a přidejte cestu k textovému souboru do kolekce:  
  
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
  
8.  Následující kód, který jste přidali v předchozím kroku, přidejte následující kód přidejte nový <xref:System.Runtime.Caching.HostFileChangeMonitor> objektu do kolekce změny monitoruje položky mezipaměti:  
  
    ```vb  
    policy.ChangeMonitors.Add(New HostFileChangeMonitor(filePaths))  
    ```  
  
    ```csharp  
    policy.ChangeMonitors.Add(new HostFileChangeMonitor(filePaths));  
    ```  
  
     <xref:System.Runtime.Caching.HostFileChangeMonitor> Objekt monitoruje cesta k textovému souboru a upozorní mezipaměti, pokud dojde ke změnám. V tomto příkladu položky mezipaměti vyprší, pokud se změní obsah souboru.  
  
9. Následující kód, který jste přidali v předchozím kroku přidejte následující kód ke čtení obsahu textového souboru:  
  
    ```vb  
    fileContents = File.ReadAllText("c:\cache\cacheText.txt") & vbCrLf & DateTime.Now.ToString()  
    ```  
  
    ```csharp  
    fileContents = File.ReadAllText("c:\\cache\\cacheText.txt") + + "\n" + DateTime.Now;   
    ```  
  
     Datum a čas časové razítko je přidat tak, že nebudete moci zobrazit, když vyprší platnost položky mezipaměti.  
  
10. Následující kód, který jste přidali v předchozím kroku, přidejte následující kód pro vložení do objektu mezipaměti jako obsah souboru <xref:System.Runtime.Caching.CacheItem> instance:  
  
    ```vb  
    cache.Set("filecontents", fileContents, policy)  
    ```  
  
    ```csharp  
    cache.Set("filecontents", fileContents, policy);  
    ```  
  
     Zadejte informace o tom, jak by měla být položky mezipaměti pomocí předání vyřazena <xref:System.Runtime.Caching.CacheItemPolicy> objekt, který jste vytvořili dříve jako parametr.  
  
11. Po `if/then` blokovat, přidejte následující kód k zobrazení souborů uložených v mezipaměti obsahu v okně se zprávou:  
  
    ```vb  
    MessageBox.Show(fileContents)  
    ```  
  
    ```csharp  
    MessageBox.Show(fileContents);  
    ```  
  
12. V **sestavení** nabídky, klikněte na tlačítko **sestavení WPFCaching** k sestavení projektu.  
  
## <a name="testing-caching-in-the-wpf-application"></a>Testování ukládání do mezipaměti v aplikaci WPF  
 Nyní můžete aplikaci otestovat.  
  
#### <a name="to-test-caching-in-the-wpf-application"></a>K testování ukládání do mezipaměti v aplikaci WPF  
  
1.  Stisknutím kombinace kláves CTRL + F5 a spusťte aplikaci.  
  
     `MainWindow` Zobrazí se okno.  
  
2.  Klikněte na tlačítko **získat mezipaměti**.  
  
     Obsah uložený v mezipaměti z textového souboru se zobrazí v okně se zprávou. Všimněte si, časové razítko souboru.  
  
3.  Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu **.**  
  
     Časové razítko je beze změny. To znamená, že se zobrazí obsah v mezipaměti.  
  
4.  Počkejte 10 sekund nebo více a pak klikněte na tlačítko **získat mezipaměti** znovu.  
  
     Tento čas se zobrazí nový časové razítko. To znamená, že zásady umožňují vypršení platnosti položky mezipaměti a že se zobrazí nový obsah v mezipaměti.  
  
5.  V textovém editoru otevřete textový soubor, který jste vytvořili. Zatím neprovádějte žádné změny.  
  
6.  Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu **.**  
  
     Všimněte si znovu časové razítko.  
  
7.  Změňte na textový soubor a pak soubor uložte.  
  
8.  Zavřete okno se zprávou a pak klikněte na tlačítko **získat mezipaměti** znovu.  
  
     Toto okno se zprávou obsahuje aktualizovaný obsah z textového souboru a nové časové razítko. To znamená, že soubor hostitele sledování změn vyřazování položky mezipaměti okamžitě, pokud jste změnili soubor, i když kdyby vypršel absolutní časový limit.  
  
    > [!NOTE]
    >  Může se prodloužit doba vyřazení na 20 sekund nebo více času pro vás k provedení změny v souboru.  
  
## <a name="code-example"></a>Příklad kódu  
 Po dokončení tohoto průvodce, kód pro projekt, který jste vytvořili bude vypadat podobně jako v následujícím příkladu.  
  
 [!code-csharp[CachingWPFApplications#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CachingWPFApplications/CSharp/MainWindow.xaml.cs#1)]
 [!code-vb[CachingWPFApplications#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CachingWPFApplications/VisualBasic/MainWindow.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Caching.MemoryCache>  
 <xref:System.Runtime.Caching.ObjectCache>  
 <xref:System.Runtime.Caching>  
 [Ukládání do vyrovnávací paměti v aplikacích .NET Framework](../../../../docs/framework/performance/caching-in-net-framework-applications.md)
