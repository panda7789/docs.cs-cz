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
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Úkol 3: vytvoření podoken nástrojů a PropertyGrid

V této úloze vytvoříte podokna **nástrojů** a **PropertyGrid** a přidáte je do [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].

Pro referenci, kód, který by měl být v souboru MainWindow.xaml.cs po dokončení tří úloh při opětovném [hostování Návrhář postupu provádění](rehosting-the-workflow-designer.md) řady témat, je k dispozici na konci tohoto tématu.

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Chcete-li vytvořit sadu nástrojů a přidat ji do mřížky

1. Otevřete projekt HostingApplication, který jste získali pomocí postupu popsaného v části [Úloha 2: hostování Návrhář postupu provádění](task-2-host-the-workflow-designer.md).

2. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor *MainWindow. XAML* a vyberte možnost **Zobrazit kód**.

3. Přidejte metodu `GetToolboxControl` do třídy `MainWindow`, která vytvoří <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, přidá novou kategorii **nástrojů** do **sady nástrojů**a přiřadí do této kategorie typy aktivit <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence>.

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

4. Přidejte metodu Private `AddToolbox` do třídy `MainWindow`, která umístí **sadu nástrojů** do levého sloupce v mřížce.

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. Přidejte volání metody `AddToolBox` v konstruktoru třídy `MainWindow()`, jak je znázorněno v následujícím kódu:

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte vaše řešení. Měla by se zobrazit **Sada nástrojů** obsahující aktivity <xref:System.Activities.Statements.Assign> a <xref:System.Activities.Statements.Sequence>.

## <a name="to-create-the-propertygrid"></a>Vytvoření prvku PropertyGrid

1. V podokně **Průzkumník řešení** klikněte pravým tlačítkem myši na soubor *MainWindow. XAML* a vyberte možnost **Zobrazit kód**.

2. Přidejte do třídy `MainWindow` metodu `AddPropertyInspector` k umístění podokna **PropertyGrid** do sloupce v mřížce vpravo:

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. Přidejte volání metody `AddPropertyInspector` v konstruktoru třídy `MainWindow()`, jak je znázorněno v následujícím kódu:

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

4. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte řešení. Všechna okna **panelu nástrojů**, plátna návrhu pracovního postupu a podokna **PropertyGrid** by se měla zobrazit, a když přetáhnete aktivitu <xref:System.Activities.Statements.Assign> nebo aktivitu <xref:System.Activities.Statements.Sequence> na plátno návrhu, měla by se v závislosti na zvýrazněné aktivitě aktualizovat Mřížka vlastností.

## <a name="example"></a>Příklad:

Soubor *MainWindow.XAML.cs* by teď měl obsahovat následující kód:

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

## <a name="see-also"></a>Další informace najdete v tématech

- [Opětovné hostování Návrhář postupu provádění](rehosting-the-workflow-designer.md)
- [Úloha 1: vytvoření nové aplikace Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Úkol 2: hostování Návrhář postupu provádění](task-2-host-the-workflow-designer.md)
