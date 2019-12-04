---
title: Návrháři vlastního skládání – místo pro položky pracovních postupů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 542440d6bf9d6809abee1ec37c85c44ce72fd132
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715162"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="5f2a6-102">Návrháři vlastního skládání – místo pro položky pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="5f2a6-102">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="5f2a6-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> je typ klíče v programovacím modelu Návrháře WF, který umožňuje úpravu kolekce obsažených prvků.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="5f2a6-104">V této ukázce se dozvíte, jak vytvořit Návrhář aktivity, který je povrchem takové upravitelné kolekce.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="5f2a6-105">Tato ukázka demonstruje:</span><span class="sxs-lookup"><span data-stu-id="5f2a6-105">This sample demonstrates:</span></span>

- <span data-ttu-id="5f2a6-106">Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="5f2a6-107">Vytvoření návrháře aktivit se zobrazením "sbalené" a "rozšířené".</span><span class="sxs-lookup"><span data-stu-id="5f2a6-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="5f2a6-108">Přepsání výchozího návrháře v znovu hostované aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-108">Overriding a default designer in a rehosted application.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f2a6-109">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5f2a6-109">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5f2a6-110">Otevřete ukázkové řešení **UsingWorkflowItemsPresenter. sln** pro C# nebo pro jazyk VB v aplikaci Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for VB in Visual Studio 2010.</span></span>

2. <span data-ttu-id="5f2a6-111">Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-111">Build and run the solution.</span></span> <span data-ttu-id="5f2a6-112">Měla by se otevřít znovu hostující aplikace návrháře pracovních postupů a aktivity můžete přetáhnout na plátno.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-112">A rehosted workflow designer application should open, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="5f2a6-113">Ukázka světel</span><span class="sxs-lookup"><span data-stu-id="5f2a6-113">Sample Highlights</span></span>

<span data-ttu-id="5f2a6-114">Kód pro tuto ukázku ukazuje následující:</span><span class="sxs-lookup"><span data-stu-id="5f2a6-114">The code for this sample shows the following:</span></span>

- <span data-ttu-id="5f2a6-115">Aktivita, pro kterou je Návrhář sestavený: `Parallel`</span><span class="sxs-lookup"><span data-stu-id="5f2a6-115">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="5f2a6-116">Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f2a6-117">Pár věcí k ukázání:</span><span class="sxs-lookup"><span data-stu-id="5f2a6-117">A few things to point out:</span></span>

  - <span data-ttu-id="5f2a6-118">Všimněte si, že použití datové vazby WPF pro vazbu na `ModelItem.Branches`.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="5f2a6-119">`ModelItem` je vlastnost u `WorkflowElementDesigner`, která odkazuje na podkladový objekt, pro který je Návrhář používán, v tomto případě naše `Parallel`.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="5f2a6-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> lze použít k vložení vizuálu pro zobrazení mezi jednotlivými položkami v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="5f2a6-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> je šablona, kterou lze zadat k určení rozložení položek v kolekci.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="5f2a6-122">V takovém případě se použije vodorovný panel zásobníku.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-122">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="5f2a6-123">Následující příklad kódu ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-123">This following example code shows this.</span></span>

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

- <span data-ttu-id="5f2a6-124">Provede přidružení `DesignerAttribute` k typu `Parallel` a pak výstup nahlášených atributů.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="5f2a6-125">Nejprve Zaregistrujte všechny výchozí návrháře.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-125">First, register all of the default designers.</span></span>

    <span data-ttu-id="5f2a6-126">Následuje příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-126">The following is the code example.</span></span>

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

  - <span data-ttu-id="5f2a6-127">Pak přepište paralelní v metodě `RegisterCustomMetadata`.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="5f2a6-128">Následující kód ukazuje to v C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-128">The following code shows this in C# and Visual Basic.</span></span>

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

- <span data-ttu-id="5f2a6-129">Nakonec si všimněte použití různých datových šablon a triggerů k výběru vhodné šablony na základě vlastnosti `IsRootDesigner`.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="5f2a6-130">Následuje příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-130">The following is the code example.</span></span>

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
> <span data-ttu-id="5f2a6-131">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f2a6-132">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5f2a6-133">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f2a6-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5f2a6-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="5f2a6-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f2a6-135">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="5f2a6-136">Vývoj aplikací pomocí návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="5f2a6-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
