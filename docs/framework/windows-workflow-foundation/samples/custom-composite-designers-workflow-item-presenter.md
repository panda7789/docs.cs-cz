---
title: Návrháři vlastního - skládání položky pracovního postupu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: d201dad45f4ed31d7c06f3302a9cdfbb01647722
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54731007"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="2e09b-102">Návrháři vlastního - skládání položky pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2e09b-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="2e09b-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> Je typ klíče v WF návrháře programovací model, který umožňuje vytváření "rozevírací zónu" umístění libovolné aktivity.</span><span class="sxs-lookup"><span data-stu-id="2e09b-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="2e09b-104">Tento příklad ukazuje, jak vytvářet Návrhář aktivity tohoto zařízení Surface takovou "rozevírací zónu."</span><span class="sxs-lookup"><span data-stu-id="2e09b-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

 <span data-ttu-id="2e09b-105">V této ukázce:</span><span class="sxs-lookup"><span data-stu-id="2e09b-105">This sample demonstrates:</span></span>

## <a name="demonstrates"></a><span data-ttu-id="2e09b-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="2e09b-106">Demonstrates</span></span>

-   <span data-ttu-id="2e09b-107">Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="2e09b-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

-   <span data-ttu-id="2e09b-108">Registrace vlastní úložiště metadat pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="2e09b-108">Registering the custom designer using the metadata store.</span></span>

-   <span data-ttu-id="2e09b-109">Deklarativní a imperativně programování provádění se změněným hostováním sady nástrojů.</span><span class="sxs-lookup"><span data-stu-id="2e09b-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="2e09b-110">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2e09b-110">Sample Details</span></span>
 <span data-ttu-id="2e09b-111">Kód pro tento příklad ukazuje:</span><span class="sxs-lookup"><span data-stu-id="2e09b-111">The code for this sample shows:</span></span>

-   <span data-ttu-id="2e09b-112">Návrháři vlastních aktivit je sestaven pro `SimpleNativeActivity` třídy.</span><span class="sxs-lookup"><span data-stu-id="2e09b-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

-   <span data-ttu-id="2e09b-113">Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="2e09b-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

```xaml
<sap:ActivityDesigner x:Class="Microsoft.Samples.UsingWorkflowItemPresenter.SimpleNativeDesigner"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
    xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
    <sap:ActivityDesigner.Resources>
        <DataTemplate x:Key="Collapsed">
            <StackPanel>
                <TextBlock>This is the collapsed view</TextBlock>
            </StackPanel>
        </DataTemplate>
        <DataTemplate x:Key="Expanded">
            <StackPanel>
                <TextBlock>Custom Text</TextBlock>
                <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                        HintText="Please drop an activity here" />
            </StackPanel>
        </DataTemplate>
        <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
            <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
            <Style.Triggers>
                <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                    <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                </DataTrigger>
            </Style.Triggers>
        </Style>
    </sap:ActivityDesigner.Resources>
    <Grid>
        <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
    </Grid>
</sap:ActivityDesigner>
```

 <span data-ttu-id="2e09b-114">Všimněte si použití datové vazby WPF vytvořit vazbu na `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="2e09b-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="2e09b-115">`ModelItem` je vlastnost na <xref:System.Activities.Presentation.ActivityDesigner> , který odkazuje na základní objekt návrháře se používá, v tomto případě **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="2e09b-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="2e09b-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2e09b-116">To setup, build, and run the sample</span></span>

1.  <span data-ttu-id="2e09b-117">Otevřete řešení v sadě Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2e09b-117">Open the solution in Visual Studio 2010.</span></span>

2.  <span data-ttu-id="2e09b-118">Stiskněte klávesu F5 ke kompilaci a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="2e09b-118">Press F5 to compile and run the application.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="2e09b-119">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="2e09b-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2e09b-120">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="2e09b-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2e09b-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="2e09b-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2e09b-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2e09b-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="2e09b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e09b-123">See also</span></span>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="2e09b-124">Vývoj aplikací pomocí návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="2e09b-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
