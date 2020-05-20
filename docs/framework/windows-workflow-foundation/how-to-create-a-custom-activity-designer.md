---
title: 'Postupy: Vytvoření vlastního návrháře aktivity'
description: Tento článek popisuje, jak vytvořit návrháře vlastní aktivity v modulu Workflow Foundation, který má ukládací zónu, kde lze umístit libovolnou aktivitu.
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419782"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="2530c-103">Postupy: Vytvoření vlastního návrháře aktivity</span><span class="sxs-lookup"><span data-stu-id="2530c-103">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="2530c-104">Obvykle se implementují vlastní návrháři aktivit, aby se jejich přidružené aktivity mohly vytvářet s ostatními aktivitami, jejichž návrháři se můžou na návrhovou plochu na návrhové ploše vyřadit.</span><span class="sxs-lookup"><span data-stu-id="2530c-104">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="2530c-105">Tato funkce vyžaduje, aby vlastní Návrhář aktivity poskytoval "ukládací zónu", kde lze umístit libovolnou aktivitu, a také způsob, jak spravovat výslednou kolekci prvků na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="2530c-105">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="2530c-106">Toto téma popisuje, jak vytvořit vlastního návrháře aktivit, který obsahuje takovou odkládací zónu a jak vytvořit vlastního návrháře aktivit, který poskytuje funkce pro úpravy potřebné ke správě kolekce prvků návrháře.</span><span class="sxs-lookup"><span data-stu-id="2530c-106">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="2530c-107">Vlastní návrháři aktivit obvykle dědí z <xref:System.Activities.Presentation.ActivityDesigner> výchozího typu návrháře základní aktivity pro všechny aktivity bez konkrétního návrháře.</span><span class="sxs-lookup"><span data-stu-id="2530c-107">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="2530c-108">Tento typ poskytuje uživatelské prostředí pro interakci s mřížkou vlastností a konfiguraci základních aspektů, jako je například Správa barev a ikon.</span><span class="sxs-lookup"><span data-stu-id="2530c-108">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="2530c-109"><xref:System.Activities.Presentation.ActivityDesigner>používá dva ovládací prvky pro pomoc a usnadňuje <xref:System.Activities.Presentation.WorkflowItemPresenter> <xref:System.Activities.Presentation.WorkflowItemsPresenter> vývoj vlastních návrhářů aktivit.</span><span class="sxs-lookup"><span data-stu-id="2530c-109"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="2530c-110">Zpracovávají společné funkce, jako je přetahování a odstraňování podřízených prvků, odstranění, výběru a přidání těchto podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="2530c-110">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="2530c-111"><xref:System.Activities.Presentation.WorkflowItemPresenter>Umožňuje jeden podřízený prvek uživatelského rozhraní uvnitř a poskytuje "ukládací zónu", zatímco <xref:System.Activities.Presentation.WorkflowItemsPresenter> může poskytovat podporu více prvků uživatelského rozhraní, včetně dalších funkcí, jako je řazení, přesunutí, odstranění a přidání podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="2530c-111">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="2530c-112">Druhá klíčová část scénáře, která vyžaduje zvýraznění v implementaci vlastního návrháře aktivit, se týká způsobu, jakým jsou úpravy vizuálů svázány pomocí datové vazby WPF s instancí uloženou v paměti, kterou upravujeme v návrháři.</span><span class="sxs-lookup"><span data-stu-id="2530c-112">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using WPF data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="2530c-113">Toho je dosaženo stromem položky modelu, který je také zodpovědný za povolení oznámení o změně a sledování událostí, jako jsou změny v stavech.</span><span class="sxs-lookup"><span data-stu-id="2530c-113">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="2530c-114">Toto téma popisuje dva postupy.</span><span class="sxs-lookup"><span data-stu-id="2530c-114">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="2530c-115">První postup popisuje, jak vytvořit vlastního návrháře aktivit s <xref:System.Activities.Presentation.WorkflowItemPresenter> , který poskytuje ukládací zónu, která přijímá další aktivity.</span><span class="sxs-lookup"><span data-stu-id="2530c-115">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="2530c-116">Tento postup je založený na ukázce [vlastního složeného návrháře – ukázka předvádějící položky pracovního postupu](./samples/custom-composite-designers-workflow-item-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="2530c-116">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="2530c-117">Druhý postup popisuje, jak vytvořit vlastního návrháře aktivit s nástrojem <xref:System.Activities.Presentation.WorkflowItemsPresenter> , který poskytuje funkce potřebné pro úpravu kolekce obsažených prvků.</span><span class="sxs-lookup"><span data-stu-id="2530c-117">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="2530c-118">Tento postup je založený na ukázce [vlastního složeného návrháře – pracovní postup položky pracovního postupu](./samples/custom-composite-designers-workflow-items-presenter.md) .</span><span class="sxs-lookup"><span data-stu-id="2530c-118">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="2530c-119">Vytvoření vlastního návrháře aktivit pomocí přetažení zóny pomocí WorkflowItemPresenter</span><span class="sxs-lookup"><span data-stu-id="2530c-119">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="2530c-120">Spusťte Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="2530c-120">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="2530c-121">V nabídce **soubor** přejděte na příkaz **Nový**a vyberte možnost **projekt...**.</span><span class="sxs-lookup"><span data-stu-id="2530c-121">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="2530c-122">Otevře se dialogové okno **Nový projekt** .</span><span class="sxs-lookup"><span data-stu-id="2530c-122">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="2530c-123">V podokně **Nainstalované šablony** vyberte možnost **Windows** z kategorie preferovaný jazyk.</span><span class="sxs-lookup"><span data-stu-id="2530c-123">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="2530c-124">V podokně **šablony** vyberte možnost **aplikace WPF**.</span><span class="sxs-lookup"><span data-stu-id="2530c-124">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="2530c-125">Do pole **název** zadejte `UsingWorkflowItemPresenter` .</span><span class="sxs-lookup"><span data-stu-id="2530c-125">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="2530c-126">Do pole **umístění** zadejte adresář, do kterého chcete uložit projekt, nebo klikněte na tlačítko **Procházet** a přejděte na něj.</span><span class="sxs-lookup"><span data-stu-id="2530c-126">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="2530c-127">V poli **řešení** přijměte výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2530c-127">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="2530c-128">Klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="2530c-128">Click **OK**.</span></span>

