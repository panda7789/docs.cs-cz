---
title: Návrháři vlastního skládání – místo pro položku pracovního postupu
ms.date: 03/30/2017
ms.assetid: f85224cf-9e30-44a5-9a81-3bc438a34364
ms.openlocfilehash: 239f7ccd81d5bb60eed32298220df215b09e3e47
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038375"
---
# <a name="custom-composite-designers---workflow-item-presenter"></a>Návrháři vlastního skládání – místo pro položku pracovního postupu
<xref:System.Activities.Presentation.WorkflowItemPresenter> Je typ klíče v programovacím modelu Návrháře WF, který umožňuje vytvoření "ukládací zóny", kde lze umístit libovolnou aktivitu. V této ukázce se dozvíte, jak vytvořit Návrhář aktivity, který je povrchem "ukládací zóny".

 Tato ukázka demonstruje:

## <a name="demonstrates"></a>Demonstruje

- Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemPresenter>.

- Vlastní Návrhář se registruje pomocí úložiště metadat.

- Deklarativní a imperativní programování znovu hostující sady nástrojů.

## <a name="sample-details"></a>Podrobnosti ukázky
 Kód pro tuto ukázku ukazuje:

- Návrhář vlastní aktivity je sestaven pro `SimpleNativeActivity` třídu.

- Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemPresenter>.

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

 Všimněte si použití datové vazby WPF k vytvoření vazby na `ModelItem.Body`. `ModelItem`je vlastnost <xref:System.Activities.Presentation.ActivityDesigner> , která odkazuje na podkladový objekt, pro který je Návrhář používán, v tomto případě **SimpleNativeActivity**.

#### <a name="to-setup-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete řešení v aplikaci Visual Studio 2010.

2. Pro zkompilování a spuštění aplikace stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemPresenter`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
