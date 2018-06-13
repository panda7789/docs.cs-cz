---
title: 'Postupy: vytvoření vlastního návrháře aktivit'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: e4aab60a598be2d6df5546ab1c98a289b4aef04a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520341"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Postupy: vytvoření vlastního návrháře aktivit
Návrháři vlastních aktivit jsou obvykle implementovány tak, aby jejich aktivity související s ostatními aktivitami, jejichž Designer může být přetažen na návrhovou plochu, která s nimi bez možnosti složení. Tato funkce vyžaduje, aby zadali Návrhář vlastní aktivity "rozevírací zónu" umístění libovolné aktivity a také způsob, jak spravovat výsledné kolekci elementů na návrhovou plochu. Toto téma popisuje, jak vytvořit vlastní aktivity návrháře obsahující rozevírací zóny a jak vytvořit Návrhář vlastní aktivity, který zajišťuje, že úpravy funkce potřebné ke správě kolekci elementů návrháře.  
  
 Návrháři vlastních aktivit obvykle dědí <xref:System.Activities.Presentation.ActivityDesigner> což je výchozí základní aktivitě návrháře typ pro všechny aktivity bez konkrétní návrháře. Tento typ poskytuje prostředí návrhu interakci s mřížku vlastností a konfigurace základní aspekty například správu barvy a ikony.  
  
 <xref:System.Activities.Presentation.ActivityDesigner> pomocí dvou ovládacích prvků pomocné rutiny, <xref:System.Activities.Presentation.WorkflowItemPresenter> a <xref:System.Activities.Presentation.WorkflowItemsPresenter> aby bylo snazší vývoj Návrháře vlastních aktivit. Běžné funkce jako přetahování podřízené elementy, odstranění, výběru a přidání těchto podřízených elementů, které zpracovávají. <xref:System.Activities.Presentation.WorkflowItemPresenter> Umožňuje jeden podřízený element uživatelského rozhraní uvnitř, zajištění "rozevírací zóně", je při <xref:System.Activities.Presentation.WorkflowItemsPresenter> může poskytnout podporu více prvky uživatelského rozhraní, včetně další funkce, jako je řazení, přesunutí, odstranění a přidání podřízených elementů.  
  
 Další část klíče scénáře, který potřebuje zvýraznění implementace Návrhář vlastní aktivity se týká způsob, ve kterém jsou visual úpravy svázán pomocí [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] datové vazby k instanci uložené v paměti co jsme jsou úpravy v návrháři. To lze provést stromu položku modelu, který zodpovídá taky pro povolení oznámení o změně a sledování událostí jako změny ve stavu.  
  
 Toto téma popisuje dva postupy.  
  
1.  První postup popisuje, jak vytvořit vlastní aktivity designer s <xref:System.Activities.Presentation.WorkflowItemPresenter> rozevírací zóny, která obdrží ostatní aktivity, která poskytuje. Tento postup je založen na [vlastní složený Designer - přednášejícího položky pracovního postupu](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-item-presenter.md) ukázka.  
  
2.  Druhý postup popisuje, jak vytvořit vlastní aktivity designer s <xref:System.Activities.Presentation.WorkflowItemsPresenter> poskytující funkce potřebná pro úpravu kolekce elementech, které obsahují. Tento postup je založen na [vlastní složený Designer - přednášejícího položky pracovního postupu](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-designers-workflow-items-presenter.md) ukázka.  
  
### <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Vytvoření vlastního návrháře aktivit s rozevírací zóny pomocí WorkflowItemPresenter  
  
