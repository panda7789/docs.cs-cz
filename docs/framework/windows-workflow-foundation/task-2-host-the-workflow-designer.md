---
title: "Úloha 2: Hostování návrháře pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fffc934bbbd1fc707e0bf5c0afbf79a40fc8c633
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="e514e-102">Úloha 2: Hostování návrháře pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e514e-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="e514e-103">Toto téma popisuje postup pro hostování instanci [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] v [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="e514e-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] application.</span></span>  
  
 <span data-ttu-id="e514e-104">Postup konfiguruje **mřížky** ovládací prvek, který obsahuje návrháře, prostřednictvím kódu programu vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner> obsahující výchozí <xref:System.Activities.Statements.Sequence> aktivity, zaregistruje návrháře metadata zajistit Podpora návrháře pro všechny zabudované aktivity a hostitelé [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="e514e-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="e514e-105">K hostování návrháře pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e514e-105">To host the workflow designer</span></span>  
  
1.  <span data-ttu-id="e514e-106">Otevřete HostingApplication projektu, kterou jste vytvořili v [úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="e514e-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).</span></span>  
  
2.  <span data-ttu-id="e514e-107">Upravit velikost okna, aby bylo snazší používat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e514e-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="e514e-108">Chcete-li to provést, vyberte **MainWindow** v návrháři, zobrazte stisknutím klávesy F4 **vlastnosti** okno a v **rozložení** části existuje, nastavte **šířka** na hodnotu 600 a **výška** na hodnotu 350.</span><span class="sxs-lookup"><span data-stu-id="e514e-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3.  <span data-ttu-id="e514e-109">Název mřížky nastavit tak, že vyberete **mřížky** panelu v Návrháři (klikněte na pole uvnitř **MainWindow**) a nastavení **název** vlastnost v horní části  **Vlastnosti** okno "grid1".</span><span class="sxs-lookup"><span data-stu-id="e514e-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4.  <span data-ttu-id="e514e-110">V **vlastnosti** okně klikněte na tlačítko se třemi tečkami (**...** ) vedle položky `ColumnDefinitions` vlastnost otevřete **Editor kolekce** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="e514e-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="e514e-111">V **Editor kolekce** dialogové okno, klikněte **přidat** tlačítko třikrát na tři sloupce k vložení do rozložení.</span><span class="sxs-lookup"><span data-stu-id="e514e-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="e514e-112">První sloupec bude obsahovat **sada nástrojů**, druhý sloupec bude hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a třetí sloupec se použije pro vlastnost inspector.</span><span class="sxs-lookup"><span data-stu-id="e514e-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6.  <span data-ttu-id="e514e-113">Nastavte `Width` vlastnost střední sloupce na hodnotu "4 *".</span><span class="sxs-lookup"><span data-stu-id="e514e-113">Set the `Width` property of the middle column to the value "4*".</span></span>  
  
7.  <span data-ttu-id="e514e-114">Klikněte na tlačítko **OK** a uložte změny.</span><span class="sxs-lookup"><span data-stu-id="e514e-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="e514e-115">Následující XAML se přidá do souboru MainWindow.xaml:</span><span class="sxs-lookup"><span data-stu-id="e514e-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  <span data-ttu-id="e514e-116">V **Průzkumníku řešení**, klikněte pravým tlačítkem na MainWindow.xaml a vyberte **kód zobrazení**.</span><span class="sxs-lookup"><span data-stu-id="e514e-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="e514e-117">Upravte kód pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="e514e-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="e514e-118">Přidání následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="e514e-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="e514e-119">Deklarovat privátního člena pole pro uložení instance <xref:System.Activities.Presentation.WorkflowDesigner>, přidejte následující kód, který `MainWindow` – třída.</span><span class="sxs-lookup"><span data-stu-id="e514e-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
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
  
    3.  <span data-ttu-id="e514e-120">Přidejte následující `AddDesigner` metodu `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="e514e-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="e514e-121">Implementace vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner>, přidá <xref:System.Activities.Statements.Sequence> aktivitu a umístí jej v prostředním sloupci grid1 **mřížky**.</span><span class="sxs-lookup"><span data-stu-id="e514e-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
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
  
    4.  <span data-ttu-id="e514e-122">Zaregistrujte návrháře metadata o návrháře podporu zabudované aktivity.</span><span class="sxs-lookup"><span data-stu-id="e514e-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="e514e-123">To umožňuje vyřadit aktivity z panelu nástrojů na původní <xref:System.Activities.Statements.Sequence> aktivity v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e514e-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="e514e-124">Chcete-li to provést, přidejte `RegisterMetadata` metodu `MainWindow` – třída.</span><span class="sxs-lookup"><span data-stu-id="e514e-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="e514e-125">registrace návrháře aktivit, najdete v části [postupy: vytvoření Návrháře vlastních aktivit](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="e514e-125"> registering activity designers, see [How to: Create a Custom Activity Designer](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="e514e-126">V `MainWindow` konstruktoru třídy, přidejte volání metody dříve deklarované registrujete metadata pro návrháře podporu a vytvářet <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="e514e-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
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
        >  <span data-ttu-id="e514e-127">`RegisterMetadata` Metoda registruje návrháře metadata integrovaných aktivit, včetně <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="e514e-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="e514e-128">Protože `AddDesigner` metoda používá <xref:System.Activities.Statements.Sequence> aktivity, `RegisterMetadata` metoda musí být volána nejprve.</span><span class="sxs-lookup"><span data-stu-id="e514e-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="e514e-129">Stisknutím klávesy F5 sestavení a spuštění řešení.</span><span class="sxs-lookup"><span data-stu-id="e514e-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="e514e-130">V tématu [úloha 3: vytvoření sady nástrojů a PropertyGrid podokna](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) se dozvíte, jak přidat **sada nástrojů** a **PropertyGrid** podporu do vaší opětovné hostování nástroje pracovního postupu návrháře.</span><span class="sxs-lookup"><span data-stu-id="e514e-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e514e-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="e514e-131">See Also</span></span>  
 [<span data-ttu-id="e514e-132">Opětovného hostování návrháře pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="e514e-132">Rehosting the Workflow Designer</span></span>](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [<span data-ttu-id="e514e-133">Úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="e514e-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [<span data-ttu-id="e514e-134">Úloha 3: Vytvoření sady nástrojů a PropertyGrid podokna</span><span class="sxs-lookup"><span data-stu-id="e514e-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
