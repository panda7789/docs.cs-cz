---
title: 'Postupy: Vytvoření vlastního návrháře aktivit'
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: e455d00ebd128c37eacb19df0e7f864505df04e0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716826"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="6af3c-102">Postupy: Vytvoření vlastního návrháře aktivit</span><span class="sxs-lookup"><span data-stu-id="6af3c-102">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="6af3c-103">Vlastní návrháři aktivit jsou obvykle implementovány tak, aby jejich související aktivity sestavitelný s ostatními aktivitami, jehož návrháři dá přetáhnout do návrhové plochy s nimi.</span><span class="sxs-lookup"><span data-stu-id="6af3c-103">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="6af3c-104">Tato funkce vyžaduje, aby poskytovaly vlastního návrháře aktivit "rozevírací zónu" umístění libovolné aktivity a také způsob, jak spravovat výsledný kolekci prvků na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="6af3c-104">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="6af3c-105">Toto téma popisuje, jak vytvořit vlastního návrháře aktivit, která obsahuje rozevírací zóny a jak vytvořit vlastního návrháře aktivit, které zajišťuje, že editačních funkcích museli spravovat kolekci elementů návrháře.</span><span class="sxs-lookup"><span data-stu-id="6af3c-105">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="6af3c-106">Vlastní návrháři aktivit obvykle dědí <xref:System.Activities.Presentation.ActivityDesigner> což je výchozí návrháře typ základní aktivity pro všechny aktivity bez konkrétního návrháře.</span><span class="sxs-lookup"><span data-stu-id="6af3c-106">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="6af3c-107">Tento typ poskytuje možnosti času návrhu interakci s mřížkou a konfigurace základní aspekty, jako je například Správa barvy a ikony.</span><span class="sxs-lookup"><span data-stu-id="6af3c-107">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="6af3c-108"><xref:System.Activities.Presentation.ActivityDesigner> pomocí dvou ovládacích prvků pomocné rutiny, <xref:System.Activities.Presentation.WorkflowItemPresenter> a <xref:System.Activities.Presentation.WorkflowItemsPresenter> zjednodušit vývoj vlastní návrháři aktivit.</span><span class="sxs-lookup"><span data-stu-id="6af3c-108"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="6af3c-109">Společné funkce, jako jsou přetahování podřízených prvků, odstranění, výběru a přidání těchto podřízených elementů, které zpracovávají.</span><span class="sxs-lookup"><span data-stu-id="6af3c-109">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="6af3c-110"><xref:System.Activities.Presentation.WorkflowItemPresenter> Umožňuje jeden podřízený prvek uživatelského rozhraní uvnitř, poskytuje "rozevírací věci", je při <xref:System.Activities.Presentation.WorkflowItemsPresenter> může poskytovat podporu více prvků uživatelského rozhraní, včetně další funkce, jako jsou řazení, přesouvání, odstraňování a přidávání podřízených elementů.</span><span class="sxs-lookup"><span data-stu-id="6af3c-110">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="6af3c-111">Další klíčovou součástí scénáře, který potřebuje zvýraznění v implementaci vlastního návrháře aktivit se týká způsobu, ve kterém jsou úpravy visual vázané pomocí [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] datové vazby k instanci uložených v paměti co jsme se v návrháři pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="6af3c-111">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="6af3c-112">Toho lze dosáhnout stromu položku modelu, který zodpovídá také pro povolení oznámení o změně a sledování události, jako jsou změny ve stavu.</span><span class="sxs-lookup"><span data-stu-id="6af3c-112">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="6af3c-113">Toto téma popisuje dva postupy.</span><span class="sxs-lookup"><span data-stu-id="6af3c-113">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="6af3c-114">První postup popisuje, jak vytvořit vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter> , která poskytuje oblast přetažení, která přijímá další aktivity.</span><span class="sxs-lookup"><span data-stu-id="6af3c-114">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="6af3c-115">Tento postup je založen na [vlastní návrháři - skládání položky pracovního postupu](./samples/custom-composite-designers-workflow-item-presenter.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="6af3c-115">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="6af3c-116">Druhý postup popisuje, jak vytvořit vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemsPresenter> , která poskytuje funkce pro potřebný pro úpravu z kolekce jeho prvky.</span><span class="sxs-lookup"><span data-stu-id="6af3c-116">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="6af3c-117">Tento postup je založen na [vlastní návrháři - skládání položky pracovního postupu](./samples/custom-composite-designers-workflow-items-presenter.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="6af3c-117">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="6af3c-118">Vytvoření vlastního návrháře aktivit pomocí přetažení zóny pomocí WorkflowItemPresenter</span><span class="sxs-lookup"><span data-stu-id="6af3c-118">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="6af3c-119">Start Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6af3c-119">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="6af3c-120">Na **souboru** nabídky, přejděte k **nový**a pak vyberte **projektu...** .</span><span class="sxs-lookup"><span data-stu-id="6af3c-120">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="6af3c-121">**Nový projekt** zobrazí se dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6af3c-121">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="6af3c-122">V **nainstalované šablony** vyberte **Windows** z kategorie váš preferovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="6af3c-122">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="6af3c-123">V **šablony** vyberte **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="6af3c-123">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="6af3c-124">V **název** zadejte `UsingWorkflowItemPresenter`.</span><span class="sxs-lookup"><span data-stu-id="6af3c-124">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="6af3c-125">V **umístění** zadejte adresář, ve kterém chcete projekt uložit, nebo klikněte na tlačítko **Procházet** přejít k němu.</span><span class="sxs-lookup"><span data-stu-id="6af3c-125">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="6af3c-126">V **řešení** pole, přijměte výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6af3c-126">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="6af3c-127">Klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="6af3c-127">Click **OK**.</span></span>

