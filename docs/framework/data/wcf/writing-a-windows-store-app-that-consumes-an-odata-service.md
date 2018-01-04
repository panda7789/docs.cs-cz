---
title: "Zápis aplikace pro Windows Store využívajícího služby OData"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a2eb79e8bf8a5c683c9d48a0a69e4d7f5d270eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a><span data-ttu-id="e9bc2-102">Zápis aplikace pro Windows Store využívajícího služby OData</span><span class="sxs-lookup"><span data-stu-id="e9bc2-102">Writing a Windows Store App that consumes an OData Service</span></span>
<span data-ttu-id="e9bc2-103">Windows 8 zavádí nový typ aplikace: aplikace pro Windows Store.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-103">Windows 8 introduces a new type of application: the Windows Store app.</span></span> <span data-ttu-id="e9bc2-104">Aplikace pro Windows Store mají zcela nový vzhled a chování, spusťte na různých zařízeních a jsou k dispozici ve Windows Storu.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-104">Windows Store apps have a brand new look and feel, run on a variety of devices, and are made available on the Windows Store.</span></span> <span data-ttu-id="e9bc2-105">Toto téma popisuje, jak psát aplikace pro Windows Store, který využívá služby OData, konkrétně službu OData NetFlix katalogu.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-105">This topic describes how to write a Windows Store app that consumes an OData service, specifically the NetFlix Catalog OData service.</span></span> <span data-ttu-id="e9bc2-106">Další informace o aplikacích pro Windows Store, přečtěte si prosím [Začínáme s aplikací pro Windows Store](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span><span class="sxs-lookup"><span data-stu-id="e9bc2-106">For more information about Windows Store Apps, please read [Getting Started with Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e9bc2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9bc2-107">Prerequisites</span></span>  
  
