---
title: Návrháři vlastního skládání – místo pro položku pracovního postupu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: d1047b8be35545e83eaa8788b53751b6b0056984
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338041"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="2a3c2-102">Návrháři vlastního skládání – místo pro položku pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2a3c2-102">Custom Composite Designers - Workflow Item Presenter</span></span>

<span data-ttu-id="2a3c2-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> je typ klíče v programovacím modelu Návrháře WF, který umožňuje vytvoření "ukládací zóny", kde lze umístit libovolnou aktivitu.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="2a3c2-104">V této ukázce se dozvíte, jak vytvořit Návrhář aktivity, který je povrchem "ukládací zóny".</span><span class="sxs-lookup"><span data-stu-id="2a3c2-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>

<span data-ttu-id="2a3c2-105">Tato ukázka demonstruje:</span><span class="sxs-lookup"><span data-stu-id="2a3c2-105">This sample demonstrates:</span></span>

- <span data-ttu-id="2a3c2-106">Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

- <span data-ttu-id="2a3c2-107">Vlastní Návrhář se registruje pomocí úložiště metadat.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-107">Registering the custom designer using the metadata store.</span></span>

- <span data-ttu-id="2a3c2-108">Deklarativní a imperativní programování znovu hostující sady nástrojů.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-108">Programming the rehosted toolbox declaratively and imperatively.</span></span>

## <a name="sample-details"></a><span data-ttu-id="2a3c2-109">Podrobnosti ukázky</span><span class="sxs-lookup"><span data-stu-id="2a3c2-109">Sample Details</span></span>

<span data-ttu-id="2a3c2-110">Kód pro tuto ukázku ukazuje:</span><span class="sxs-lookup"><span data-stu-id="2a3c2-110">The code for this sample shows:</span></span>

- <span data-ttu-id="2a3c2-111">Návrhář vlastní aktivity je sestaven pro třídu `SimpleNativeActivity`.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-111">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>

- <span data-ttu-id="2a3c2-112">Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-112">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>

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

 <span data-ttu-id="2a3c2-113">Všimněte si, že použití datové vazby WPF pro vazbu na `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-113">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="2a3c2-114">`ModelItem` je vlastnost na <xref:System.Activities.Presentation.ActivityDesigner>, která odkazuje na podkladový objekt, pro který je Návrhář používán, v tomto případě **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-114">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="2a3c2-115">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="2a3c2-115">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="2a3c2-116">Otevřete řešení v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-116">Open the solution in Visual Studio.</span></span>

2. <span data-ttu-id="2a3c2-117">Pro zkompilování a spuštění aplikace stiskněte klávesu **F5** .</span><span class="sxs-lookup"><span data-stu-id="2a3c2-117">Press **F5** to compile and run the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2a3c2-118">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2a3c2-119">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-119">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="2a3c2-120">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2a3c2-121">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2a3c2-121">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`

## <a name="see-also"></a><span data-ttu-id="2a3c2-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a3c2-122">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [<span data-ttu-id="2a3c2-123">Vývoj aplikací pomocí návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="2a3c2-123">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
