---
title: 'Postupy: Vytvoření vlastního návrháře aktivity'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: e455d00ebd128c37eacb19df0e7f864505df04e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945649"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Postupy: Vytvoření vlastního návrháře aktivity

Vlastní návrháři aktivit jsou obvykle implementovány tak, aby jejich související aktivity sestavitelný s ostatními aktivitami, jehož návrháři dá přetáhnout do návrhové plochy s nimi. Tato funkce vyžaduje, aby poskytovaly vlastního návrháře aktivit "rozevírací zónu" umístění libovolné aktivity a také způsob, jak spravovat výsledný kolekci prvků na návrhové ploše. Toto téma popisuje, jak vytvořit vlastního návrháře aktivit, která obsahuje rozevírací zóny a jak vytvořit vlastního návrháře aktivit, které zajišťuje, že editačních funkcích museli spravovat kolekci elementů návrháře.

Vlastní návrháři aktivit obvykle dědí <xref:System.Activities.Presentation.ActivityDesigner> což je výchozí návrháře typ základní aktivity pro všechny aktivity bez konkrétního návrháře. Tento typ poskytuje možnosti času návrhu interakci s mřížkou a konfigurace základní aspekty, jako je například Správa barvy a ikony.

<xref:System.Activities.Presentation.ActivityDesigner> pomocí dvou ovládacích prvků pomocné rutiny, <xref:System.Activities.Presentation.WorkflowItemPresenter> a <xref:System.Activities.Presentation.WorkflowItemsPresenter> zjednodušit vývoj vlastní návrháři aktivit. Společné funkce, jako jsou přetahování podřízených prvků, odstranění, výběru a přidání těchto podřízených elementů, které zpracovávají. <xref:System.Activities.Presentation.WorkflowItemPresenter> Umožňuje jeden podřízený prvek uživatelského rozhraní uvnitř, poskytuje "rozevírací věci", je při <xref:System.Activities.Presentation.WorkflowItemsPresenter> může poskytovat podporu více prvků uživatelského rozhraní, včetně další funkce, jako jsou řazení, přesouvání, odstraňování a přidávání podřízených elementů.

Další klíčovou součástí scénáře, který potřebuje zvýraznění v implementaci vlastního návrháře aktivit se týká způsobu, ve kterém jsou úpravy visual vázané pomocí [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] datové vazby k instanci uložených v paměti co jsme se v návrháři pro úpravy. Toho lze dosáhnout stromu položku modelu, který zodpovídá také pro povolení oznámení o změně a sledování události, jako jsou změny ve stavu.

Toto téma popisuje dva postupy.

1. První postup popisuje, jak vytvořit vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter> , která poskytuje oblast přetažení, která přijímá další aktivity. Tento postup je založen na [vlastní návrháři - skládání položky pracovního postupu](./samples/custom-composite-designers-workflow-item-presenter.md) vzorku.

2. Druhý postup popisuje, jak vytvořit vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter> , která poskytuje funkce pro potřebný pro úpravu z kolekce jeho prvky. Tento postup je založen na [vlastní návrháři - skládání položky pracovního postupu](./samples/custom-composite-designers-workflow-items-presenter.md) vzorku.

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Vytvoření vlastního návrháře aktivit pomocí přetažení zóny pomocí WorkflowItemPresenter

1. Start Visual Studio 2010.

2. Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu...** .

     **Nový projekt** zobrazí se dialogové okno.

3. V **nainstalované šablony** vyberte **Windows** z kategorie váš preferovaný jazyk.

4. V **šablony** vyberte **aplikace WPF**.

5. V **název** zadejte `UsingWorkflowItemPresenter`.

6. V **umístění** zadejte adresář, ve kterém chcete projekt uložit, nebo klikněte na tlačítko **Procházet** přejít k němu.

7. V **řešení** pole, přijměte výchozí hodnotu.

8. Klikněte na **OK**.

9. Klikněte pravým tlačítkem na soubor MainWindows.xaml v **Průzkumníka řešení**vyberte **odstranit** a potvrďte **OK** v **sady Microsoft Visual Studio**dialogové okno.

10. Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter v **Průzkumníka řešení**vyberte **přidat**, pak **novou položku...** Zobrazí se **přidat novou položku** dialog a vyberte **WPF** kategorie z **nainstalované šablony** části na levé straně.

