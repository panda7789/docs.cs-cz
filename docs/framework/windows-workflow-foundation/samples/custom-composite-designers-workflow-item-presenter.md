---
title: Návrháři vlastního skládání – místo pro položku pracovního postupu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 31dfae70a8b95bdfd457efe7a20ce44c2ba9c61f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715188"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="cfce9-102">Návrháři vlastního skládání – místo pro položku pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="cfce9-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="cfce9-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> je typ klíče v programovacím modelu Návrháře WF, který umožňuje vytvoření "ukládací zóny", kde lze umístit libovolnou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="cfce9-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="cfce9-104">V této ukázce se dozvíte, jak vytvořit Návrhář aktivity, který je povrchem "ukládací zóny".</span><span class="sxs-lookup"><span data-stu-id="cfce9-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

 <span data-ttu-id="cfce9-105">Tato ukázka demonstruje:</span><span class="sxs-lookup"><span data-stu-id="cfce9-105">This sample demonstrates:</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cfce9-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="cfce9-106">Demonstrates</span></span>

- <span data-ttu-id="cfce9-107">Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="cfce9-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="cfce9-108">Vlastní Návrhář se registruje pomocí úložiště metadat.</span><span class="sxs-lookup"><span data-stu-id="cfce9-108">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="cfce9-109">Deklarativní a imperativní programování znovu hostující sady nástrojů.</span><span class="sxs-lookup"><span data-stu-id="cfce9-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="cfce9-110">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="cfce9-110">Sample Details</span></span>
 <span data-ttu-id="cfce9-111">Kód pro tuto ukázku ukazuje:</span><span class="sxs-lookup"><span data-stu-id="cfce9-111">The code for this sample shows:</span></span>

- <span data-ttu-id="cfce9-112">Návrhář vlastní aktivity je sestaven pro třídu `SimpleNativeActivity`.</span><span class="sxs-lookup"><span data-stu-id="cfce9-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="cfce9-113">Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="cfce9-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

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

 <span data-ttu-id="cfce9-114">Všimněte si, že použití datové vazby WPF pro vazbu na `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="cfce9-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="cfce9-115">`ModelItem` je vlastnost na <xref:System.Activities.Presentation.ActivityDesigner>, která odkazuje na podkladový objekt, pro který je Návrhář používán, v tomto případě **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="cfce9-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="cfce9-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="cfce9-116">To setup, build, and run the sample</span></span>

1. <span data-ttu-id="cfce9-117">Otevřete řešení v aplikaci Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="cfce9-117">Open the solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="cfce9-118">Pro zkompilování a spuštění aplikace stiskněte klávesu F5.</span><span class="sxs-lookup"><span data-stu-id="cfce9-118">Press F5 to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cfce9-119">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="cfce9-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cfce9-120">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="cfce9-120">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="cfce9-121">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="cfce9-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cfce9-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="cfce9-122">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="cfce9-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfce9-123">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="cfce9-124">Vývoj aplikací pomocí návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="cfce9-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
