---
title: 'Úloha 3: Vytvořit panel nástrojů a PropertyGrid podokna'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 45819577c39185a5d95da81521cd541087a64efc
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721216"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Úloha 3: Vytvořit panel nástrojů a PropertyGrid podokna
V této úloze vytvoříte **nástrojů** a **PropertyGrid** podokna a přidat je do změněným hostováním [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Pro srovnání kód, který by měl být v souboru MainWindow.xaml.cs po dokončení tři úkoly v [změna hostování návrháře postupu provádění](rehosting-the-workflow-designer.md) řady témat najdete na konci tohoto tématu.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Vytvořit panel nástrojů a přidat do mřížky  
  
1.  Otevřete projekt HostingApplication můžete získat pomocí následujícího postupu popsaného v [úloha 2: Hostování návrháře postupu provádění](task-2-host-the-workflow-designer.md).  
  
2.  V **Průzkumníka řešení** podokně klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **zobrazit kód**.  
  
3.  Přidat `GetToolboxControl` metodu `MainWindow` třídu, která vytvoří <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, přidá nový **nástrojů** kategorii **nástrojů**a přiřadí <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence> typy aktivit do této kategorie spadají.  
  
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
  
4.  Přidat soukromé `AddToolbox` metodu `MainWindow` třídu, která umístí **nástrojů** v levém sloupci mřížky.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  Přidejte volání `AddToolBox` metoda ve `MainWindow()` konstruktoru třídy, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  Stisknutím klávesy F5 sestavte a spusťte řešení. **Nástrojů** obsahující <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence> má být zobrazena činnosti.  
  
### <a name="to-create-the-propertygrid"></a>Vytvoření ovládacího prvku PropertyGrid  
  
1.  V **Průzkumníka řešení** podokně klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **zobrazit kód**.  
  
2.  Přidat `AddPropertyInspector` metodu `MainWindow` třídy k umístění **PropertyGrid** podokně ve sloupci úplně vpravo v mřížce.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  Přidejte volání `AddPropertyInspector` metoda ve `MainWindow()` konstruktoru třídy, jak je znázorněno v následujícím kódu.  
  
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
  
4.  Stisknutím klávesy F5 sestavte a spusťte řešení. **Nástrojů**, plátno s návrhem pracovního postupu, a **PropertyGrid** podokna by měly být zobrazeny všechny a při přetažení <xref:System.Activities.Statements.Assign> aktivity nebo <xref:System.Activities.Statements.Sequence> aktivity na plátno návrhu v závislosti na aktivitě zvýrazněné by měl aktualizovat mřížku vlastností.  
  
## <a name="example"></a>Příklad  
 Soubor MainWindow.xaml.cs by měl nyní obsahovat následující kód.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Změna hostování Návrháře postupu provádění](rehosting-the-workflow-designer.md)
- [Úloha 1: Vytvoření nové aplikace Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Úloha 2: Hostování návrháře postupu provádění](task-2-host-the-workflow-designer.md)
