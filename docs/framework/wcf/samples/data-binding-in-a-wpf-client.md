---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 44a208cf081ef00396dfc874349dff57363c0df3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715390"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="ee2d9-102">Datové vazby v klientovi Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="ee2d9-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="ee2d9-103">Tato ukázka demonstruje použití datových vazeb v klientu Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ee2d9-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="ee2d9-104">Ukázka používá službu Windows Communication Foundation (WCF), která náhodně generuje pole alb pro návrat do klienta.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="ee2d9-105">Každé album má název, cenu a seznam skladeb alba.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="ee2d9-106">Stopy alba mají název a dobu trvání.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="ee2d9-107">Informace, které služba vrací, jsou automaticky svázány s uživatelským rozhraním (UI) poskytovaným klientem Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="ee2d9-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee2d9-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ee2d9-109">Datová vazba umožňuje, aby byl zdroj dat automaticky svázán s uživatelským rozhraním.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="ee2d9-110">Tím se zjednoduší programovací model, protože nevyžaduje, abyste programově aktualizovali jednotlivé prvky uživatelského rozhraní daty z datového objektu nebo pole datových objektů.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="ee2d9-111">Můžete vytvořit vazby objektu k jednomu prvku uživatelského rozhraní nebo poli k ovládacímu prvku, který přijímá více vstupů, například `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="ee2d9-112">Následující kód ukazuje, jak vytvořit vazby dat k `DataContext` prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="ee2d9-113">V předchozím příkladu je `DataContext` pro `grid` prvek rozložení s názvem `myPanel` nastavena na data vrácená metodou `GetAlbumList`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="ee2d9-114">`DataContext` umožňuje elementům zdědit informace z jejich nadřazených prvků o zdroji dat, který se používá pro vazbu, a také k dalším charakteristikám vazby, jako je například cesta.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="ee2d9-115">Řádek kódu musí být proveden při každém aktualizování dat na serveru.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="ee2d9-116">Například se spustí při inicializaci okna a přidání nového alba.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="ee2d9-117">V následujícím ukázkovém kódu jazyka XAML `ListBox` určuje `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="ee2d9-118">To určuje, že data vázaná na prvek uživatelského rozhraní nejvyšší úrovně jsou také svázána s tímto ovládacím prvkem (tj. polem alba).</span><span class="sxs-lookup"><span data-stu-id="ee2d9-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="ee2d9-119">`ItemTemplate="{StaticResource AlbumStyle}"` také určuje šablonu dat, která se má použít pro každou položku v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="ee2d9-120">Můžete také definovat datové šablony, abyste určili, jak mají být data formátována.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="ee2d9-121">Tyto datové šablony lze znovu použít pro jiné prvky uživatelského rozhraní v aplikaci. výhodou je, že je šablona dat definována a udržována na jednom místě.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="ee2d9-122">Šablona `AlbumStyle` data obsahuje mřížku se dvěma `TextBlock`y vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="ee2d9-123">Jedna Určuje název alba a druhý počet stop v albu.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="ee2d9-124">Následující kód XAML vytvoří druhý `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="ee2d9-125">Kód určuje cestu pro `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="ee2d9-126">To značí, že data vázaná na tento ovládací prvek nejsou data nejvyšší úrovně, ale vlastnost dat nejvyšší úrovně s názvem `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="ee2d9-127">Tato vlastnost představuje pole stop obsažených v albu.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="ee2d9-128">Kromě toho je určena jiná `DataTemplate` s názvem `TrackStyle`.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="ee2d9-129">Rozložení `TrackStyle` šablony se podobá šabloně `AlbumStyle`, ale `TextBlock`s jsou vázány na jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="ee2d9-130">Důvodem je to, že dvě šablony jsou používány s různými datovými objekty.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ee2d9-131">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="ee2d9-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ee2d9-132">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee2d9-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ee2d9-133">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee2d9-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="ee2d9-134">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ee2d9-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ee2d9-135">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee2d9-136">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="ee2d9-137">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee2d9-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="ee2d9-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
