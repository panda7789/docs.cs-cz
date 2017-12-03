---
title: "Úloha 3: Vytvoření sady nástrojů a PropertyGrid podokna"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cfb1d09fc8bc52a03576054197488dff0aacf841
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Úloha 3: Vytvoření sady nástrojů a PropertyGrid podokna
V této úloze se vytvoří **sada nástrojů** a **PropertyGrid** podokna a přidat je do opětovné hostování nástroje [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Pro odkaz, kód, který by měl být v souboru MainWindow.xaml.cs po dokončení tří úloh v [opětovného hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md) řady témat je k dispozici na konci tohoto tématu.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Vytvoření sady nástrojů a přidejte ho k mřížce.  
  
1.  Otevřete projekt HostingApplication jste získali podle postupu popsaného v [úloha 2: hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md).  
  
2.  V **Průzkumníku řešení** podokně klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **kód zobrazení**.  
  
3.  Přidat `GetToolboxControl` metodu `MainWindow` třídu, která vytvoří <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, přidá nový **sada nástrojů** kategorii, která se **sada nástrojů**a přiřadí <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence> typy aktivit do této kategorie spadají.  
  
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
  
4.  Přidat privátního `AddToolbox` metodu `MainWindow` třídu, která umístí **sada nástrojů** v levém sloupci v mřížce.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5.  Přidejte volání `AddToolBox` metoda v `MainWindow()` konstruktoru třídy, jak je znázorněno v následujícím kódu.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6.  Stisknutím klávesy F5 sestavení a spuštění řešení. **Sada nástrojů** obsahující <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence> aktivity mají být zobrazeny.  
  
### <a name="to-create-the-propertygrid"></a>Vytvoření ovládacího prvku PropertyGrid  
  
1.  V **Průzkumníku řešení** podokně klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **kód zobrazení**.  
  
2.  Přidat `AddPropertyInspector` metodu `MainWindow` třída umístit **PropertyGrid** podokně ve sloupci úplně vpravo v mřížce.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3.  Přidejte volání `AddPropertyInspector` metoda v `MainWindow()` konstruktoru třídy, jak je znázorněno v následujícím kódu.  
  
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
  
4.  Stisknutím klávesy F5 sestavení a spuštění řešení. **Sada nástrojů**, plátno návrhu pracovního postupu, a **PropertyGrid** podokna by měly být zobrazeny všechny a při přetažení <xref:System.Activities.Statements.Assign> aktivity nebo <xref:System.Activities.Statements.Sequence> aktivity na plátno návrhu v závislosti na zvýrazněné aktivity by měl aktualizovat mřížkou vlastností.  
  
## <a name="example"></a>Příklad  
 Soubor MainWindow.xaml.cs teď by měla obsahovat následující kód.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Opětovného hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Úloha 2: Hostování návrháře pracovních postupů](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
