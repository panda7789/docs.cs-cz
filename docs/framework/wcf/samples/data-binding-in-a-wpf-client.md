---
title: Datové vazby v klientovi Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 225bdedb67e218092ff3369d4fe742c4fc897fc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502543"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="d5dd4-102">Datové vazby v klientovi Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d5dd4-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="d5dd4-103">Tento příklad znázorňuje použití datové vazby v klientovi Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d5dd4-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="d5dd4-104">Příklad používá služba Windows Communication Foundation (WCF), která generuje náhodně pole alb se vraťte do klienta.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="d5dd4-105">Každé album má název, ceny a seznam album sleduje.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="d5dd4-106">Sleduje album mít název, doba trvání.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="d5dd4-107">Informace, které je vrácena službou je automaticky vázána uživatelské rozhraní (UI) poskytnutý klientem Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d5dd4-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5dd4-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d5dd4-109">Datová vazba umožňuje zdroj dat automaticky vázat uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="d5dd4-110">To usnadňuje programovací model, protože nevyžaduje s daty z datový objekt nebo pole objektů dat prostřednictvím kódu programu aktualizovat jednotlivých prvků uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="d5dd4-111">Objekt můžete vázat na jeden element uživatelského rozhraní nebo pole do ovládacího prvku, který přebírá více vstupů, například `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="d5dd4-112">Následující kód ukazuje, jak vytvořit vazbu dat `DataContext` elementu uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="d5dd4-113">V předchozí ukázce `DataContext` pro `grid` rozložení element s názvem `myPanel` je nastaven na hodnotu data vrácený `GetAlbumList` metoda.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="d5dd4-114">`DataContext` Umožňuje elementy dědění informace z jejich nadřazené elementy o zdroji dat, který se používá pro vazbu, jakož i dalších vlastností vazby například cestu.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="d5dd4-115">Pokaždé, když se aktualizuje data na serveru, je třeba spustit na řádek kódu.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="d5dd4-116">Například se spustí, když je inicializován okna a při přidání nové album.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="d5dd4-117">V následujícím vzorovém kódu XAML `ListBox` Určuje `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="d5dd4-118">Určuje, že data vázaná na element nejvyšší úrovně uživatelského rozhraní je také vázána na tento ovládací prvek (tj. pole alb).</span><span class="sxs-lookup"><span data-stu-id="d5dd4-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="d5dd4-119">Kromě toho `ItemTemplate="{StaticResource AlbumStyle}"` Určuje šablonu dat, který se má použít pro každou položku v `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="d5dd4-120">Můžete také definovat data šablony, které určují způsob formátování data.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="d5dd4-121">Těchto datových šablony můžete znovu použít pro další prvky uživatelského rozhraní v aplikaci, výhodou je, že šablona dat je definovaný a spravovaný na jednom místě.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="d5dd4-122">`AlbumStyle` Datová šablona rozložen mřížky se dvěma `TextBlock`s vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="d5dd4-123">Jeden z alba Určuje název alba a jiných počet stop.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="d5dd4-124">Následující kód XAML vytvoří druhý `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="d5dd4-125">Určuje cestu pro kód `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="d5dd4-126">To znamená, že data vázaná na tento ovládací prvek není dat nejvyšší úrovně, ale vlastnost dat nejvyšší úrovně s názvem `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="d5dd4-127">Tato vlastnost představuje pole sleduje obsažené v alba.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="d5dd4-128">Kromě toho jiné `DataTemplate` s názvem `TrackStyle` je zadán.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="d5dd4-129">Rozložení `TrackStyle` šablony je podobné jako `AlbumStyle` šablony, ale `TextBlock`s jsou vázány na jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="d5dd4-130">Je to proto, že se různé datové objekty se používají dvě šablony.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d5dd4-131">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d5dd4-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d5dd4-132">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5dd4-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d5dd4-133">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5dd4-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d5dd4-134">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d5dd4-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d5dd4-135">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d5dd4-136">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d5dd4-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d5dd4-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d5dd4-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d5dd4-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a><span data-ttu-id="d5dd4-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5dd4-139">See Also</span></span>
