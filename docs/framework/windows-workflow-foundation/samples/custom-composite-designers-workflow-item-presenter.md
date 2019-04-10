---
title: Návrháři vlastního skládání – místo pro položku pracovního postupu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: f3c7620f719b8412b6b34bda7be5d607dccda75f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311120"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Návrháři vlastního skládání – místo pro položku pracovního postupu
<xref:System.Activities.Presentation.WorkflowItemPresenter> Je typ klíče v WF návrháře programovací model, který umožňuje vytváření "rozevírací zónu" umístění libovolné aktivity. Tento příklad ukazuje, jak vytvářet Návrhář aktivity tohoto zařízení Surface takovou "rozevírací zónu."

 V této ukázce:

## <a name="demonstrates"></a>Demonstruje

-   Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter>.

-   Registrace vlastní úložiště metadat pomocí návrháře.

-   Deklarativní a imperativně programování provádění se změněným hostováním sady nástrojů.

## <a name="sample-details"></a>Ukázka podrobnosti
 Kód pro tento příklad ukazuje:

-   Návrháři vlastních aktivit je sestaven pro `SimpleNativeActivity` třídy.

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

 Všimněte si použití datové vazby WPF vytvořit vazbu na `ModelItem.Body`. `ModelItem` je vlastnost na <xref:System.Activities.Presentation.ActivityDesigner> , který odkazuje na základní objekt návrháře se používá, v tomto případě **SimpleNativeActivity**.

#### <a name="to-setup-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete řešení v sadě Visual Studio 2010.

2. Stiskněte klávesu F5 ke kompilaci a spuštění aplikace.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
