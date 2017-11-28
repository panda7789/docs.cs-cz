---
title: "Vlastní složený Designer - přednášejícího položky pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3fa40a7a864ae65d15d787f5dec58a8da7b8e9a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="custom-composite-designers---workflow-item-presenter"></a><span data-ttu-id="bea18-102">Vlastní složený Designer - přednášejícího položky pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="bea18-102">Custom Composite Designers - Workflow Item Presenter</span></span>
<span data-ttu-id="bea18-103"><xref:System.Activities.Presentation.WorkflowItemPresenter> Je typ klíče v WF návrháře programovací model, který umožňuje vytváření "rozevírací zónu" umístění libovolné aktivity.</span><span class="sxs-lookup"><span data-stu-id="bea18-103">The <xref:System.Activities.Presentation.WorkflowItemPresenter> is a key type in the WF designer programming model that allows for the creation of a "drop zone" where an arbitrary activity can be placed.</span></span> <span data-ttu-id="bea18-104">Tento příklad ukazuje, jak stavět Návrhář aktivity tohoto povrchy takovou "rozevírací zónu."</span><span class="sxs-lookup"><span data-stu-id="bea18-104">This sample shows how to build an activity designer that surfaces such a "drop zone."</span></span>  
  
 <span data-ttu-id="bea18-105">Tento příklad znázorňuje:</span><span class="sxs-lookup"><span data-stu-id="bea18-105">This sample demonstrates:</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="bea18-106">Demonstruje</span><span class="sxs-lookup"><span data-stu-id="bea18-106">Demonstrates</span></span>  
  
-   <span data-ttu-id="bea18-107">Vytváření Návrháře vlastních aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="bea18-107">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
-   <span data-ttu-id="bea18-108">Probíhá registrace návrháře vlastní pomocí úložiště metadat.</span><span class="sxs-lookup"><span data-stu-id="bea18-108">Registering the custom designer using the metadata store.</span></span>  
  
-   <span data-ttu-id="bea18-109">Programování opětovné hostování nástroje sady nástrojů deklarativně a imperativní.</span><span class="sxs-lookup"><span data-stu-id="bea18-109">Programming the rehosted toolbox declaratively and imperatively.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="bea18-110">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bea18-110">Sample Details</span></span>  
 <span data-ttu-id="bea18-111">Kód pro tento příklad ukazuje:</span><span class="sxs-lookup"><span data-stu-id="bea18-111">The code for this sample shows:</span></span>  
  
-   <span data-ttu-id="bea18-112">Návrhář vlastní aktivity je vytvořené pro `SimpleNativeActivity` třídy.</span><span class="sxs-lookup"><span data-stu-id="bea18-112">The custom activity designer is built for the `SimpleNativeActivity` class.</span></span>  
  
-   <span data-ttu-id="bea18-113">Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span><span class="sxs-lookup"><span data-stu-id="bea18-113">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter>.</span></span>  
  
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
  
 <span data-ttu-id="bea18-114">Všimněte si použití datové vazby WPF k vytvoření vazby `ModelItem.Body`.</span><span class="sxs-lookup"><span data-stu-id="bea18-114">Note the use of WPF data binding to bind to `ModelItem.Body`.</span></span> <span data-ttu-id="bea18-115">`ModelItem`je vlastnost na <xref:System.Activities.Presentation.ActivityDesigner> který odkazuje na základní objekt návrháře se používá, v takovém případě **SimpleNativeActivity**.</span><span class="sxs-lookup"><span data-stu-id="bea18-115">`ModelItem` is the property on <xref:System.Activities.Presentation.ActivityDesigner> that refers to the underlying object the designer is being used for, in this case, **SimpleNativeActivity**.</span></span>  
  
#### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="bea18-116">Instalační program, sestavení a spuštění vzorku</span><span class="sxs-lookup"><span data-stu-id="bea18-116">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="bea18-117">Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bea18-117">Open the solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="bea18-118">Stisknutím klávesy F5 zkompilování a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="bea18-118">Press F5 to compile and run the application.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bea18-119">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="bea18-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bea18-120">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="bea18-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bea18-121">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="bea18-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bea18-122">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="bea18-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a><span data-ttu-id="bea18-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="bea18-123">See Also</span></span>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [<span data-ttu-id="bea18-124">Vývoj aplikací pomocí návrháře pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="bea18-124">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
