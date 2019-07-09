---
title: Návrháři vlastního skládání – místo pro položky pracovních postupů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: b28981196490e249d053ecd1704f6ba978585520
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662856"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="623db-102">Návrháři vlastního skládání – místo pro položky pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="623db-102">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="623db-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Je typ klíče v WF návrháře programovací model, který umožňuje úpravy kolekci elementů obsažených.</span><span class="sxs-lookup"><span data-stu-id="623db-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="623db-104">Tato ukázka předvádí, jak vytvářet návrháře aktivit, který poskytuje informace o upravitelné kolekce.</span><span class="sxs-lookup"><span data-stu-id="623db-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="623db-105">V této ukázce:</span><span class="sxs-lookup"><span data-stu-id="623db-105">This sample demonstrates:</span></span>

- <span data-ttu-id="623db-106">Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="623db-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="623db-107">Vytváření návrháře aktivit se zobrazením "sbalené" a "Rozšířená".</span><span class="sxs-lookup"><span data-stu-id="623db-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="623db-108">Přepsání výchozího návrháře v provádění se změněným hostováním aplikací.</span><span class="sxs-lookup"><span data-stu-id="623db-108">Overriding a default designer in a rehosted application.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="623db-109">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="623db-109">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="623db-110">Otevřít **UsingWorkflowItemsPresenter.sln** ukázkové řešení pro jazyk C# nebo vb v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="623db-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in Visual Studio 2010.</span></span>

2. <span data-ttu-id="623db-111">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="623db-111">Build and run the solution.</span></span> <span data-ttu-id="623db-112">By měla otevřít návrháře aplikaci provádění se změněným hostováním pracovního postupu a můžete přetáhnout aktivity na plátno.</span><span class="sxs-lookup"><span data-stu-id="623db-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="623db-113">Stručný přehled ukázky</span><span class="sxs-lookup"><span data-stu-id="623db-113">Sample Highlights</span></span>

<span data-ttu-id="623db-114">Kód pro tento příklad ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="623db-114">The code for this sample shows the following:</span></span>

- <span data-ttu-id="623db-115">Návrhář aktivity je sestaven pro:  `Parallel`</span><span class="sxs-lookup"><span data-stu-id="623db-115">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="623db-116">Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="623db-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="623db-117">Pár věcí, které upozorňují na:</span><span class="sxs-lookup"><span data-stu-id="623db-117">A few things to point out:</span></span>

  - <span data-ttu-id="623db-118">Všimněte si použití datové vazby WPF vytvořit vazbu na `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="623db-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="623db-119">`ModelItem` je vlastnost na `WorkflowElementDesigner` , který odkazuje na základní objekt návrháře se používá, v tomto případě naší `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="623db-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="623db-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Je možné do vizuálu zobrazit mezi jednotlivých položek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="623db-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="623db-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> je šablonu, která je možné poskytnout určit rozložení položek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="623db-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="623db-122">V takovém případě se používá panel vodorovné zásobníku.</span><span class="sxs-lookup"><span data-stu-id="623db-122">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="623db-123">Tento následující příklad kódu ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="623db-123">This following example code shows this.</span></span>

  ```xaml
  <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                Items="{Binding Path=ModelItem.Branches}">
      <sad:WorkflowItemsPresenter.SpacerTemplate>
        <DataTemplate>
          <Ellipse Width="10" Height="10" Fill="Black"/>
        </DataTemplate>
      </sad:WorkflowItemsPresenter.SpacerTemplate>
      <sad:WorkflowItemsPresenter.ItemsPanel>
        <ItemsPanelTemplate>
          <StackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
      </sad:WorkflowItemsPresenter.ItemsPanel>
    </sad:WorkflowItemsPresenter>
  ```

- <span data-ttu-id="623db-124">Provedení sdružení `DesignerAttribute` k `Parallel` typu a potom výstup hlášené atributy.</span><span class="sxs-lookup"><span data-stu-id="623db-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="623db-125">Nejprve zaregistrujte všechny výchozí návrháře.</span><span class="sxs-lookup"><span data-stu-id="623db-125">First, register all of the default designers.</span></span>

    <span data-ttu-id="623db-126">Tady je příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="623db-126">The following is the code example.</span></span>

    ```csharp
    // register metadata
    (new DesignerMetadata()).Register();
    RegisterCustomMetadata();
    ```

    ```vb
    ' register metadata
    Dim metadata = New DesignerMetadata()
    metadata.Register()
    ' register custom metadata
    RegisterCustomMetadata()
    ```

  - <span data-ttu-id="623db-127">Potom přepsat paralelní v `RegisterCustomMetadata` metody.</span><span class="sxs-lookup"><span data-stu-id="623db-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="623db-128">Následující kód ukazuje to v C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="623db-128">The following code shows this in C# and Visual Basic.</span></span>

    ```csharp
    void RegisterCustomMetadata()
    {
          AttributeTableBuilder builder = new AttributeTableBuilder();
          builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
          MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

    ```vb
    Sub RegisterCustomMetadata()
       Dim builder As New AttributeTableBuilder()
       builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
       MetadataStore.AddAttributeTable(builder.CreateTable())
    End Sub
    ```

- <span data-ttu-id="623db-129">A konečně, Všimněte si použití odlišné datové šablony a aktivační události vyberte příslušnou šablonu na základě `IsRootDesigner` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="623db-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="623db-130">Tady je příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="623db-130">The following is the code example.</span></span>

  ```xaml
  <sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
      xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
    <sad:ActivityDesigner.Resources>
      <DataTemplate x:Key="Expanded">
        <StackPanel>
          <TextBlock>This is the Expanded View</TextBlock>
          <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                      Items="{Binding Path=ModelItem.Branches}">
            <sad:WorkflowItemsPresenter.SpacerTemplate>
              <DataTemplate>
                <Ellipse Width="10" Height="10" Fill="Black"/>
              </DataTemplate>
            </sad:WorkflowItemsPresenter.SpacerTemplate>
            <sad:WorkflowItemsPresenter.ItemsPanel>
              <ItemsPanelTemplate>
                <StackPanel Orientation="Horizontal"/>
              </ItemsPanelTemplate>
            </sad:WorkflowItemsPresenter.ItemsPanel>
          </sad:WorkflowItemsPresenter>
        </StackPanel>
      </DataTemplate>
      <DataTemplate x:Key="Collapsed">
        <TextBlock>This is the Collapsed View</TextBlock>
      </DataTemplate>
      <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
        <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
        <Style.Triggers>
          <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
            <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
          </DataTrigger>
        </Style.Triggers>
      </Style>
    </sad: ActivityDesigner.Resources>
    <Grid>
      <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
    </Grid>
  </sad: ActivityDesigner>
  ```

> [!IMPORTANT]
> <span data-ttu-id="623db-131">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="623db-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="623db-132">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="623db-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="623db-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="623db-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="623db-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="623db-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="623db-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="623db-135">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="623db-136">Vývoj aplikací pomocí návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="623db-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