11. Vyberte **okno (WPF)** šablony, pojmenujte ho `RehostingWFDesigner`a klikněte na tlačítko **přidat**.

12. Otevřete soubor RehostingWFDesigner.xaml a vložte následující kód do ní k definování uživatelského rozhraní pro aplikaci.

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

13. Pokud chcete přidružit Návrhář aktivity typu aktivity, musíte zaregistrovat tento Návrhář aktivity s úložištěm metadat. Chcete-li to provést, přidejte `RegisterMetadata` metodu `RehostingWFDesigner` třídy. V rámci oboru `RegisterMetadata` metody vytvoření <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> objektu a volání <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodu přidejte atributy do ní. Volání <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> způsob, jak přidat <xref:System.Activities.Presentation.Metadata.AttributeTable> do úložiště metadat. Následující kód obsahuje rehosting logiku pro návrháře. Zaregistruje metadata, vloží `SimpleNativeActivity` do panelu nástrojů a vytvoří pracovní postup. Vložte tento kód do souboru RehostingWFDesigner.xaml.cs.

    ```csharp
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

14. Adresáře odkazů v Průzkumníku řešení klikněte pravým tlačítkem a vyberte **přidat odkaz...** Zobrazí se **přidat odkaz** dialogu.

15. Klikněte na tlačítko **.NET** kartu, vyhledejte sestavení s názvem **System.Activities.Core.Presentation**, vyberte ho a klikněte na tlačítko **OK**.

16. Pomocí stejného postupu, přidejte odkazy na následující sestavení:

    1. System.Data.DataSetExtensions.dll

    2. System.Activities.Presentation.dll

    3. System.ServiceModel.Activities.dll

17. Otevřete soubor App.xaml a změňte hodnotu StartUpUri na "RehostingWFDesigner.xaml".

18. Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter v **Průzkumníka řešení**vyberte **přidat**, pak **novou položku...** Zobrazí se **přidat novou položku** dialog a vyberte **pracovního postupu** formulář Kategorie **nainstalované šablony** části na levé straně.

19. Vyberte **Návrhář aktivity** šablony, pojmenujte ho `SimpleNativeDesigner`a klikněte na tlačítko **přidat**.

20. Otevřete soubor SimpleNativeDesigner.xaml a vložte do něj následující kód. Poznámka: Tento kód používá <xref:System.Activities.Presentation.ActivityDesigner> jako kořenový element a ukazuje, jak vazby slouží k integraci <xref:System.Activities.Presentation.WorkflowItemPresenter> do návrháře tak podřízený typ lze zobrazit návrháře složené aktivity.

    > [!NOTE]
    > Schéma pro <xref:System.Activities.Presentation.ActivityDesigner> lze přidat pouze jeden podřízený prvek prvku do definice návrháře vlastní aktivitu, ale může být tento element `StackPanel`, `Grid`, nebo jiného elementu složeného uživatelského rozhraní.

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

21. Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter v **Průzkumníka řešení**vyberte **přidat**, pak **novou položku...** Zobrazí se **přidat novou položku** dialog a vyberte **pracovního postupu** formulář Kategorie **nainstalované šablony** části na levé straně.

22. Vyberte **aktivita s kódem** šablony, pojmenujte ho `SimpleNativeActivity`a klikněte na tlačítko **přidat**.

23. Implementace `SimpleNativeActivity` třídy tak, že zadáte následující kód do souboru SimpleNativeActivity.cs.

    ```csharp
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

25. Vyberte **spustit bez ladění** z **ladění** nabídce otevřete okno provádění se změněným hostováním vlastní návrh.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Vytvoření vlastního návrháře aktivit pomocí WorkflowItemsPresenter

1. Postup pro druhý návrháři vlastní aktivity se parallels první z nich s několik změn, z nichž první má Pojmenujte druhou aplikaci `UsingWorkflowItemsPresenter`. Tato aplikace také nedefinuje nové vlastní aktivity.

2. Hlavní rozdíly jsou obsaženy v souborech CustomParallelDesigner.xaml a RehostingWFDesigner.xaml.cs. Tady je kód z CustomParallelDesigner.xaml soubor, který definuje uživatelské rozhraní.

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

3. Tady je kód z RehostingWFDesigner.xaml.cs soubor, který poskytuje rehosting logiku.

    ```csharp
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

## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [Přizpůsobení prostředí pro návrh pracovního postupu](customizing-the-workflow-design-experience.md)
