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
# <a name="custom-composite-designers---workflow-item-presenter"></a>Vlastní složený Designer - přednášejícího položky pracovního postupu
<xref:System.Activities.Presentation.WorkflowItemPresenter> Je typ klíče v WF návrháře programovací model, který umožňuje vytváření "rozevírací zónu" umístění libovolné aktivity. Tento příklad ukazuje, jak stavět Návrhář aktivity tohoto povrchy takovou "rozevírací zónu."  
  
 Tento příklad znázorňuje:  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Vytváření Návrháře vlastních aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter>.  
  
-   Probíhá registrace návrháře vlastní pomocí úložiště metadat.  
  
-   Programování opětovné hostování nástroje sady nástrojů deklarativně a imperativní.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Kód pro tento příklad ukazuje:  
  
-   Návrhář vlastní aktivity je vytvořené pro `SimpleNativeActivity` třídy.  
  
-   Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter>.  
  
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
  
 Všimněte si použití datové vazby WPF k vytvoření vazby `ModelItem.Body`. `ModelItem`je vlastnost na <xref:System.Activities.Presentation.ActivityDesigner> který odkazuje na základní objekt návrháře se používá, v takovém případě **SimpleNativeActivity**.  
  
#### <a name="to-setup-build-and-run-the-sample"></a>Instalační program, sestavení a spuštění vzorku  
  
1.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Stisknutím klávesy F5 zkompilování a spuštění aplikace.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 [Vývoj aplikací pomocí návrháře pracovních postupů](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