9. <span data-ttu-id="6af3c-128">Klikněte pravým tlačítkem na soubor MainWindows.xaml v **Průzkumníka řešení**vyberte **odstranit** a potvrďte **OK** v **sady Microsoft Visual Studio**dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="6af3c-128">Right-click the MainWindows.xaml file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialogue box.</span></span>

10. <span data-ttu-id="6af3c-129">Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter v **Průzkumníka řešení**vyberte **přidat**, pak **novou položku...**</span><span class="sxs-lookup"><span data-stu-id="6af3c-129">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="6af3c-130">Zobrazí se **přidat novou položku** dialog a vyberte **WPF** kategorie z **nainstalované šablony** části na levé straně.</span><span class="sxs-lookup"><span data-stu-id="6af3c-130">to bring up the **Add New Item** dialogue and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="6af3c-131">Vyberte **okno (WPF)** šablony, pojmenujte ho `RehostingWFDesigner`a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6af3c-131">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="6af3c-132">Otevřete soubor RehostingWFDesigner.xaml a vložte následující kód do ní k definování uživatelského rozhraní pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6af3c-132">Open the RehostingWFDesigner.xaml file and paste the following code into it to define the UI for the application.</span></span>

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

13. <span data-ttu-id="6af3c-133">Pokud chcete přidružit Návrhář aktivity typu aktivity, musíte zaregistrovat tento Návrhář aktivity s úložištěm metadat.</span><span class="sxs-lookup"><span data-stu-id="6af3c-133">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="6af3c-134">Chcete-li to provést, přidejte `RegisterMetadata` metodu `RehostingWFDesigner` třídy.</span><span class="sxs-lookup"><span data-stu-id="6af3c-134">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="6af3c-135">V rámci oboru `RegisterMetadata` metody vytvoření <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> objektu a volání <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodu přidejte atributy do ní.</span><span class="sxs-lookup"><span data-stu-id="6af3c-135">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="6af3c-136">Volání <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> způsob, jak přidat <xref:System.Activities.Presentation.Metadata.AttributeTable> do úložiště metadat.</span><span class="sxs-lookup"><span data-stu-id="6af3c-136">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="6af3c-137">Následující kód obsahuje rehosting logiku pro návrháře.</span><span class="sxs-lookup"><span data-stu-id="6af3c-137">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="6af3c-138">Zaregistruje metadata, vloží `SimpleNativeActivity` do panelu nástrojů a vytvoří pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="6af3c-138">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="6af3c-139">Vložte tento kód do souboru RehostingWFDesigner.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="6af3c-139">Put this code into the RehostingWFDesigner.xaml.cs file.</span></span>

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

14. <span data-ttu-id="6af3c-140">Adresáře odkazů v Průzkumníku řešení klikněte pravým tlačítkem a vyberte **přidat odkaz...**</span><span class="sxs-lookup"><span data-stu-id="6af3c-140">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="6af3c-141">Zobrazí se **přidat odkaz** dialogu.</span><span class="sxs-lookup"><span data-stu-id="6af3c-141">to bring up the **Add Reference** dialogue.</span></span>