9. <span data-ttu-id="2530c-129">V **Průzkumník řešení**klikněte pravým tlačítkem na soubor *MainWindows. XAML* , vyberte **Odstranit** a potvrďte **OK** v dialogovém okně **Microsoft Visual Studio** .</span><span class="sxs-lookup"><span data-stu-id="2530c-129">Right-click the *MainWindows.xaml* file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialog box.</span></span>

10. <span data-ttu-id="2530c-130">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter, vyberte **Přidat**a **Nová položka...**</span><span class="sxs-lookup"><span data-stu-id="2530c-130">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="2530c-131">Chcete-li vyvolat dialogové okno **Přidat novou položku** a vybrat kategorii **WPF** v části **Nainstalované šablony** na levé straně.</span><span class="sxs-lookup"><span data-stu-id="2530c-131">to bring up the **Add New Item** dialog and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="2530c-132">Vyberte šablonu **okna (WPF)** , pojmenujte ji `RehostingWFDesigner` a klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="2530c-132">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="2530c-133">Otevřete soubor *RehostingWFDesigner. XAML* a vložte do něj následující kód, který definuje uživatelské rozhraní aplikace:</span><span class="sxs-lookup"><span data-stu-id="2530c-133">Open the *RehostingWFDesigner.xaml* file and paste the following code into it to define the UI for the application:</span></span>

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

13. <span data-ttu-id="2530c-134">Chcete-li přidružit návrháře aktivit k typu aktivity, musíte tohoto návrháře aktivit zaregistrovat s úložištěm metadat.</span><span class="sxs-lookup"><span data-stu-id="2530c-134">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="2530c-135">Chcete-li to provést, přidejte `RegisterMetadata` metodu do `RehostingWFDesigner` třídy.</span><span class="sxs-lookup"><span data-stu-id="2530c-135">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="2530c-136">V rámci rozsahu `RegisterMetadata` metody vytvořte <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> objekt a zavolejte <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> metodu pro přidání atributů.</span><span class="sxs-lookup"><span data-stu-id="2530c-136">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="2530c-137">Voláním <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> metody přidejte do <xref:System.Activities.Presentation.Metadata.AttributeTable> úložiště metadat.</span><span class="sxs-lookup"><span data-stu-id="2530c-137">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="2530c-138">Následující kód obsahuje logiku opětovného hostování pro návrháře.</span><span class="sxs-lookup"><span data-stu-id="2530c-138">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="2530c-139">Registruje metadata, vloží `SimpleNativeActivity` do sady nástrojů a vytvoří pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="2530c-139">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="2530c-140">Vložte tento kód do souboru *RehostingWFDesigner.XAML.cs* .</span><span class="sxs-lookup"><span data-stu-id="2530c-140">Put this code into the *RehostingWFDesigner.xaml.cs* file.</span></span>

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

14. <span data-ttu-id="2530c-141">Klikněte pravým tlačítkem na adresář odkazy v Průzkumník řešení a vyberte **Přidat odkaz...**</span><span class="sxs-lookup"><span data-stu-id="2530c-141">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="2530c-142">Otevřete dialogové okno **Přidat odkaz** .</span><span class="sxs-lookup"><span data-stu-id="2530c-142">to bring up the **Add Reference** dialog.</span></span>

