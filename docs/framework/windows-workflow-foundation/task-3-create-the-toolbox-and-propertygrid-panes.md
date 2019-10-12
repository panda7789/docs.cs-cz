---
title: 'Úkol 3: vytvoření podoken nástrojů a PropertyGrid'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 402a25c1cb82c245afa94f58cefc180515622ea9
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275860"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="a1f14-102">Úkol 3: vytvoření podoken nástrojů a PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="a1f14-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>

<span data-ttu-id="a1f14-103">V této úloze vytvoříte podokna **nástrojů** a **PropertyGrid** a přidáte je do [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a1f14-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>

<span data-ttu-id="a1f14-104">Pro referenci, kód, který by měl být v souboru MainWindow.xaml.cs po dokončení tří úloh při opětovném [hostování Návrhář postupu provádění](rehosting-the-workflow-designer.md) řady témat, je k dispozici na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="a1f14-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="a1f14-105">Chcete-li vytvořit sadu nástrojů a přidat ji do mřížky</span><span class="sxs-lookup"><span data-stu-id="a1f14-105">To create the Toolbox and add it to the grid</span></span>

1. <span data-ttu-id="a1f14-106">Otevřete projekt HostingApplication, který jste získali pomocí postupu popsaného v části [Úloha 2: hostování Návrhář postupu provádění](task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="a1f14-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>

2. <span data-ttu-id="a1f14-107">V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor *MainWindow. XAML* a vyberte možnost **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a1f14-107">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

3. <span data-ttu-id="a1f14-108">Přidejte metodu `GetToolboxControl` do třídy `MainWindow`, která vytvoří <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, přidá novou kategorii **nástrojů** do **sady nástrojů**a přiřadí do této kategorie typy aktivit <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="a1f14-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. <span data-ttu-id="a1f14-109">Přidejte metodu Private `AddToolbox` do třídy `MainWindow`, která umístí **sadu nástrojů** do levého sloupce v mřížce.</span><span class="sxs-lookup"><span data-stu-id="a1f14-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. <span data-ttu-id="a1f14-110">Přidejte volání metody `AddToolBox` v konstruktoru třídy `MainWindow()`, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="a1f14-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. <span data-ttu-id="a1f14-111">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte vaše řešení.</span><span class="sxs-lookup"><span data-stu-id="a1f14-111">Press <kbd>F5</kbd> to build and run your solution.</span></span> <span data-ttu-id="a1f14-112">Měla by se zobrazit **Sada nástrojů** obsahující aktivity <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="a1f14-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>

## <a name="to-create-the-propertygrid"></a><span data-ttu-id="a1f14-113">Vytvoření prvku PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="a1f14-113">To create the PropertyGrid</span></span>

1. <span data-ttu-id="a1f14-114">V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor *MainWindow. XAML* a vyberte možnost **Zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="a1f14-114">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

2. <span data-ttu-id="a1f14-115">Přidejte do třídy `MainWindow` metodu `AddPropertyInspector` k umístění podokna **PropertyGrid** do sloupce v mřížce vpravo:</span><span class="sxs-lookup"><span data-stu-id="a1f14-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid:</span></span>

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. <span data-ttu-id="a1f14-116">Přidejte volání metody `AddPropertyInspector` v konstruktoru třídy `MainWindow()`, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="a1f14-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. <span data-ttu-id="a1f14-117">Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="a1f14-117">Press <kbd>F5</kbd> to build and run the solution.</span></span> <span data-ttu-id="a1f14-118">Všechna okna **panelu nástrojů**, plátna návrhu pracovního postupu a podokna **PropertyGrid** by se měla zobrazit, a když přetáhnete aktivitu <xref:System.Activities.Statements.Assign> nebo aktivitu <xref:System.Activities.Statements.Sequence> na plátno návrhu, měla by se v závislosti na zvýrazněné aktivitě aktualizovat Mřížka vlastností.</span><span class="sxs-lookup"><span data-stu-id="a1f14-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>

## <a name="example"></a><span data-ttu-id="a1f14-119">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a1f14-119">Example</span></span>

<span data-ttu-id="a1f14-120">Soubor *MainWindow.XAML.cs* by teď měl obsahovat následující kód:</span><span class="sxs-lookup"><span data-stu-id="a1f14-120">The *MainWindow.xaml.cs* file should now contain the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a><span data-ttu-id="a1f14-121">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="a1f14-121">See also</span></span>

- [<span data-ttu-id="a1f14-122">Opětovné hostování Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="a1f14-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="a1f14-123">Úloha 1: vytvoření nové aplikace Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="a1f14-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="a1f14-124">Úkol 2: hostování Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="a1f14-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
