---
title: Návrháři vlastního skládání – místo pro položky pracovních postupů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: d9da37d2fb9797c9074765326df1e6eca2469607
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622473"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Návrháři vlastního skládání – místo pro položky pracovních postupů
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Je typ klíče v WF návrháře programovací model, který umožňuje úpravy kolekci elementů obsažených. Tato ukázka předvádí, jak vytvářet návrháře aktivit, který poskytuje informace o upravitelné kolekce.

 V této ukázce:

- Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.

- Vytváření návrháře aktivit se zobrazením "sbalené" a "Rozšířená".

- Přepsání výchozího návrháře v provádění se změněným hostováním aplikací.

### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku

1. Otevřít **UsingWorkflowItemsPresenter.sln** ukázkové řešení pro jazyk C# nebo vb v sadě Visual Studio 2010.

2. Sestavte a spusťte řešení. By měla otevřít návrháře aplikaci provádění se změněným hostováním pracovního postupu a můžete přetáhnout aktivity na plátno.

## <a name="sample-highlights"></a>Stručný přehled ukázky
 Kód pro tento příklad ukazuje následující:

- Návrhář aktivity je sestaven pro:  `Parallel`

- Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Pár věcí, které upozorňují na:

    - Všimněte si použití datové vazby WPF vytvořit vazbu na `ModelItem.Branches`. `ModelItem` je vlastnost na `WorkflowElementDesigner` , který odkazuje na základní objekt návrháře se používá, v tomto případě naší `Parallel`.

    - <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Je možné do vizuálu zobrazit mezi jednotlivých položek v kolekci.

    - <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> je šablonu, která je možné poskytnout určit rozložení položek v kolekci. V takovém případě se používá panel vodorovné zásobníku.

 Tento následující příklad kódu ukazuje to.

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

- Provedení sdružení `DesignerAttribute` k `Parallel` typu a potom výstup hlášené atributy.

    - Nejprve zaregistrujte všechny výchozí návrháře.

 Tady je příklad kódu.

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

    - Potom přepsat paralelní v `RegisterCustomMetadata` metody.

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

- A konečně, Všimněte si použití odlišné datové šablony a aktivační události vyberte příslušnou šablonu na základě `IsRootDesigner` vlastnost.

 Tady je příklad kódu.

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
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
