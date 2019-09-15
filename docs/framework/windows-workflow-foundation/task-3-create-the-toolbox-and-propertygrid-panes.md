---
title: 'Úkol 3: Vytvoření podoken pro sady nástrojů a mřížku vlastností'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 6339969c52a5c4eedfb0e89eebdc982ca3fe6686
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988714"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Úkol 3: Vytvoření podoken pro sady nástrojů a mřížku vlastností
V této úloze vytvoříte podokna **nástrojů** a **PropertyGrid** a přidáte je do hostitele [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Pro referenci, kód, který by měl být v souboru MainWindow.xaml.cs po dokončení tří úloh při opětovném [hostování Návrhář postupu provádění](rehosting-the-workflow-designer.md) řady témat, je k dispozici na konci tohoto tématu.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Chcete-li vytvořit sadu nástrojů a přidat ji do mřížky  
  
1. Otevřete projekt HostingApplication, který jste získali pomocí postupu popsaného v [úloze 2: Hostování Návrhář postupu provádění](task-2-host-the-workflow-designer.md).  
  
2. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor MainWindow. XAML a vyberte možnost **Zobrazit kód**.  
  
3. <xref:System.Activities.Statements.Sequence> <xref:System.Activities.Presentation.Toolbox.ToolboxControl> <xref:System.Activities.Statements.Assign>Přidejte metodu do třídy, která vytvoří, přidá novou kategorii nástrojů do sady nástrojů a přiřadí k této kategorii typy aktivity a. `MainWindow` `GetToolboxControl`  
  
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
  
4. Přidejte soukromou `AddToolbox` metodu `MainWindow` do třídy, která umístí **sadu nástrojů** do levého sloupce v mřížce.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5. Přidejte volání `AddToolBox` metody `MainWindow()` v konstruktoru třídy, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6. Stisknutím klávesy F5 Sestavte a spusťte vaše řešení. Měla by se zobrazit <xref:System.Activities.Statements.Assign> **Sada nástrojů** obsahující aktivity a <xref:System.Activities.Statements.Sequence> .  
  
### <a name="to-create-the-propertygrid"></a>Vytvoření prvku PropertyGrid  
  
1. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor MainWindow. XAML a vyberte možnost **Zobrazit kód**.  
  
2. Přidejte do `MainWindow` třídy metodu pro umístění podokna PropertyGrid do sloupce vpravo v mřížce `AddPropertyInspector` .  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3. Přidejte volání `AddPropertyInspector` metody `MainWindow()` v konstruktoru třídy, jak je znázorněno v následujícím kódu.  
  
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
  
4. Stisknutím klávesy F5 Sestavte a spusťte řešení. Všechna okna **panelu nástrojů**, plátna návrhu pracovního postupu a podokna **PropertyGrid** by se měla zobrazit, a když <xref:System.Activities.Statements.Assign> přetáhnete <xref:System.Activities.Statements.Sequence> aktivitu nebo aktivitu na plátno návrhu, měla by se aktualizovat tabulka vlastností v závislosti na zvýrazněná aktivita.  
  
## <a name="example"></a>Příklad  
 Soubor MainWindow.xaml.cs by teď měl obsahovat následující kód.  
  
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
- [Úkol 2: Hostování Návrhář postupu provádění](task-2-host-the-workflow-designer.md)
