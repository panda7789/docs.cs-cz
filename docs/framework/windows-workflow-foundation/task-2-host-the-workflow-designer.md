---
title: 'Úloha 2: Hostování návrháře postupu provádění'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: e02134408b38e5c9aee9c59d86b1dfce032653d1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708636"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="42fbc-102">Úloha 2: Hostování návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="42fbc-102">Task 2: Host the Workflow Designer</span></span>
<span data-ttu-id="42fbc-103">Toto téma popisuje postup, pro který je hostitelem instance [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="42fbc-103">This topic describes the procedure for hosting an instance of the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="42fbc-104">Postup konfiguruje **mřížky** ovládací prvek, který obsahuje Návrhář, prostřednictvím kódu programu vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner> , který obsahuje výchozí <xref:System.Activities.Statements.Sequence> aktivity, zaregistruje metadata návrháře k poskytování Podpora návrhářů pro všechny vestavěné aktivity a hostitele [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="42fbc-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] in the [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application.</span></span>  
  
### <a name="to-host-the-workflow-designer"></a><span data-ttu-id="42fbc-105">K hostování návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="42fbc-105">To host the workflow designer</span></span>  
  
1.  <span data-ttu-id="42fbc-106">Otevřít HostingApplication projektu, kterou jste vytvořili v [úkol 1: Vytvoření nové aplikace Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="42fbc-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>  
  
2.  <span data-ttu-id="42fbc-107">Úprava velikosti okna, které usnadňují použití [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42fbc-107">Adjust the size of the window to make it easier to use the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="42fbc-108">Chcete-li to provést, vyberte **hlavního okna MainWindow** v návrháři, zobrazíte stisknutím klávesy F4 **vlastnosti** okna a v **rozložení** části existuje, nastavte **šířku** k hodnotě čítače 600 a **výška** na hodnotu 350.</span><span class="sxs-lookup"><span data-stu-id="42fbc-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>  
  
3.  <span data-ttu-id="42fbc-109">Nastavte název tabulky tak, že vyberete **mřížky** panelu v Návrháři (klikněte na pole uvnitř **hlavního okna MainWindow**) a nastavení **název** vlastnost v horní části  **Vlastnosti** okno "grid1".</span><span class="sxs-lookup"><span data-stu-id="42fbc-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>  
  
4.  <span data-ttu-id="42fbc-110">V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami (**...** ) vedle položky `ColumnDefinitions` vlastnosti otevřít **Editor kolekce** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="42fbc-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>  
  
5.  <span data-ttu-id="42fbc-111">V **Editor kolekce** dialogové okno, klikněte na tlačítko **přidat** tlačítko třikrát pro vložení tři sloupce do požadovaného rozložení.</span><span class="sxs-lookup"><span data-stu-id="42fbc-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="42fbc-112">První sloupec bude obsahovat **nástrojů**, druhý sloupec bude hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a třetí sloupec bude použit pro vlastnost inspector.</span><span class="sxs-lookup"><span data-stu-id="42fbc-112">The first column will contain the **Toolbox**, the second column will host the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], and the third column will be used for the property inspector.</span></span>  
  
6.  <span data-ttu-id="42fbc-113">Nastavte `Width` vlastnost v prostředním sloupci na hodnotu "4 \*".</span><span class="sxs-lookup"><span data-stu-id="42fbc-113">Set the `Width` property of the middle column to the value "4\*".</span></span>  
  
7.  <span data-ttu-id="42fbc-114">Změny uložíte kliknutím na tlačítko **OK** .</span><span class="sxs-lookup"><span data-stu-id="42fbc-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="42fbc-115">Do souboru MainWindow.xaml je přidána následující XAML:</span><span class="sxs-lookup"><span data-stu-id="42fbc-115">The following XAML is added to your MainWindow.xaml file:</span></span>  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  <span data-ttu-id="42fbc-116">V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **zobrazit kód**.</span><span class="sxs-lookup"><span data-stu-id="42fbc-116">In **Solution Explorer**, right-click MainWindow.xaml and select **View Code**.</span></span> <span data-ttu-id="42fbc-117">Úprava kódu pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="42fbc-117">Modify the code by following these steps:</span></span>  
  
    1.  <span data-ttu-id="42fbc-118">Přidejte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="42fbc-118">Add the following namespaces:</span></span>  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  <span data-ttu-id="42fbc-119">Chcete-li deklarovat pole soukromý člen pro uložení instance <xref:System.Activities.Presentation.WorkflowDesigner>, přidejte následující kód, který `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="42fbc-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class.</span></span>  
  
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
  
    3.  <span data-ttu-id="42fbc-120">Přidejte následující `AddDesigner` metodu `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="42fbc-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="42fbc-121">Implementace vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner>, přidá <xref:System.Activities.Statements.Sequence> aktivitu a umístí ji v prostředním sloupci grid1 **mřížky**.</span><span class="sxs-lookup"><span data-stu-id="42fbc-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>  
  
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
  
    4.  <span data-ttu-id="42fbc-122">Zaregistrujte metadata návrháře návrháře podporu pro všechny vestavěné aktivity.</span><span class="sxs-lookup"><span data-stu-id="42fbc-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="42fbc-123">To umožňuje umístit aktivity z panelu nástrojů do původní <xref:System.Activities.Statements.Sequence> aktivity v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="42fbc-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the [!INCLUDE[wfd2](../../../includes/wfd2-md.md)].</span></span> <span data-ttu-id="42fbc-124">Chcete-li to provést, přidejte `RegisterMetadata` metodu `MainWindow` třídy.</span><span class="sxs-lookup"><span data-stu-id="42fbc-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class.</span></span>  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         <span data-ttu-id="42fbc-125">Další informace o registraci návrháři aktivit najdete v tématu [jak: Vytvoření vlastního návrháře aktivit](how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="42fbc-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>  
  
    5.  <span data-ttu-id="42fbc-126">V `MainWindow` konstruktor třídy, přidejte volání metody deklarované dříve zaregistrovat metadata pro podporu návrháře a vytvořit <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="42fbc-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>  
  
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
        >  <span data-ttu-id="42fbc-127">`RegisterMetadata` Metoda registruje metadata návrháře integrovaných aktivit, včetně <xref:System.Activities.Statements.Sequence> aktivity.</span><span class="sxs-lookup"><span data-stu-id="42fbc-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="42fbc-128">Protože `AddDesigner` metoda používá <xref:System.Activities.Statements.Sequence> aktivity, `RegisterMetadata` metoda musí být nejdříve volána.</span><span class="sxs-lookup"><span data-stu-id="42fbc-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>  
  
9. <span data-ttu-id="42fbc-129">Stisknutím klávesy F5 sestavte a spusťte řešení.</span><span class="sxs-lookup"><span data-stu-id="42fbc-129">Press F5 to build and run the solution.</span></span>  
  
10. <span data-ttu-id="42fbc-130">Zobrazit [úloha 3: Vytvořit panel nástrojů a podokna PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) Další informace o přidání **nástrojů** a **PropertyGrid** podporují do návrháře postupu provádění se změněným hostováním.</span><span class="sxs-lookup"><span data-stu-id="42fbc-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42fbc-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42fbc-131">See also</span></span>
- [<span data-ttu-id="42fbc-132">Změna hostování Návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="42fbc-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="42fbc-133">Úloha 1: Vytvoření nové aplikace Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="42fbc-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="42fbc-134">Úloha 3: Vytvořit panel nástrojů a PropertyGrid podokna</span><span class="sxs-lookup"><span data-stu-id="42fbc-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
