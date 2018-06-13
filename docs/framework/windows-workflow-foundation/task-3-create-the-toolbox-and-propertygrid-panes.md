---
title: 'Úloha 3: Vytvoření sady nástrojů a PropertyGrid podokna'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 9bfce22e9de1d6115cb88daddcd2dca355b6bae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519747"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="5d0c8-102">Úloha 3: Vytvoření sady nástrojů a PropertyGrid podokna</span><span class="sxs-lookup"><span data-stu-id="5d0c8-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>
<span data-ttu-id="5d0c8-103">V této úloze se vytvoří **sada nástrojů** a **PropertyGrid** podokna a přidat je do opětovné hostování nástroje [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5d0c8-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>  
  
 <span data-ttu-id="5d0c8-104">Pro odkaz, kód, který by měl být v souboru MainWindow.xaml.cs po dokončení tří úloh v [opětovného hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) řady témat je k dispozici na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="5d0c8-105">Vytvoření sady nástrojů a přidejte ho k mřížce.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-105">To create the Toolbox and add it to the grid</span></span>  
  
1.  <span data-ttu-id="5d0c8-106">Otevřete projekt HostingApplication jste získali podle postupu popsaného v [úloha 2: hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="5d0c8-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).</span></span>  
  
2.  <span data-ttu-id="5d0c8-107">V **Průzkumníku řešení** podokně klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-107">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
3.  <span data-ttu-id="5d0c8-108">Přidat `GetToolboxControl` metodu `MainWindow` třídu, která vytvoří <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, přidá nový **sada nástrojů** kategorii, která se **sada nástrojů**a přiřadí <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence> typy aktivit do této kategorie spadají.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4.  <span data-ttu-id="5d0c8-109">Přidat privátního `AddToolbox` metodu `MainWindow` třídu, která umístí **sada nástrojů** v levém sloupci v mřížce.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  <span data-ttu-id="5d0c8-110">Přidejte volání `AddToolBox` metoda v `MainWindow()` konstruktoru třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  <span data-ttu-id="5d0c8-111">Stisknutím klávesy F5 sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-111">Press F5 to build and run your solution.</span></span> <span data-ttu-id="5d0c8-112">**Sada nástrojů** obsahující <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence> aktivity mají být zobrazeny.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>  
  
### <a name="to-create-the-propertygrid"></a><span data-ttu-id="5d0c8-113">Vytvoření ovládacího prvku PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="5d0c8-113">To create the PropertyGrid</span></span>  
  
1.  <span data-ttu-id="5d0c8-114">V **Průzkumníku řešení** podokně klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-114">In the **Solution Explorer** pane, right-click the MainWindow.xaml file and select **View Code**.</span></span>  
  
2.  <span data-ttu-id="5d0c8-115">Přidat `AddPropertyInspector` metodu `MainWindow` třída umístit **PropertyGrid** podokně ve sloupci úplně vpravo v mřížce.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid.</span></span>  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  <span data-ttu-id="5d0c8-116">Přidejte volání `AddPropertyInspector` metoda v `MainWindow()` konstruktoru třídy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code.</span></span>  
  
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
  
4.  <span data-ttu-id="5d0c8-117">Stisknutím klávesy F5 sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-117">Press F5 to build and run the solution.</span></span> <span data-ttu-id="5d0c8-118">**Sada nástrojů**, plátno návrhu pracovního postupu, a **PropertyGrid** podokna by měly být zobrazeny všechny a při přetažení <xref:System.Activities.Statements.Assign> aktivity nebo <xref:System.Activities.Statements.Sequence> aktivity na plátno návrhu v závislosti na zvýrazněné aktivity by měl aktualizovat mřížkou vlastností.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d0c8-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d0c8-119">Example</span></span>  
 <span data-ttu-id="5d0c8-120">Soubor MainWindow.xaml.cs teď by měla obsahovat následující kód.</span><span class="sxs-lookup"><span data-stu-id="5d0c8-120">The MainWindow.xaml.cs file should now contain the following code.</span></span>  
  
```  
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
//dlls added  
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
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
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
  
## <a name="see-also"></a><span data-ttu-id="5d0c8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d0c8-121">See Also</span></span>  
 [<span data-ttu-id="5d0c8-122">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="5d0c8-122">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="5d0c8-123">Úkol 1: Vytvoření nové aplikace Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="5d0c8-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="5d0c8-124">Úkol 2: Hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="5d0c8-124">Task 2: Host the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