1.  [<span data-ttu-id="e9bc2-108">Microsoft Windows 8</span><span class="sxs-lookup"><span data-stu-id="e9bc2-108">Microsoft Windows 8</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [<span data-ttu-id="e9bc2-109">Microsoft Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="e9bc2-109">Microsoft Visual Studio 2012</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [<span data-ttu-id="e9bc2-110">Služby WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="e9bc2-110">WCF Data Services</span></span>](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a><span data-ttu-id="e9bc2-111">Vytváření výchozí aplikaci pro Windows Store mřížky</span><span class="sxs-lookup"><span data-stu-id="e9bc2-111">Creating the default Windows Store Grid Application</span></span>  
  
1.  <span data-ttu-id="e9bc2-112">Vytvoření nového úložiště mřížky aplikace Windows pomocí jazyka C# a XAML.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-112">Create a new Windows Store Grid Application using C# and XAML.</span></span> <span data-ttu-id="e9bc2-113">Název aplikace OData.WindowsStore.NetflixDemo:</span><span class="sxs-lookup"><span data-stu-id="e9bc2-113">Name the application OData.WindowsStore.NetflixDemo:</span></span>  
  
     <span data-ttu-id="e9bc2-114">![Dialogové okno Nový projekt](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-114">![New Project Dialog](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span></span>  
  
2.  <span data-ttu-id="e9bc2-115">Otevřete Package.appxmanifest a zadejte popisný název do textového pole název zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-115">Open the Package.appxmanifest and enter a friendly name in the Display name text box.</span></span> <span data-ttu-id="e9bc2-116">Určuje, že název aplikace použít s Windows 8 funkce vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-116">This specifies the application name used with the Windows 8 search functionality.</span></span>  
  
     <span data-ttu-id="e9bc2-117">![Soubor manifestu aplikace](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-117">![Application manifest file](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span></span>  
  
3.  <span data-ttu-id="e9bc2-118">Zadejte popisný název v \<AppName > element v souboru App.xaml.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-118">Enter a friendly name in the \<AppName> element in the App.xaml file.</span></span> <span data-ttu-id="e9bc2-119">Toto nastaví název aplikace, který se zobrazí při spuštění aplikace:</span><span class="sxs-lookup"><span data-stu-id="e9bc2-119">This sets the application name that is displayed when the application is launched:</span></span>  
  
     <span data-ttu-id="e9bc2-120">![Soubor App.XAML](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-120">![App.xaml file](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span></span>  
  
4.  <span data-ttu-id="e9bc2-121">Sestavení a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-121">Build and launch the application.</span></span> <span data-ttu-id="e9bc2-122">Nejprve zobrazí úvodní obrazovka aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-122">You first see the application’s splash screen.</span></span> <span data-ttu-id="e9bc2-123">Následující snímek obrazovky se zobrazí na výchozí úvodní obrazovce.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-123">The screenshot below displays the default splash screen.</span></span> <span data-ttu-id="e9bc2-124">Obrázek použitý je uložen ve složce projektu prostředky.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-124">The image used is stored in the project’s Assets folder.</span></span>  
  
     <span data-ttu-id="e9bc2-125">![Úvodní obrazovka výchozí aplikace](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-125">![The default app splash screen](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span></span>  
  
     <span data-ttu-id="e9bc2-126">Potom zobrazí aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-126">Then the application will be displayed.</span></span>  
  
     <span data-ttu-id="e9bc2-127">![Výchozí aplikace](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-127">![The default application](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span></span>  
  
     <span data-ttu-id="e9bc2-128">Výchozí aplikace definuje sadu tříd v SampleDataSource.cs: SampleDataGroup a SampleDataItem, které jsou odvozeny od SampleDataCommon, které je odvozený od BindableBase.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-128">The default application defines a set of classes in SampleDataSource.cs: SampleDataGroup and SampleDataItem, both of which are derived from SampleDataCommon, which itself is derived from BindableBase.</span></span> <span data-ttu-id="e9bc2-129">Rutina GridView na výchozí hodnoty jsou svázané s SampleDataGroup a SampleDataItem.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-129">SampleDataGroup and SampleDataItem are bound to the default GridView.</span></span> <span data-ttu-id="e9bc2-130">SampleDataSource.cs se nachází ve složce DataModel v rámci NetflixDemo projektu.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-130">SampleDataSource.cs is located in the DataModel folder within the NetflixDemo project.</span></span> <span data-ttu-id="e9bc2-131">Aplikace zobrazí seskupené kolekce.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-131">The application displays a grouped collection.</span></span> <span data-ttu-id="e9bc2-132">Každá skupina obsahuje libovolný počet položek, reprezentována SampleDataGroup a SampleDataItem, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-132">Each group contains any number of items, represented by SampleDataGroup and SampleDataItem, respectively.</span></span> <span data-ttu-id="e9bc2-133">V předchozí snímek obrazovky se zobrazí skupinu s názvem 1. skupina název a všechny položky ve skupině zobrazí společně.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-133">In the previous screen shot you can see a group called Group Title 1 and all of the items in the group displayed together.</span></span>  
  
     <span data-ttu-id="e9bc2-134">Hlavní stránka aplikace je GroupedItemsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-134">The main page of the application is GroupedItemsPage.xaml.</span></span> <span data-ttu-id="e9bc2-135">Obsahuje GridView, zobrazující vytvořené třídy SampleDataSource.cs ukázková data.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-135">It contains a GridView that displays the sample data created by the SampleDataSource.cs class.</span></span> <span data-ttu-id="e9bc2-136">GroupedItemsPage zavedená App.xaml.cs v volání rootFrame.Navigate:</span><span class="sxs-lookup"><span data-stu-id="e9bc2-136">The GroupedItemsPage is loaded by the App.xaml.cs in a call to rootFrame.Navigate:</span></span>  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     <span data-ttu-id="e9bc2-137">To způsobí, že GroupedItemsPage chcete vytvořit instanci a LoadState metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-137">This causes the GroupedItemsPage to be instantiated and it’s LoadState method is called.</span></span> <span data-ttu-id="e9bc2-138">LoadState způsobí, že statická instance SampleDataSource má být vytvořen, který vytvoří kolekci SampleDataGroup objektů.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-138">LoadState causes the static SampleDataSource instance to be created, which creates a collection of SampleDataGroup objects.</span></span> <span data-ttu-id="e9bc2-139">Každý objekt SampleDataGroup obsahuje kolekci SampleDataItem objektů.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-139">Each SampleDataGroup object contains a collection of SampleDataItem objects.</span></span> <span data-ttu-id="e9bc2-140">LoadState ukládá kolekci SampleDataGroup objektů, které DefaultViewModel:</span><span class="sxs-lookup"><span data-stu-id="e9bc2-140">LoadState stores the collection of SampleDataGroup objects in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="e9bc2-141">DefaultViewModel je pak vázána GridView.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-141">The DefaultViewModel is then bound to the GridView.</span></span> <span data-ttu-id="e9bc2-142">To se odkazuje v souboru GroupedItemsPage.xaml při konfiguraci datové vazby.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-142">This is referenced in the GroupedItemsPage.xaml file when configuring the data binding.</span></span>  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     <span data-ttu-id="e9bc2-143">CollectionViewSource slouží jako proxy pro zpracování seskupené kolekce.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-143">The CollectionViewSource is used as a proxy for handling grouped collections.</span></span> <span data-ttu-id="e9bc2-144">Když dojde k vazby, iteruje kolekcí objektů SampleDataGroup k naplnění GridView.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-144">When binding occurs, it iterates through the collection of SampleDataGroup objects to populate the GridView.</span></span>  <span data-ttu-id="e9bc2-145">Atribut ItemsPath informuje CollectionViewSource, jaké vlastnosti na každém objektu SampleDataGroup vyhledejte SampleDataItems obsahuje.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-145">The ItemsPath attribute tells the CollectionViewSource what property on each SampleDataGroup object to use to find the SampleDataItems it contains.</span></span> <span data-ttu-id="e9bc2-146">V takovém případě každý objekt SampleDataGroup obsahuje kolekci TopItems SampleDataItem objektů.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-146">In this case each SampleDataGroup object contains a TopItems collection of SampleDataItem objects.</span></span>  
  
     <span data-ttu-id="e9bc2-147">Pro aplikaci Netflix filmy jsou seskupené podle genre.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-147">For the Netflix application, movies are grouped by genre.</span></span> <span data-ttu-id="e9bc2-148">Proto aplikace zobrazí určitý počet žánry a seznam filmy v rámci této genre.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-148">So the application displays a number of genres and a list of movies within that genre.</span></span>  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a><span data-ttu-id="e9bc2-149">Přidat odkaz na službu ve službě Netflix OData</span><span class="sxs-lookup"><span data-stu-id="e9bc2-149">Add a Service Reference to the Netflix OData Service</span></span>  
  
1.  <span data-ttu-id="e9bc2-150">Abychom mohli provádět volání služby Netflix OData musíme přidat odkaz na službu.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-150">Before we can make any calls to the Netflix OData service we need to add a service reference.</span></span> <span data-ttu-id="e9bc2-151">Klikněte pravým tlačítkem na projekt v Průzkumníku řešení a vyberte možnost Přidat odkaz na službu...</span><span class="sxs-lookup"><span data-stu-id="e9bc2-151">Right-click the project in the Solution Explorer and select Add Service Reference…</span></span>  
  
     <span data-ttu-id="e9bc2-152">![Přidat odkaz na službu – dialogové okno](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-152">![Add Service Reference Dialog](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span></span>  
  
2.  <span data-ttu-id="e9bc2-153">Zadejte adresu URL služby Netflix OData do adresního řádku a kliknutím na Přejít.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-153">Enter the URL for the Netflix OData service in the Address bar and click Go.</span></span> <span data-ttu-id="e9bc2-154">Nastavte Namespace služby odkazu na Netflix a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-154">Set the Namespace of the service reference to Netflix and click OK.</span></span>  
  
     <span data-ttu-id="e9bc2-155">![Chyba odkazu služby přidat](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-155">![Add Service Reference Error](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9bc2-156">Pokud jste ještě nenainstalovali [WCF Data Services nástroje pro aplikace Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=266652), zobrazí se výzva s zprávou, jako je třeba výše.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-156">If you have not yet installed [WCF Data Services Tools for Windows Store Apps](http://go.microsoft.com/fwlink/p/?LinkId=266652), you will be prompted with a message such as the one above.</span></span> <span data-ttu-id="e9bc2-157">Musíte se ke stažení a instalaci nástroje odkazované ve vazbě na pokračovat.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-157">You will need to download and install the tools referenced in the link to continue.</span></span>  
  
 <span data-ttu-id="e9bc2-158">Přidání že odkazu na službu generuje silně typované třídy, které součásti WCF Data Services použije k analýze OData vrácený službou Netflix OData.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-158">Adding a service reference generates strongly typed classes that WCF Data Services will use to parse the OData returned by the Netflix OData service.</span></span> <span data-ttu-id="e9bc2-159">Třídy definované v SampleDataSource.cs mohou být vázány na GridView, takže potřebujeme k přenosu dat z vygenerované třídy klienta OData do vazbu třídy definované v SampleDataSource.cs.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-159">The classes defined in SampleDataSource.cs can be bound to the GridView so we need to transfer the data from the generated OData client classes into the bindable classes defined in SampleDataSource.cs.</span></span>  <span data-ttu-id="e9bc2-160">Chcete-li to provést, je potřeba provést některé změny do datového modelu, který je definován v SampleDataSource.cs.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-160">In order to do this, we need to make some changes to the data model defined in SampleDataSource.cs.</span></span>  
  
#### <a name="update-the-data-model-for-the-application"></a><span data-ttu-id="e9bc2-161">Aktualizovat data modelu pro aplikace</span><span class="sxs-lookup"><span data-stu-id="e9bc2-161">Update the data model for the application</span></span>  
  
1.  <span data-ttu-id="e9bc2-162">Nahraďte kód z existujícího kódu v SampleDataSource.cs [tento gist](https://gist.github.com/3419288).</span><span class="sxs-lookup"><span data-stu-id="e9bc2-162">Replace the existing code in SampleDataSource.cs with the code from [this gist](https://gist.github.com/3419288).</span></span> <span data-ttu-id="e9bc2-163">Aktualizovaný kódu přidá metoda LoadMovies (k třídě SampleDataSource), který provádí dotazy na službu Netflix OData a naplní seznam žánry (allGroups) a v rámci každé genre seznam filmy.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-163">The updated code adds a LoadMovies method (to the SampleDataSource class)  that performs a query against the Netflix OData service and populates a list of genres (allGroups) and within each genre a list of movies.</span></span> <span data-ttu-id="e9bc2-164">SampleDataGroup třída se používá k reprezentování genre a SampleDataItem třída se používá k reprezentování film.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-164">The SampleDataGroup class is used to represent a genre and the SampleDataItem class is used to represent a movie.</span></span>  
  
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
  
     <span data-ttu-id="e9bc2-165">[Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) se používá k získání asynchronně 300 (provést) poslední (OrderByDescending) PG hodnocení (kde) filmy zpět z Netflix.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-165">The [Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) is used to asynchronously get 300 (Take) recent (OrderByDescending) PG-rated (Where) movies back from Netflix.</span></span> <span data-ttu-id="e9bc2-166">Zbytek kód vytvoří SimpleDataItems a SimpleDataGroups z entit, které byly vráceny v datovém kanálu OData.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-166">The rest of the code constructs SimpleDataItems and SimpleDataGroups from the entities that were returned in the OData feed.</span></span>  
  
     <span data-ttu-id="e9bc2-167">Třída SampleDataSource také implementuje metodu jednoduché hledání.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-167">The SampleDataSource class also implements a simple search method.</span></span> <span data-ttu-id="e9bc2-168">V takovém případě se načíst filmy jednoduché hledání v paměti.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-168">In this case, it does a simple in-memory search of the loaded movies.</span></span>  
  
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
  
     <span data-ttu-id="e9bc2-169">Také v SampleDataSource.cs třídy s názvem ExtensionMethods definován.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-169">Also in SampleDataSource.cs a class called ExtensionMethods is defined.</span></span> <span data-ttu-id="e9bc2-170">Každá z těchto metod rozšíření na základě vzoru klepněte na umožní SampleDataSource provést dotaz OData bez blokování uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-170">Each of these extension methods uses the TAP pattern to allow the SampleDataSource to execute an OData query without blocking the UI.</span></span> <span data-ttu-id="e9bc2-171">Například následující kód používá metodu Task.Factory.FromAsync k implementaci klepnutím.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-171">For example, the following code uses the Task.Factory.FromAsync method to implement TAP.</span></span>  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     <span data-ttu-id="e9bc2-172">Stejně jako u výchozí aplikace je hlavní stránce aplikace GroupedItemsPage.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-172">As in the default application, the main page of the application is GroupedItemsPage.</span></span> <span data-ttu-id="e9bc2-173">Tentokrát, ale zobrazuje filmy z Netflix seskupené podle genre načíst.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-173">This time, however, it displays the movies retrieved from Netflix grouped by genre.</span></span>  <span data-ttu-id="e9bc2-174">Když je vytvořena GroupedItemsPage, jeho LoadState metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-174">When the GroupedItemsPage is instantiated, its LoadState method is called.</span></span> <span data-ttu-id="e9bc2-175">LoadState způsobí, že statická instance SampleDataSource vytvořit, vytvořit volání ke službě Netflix OData, jak je popsáno dříve.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-175">LoadState causes the static SampleDataSource instance to be created, making a call to the Netflix OData service as discussed previously.</span></span> <span data-ttu-id="e9bc2-176">LoadState ukládá DefaultViewModel kolekce žánry (SampleDataGroup objekty):</span><span class="sxs-lookup"><span data-stu-id="e9bc2-176">LoadState stores the collection of genres (SampleDataGroup objects) in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="e9bc2-177">Jak je popsáno dříve, DefaultViewModel se pak používá k vytvoření vazby dat GridView.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-177">As described previously, the DefaultViewModel is then used to bind the data to the GridView.</span></span>  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a><span data-ttu-id="e9bc2-178">Přidat smlouvu vyhledávání umožňující aplikace k účasti ve službě Windows search</span><span class="sxs-lookup"><span data-stu-id="e9bc2-178">Add a search contract to allow the application to participate in Windows search</span></span>  
  
1.  <span data-ttu-id="e9bc2-179">Přidáte smlouvy vyhledávání k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-179">Add a search contract to the application.</span></span> <span data-ttu-id="e9bc2-180">To umožňuje aplikaci k integraci s vyhledáváním systému Windows 8.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-180">This allows the application to integrate with the Windows 8 search experience.</span></span> <span data-ttu-id="e9bc2-181">Název smlouvy vyhledávání SearchResultsPage.xaml</span><span class="sxs-lookup"><span data-stu-id="e9bc2-181">Name the search contract SearchResultsPage.xaml</span></span>  
  
     <span data-ttu-id="e9bc2-182">![Přidat smlouvu vyhledávání](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span><span class="sxs-lookup"><span data-stu-id="e9bc2-182">![Add a search contract](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span></span>  
  
2.  <span data-ttu-id="e9bc2-183">Upravte řádku 58 SearchResultsPage.xaml.cs odebráním embedded uvozovkách queryText.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-183">Modify line 58 of SearchResultsPage.xaml.cs by removing the embedded quotes around queryText.</span></span>  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  <span data-ttu-id="e9bc2-184">Vložte následující dva řádky kódu na řádku 81 v SearchResultsPage.xaml.cs načíst výsledky hledání.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-184">Insert the following two lines of code at line 81 in SearchResultsPage.xaml.cs to retrieve the search results.</span></span>  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 <span data-ttu-id="e9bc2-185">Pokud je uživatel vyvolá Windows search, typy v hledaný termín a potom dotykem ikonu Netflix ukázkové aplikace v panelu vyhledávání, metodě LoadState SearchResultsPage je spustit.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-185">When a user invokes Windows search, types in a search term and then touches the Netflix Demo app icon in the search bar, the LoadState method of the SearchResultsPage is executed.</span></span> <span data-ttu-id="e9bc2-186">Parametr navigační posílá LoadState obsahuje text dotazu.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-186">The navigation parameter sent to LoadState contains the query text.</span></span> <span data-ttu-id="e9bc2-187">Další Filter_SelectionChanged metoda je volána, který potom volá metodu Search k třídě SampleDataSource.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-187">Next the Filter_SelectionChanged method is called which then calls the Search method on the SampleDataSource class.</span></span> <span data-ttu-id="e9bc2-188">Výsledky se vrátí a zobrazí na stránce SearchResultsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-188">The results are returned and displayed in the SearchResultsPage.xaml page.</span></span>  
  
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
  
 <span data-ttu-id="e9bc2-189">Další informace o integraci hledání do aplikace najdete [vyhledávání: integraci do prostředí Windows 8 vyhledávání](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span><span class="sxs-lookup"><span data-stu-id="e9bc2-189">For more information on integrating search into an application see, [Search: integrating into the Windows 8 search experience](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span></span>  
  
## <a name="run-the-application"></a><span data-ttu-id="e9bc2-190">Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="e9bc2-190">Run the application</span></span>  
 <span data-ttu-id="e9bc2-191">Spusťte aplikaci stisknutím klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-191">Launch the application by pressing F5.</span></span> <span data-ttu-id="e9bc2-192">Všimněte si, že bude trvat několik sekund načíst obrázků při spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-192">Note that it will take a few seconds to load the images upon application launch.</span></span> <span data-ttu-id="e9bc2-193">Vaše první pokus o vyhledávání navíc nemusí nevrátí žádné výsledky.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-193">Also, your first search attempt may not return any results.</span></span> <span data-ttu-id="e9bc2-194">V reálné aplikaci byste chcete řešit oba tyto problémy.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-194">In a real-world application, you would want to deal with both of these issues.</span></span>  
  
 <span data-ttu-id="e9bc2-195">Aplikace volá službu Netflix OData, obdrží data v vygenerované třídy klienta OData a pak přenáší data do vázat datové třídy (SampleDataSource, SampleDataGroup a SampleDataItem).</span><span class="sxs-lookup"><span data-stu-id="e9bc2-195">The application calls the Netflix OData service, receives the data in the generated OData client classes and then transfers that data to bindable data classes (SampleDataSource, SampleDataGroup, and SampleDataItem).</span></span> <span data-ttu-id="e9bc2-196">Tyto třídy vazbu používá k vytvoření vazby dat GridView.</span><span class="sxs-lookup"><span data-stu-id="e9bc2-196">It uses these bindable classes to bind the data to the GridView.</span></span> <span data-ttu-id="e9bc2-197">Pokud jste obeznámeni s fungování datové vazby XAML najdete [jak seskupit položky v seznamu nebo v mřížce (aplikace pro Windows Store pomocí jazyka C# / VB/C++ a XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span><span class="sxs-lookup"><span data-stu-id="e9bc2-197">If you are unfamiliar with how XAML databinding works see [How to group items in a list or grid (Windows Store apps using C#/VB/C++ and XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span></span>
