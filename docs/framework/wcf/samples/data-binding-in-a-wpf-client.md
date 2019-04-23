---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 1bc6dd2ef981115068cbd4cd491a14fea70d7e3a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979859"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="9f06b-102">Datové vazby v klientovi Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="9f06b-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="9f06b-103">Tento příklad ukazuje použití datové vazby v klientovi Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="9f06b-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="9f06b-104">Ukázka používá služba Windows Communication Foundation (WCF), která náhodně generovat pole alb vrácena klientovi.</span><span class="sxs-lookup"><span data-stu-id="9f06b-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="9f06b-105">Každé album má název, cenu a seznam alba stopy.</span><span class="sxs-lookup"><span data-stu-id="9f06b-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="9f06b-106">Sleduje alba mají název a doba trvání.</span><span class="sxs-lookup"><span data-stu-id="9f06b-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="9f06b-107">Informace, které je vrácena službou je automaticky vázán na uživatelské rozhraní (UI) poskytuje klientovi Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="9f06b-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9f06b-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9f06b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9f06b-109">Datová vazba umožňuje zdroj dat se automaticky svázán s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="9f06b-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="9f06b-110">To usnadňuje programovací model, protože nevyžaduje programově aktualizovat každého prvku uživatelského rozhraní pomocí dat z datového objektu nebo pole datových objektů.</span><span class="sxs-lookup"><span data-stu-id="9f06b-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="9f06b-111">Objekt můžete vázat na jeden prvek uživatelského rozhraní nebo pole do ovládacího prvku, který přijímá více vstupů, například `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="9f06b-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="9f06b-112">Následující kód ukazuje, jak vytvořit vazbu dat `DataContext` prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9f06b-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="9f06b-113">V předchozí ukázce `DataContext` pro `grid` rozložení element s názvem `myPanel` nastavená na dat vrácených `GetAlbumList` metoda.</span><span class="sxs-lookup"><span data-stu-id="9f06b-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="9f06b-114">`DataContext` Umožňuje prvkům dědit informace jejich nadřazených prvků o zdroji dat, který se používá pro vazbu, stejně jako ostatní vlastnosti vazby, jako je například cesta.</span><span class="sxs-lookup"><span data-stu-id="9f06b-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="9f06b-115">Pokaždé, když se aktualizuje data na serveru, je třeba spustit na řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="9f06b-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="9f06b-116">Například se provede při inicializaci okna a když se přidá nový obrázek.</span><span class="sxs-lookup"><span data-stu-id="9f06b-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="9f06b-117">V následujícím ukázkovém kódu XAML `ListBox` Určuje `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="9f06b-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="9f06b-118">Určuje, že data vázaná na element nejvyšší úrovně uživatelského rozhraní je dále vázané na tento ovládací prvek (tedy pole alb).</span><span class="sxs-lookup"><span data-stu-id="9f06b-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="9f06b-119">Kromě toho `ItemTemplate="{StaticResource AlbumStyle}"` Určuje šablonu, data se použije pro každou položku v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="9f06b-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="9f06b-120">Můžete také definovat data šablony, které určují způsob formátování data.</span><span class="sxs-lookup"><span data-stu-id="9f06b-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="9f06b-121">Tyto údaje, které šablony lze znovu použít pro ostatní prvky uživatelského rozhraní v aplikaci, výhodou je, že šablony je definovaný a spravovaný na jednom místě.</span><span class="sxs-lookup"><span data-stu-id="9f06b-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="9f06b-122">`AlbumStyle` Šablona rozložen mřížky se dvěma `TextBlock`s vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="9f06b-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="9f06b-123">Jeden alba Určuje název alba a jiných počet stop.</span><span class="sxs-lookup"><span data-stu-id="9f06b-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="9f06b-124">Následující kód XAML vytvoří druhou `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="9f06b-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="9f06b-125">Určuje cestu pro kód `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="9f06b-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="9f06b-126">To znamená, že data vázaná na tento ovládací prvek není dat nejvyšší úrovně, ale vlastnost dat nejvyšší úrovně s názvem `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="9f06b-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="9f06b-127">Tato vlastnost představuje pole obsažené v alba sleduje.</span><span class="sxs-lookup"><span data-stu-id="9f06b-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="9f06b-128">Kromě toho jiný `DataTemplate` s názvem `TrackStyle` určena.</span><span class="sxs-lookup"><span data-stu-id="9f06b-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="9f06b-129">Rozložení `TrackStyle` šablona je podobná `AlbumStyle` šablony, ale `TextBlock`s jsou vázány na jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9f06b-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="9f06b-130">Je to proto, že tyto dvě šablony se používají s různými datovými objekty.</span><span class="sxs-lookup"><span data-stu-id="9f06b-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9f06b-131">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9f06b-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9f06b-132">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9f06b-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9f06b-133">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9f06b-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9f06b-134">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9f06b-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9f06b-135">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="9f06b-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9f06b-136">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9f06b-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9f06b-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9f06b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9f06b-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9f06b-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
