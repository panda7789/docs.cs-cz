---
title: "Vlastní složený Designer - přednášejícího položky pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b708d39ba6e5f53579f575d5e228de43db3d90a9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="custom-composite-designers---workflow-items-presenter"></a>Vlastní složený Designer - přednášejícího položky pracovního postupu
<xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> Je typ klíče v WF návrháře programovací model, který umožňuje úpravu kolekci elementů obsažené. Tento příklad ukazuje, jak sestavit Návrhář aktivity, která vyvolá upravitelné kolekce.  
  
 Tento příklad znázorňuje:  
  
-   Vytváření Návrháře vlastních aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.  
  
-   Vytvoření Návrhář aktivity se zobrazením "sbalené" a "Rozšířená".  
  
-   Přepíše výchozí Návrhář v opětovné hostování nástroje aplikace.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Otevřete **UsingWorkflowItemsPresenter.sln** ukázkové řešení pro jazyk C# nebo VB v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavení a spuštění řešení. Opětovné hostování nástroje pracovního postupu návrháře aplikace by měla otevřít a aktivity můžete přetáhněte na plátno.  
  
## <a name="sample-highlights"></a>Ukázka označuje  
 Kód pro tato ukázka obsahuje následující informace:  
  
-   Návrhář aktivity je vytvořené pro:`Parallel`  
  
-   Vytvoření vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>. Pár věcí tak, aby odkazoval:  
  
    -   Všimněte si použití datové vazby WPF k vytvoření vazby `ModelItem.Branches`. `ModelItem`je vlastnost na `WorkflowElementDesigner` který odkazuje na základní objekt návrháře se používá, v takovém případě naší `Parallel`.  
  
    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> Lze uvést visual zobrazíte mezi jednotlivé položky v kolekci.  
  
    -   <xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType>je šablonu, která může být k dispozici pro určení rozložení položek v kolekci. V takovém případě se používá panel vodorovné zásobníku.  
  
 Tato následující příklad kódu ukazuje to.  
  
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
  
-   Provést přidružením `DesignerAttribute` k `Parallel` typu a potom výstup hlášené atributy.  
  
    -   Nejprve zaregistrujte všechny výchozí Designer.  
  
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
  
    -   Potom přepsat paralelní v `RegisterCustomMetadata` metoda.  
  
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
  
-   Nakonec, Všimněte si použití různé šablony dat a aktivační události a vyberte příslušnou šablonu na základě `IsRootDesigner` vlastnost.  
  
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
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