15. <span data-ttu-id="2530c-143">Klikněte na kartu **.NET** , vyhledejte sestavení s názvem **System. Activities. Core. Presentation**, vyberte ho a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="2530c-143">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="2530c-144">Pomocí stejného postupu přidejte odkazy na následující sestavení:</span><span class="sxs-lookup"><span data-stu-id="2530c-144">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="2530c-145">System. data. DataSetExtensions. dll</span><span class="sxs-lookup"><span data-stu-id="2530c-145">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="2530c-146">System. Activities. Presentation. dll</span><span class="sxs-lookup"><span data-stu-id="2530c-146">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="2530c-147">System. ServiceModel. Activities. dll</span><span class="sxs-lookup"><span data-stu-id="2530c-147">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="2530c-148">Otevřete soubor *App. XAML* a změňte hodnotu StartUpUri na RehostingWFDesigner. XAML.</span><span class="sxs-lookup"><span data-stu-id="2530c-148">Open the *App.xaml* file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="2530c-149">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter, vyberte **Přidat**a **Nová položka...**</span><span class="sxs-lookup"><span data-stu-id="2530c-149">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="2530c-150">Chcete-li vyvolat dialogové okno **Přidat novou položku** a vybrat kategorii **pracovního postupu** , otevřete část **Nainstalované šablony** na levé straně.</span><span class="sxs-lookup"><span data-stu-id="2530c-150">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="2530c-151">Vyberte šablonu **návrháře aktivit** , pojmenujte ji `SimpleNativeDesigner` a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="2530c-151">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="2530c-152">Otevřete soubor *SimpleNativeDesigner. XAML* a vložte do něj následující kód.</span><span class="sxs-lookup"><span data-stu-id="2530c-152">Open the *SimpleNativeDesigner.xaml* file and paste the following code into it.</span></span> <span data-ttu-id="2530c-153">Všimněte si, že tento kód používá <xref:System.Activities.Presentation.ActivityDesigner> jako kořenový element a ukazuje, jak se vazba používá pro integraci <xref:System.Activities.Presentation.WorkflowItemPresenter> do návrháře, takže podřízený typ lze zobrazit v návrháři složených aktivit.</span><span class="sxs-lookup"><span data-stu-id="2530c-153">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2530c-154">Schéma pro <xref:System.Activities.Presentation.ActivityDesigner> umožňuje přidání pouze jednoho podřízeného prvku do vaší definice návrháře vlastní aktivity; tento element však může být `StackPanel` , `Grid` nebo nějaký jiný složený prvek uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2530c-154">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

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

21. <span data-ttu-id="2530c-155">V **Průzkumník řešení**klikněte pravým tlačítkem na projekt UsingWorkflowItemPresenter, vyberte **Přidat**a **Nová položka...**</span><span class="sxs-lookup"><span data-stu-id="2530c-155">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="2530c-156">Chcete-li vyvolat dialogové okno **Přidat novou položku** a vybrat kategorii **pracovního postupu** , otevřete část **Nainstalované šablony** na levé straně.</span><span class="sxs-lookup"><span data-stu-id="2530c-156">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="2530c-157">Vyberte šablonu **aktivita kódu** , pojmenujte ji `SimpleNativeActivity` a klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="2530c-157">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="2530c-158">Implementujte `SimpleNativeActivity` třídu zadáním následujícího kódu do souboru *SimpleNativeActivity.cs* :</span><span class="sxs-lookup"><span data-stu-id="2530c-158">Implement the `SimpleNativeActivity` class by entering the following code into the *SimpleNativeActivity.cs* file:</span></span>

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

24. <span data-ttu-id="2530c-159">V nabídce **sestavení** vyberte **sestavení řešení** .</span><span class="sxs-lookup"><span data-stu-id="2530c-159">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="2530c-160">Vyberte možnost **Spustit bez ladění** z nabídky **ladění** a otevřete tak opětovné hostování vlastního návrhového okna.</span><span class="sxs-lookup"><span data-stu-id="2530c-160">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="2530c-161">Vytvoření vlastního návrháře aktivit pomocí WorkflowItemsPresenter</span><span class="sxs-lookup"><span data-stu-id="2530c-161">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="2530c-162">Postup pro druhý Návrhář vlastní aktivity je souběžně první s několika úpravami, první z nich je pojmenovat druhou aplikaci `UsingWorkflowItemsPresenter` .</span><span class="sxs-lookup"><span data-stu-id="2530c-162">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="2530c-163">Tato aplikace také nedefinuje novou vlastní aktivitu.</span><span class="sxs-lookup"><span data-stu-id="2530c-163">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="2530c-164">Klíčové rozdíly jsou obsaženy v souborech *CustomParallelDesigner. XAML* a *RehostingWFDesigner.XAML.cs* .</span><span class="sxs-lookup"><span data-stu-id="2530c-164">Key differences are contained in the *CustomParallelDesigner.xaml* and *RehostingWFDesigner.xaml.cs* files.</span></span> <span data-ttu-id="2530c-165">Zde je kód ze souboru *CustomParallelDesigner. XAML* , který definuje uživatelské rozhraní:</span><span class="sxs-lookup"><span data-stu-id="2530c-165">Here is the code from the *CustomParallelDesigner.xaml* file that defines the UI:</span></span>

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

3. <span data-ttu-id="2530c-166">Zde je kód ze souboru *RehostingWFDesigner.XAML.cs* , který poskytuje logiku opětovného hostování:</span><span class="sxs-lookup"><span data-stu-id="2530c-166">Here is the code from the *RehostingWFDesigner.xaml.cs* file that provides the rehosting logic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2530c-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="2530c-167">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="2530c-168">Přizpůsobení prostředí pro návrh pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2530c-168">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
