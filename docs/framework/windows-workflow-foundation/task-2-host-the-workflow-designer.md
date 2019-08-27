---
title: 'Úkol 2: Hostování Návrháře postupu provádění'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037858"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="3c911-102">Úkol 2: Hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="3c911-102">Task 2: Host the Workflow Designer</span></span>

<span data-ttu-id="3c911-103">Toto téma popisuje postup hostování instance [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="3c911-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="3c911-104">Procedura nakonfiguruje ovládací prvek **mřížky** , který obsahuje návrháře, programově vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner> , která obsahuje výchozí <xref:System.Activities.Statements.Sequence> aktivitu, zaregistruje metadata návrháře pro zajištění podpory návrháře pro všechny vestavěné aktivity a hostují [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="3c911-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the WPF application.</span></span>

### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="3c911-105">Hostování návrháře pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="3c911-105">To host the workflow designer</span></span>

1. <span data-ttu-id="3c911-106">Otevřete projekt HostingApplication, který jste vytvořili [v úloze 1: Vytvořte novou Windows Presentation Foundation aplikaci](task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="3c911-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>

2. <span data-ttu-id="3c911-107">Upravte velikost okna tak, aby bylo snazší používat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3c911-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="3c911-108">Provedete to tak, že v Návrháři vyberete **MainWindow** a stisknutím klávesy F4 zobrazíte okno **vlastnosti** , v části **rozložení** nastavíte **šířku** na hodnotu 600 a **výšku** na hodnotu 350.</span><span class="sxs-lookup"><span data-stu-id="3c911-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>

3. <span data-ttu-id="3c911-109">Nastavte název mřížky výběrem panelu **mřížky** v Návrháři (klikněte na pole uvnitř **MainWindow**) a nastavte vlastnost **název** v horní části okna **vlastností** na hodnotu "grid1".</span><span class="sxs-lookup"><span data-stu-id="3c911-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>

4. <span data-ttu-id="3c911-110">V okně **vlastnosti** klikněte na tlačítko se třemi tečkami ( **...** ) `ColumnDefinitions` vedle vlastnosti. tím otevřete dialogové okno **Editor kolekcí** .</span><span class="sxs-lookup"><span data-stu-id="3c911-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>

5. <span data-ttu-id="3c911-111">V dialogovém okně **Editor kolekce** klikněte třikrát na tlačítko **Přidat** a vložte do rozložení tři sloupce.</span><span class="sxs-lookup"><span data-stu-id="3c911-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="3c911-112">První sloupec bude obsahovat **sadu nástrojů**, druhý sloupec bude hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]a třetí sloupec bude použit pro inspektora vlastností.</span><span class="sxs-lookup"><span data-stu-id="3c911-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>

6. <span data-ttu-id="3c911-113">`Width` Nastavte vlastnost prostřední sloupec na hodnotu "4 \*".</span><span class="sxs-lookup"><span data-stu-id="3c911-113">Set the `Width` property of the middle column to the value "4\*".</span></span>

7. <span data-ttu-id="3c911-114">Změny uložíte kliknutím na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="3c911-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="3c911-115">Do souboru MainWindow. XAML je přidán následující kód XAML:</span><span class="sxs-lookup"><span data-stu-id="3c911-115">The following XAML is added to your MainWindow.xaml file:</span></span>

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. <span data-ttu-id="3c911-116">V **Průzkumník řešení**klikněte pravým tlačítkem na MainWindow. XAML a vyberte **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="3c911-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="3c911-117">Upravte kód pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="3c911-117">Modify the code by following these steps:</span></span>

    1. <span data-ttu-id="3c911-118">Přidejte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="3c911-118">Add the following namespaces:</span></span>

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. <span data-ttu-id="3c911-119">Chcete-li deklarovat pole private member pro uložení instance <xref:System.Activities.Presentation.WorkflowDesigner>, přidejte `MainWindow` do třídy následující kód.</span><span class="sxs-lookup"><span data-stu-id="3c911-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. <span data-ttu-id="3c911-120">Do třídy přidejte `AddDesigner`následujícímetodu `MainWindow` .</span><span class="sxs-lookup"><span data-stu-id="3c911-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="3c911-121">Implementace vytvoří instanci instance <xref:System.Activities.Presentation.WorkflowDesigner>, <xref:System.Activities.Statements.Sequence> přidá do ní aktivitu a umístí ji do prostřední sloupec grid1 **mřížky**.</span><span class="sxs-lookup"><span data-stu-id="3c911-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>

        ```csharp
        private void AddDesigner()
        {
            //Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            //Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            //Load a new Sequence as default.
            this.wd.Load(new Sequence());

            //Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. <span data-ttu-id="3c911-122">Zaregistrujte metadata návrháře pro přidání podpory návrháře pro všechny předdefinované aktivity.</span><span class="sxs-lookup"><span data-stu-id="3c911-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="3c911-123">To umožňuje vyřadit aktivity z panelu nástrojů na původní <xref:System.Activities.Statements.Sequence> aktivitu [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]v.</span><span class="sxs-lookup"><span data-stu-id="3c911-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="3c911-124">Chcete-li to provést, `RegisterMetadata` přidejte metodu `MainWindow` do třídy.</span><span class="sxs-lookup"><span data-stu-id="3c911-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        <span data-ttu-id="3c911-125">Další informace o registraci návrháře aktivit najdete v tématu [How to: Vytvořte vlastního návrháře](how-to-create-a-custom-activity-designer.md)aktivit.</span><span class="sxs-lookup"><span data-stu-id="3c911-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>

    5. <span data-ttu-id="3c911-126">V konstruktoru <xref:System.Activities.Presentation.WorkflowDesigner>třídy přidejte volání metod deklarovaných dříve pro registraci metadat pro podporu návrháře a vytvoření. `MainWindow`</span><span class="sxs-lookup"><span data-stu-id="3c911-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata
            RegisterMetadata();

            // Add the WFF Designer
            AddDesigner();
        }
        ```

        > [!NOTE]
        > <span data-ttu-id="3c911-127">Metoda zaregistruje metadata návrháře vestavěných aktivit, <xref:System.Activities.Statements.Sequence> včetně aktivity. `RegisterMetadata`</span><span class="sxs-lookup"><span data-stu-id="3c911-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="3c911-128">Vzhledem k tomu, že <xref:System.Activities.Statements.Sequence> `RegisterMetadata`Metodapoužívá aktivitu, musí být metoda volána jako první. `AddDesigner`</span><span class="sxs-lookup"><span data-stu-id="3c911-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>

9. <span data-ttu-id="3c911-129">Stisknutím klávesy F5 Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="3c911-129">Press F5 to build and run the solution.</span></span>

10. <span data-ttu-id="3c911-130">Viz [úloha 3: Vytvořte podokno nástrojů a podokna](task-3-create-the-toolbox-and-propertygrid-panes.md) PropertyGrid, abyste se seznámili s tím, jak přidat do návrháře pracovního postupu, který je hostitelem, a podpora **PropertyGrid** .</span><span class="sxs-lookup"><span data-stu-id="3c911-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="3c911-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3c911-131">See also</span></span>

- [<span data-ttu-id="3c911-132">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="3c911-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="3c911-133">Úloha 1: Vytvoření nové aplikace Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="3c911-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="3c911-134">Úloha 3: Vytvoření podoken nástrojů a PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="3c911-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