1.  Spustit [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Na **soubor** nabídky, přejděte na příkaz **nový**a potom vyberte **projektu...** .  
  
     **Nový projekt** otevře se dialogové okno.  
  
3.  V **nainstalovaných šablonách** podokně, vyberte **Windows** z vaší upřednostňovaný jazyk kategorie.  
  
4.  V **šablony** podokně, vyberte **aplikaci WPF**.  
  
5.  V **název** zadejte `UsingWorkflowItemPresenter`.  
  
6.  V **umístění** zadejte adresář, ve kterém chcete uložit projektu, nebo klikněte na tlačítko **Procházet** přejděte k němu.  
  
7.  V **řešení** pole, přijměte výchozí hodnotu.  
  
8.  Click **OK**.  
  
9. Klikněte pravým tlačítkem na soubor MainWindows.xaml v **Průzkumníku řešení**, vyberte **odstranit** a potvrďte **OK** v **Microsoft Visual Studio**dialogové okno.  
  
10. Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter **Průzkumníku řešení**, vyberte **přidat**, pak **novou položku...** se zprovoznit **přidat novou položku** dialogový a vyberte **WPF** kategorie z **nainstalovaných šablonách** na levé straně.  
  
11. Vyberte **okno (WPF)** šablony, pojmenujte ji `RehostingWFDesigner`a klikněte na tlačítko **přidat**.  
  
12. Otevřete soubor RehostingWFDesigner.xaml a vložte následující kód do ní k zadání uživatelského rozhraní pro aplikaci.  
  
    ```xml  
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
            xmlns:sys="clr-namespace:System;assembly=mscorlib"  
            Title="Window1" Height="600" Width="900">  
        <Window.Resources>  
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
        </Window.Resources>  
        <Grid>  
            <Grid.ColumnDefinitions>  
                <ColumnDefinition Width="2*"/>  
                <ColumnDefinition Width="7*"/>  
                <ColumnDefinition Width="3*"/>  
            </Grid.ColumnDefinitions>  
            <Border Grid.Column="0">  
                <sapt:ToolboxControl Name="Toolbox">  
                    <sapt:ToolboxCategory CategoryName="Basic">  
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.Sequence  
                            </sapt:ToolboxItemWrapper.ToolName>  
                           </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.WriteLine  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.If  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                            <sapt:ToolboxItemWrapper.ToolName>  
                                System.Activities.Statements.While  
                            </sapt:ToolboxItemWrapper.ToolName>  
  
                        </sapt:ToolboxItemWrapper>  
                    </sapt:ToolboxCategory>  
                </sapt:ToolboxControl>  
            </Border>  
            <Border Grid.Column="1" Name="DesignerBorder"/>  
            <Border Grid.Column="2" Name="PropertyBorder"/>  
        </Grid>  
    </Window>  
    ```  
  
13. Pokud chcete přidružit Návrhář aktivity typu aktivity, je nutné zaregistrovat tento Návrhář aktivity s úložištěm metadat. Chcete-li to provést, přidejte `RegisterMetadata` metodu `RehostingWFDesigner` – třída. V rámci oboru `RegisterMetadata` metody vytvoření <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> objekt a volání <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metoda pro přidání atributů do ní. Volání <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> metody přidat <xref:System.Activities.Presentation.Metadata.AttributeTable> k úložišti metadat. Následující kód obsahuje rehosting logiku pro návrháře. Ho zaregistruje metadata, umístí `SimpleNativeActivity` do sady nástrojů a vytvoří pracovní postup. Tento kód vložte do souboru RehostingWFDesigner.xaml.cs.  
  
    ```  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Presentation.Toolbox;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        // Interaction logic for RehostingWFDesigner.xaml  
        public partial class RehostingWFDesigner  
        {  
            public RehostingWFDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
                // add custom activity to toolbox  
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));  
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
14. V adresáři odkazy v Průzkumníku řešení klikněte pravým tlačítkem a vyberte **přidat odkaz na...** Chcete-li zprovoznit **přidat odkaz na** dialogu.  
  
15. Klikněte **.NET** najděte sestavení s názvem **System.Activities.Core.Presentation**, vyberte ho a klikněte na tlačítko **OK**.  
  
16. Pomocí stejného postupu, přidejte odkazy na následující:  
  
    1.  System.Data.DataSetExtensions.dll  
  
    2.  System.Activities.Presentation.dll  
  
    3.  System.ServiceModel.Activities.dll  
  
17. Otevřete soubor App.xaml a změňte hodnotu StartUpUri na "RehostingWFDesigner.xaml".  
  
18. Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter **Průzkumníku řešení**, vyberte **přidat**, pak **novou položku...** se zprovoznit **přidat novou položku** dialogový a vyberte **pracovního postupu** kategorie formuláře **nainstalovaných šablonách** na levé straně.  
  
19. Vyberte **Návrhář aktivity** šablony, pojmenujte ji `SimpleNativeDesigner`a klikněte na tlačítko **přidat**.  
  
20. Otevřete soubor SimpleNativeDesigner.xaml a vložte následující kód do ní. Poznámka: Tento kód používá <xref:System.Activities.Presentation.ActivityDesigner> jako kořenový element a ukazuje, jak vazby slouží k integraci <xref:System.Activities.Presentation.WorkflowItemPresenter> do vašeho návrháře tak podřízený typ zobrazený ve vaší Návrhář složené aktivity.  
  
    > [!NOTE]
    >  Schéma pro <xref:System.Activities.Presentation.ActivityDesigner> lze přidat pouze jeden podřízený element pro návrháře definici vlastní aktivity; však může být tento prvek `StackPanel`, `Grid`, nebo některých jiných složený prvek uživatelského rozhraní.  
  
    ```xml  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"  
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
  
21. Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter **Průzkumníku řešení**, vyberte **přidat**, pak **novou položku...** se zprovoznit **přidat novou položku** dialogový a vyberte **pracovního postupu** kategorie formuláře **nainstalovaných šablonách** na levé straně.  
  
22. Vyberte **kód aktivity** šablony, pojmenujte ji `SimpleNativeActivity`a klikněte na tlačítko **přidat**.  
  
23. Implementace `SimpleNativeActivity` třídy tak, že zadáte následující kód do souboru SimpleNativeActivity.cs.  
  
    ```  
    using System.Activities;  
  
    namespace UsingWorkflowItemPresenter  
    {  
        public sealed class SimpleNativeActivity : NativeActivity  
        {  
            // this property contains an activity that will be scheduled in the execute method  
    // the WorkflowItemPresenter in the designer is bound to this to enable editing  
    // of the value  
            public Activity Body { get; set; }  
  
            protected override void CacheMetadata(NativeActivityMetadata metadata)  
            {  
               metadata.AddChild(Body);  
               base.CacheMetadata(metadata);  
  
            }  
  
            protected override void Execute(NativeActivityContext context)  
            {  
                context.ScheduleActivity(Body);  
            }  
        }  
    }  
    ```  
  
24. Vyberte **sestavit řešení** z **sestavení** nabídky.  
  
25. Vyberte **spustit bez ladění** z **ladění** chcete otevřít okno opětovné hostování nástroje vlastní návrh v nabídce.  
  
### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Chcete-li vytvořit vlastní aktivity návrháře pomocí WorkflowItemsPresenter  
  
1.  Postup pro druhý Návrhář vlastní aktivity se parallels první s několik změn, z nichž první je název aplikace druhý `UsingWorkflowItemsPresenter`. Tato aplikace také nedefinuje nové vlastní aktivity.  
  
2.  Hlavní rozdíly jsou obsažené v souborech CustomParallelDesigner.xaml a RehostingWFDesigner.xaml.cs. Tady je kód od CustomParallelDesigne.xaml souboru, který definuje uživatelské rozhraní.  
  
    ```xml  
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"  
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">  
        <sap:ActivityDesigner.Resources>  
            <DataTemplate x:Key="Collapsed">  
                <TextBlock>This is the Collapsed View</TextBlock>  
            </DataTemplate>  
            <DataTemplate x:Key="Expanded">  
                <StackPanel>  
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>  
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>  
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"  
                                        Items="{Binding Path=ModelItem.Branches}">  
                        <sap:WorkflowItemsPresenter.SpacerTemplate>  
                            <DataTemplate>  
                                <Ellipse Width="10" Height="10" Fill="Black"/>  
                            </DataTemplate>  
                        </sap:WorkflowItemsPresenter.SpacerTemplate>  
                        <sap:WorkflowItemsPresenter.ItemsPanel>  
                            <ItemsPanelTemplate>  
                                <StackPanel Orientation="Horizontal"/>  
                            </ItemsPanelTemplate>  
                        </sap:WorkflowItemsPresenter.ItemsPanel>  
                    </sap:WorkflowItemsPresenter>  
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
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>  
        </Grid>  
    </sap:ActivityDesigner>  
    ```  
  
3.  Tady je kód od RehostingWFDesigner.xaml.cs souboru, který poskytuje rehosting logiku.  
  
    ```  
    using System;  
    using System.Activities.Core.Presentation;  
    using System.Activities.Presentation;  
    using System.Activities.Presentation.Metadata;  
    using System.Activities.Statements;  
    using System.ComponentModel;  
    using System.Windows;  
  
    namespaceUsingWorkflowItemsPresenter  
    {  
        public partial class RehostingWfDesigner : Window  
        {  
            public RehostingWfDesigner()  
            {  
                InitializeComponent();  
            }  
  
            protected override void OnInitialized(EventArgs e)  
            {  
                base.OnInitialized(e);  
                // register metadata  
                (new DesignerMetadata()).Register();  
                RegisterCustomMetadata();  
  
                // create the workflow designer  
                WorkflowDesigner wd = new WorkflowDesigner();  
                wd.Load(new Sequence());  
                DesignerBorder.Child = wd.View;  
                PropertyBorder.Child = wd.PropertyInspectorView;  
  
            }  
  
            void RegisterCustomMetadata()  
            {  
                AttributeTableBuilder builder = new AttributeTableBuilder();  
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));  
                MetadataStore.AddAttributeTable(builder.CreateTable());  
            }  
        }  
    }  
    ```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Activities.Presentation.ActivityDesigner>  
 <xref:System.Activities.Presentation.WorkflowItemPresenter>  
 <xref:System.Activities.Presentation.WorkflowItemsPresenter>  
 <xref:System.Activities.Presentation.WorkflowViewElement>  
 <xref:System.Activities.Presentation.Model.ModelItem>  
 [Přizpůsobení prostředí pro návrh pracovního postupu](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)
