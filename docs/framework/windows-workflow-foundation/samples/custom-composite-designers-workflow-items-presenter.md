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
# <a name="custom-composite-designers---workflow-items-presenter"></a>Návrháři vlastního skládání – místo pro položky pracovních postupů

<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> je typ klíče v programovacím modelu Návrháře WF, který umožňuje úpravu kolekce obsažených prvků. V této ukázce se dozvíte, jak vytvořit Návrhář aktivity, který je povrchem takové upravitelné kolekce.

Tato ukázka demonstruje:

- Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.

- Vytvoření návrháře aktivit se zobrazením "sbalené" a "rozšířené".

- Přepsání výchozího návrháře v znovu hostované aplikaci.

### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky

1. Otevřete ukázkové řešení **UsingWorkflowItemsPresenter. sln** pro C# nebo pro jazyk VB v aplikaci Visual Studio 2010.

2. Sestavte a spusťte řešení. Měla by se otevřít znovu hostující aplikace návrháře pracovních postupů a aktivity můžete přetáhnout na plátno.

## <a name="sample-highlights"></a>Ukázka světel

Kód pro tuto ukázku ukazuje následující:

- Aktivita, pro kterou je Návrhář sestavený: `Parallel`

- Vytvoření vlastního návrháře aktivit pomocí <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Pár věcí k ukázání:

  - Všimněte si, že použití datové vazby WPF pro vazbu na `ModelItem.Branches`. `ModelItem` je vlastnost u `WorkflowElementDesigner`, která odkazuje na podkladový objekt, pro který je Návrhář používán, v tomto případě naše `Parallel`.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> lze použít k vložení vizuálu pro zobrazení mezi jednotlivými položkami v kolekci.

  - <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> je šablona, kterou lze zadat k určení rozložení položek v kolekci. V takovém případě se použije vodorovný panel zásobníku.

  Následující příklad kódu ukazuje toto.

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

- Provede přidružení `DesignerAttribute` k typu `Parallel` a pak výstup nahlášených atributů.

  - Nejprve Zaregistrujte všechny výchozí návrháře.

    Následuje příklad kódu.

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

  - Pak přepište paralelní v metodě `RegisterCustomMetadata`.

    Následující kód ukazuje to v C# a Visual Basic.

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

- Nakonec si všimněte použití různých datových šablon a triggerů k výběru vhodné šablony na základě vlastnosti `IsRootDesigner`.

  Následuje příklad kódu.

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
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
