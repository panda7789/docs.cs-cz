---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 7bc389056872841905336dcf658a07223906bf82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183823"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="d93c5-102">Datové vazby v klientovi Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d93c5-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="d93c5-103">Tato ukázka ukazuje použití datové vazby v klientovi WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="d93c5-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="d93c5-104">Ukázka používá službu WCF (Windows Communication Foundation), která náhodně generuje pole alb pro návrat do klienta.</span><span class="sxs-lookup"><span data-stu-id="d93c5-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="d93c5-105">Každé album má název, cenu a seznam skladeb alb.</span><span class="sxs-lookup"><span data-stu-id="d93c5-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="d93c5-106">Skladby alba mají název a dobu trvání.</span><span class="sxs-lookup"><span data-stu-id="d93c5-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="d93c5-107">Informace vrácené službou jsou automaticky vázány na uživatelské rozhraní poskytované klientem WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="d93c5-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d93c5-108">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d93c5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d93c5-109">Datová vazba umožňuje zdroj dat automaticky vázán na ui.</span><span class="sxs-lookup"><span data-stu-id="d93c5-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="d93c5-110">To zjednodušuje programovací model, protože nevyžaduje programovou aktualizaci každého prvku rozhraní s daty z datového objektu nebo pole datových objektů.</span><span class="sxs-lookup"><span data-stu-id="d93c5-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="d93c5-111">Objekt můžete svázat s jedním prvkem rozhraní nebo polem s ovládacím prvkem, který přebírá více vstupů, například `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d93c5-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="d93c5-112">Následující kód ukazuje, jak vázat `DataContext` data na prvek ui.</span><span class="sxs-lookup"><span data-stu-id="d93c5-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="d93c5-113">V předchozí ukázce `grid` je `myPanel` prvek `DataContext` rozložení pojmenovaný nastaven `GetAlbumList` na data vrácená metodou.</span><span class="sxs-lookup"><span data-stu-id="d93c5-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="d93c5-114">Umožňuje `DataContext` prvky dědit informace z jejich nadřazené prvky o zdroj dat, který se používá pro vazbu, jakož i další charakteristiky vazby, jako je například cesta.</span><span class="sxs-lookup"><span data-stu-id="d93c5-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="d93c5-115">Řádek kódu musí být proveden při každé aktualizaci dat na serveru.</span><span class="sxs-lookup"><span data-stu-id="d93c5-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="d93c5-116">Například je spuštěn při inicializování okna a při přidání nového alba.</span><span class="sxs-lookup"><span data-stu-id="d93c5-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="d93c5-117">V následujícím vzorku kódu XAML `ListBox` `ItemsSource="{Binding }"`určuje .</span><span class="sxs-lookup"><span data-stu-id="d93c5-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="d93c5-118">To určuje, že data vázaná na prvek hlavní úrovně ui je také vázána na tento ovládací prvek (to znamená pole alba).</span><span class="sxs-lookup"><span data-stu-id="d93c5-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="d93c5-119">Kromě toho `ItemTemplate="{StaticResource AlbumStyle}"` určuje šablonu dat, která má `ListBox`být použita pro každou položku v .</span><span class="sxs-lookup"><span data-stu-id="d93c5-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="d93c5-120">Můžete také definovat šablony dat a určit způsob formátování dat.</span><span class="sxs-lookup"><span data-stu-id="d93c5-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="d93c5-121">Tyto šablony dat lze znovu použít pro jiné prvky uživatelského rozhraní v aplikaci, výhodou je, že šablona dat je definována a udržována na jednom místě.</span><span class="sxs-lookup"><span data-stu-id="d93c5-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="d93c5-122">Šablona `AlbumStyle` dat obsahuje mřížku `TextBlock`se dvěma s vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="d93c5-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="d93c5-123">Jeden určuje název alba a druhý počet skladeb v albu.</span><span class="sxs-lookup"><span data-stu-id="d93c5-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="d93c5-124">Následující kód XAML vytvoří `ListBox`druhý .</span><span class="sxs-lookup"><span data-stu-id="d93c5-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="d93c5-125">Kód určuje cestu pro `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="d93c5-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="d93c5-126">To znamená, že data vázaná na tento ovládací prvek nejsou data nejvyšší `Tracks`úrovně, ale vlastnost dat nejvyšší úrovně s názvem .</span><span class="sxs-lookup"><span data-stu-id="d93c5-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="d93c5-127">Tato vlastnost představuje pole skladeb obsažených v albu.</span><span class="sxs-lookup"><span data-stu-id="d93c5-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="d93c5-128">Kromě toho je `DataTemplate` `TrackStyle` zadán jiný název.</span><span class="sxs-lookup"><span data-stu-id="d93c5-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="d93c5-129">Rozložení `TrackStyle` šablony je podobné rozložení `AlbumStyle` šablony, ale `TextBlock`s jsou vázány na různé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d93c5-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="d93c5-130">Důvodem je, že dvě šablony se používají s různými datovými objekty.</span><span class="sxs-lookup"><span data-stu-id="d93c5-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d93c5-131">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="d93c5-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d93c5-132">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d93c5-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d93c5-133">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d93c5-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d93c5-134">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d93c5-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d93c5-135">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="d93c5-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d93c5-136">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="d93c5-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d93c5-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d93c5-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d93c5-138">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d93c5-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