15. <span data-ttu-id="6af3c-142">Klikněte na tlačítko **.NET** kartu, vyhledejte sestavení s názvem **System.Activities.Core.Presentation**, vyberte ho a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="6af3c-142">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="6af3c-143">Pomocí stejného postupu, přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="6af3c-143">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="6af3c-144">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="6af3c-144">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="6af3c-145">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="6af3c-145">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="6af3c-146">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="6af3c-146">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="6af3c-147">Otevřete soubor App.xaml a změňte hodnotu StartUpUri na "RehostingWFDesigner.xaml".</span><span class="sxs-lookup"><span data-stu-id="6af3c-147">Open the App.xaml file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="6af3c-148">Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter v **Průzkumníka řešení**vyberte **přidat**, pak **novou položku...**</span><span class="sxs-lookup"><span data-stu-id="6af3c-148">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="6af3c-149">Zobrazí se **přidat novou položku** dialog a vyberte **pracovního postupu** formulář Kategorie **nainstalované šablony** části na levé straně.</span><span class="sxs-lookup"><span data-stu-id="6af3c-149">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="6af3c-150">Vyberte **Návrhář aktivity** šablony, pojmenujte ho `SimpleNativeDesigner`a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6af3c-150">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="6af3c-151">Otevřete soubor SimpleNativeDesigner.xaml a vložte do něj následující kód.</span><span class="sxs-lookup"><span data-stu-id="6af3c-151">Open the SimpleNativeDesigner.xaml file and paste the following code into it.</span></span> <span data-ttu-id="6af3c-152">Poznámka: Tento kód používá <xref:System.Activities.Presentation.ActivityDesigner> jako kořenový element a ukazuje, jak vazby slouží k integraci <xref:System.Activities.Presentation.WorkflowItemPresenter> do návrháře tak podřízený typ lze zobrazit návrháře složené aktivity.</span><span class="sxs-lookup"><span data-stu-id="6af3c-152">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6af3c-153">Schéma pro <xref:System.Activities.Presentation.ActivityDesigner> lze přidat pouze jeden podřízený prvek prvku do definice návrháře vlastní aktivitu, ale může být tento element `StackPanel`, `Grid`, nebo jiného elementu složeného uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6af3c-153">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

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

21. <span data-ttu-id="6af3c-154">Klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter v **Průzkumníka řešení**vyberte **přidat**, pak **novou položku...**</span><span class="sxs-lookup"><span data-stu-id="6af3c-154">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="6af3c-155">Zobrazí se **přidat novou položku** dialog a vyberte **pracovního postupu** formulář Kategorie **nainstalované šablony** části na levé straně.</span><span class="sxs-lookup"><span data-stu-id="6af3c-155">to bring up the **Add New Item** dialogue and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="6af3c-156">Vyberte **aktivita s kódem** šablony, pojmenujte ho `SimpleNativeActivity`a klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="6af3c-156">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="6af3c-157">Implementace `SimpleNativeActivity` třídy tak, že zadáte následující kód do souboru SimpleNativeActivity.cs.</span><span class="sxs-lookup"><span data-stu-id="6af3c-157">Implement the `SimpleNativeActivity` class by entering the following code into the SimpleNativeActivity.cs file.</span></span>

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

24. <span data-ttu-id="6af3c-158">Vyberte **sestavit řešení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="6af3c-158">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="6af3c-159">Vyberte **spustit bez ladění** z **ladění** nabídce otevřete okno provádění se změněným hostováním vlastní návrh.</span><span class="sxs-lookup"><span data-stu-id="6af3c-159">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="6af3c-160">Vytvoření vlastního návrháře aktivit pomocí WorkflowItemsPresenter</span><span class="sxs-lookup"><span data-stu-id="6af3c-160">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="6af3c-161">Postup pro druhý návrháři vlastní aktivity se parallels první z nich s několik změn, z nichž první má Pojmenujte druhou aplikaci `UsingWorkflowItemsPresenter`.</span><span class="sxs-lookup"><span data-stu-id="6af3c-161">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="6af3c-162">Tato aplikace také nedefinuje nové vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="6af3c-162">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="6af3c-163">Hlavní rozdíly jsou obsaženy v souborech CustomParallelDesigner.xaml a RehostingWFDesigner.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="6af3c-163">Key differences are contained in the CustomParallelDesigner.xaml and RehostingWFDesigner.xaml.cs files.</span></span> <span data-ttu-id="6af3c-164">Tady je kód z CustomParallelDesigner.xaml soubor, který definuje uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6af3c-164">Here is the code from the CustomParallelDesigner.xaml file that defines the UI.</span></span>

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

3. <span data-ttu-id="6af3c-165">Tady je kód z RehostingWFDesigner.xaml.cs soubor, který poskytuje rehosting logiku.</span><span class="sxs-lookup"><span data-stu-id="6af3c-165">Here is the code from the RehostingWFDesigner.xaml.cs file that provides the rehosting logic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="6af3c-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6af3c-166">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="6af3c-167">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="6af3c-167">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
