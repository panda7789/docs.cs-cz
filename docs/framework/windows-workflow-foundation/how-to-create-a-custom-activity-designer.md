---
title: 'Postupy: Vytvoření vlastního návrháře aktivity'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 3c326508744f2aa2b34f5ee574cc9ec1e2863cf6
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306345"
---
# <a name="how-to-create-a-custom-activity-designer"></a>Postupy: Vytvoření vlastního návrháře aktivity

Obvykle se implementují vlastní návrháři aktivit, aby se jejich přidružené aktivity mohly vytvářet s ostatními aktivitami, jejichž návrháři se můžou na návrhovou plochu na návrhové ploše vyřadit. Tato funkce vyžaduje, aby vlastní Návrhář aktivity poskytoval "ukládací zónu", kde lze umístit libovolnou aktivitu, a také způsob, jak spravovat výslednou kolekci prvků na návrhové ploše. Toto téma popisuje, jak vytvořit vlastního návrháře aktivit, který obsahuje takovou odkládací zónu a jak vytvořit vlastního návrháře aktivit, který poskytuje funkce pro úpravy potřebné ke správě kolekce prvků návrháře.

Vlastní návrháři aktivit obvykle dědí z <xref:System.Activities.Presentation.ActivityDesigner> výchozího typu návrháře základní aktivity pro všechny aktivity bez konkrétního návrháře. Tento typ poskytuje uživatelské prostředí pro interakci s mřížkou vlastností a konfiguraci základních aspektů, jako je například Správa barev a ikon.

<xref:System.Activities.Presentation.ActivityDesigner>používá dva ovládací prvky <xref:System.Activities.Presentation.WorkflowItemPresenter> pro pomoc a <xref:System.Activities.Presentation.WorkflowItemsPresenter> usnadňuje vývoj vlastních návrhářů aktivit. Zpracovávají společné funkce, jako je přetahování a odstraňování podřízených prvků, odstranění, výběru a přidání těchto podřízených prvků. Umožňuje jeden podřízený prvek uživatelského rozhraní uvnitř a poskytuje "ukládací zónu", <xref:System.Activities.Presentation.WorkflowItemsPresenter> zatímco může poskytovat podporu více prvků uživatelského rozhraní, včetně dalších funkcí, jako je řazení, přesunutí, odstranění a přidání podřízených prvků. <xref:System.Activities.Presentation.WorkflowItemPresenter>

Druhá klíčová část scénáře, která vyžaduje zvýraznění v implementaci vlastního návrháře aktivit, se týká způsobu, jakým jsou úpravy vizuálů svázány pomocí datové vazby WPF s instancí uloženou v paměti, kterou upravujeme v návrháři. Toho je dosaženo stromem položky modelu, který je také zodpovědný za povolení oznámení o změně a sledování událostí, jako jsou změny v stavech.

Toto téma popisuje dva postupy.

1. První postup popisuje <xref:System.Activities.Presentation.WorkflowItemPresenter> , jak vytvořit vlastního návrháře aktivit s, který poskytuje ukládací zónu, která přijímá další aktivity. Tento postup je založený na ukázce [vlastního složeného návrháře – ukázka předvádějící položky pracovního postupu](./samples/custom-composite-designers-workflow-item-presenter.md) .

2. Druhý postup popisuje <xref:System.Activities.Presentation.WorkflowItemsPresenter> , jak vytvořit vlastního návrháře aktivit s nástrojem, který poskytuje funkce potřebné pro úpravu kolekce obsažených prvků. Tento postup je založený na ukázce [vlastního složeného návrháře – pracovní postup položky pracovního postupu](./samples/custom-composite-designers-workflow-items-presenter.md) .

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a>Vytvoření vlastního návrháře aktivit pomocí přetažení zóny pomocí WorkflowItemPresenter

1. Spusťte Visual Studio 2010.

2. V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt...** .

     **Nový projekt** zobrazí se dialogové okno.

3. V podokně **Nainstalované šablony** vyberte možnost **Windows** z kategorie preferovaný jazyk.

4. V podokně **šablony** vyberte možnost **aplikace WPF**.

5. Do pole **název** zadejte `UsingWorkflowItemPresenter`.

6. Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.

7. V poli **řešení** přijměte výchozí hodnotu.

8. Klikněte na **OK**.

9. V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *MainWindows. XAML* , vyberte **Odstranit** a potvrďte **OK** v dialogovém okně **Microsoft Visual Studio** .

10. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter, vyberte **Přidat**a **Nová položka...** Chcete-li vyvolat dialogové okno **Přidat novou položku** a vybrat kategorii **WPF** v části **Nainstalované šablony** na levé straně.

