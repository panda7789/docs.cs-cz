---
title: "Zápis aplikace pro Windows Store využívajícího služby OData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a2eb79e8bf8a5c683c9d48a0a69e4d7f5d270eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a>Zápis aplikace pro Windows Store využívajícího služby OData
Windows 8 zavádí nový typ aplikace: aplikace pro Windows Store. Aplikace pro Windows Store mají zcela nový vzhled a chování, spusťte na různých zařízeních a jsou k dispozici ve Windows Storu. Toto téma popisuje, jak psát aplikace pro Windows Store, který využívá služby OData, konkrétně službu OData NetFlix katalogu. Další informace o aplikacích pro Windows Store, přečtěte si prosím [Začínáme s aplikací pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).  
  
## <a name="prerequisites"></a>Požadavky  
  
1.  [Microsoft Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [Microsoft Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [Služby WCF Data Services](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a>Vytváření výchozí aplikaci pro Windows Store mřížky  
  
1.  Vytvoření nového úložiště mřížky aplikace Windows pomocí jazyka C# a XAML. Název aplikace OData.WindowsStore.NetflixDemo:  
  
     ![Dialogové okno Nový projekt](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")  
  
2.  Otevřete Package.appxmanifest a zadejte popisný název do textového pole název zobrazení. Určuje, že název aplikace použít s Windows 8 funkce vyhledávání.  
  
     ![Soubor manifestu aplikace](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")  
  
3.  Zadejte popisný název v \<AppName > element v souboru App.xaml. Toto nastaví název aplikace, který se zobrazí při spuštění aplikace:  
  
     ![Soubor App.XAML](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")  
  
4.  Sestavení a spuštění aplikace. Nejprve zobrazí úvodní obrazovka aplikace. Následující snímek obrazovky se zobrazí na výchozí úvodní obrazovce. Obrázek použitý je uložen ve složce projektu prostředky.  
  
     ![Úvodní obrazovka výchozí aplikace](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")  
  
     Potom zobrazí aplikace.  
  
     ![Výchozí aplikace](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")  
  
     Výchozí aplikace definuje sadu tříd v SampleDataSource.cs: SampleDataGroup a SampleDataItem, které jsou odvozeny od SampleDataCommon, které je odvozený od BindableBase. Rutina GridView na výchozí hodnoty jsou svázané s SampleDataGroup a SampleDataItem. SampleDataSource.cs se nachází ve složce DataModel v rámci NetflixDemo projektu. Aplikace zobrazí seskupené kolekce. Každá skupina obsahuje libovolný počet položek, reprezentována SampleDataGroup a SampleDataItem, v uvedeném pořadí. V předchozí snímek obrazovky se zobrazí skupinu s názvem 1. skupina název a všechny položky ve skupině zobrazí společně.  
  
     Hlavní stránka aplikace je GroupedItemsPage.xaml. Obsahuje GridView, zobrazující vytvořené třídy SampleDataSource.cs ukázková data. GroupedItemsPage zavedená App.xaml.cs v volání rootFrame.Navigate:  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     To způsobí, že GroupedItemsPage chcete vytvořit instanci a LoadState metoda je volána. LoadState způsobí, že statická instance SampleDataSource má být vytvořen, který vytvoří kolekci SampleDataGroup objektů. Každý objekt SampleDataGroup obsahuje kolekci SampleDataItem objektů. LoadState ukládá kolekci SampleDataGroup objektů, které DefaultViewModel:  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     DefaultViewModel je pak vázána GridView. To se odkazuje v souboru GroupedItemsPage.xaml při konfiguraci datové vazby.  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     CollectionViewSource slouží jako proxy pro zpracování seskupené kolekce. Když dojde k vazby, iteruje kolekcí objektů SampleDataGroup k naplnění GridView.  Atribut ItemsPath informuje CollectionViewSource, jaké vlastnosti na každém objektu SampleDataGroup vyhledejte SampleDataItems obsahuje. V takovém případě každý objekt SampleDataGroup obsahuje kolekci TopItems SampleDataItem objektů.  
  
     Pro aplikaci Netflix filmy jsou seskupené podle genre. Proto aplikace zobrazí určitý počet žánry a seznam filmy v rámci této genre.  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a>Přidat odkaz na službu ve službě Netflix OData  
  
1.  Abychom mohli provádět volání služby Netflix OData musíme přidat odkaz na službu. Klikněte pravým tlačítkem na projekt v Průzkumníku řešení a vyberte možnost Přidat odkaz na službu...  
  
     ![Přidat odkaz na službu – dialogové okno](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")  
  
2.  Zadejte adresu URL služby Netflix OData do adresního řádku a kliknutím na Přejít. Nastavte Namespace služby odkazu na Netflix a klikněte na tlačítko OK.  
  
     ![Chyba odkazu služby přidat](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")  
  
    > [!NOTE]
    >  Pokud jste ještě nenainstalovali [WCF Data Services nástroje pro aplikace Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=266652), zobrazí se výzva s zprávou, jako je třeba výše. Musíte se ke stažení a instalaci nástroje odkazované ve vazbě na pokračovat.  
  
 Přidání že odkazu na službu generuje silně typované třídy, které součásti WCF Data Services použije k analýze OData vrácený službou Netflix OData. Třídy definované v SampleDataSource.cs mohou být vázány na GridView, takže potřebujeme k přenosu dat z vygenerované třídy klienta OData do vazbu třídy definované v SampleDataSource.cs.  Chcete-li to provést, je potřeba provést některé změny do datového modelu, který je definován v SampleDataSource.cs.  
  
#### <a name="update-the-data-model-for-the-application"></a>Aktualizovat data modelu pro aplikace  
  
1.  Nahraďte kód z existujícího kódu v SampleDataSource.cs [tento gist](https://gist.github.com/3419288). Aktualizovaný kódu přidá metoda LoadMovies (k třídě SampleDataSource), který provádí dotazy na službu Netflix OData a naplní seznam žánry (allGroups) a v rámci každé genre seznam filmy. SampleDataGroup třída se používá k reprezentování genre a SampleDataItem třída se používá k reprezentování film.  
  
    ```csharp  
    public static async void LoadMovies()  
    {  
        IEnumerable<Title> titles = await ((DataServiceQuery<Title>)Context.Titles  
            .Expand("Genres,AudioFormats,AudioFormats/Language,Awards,Cast")  
            .Where(t => t.Rating == "PG")  
            .OrderByDescending(t => t.ReleaseYear)  
            .Take(300)).ExecuteAsync();  
  
        foreach (Title title in titles)  
        {  
            foreach (Genre netflixGenre in title.Genres)  
            {  
                SampleDataGroup genre = GetGroup(netflixGenre.Name);  
                if (genre == null)  
                {  
                    genre = new SampleDataGroup(netflixGenre.Name, netflixGenre.Name, String.Empty, title.BoxArt.LargeUrl, String.Empty);  
                    Instance.AllGroups.Add(genre);  
                }  
                var content = new StringBuilder();  
                // Write additional things to content here if you want them to display in the item detail.  
                genre.Items.Add(new SampleDataItem(title.Id, title.Name, String.Format("{0}rnrn{1} ({2})", title.Synopsis, title.Rating, title.ReleaseYear), title.BoxArt.HighDefinitionUrl ?? title.BoxArt.LargeUrl, "Description", content.ToString()));  
            }  
        }  
    }  
    ```  
  
     [Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) se používá k získání asynchronně 300 (provést) poslední (OrderByDescending) PG hodnocení (kde) filmy zpět z Netflix. Zbytek kód vytvoří SimpleDataItems a SimpleDataGroups z entit, které byly vráceny v datovém kanálu OData.  
  
     Třída SampleDataSource také implementuje metodu jednoduché hledání. V takovém případě se načíst filmy jednoduché hledání v paměti.  
  
    ```csharp  
    public static IEnumerable<SampleDataItem> Search(string searchString)  
    {  
            var regex = new Regex(searchString, RegexOptions.CultureInvariant | RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace);  
            return Instance.AllGroups  
                .SelectMany(g => g.Items)  
                .Where(m => regex.IsMatch(m.Title) || regex.IsMatch(m.Subtitle))  
                    .Distinct(new SampleDataItemComparer());  
    }  
    ```  
  
     Také v SampleDataSource.cs třídy s názvem ExtensionMethods definován. Každá z těchto metod rozšíření na základě vzoru klepněte na umožní SampleDataSource provést dotaz OData bez blokování uživatelského rozhraní. Například následující kód používá metodu Task.Factory.FromAsync k implementaci klepnutím.  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     Stejně jako u výchozí aplikace je hlavní stránce aplikace GroupedItemsPage. Tentokrát, ale zobrazuje filmy z Netflix seskupené podle genre načíst.  Když je vytvořena GroupedItemsPage, jeho LoadState metoda je volána. LoadState způsobí, že statická instance SampleDataSource vytvořit, vytvořit volání ke službě Netflix OData, jak je popsáno dříve. LoadState ukládá DefaultViewModel kolekce žánry (SampleDataGroup objekty):  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     Jak je popsáno dříve, DefaultViewModel se pak používá k vytvoření vazby dat GridView.  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a>Přidat smlouvu vyhledávání umožňující aplikace k účasti ve službě Windows search  
  
1.  Přidáte smlouvy vyhledávání k aplikaci. To umožňuje aplikaci k integraci s vyhledáváním systému Windows 8. Název smlouvy vyhledávání SearchResultsPage.xaml  
  
     ![Přidat smlouvu vyhledávání](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")  
  
2.  Upravte řádku 58 SearchResultsPage.xaml.cs odebráním embedded uvozovkách queryText.  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  Vložte následující dva řádky kódu na řádku 81 v SearchResultsPage.xaml.cs načíst výsledky hledání.  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 Pokud je uživatel vyvolá Windows search, typy v hledaný termín a potom dotykem ikonu Netflix ukázkové aplikace v panelu vyhledávání, metodě LoadState SearchResultsPage je spustit. Parametr navigační posílá LoadState obsahuje text dotazu. Další Filter_SelectionChanged metoda je volána, který potom volá metodu Search k třídě SampleDataSource. Výsledky se vrátí a zobrazí na stránce SearchResultsPage.xaml.  
  
```csharp  
/// <summary>  
        /// Invoked when a filter is selected using the ComboBox in snapped view state.  
        /// </summary>  
        /// <param name="sender">The ComboBox instance.</param>  
        /// <param name="e">Event data describing how the selected filter was changed.</param>  
        void Filter_SelectionChanged(object sender, SelectionChangedEventArgs e)  
        {  
            // Determine what filter was selected  
            var selectedFilter = e.AddedItems.FirstOrDefault() as Filter;  
            if (selectedFilter != null)  
            {  
                // Mirror the results into the corresponding Filter object to allow the  
                // RadioButton representation used when not snapped to reflect the change  
                selectedFilter.Active = true;  
  
                // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                var searchValue = (string)this.DefaultViewModel["QueryText"];  
                this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
  
                // Ensure results are found  
                object results;  
                ICollection resultsCollection;  
                if (this.DefaultViewModel.TryGetValue("Results", out results) &&  
                    (resultsCollection = results as ICollection) != null &&  
                    resultsCollection.Count != 0)  
                {  
                    VisualStateManager.GoToState(this, "ResultsFound", true);  
                    return;  
                }  
            }  
  
            // Display informational text when there are no search results.  
            VisualStateManager.GoToState(this, "NoResultsFound", true);  
        }  
```  
  
 Další informace o integraci hledání do aplikace najdete [vyhledávání: integraci do prostředí Windows 8 vyhledávání](http://go.microsoft.com/fwlink/p/?LinkId=266650).  
  
## <a name="run-the-application"></a>Spuštění aplikace  
 Spusťte aplikaci stisknutím klávesy F5. Všimněte si, že bude trvat několik sekund načíst obrázků při spuštění aplikace. Vaše první pokus o vyhledávání navíc nemusí nevrátí žádné výsledky. V reálné aplikaci byste chcete řešit oba tyto problémy.  
  
 Aplikace volá službu Netflix OData, obdrží data v vygenerované třídy klienta OData a pak přenáší data do vázat datové třídy (SampleDataSource, SampleDataGroup a SampleDataItem). Tyto třídy vazbu používá k vytvoření vazby dat GridView. Pokud jste obeznámeni s fungování datové vazby XAML najdete [jak seskupit položky v seznamu nebo v mřížce (aplikace pro Windows Store pomocí jazyka C# / VB/C++ a XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).