11. Vyberte šablonu **okna (WPF)** , pojmenujte `RehostingWFDesigner`ji a klikněte na tlačítko **Přidat**.

12. Otevřete soubor *RehostingWFDesigner. XAML* a vložte do něj následující kód, který definuje uživatelské rozhraní aplikace:

    ```xaml
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

13. Chcete-li přidružit návrháře aktivit k typu aktivity, musíte tohoto návrháře aktivit zaregistrovat s úložištěm metadat. Chcete-li to provést, `RegisterMetadata` přidejte metodu `RehostingWFDesigner` do třídy. V rámci rozsahu `RegisterMetadata` metody <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> vytvořte objekt a zavolejte <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodu pro přidání atributů. Voláním <xref:System.Activities.Presentation.Metadata.AttributeTable> metody přidejte do úložiště metadat. <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> Následující kód obsahuje logiku opětovného hostování pro návrháře. Registruje metadata, vloží `SimpleNativeActivity` do sady nástrojů a vytvoří pracovní postup. Vložte tento kód do souboru *RehostingWFDesigner.XAML.cs* .

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
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. Klikněte pravým tlačítkem na adresář odkazy v Průzkumník řešení a vyberte **Přidat odkaz...** Otevřete dialogové okno **Přidat odkaz** .

15. Klikněte na kartu **.NET** , vyhledejte sestavení s názvem **System. Activities. Core. Presentation**, vyberte ho a klikněte na tlačítko **OK**.

16. Pomocí stejného postupu přidejte odkazy na následující sestavení:

    1. System.Data.DataSetExtensions.dll

    2. System.Activities.Presentation.dll

    3. System.ServiceModel.Activities.dll

17. Otevřete soubor *App. XAML* a změňte hodnotu StartUpUri na RehostingWFDesigner. XAML.

18. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter, vyberte **Přidat**a **Nová položka...** Chcete-li vyvolat dialogové okno **Přidat novou položku** a vybrat kategorii **pracovního postupu** , otevřete část **Nainstalované šablony** na levé straně.

19. Vyberte šablonu **návrháře aktivit** , pojmenujte `SimpleNativeDesigner`ji a klikněte na **Přidat**.

20. Otevřete soubor *SimpleNativeDesigner. XAML* a vložte do něj následující kód. Všimněte si, že <xref:System.Activities.Presentation.ActivityDesigner> tento kód používá jako kořenový element a ukazuje, jak se vazba <xref:System.Activities.Presentation.WorkflowItemPresenter> používá pro integraci do návrháře, takže podřízený typ lze zobrazit v návrháři složených aktivit.

    > [!NOTE]
    > Schéma pro <xref:System.Activities.Presentation.ActivityDesigner> umožňuje přidání pouze jednoho podřízeného prvku do vaší definice návrháře vlastní aktivity; tento element však může `StackPanel`být, `Grid`nebo nějaký jiný složený prvek uživatelského rozhraní.

    ```xaml
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

21. V **Průzkumník řešení**klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter, vyberte **Přidat**a **Nová položka...** Chcete-li vyvolat dialogové okno **Přidat novou položku** a vybrat kategorii **pracovního postupu** , otevřete část **Nainstalované šablony** na levé straně.

22. Vyberte šablonu **aktivita kódu** , pojmenujte `SimpleNativeActivity`ji a klikněte na **Přidat**.

23. Implementujte třídu zadáním následujícího kódu do souboru *SimpleNativeActivity.cs:* `SimpleNativeActivity`

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

24. V nabídce **sestavení** vyberte **sestavení řešení** .

25. Vyberte možnost **Spustit bez ladění** z nabídky **ladění** a otevřete tak opětovné hostování vlastního návrhového okna.

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a>Vytvoření vlastního návrháře aktivit pomocí WorkflowItemsPresenter

1. Postup pro druhý Návrhář vlastní aktivity je souběžně první s několika úpravami, první z nich je pojmenovat druhou aplikaci `UsingWorkflowItemsPresenter`. Tato aplikace také nedefinuje novou vlastní aktivitu.

2. Klíčové rozdíly jsou obsaženy v souborech *CustomParallelDesigner. XAML* a *RehostingWFDesigner.XAML.cs* . Zde je kód ze souboru *CustomParallelDesigner. XAML* , který definuje uživatelské rozhraní:

    ```xaml
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

3. Zde je kód ze souboru *RehostingWFDesigner.XAML.cs* , který poskytuje logiku opětovného hostování:

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
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
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
