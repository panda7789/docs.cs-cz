---
title: 'Úkol 2: hostování Návrhář postupu provádění'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8e4c17ed182cec7748b9a1f11f76ff90aa60c39e
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715779"
---
# <a name="task-2-host-the-workflow-designer"></a>Úkol 2: hostování Návrhář postupu provádění

Toto téma popisuje postup hostování instance Návrhář postupu provádění systému Windows v aplikaci Windows Presentation Foundation (WPF).

Procedura nakonfiguruje ovládací prvek **mřížky** , který obsahuje návrháře, programově vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner>, která obsahuje výchozí aktivitu <xref:System.Activities.Statements.Sequence>, zaregistruje metadata návrháře, aby poskytovala podporu návrháře pro všechny integrované aktivity a hostuje Návrhář postupu provádění v aplikaci WPF.

## <a name="to-host-the-workflow-designer"></a>Hostování návrháře pracovních postupů

1. Otevřete projekt HostingApplication, který jste vytvořili v [úloze 1: Vytvořte novou Windows Presentation Foundation aplikaci](task-1-create-a-new-wpf-app.md).

2. Upravte velikost okna tak, aby bylo snazší používat Návrhář postupu provádění. Provedete to tak, že v Návrháři vyberete **MainWindow** a stisknutím klávesy F4 zobrazíte okno **vlastnosti** , v části **rozložení** nastavíte **šířku** na hodnotu 600 a **výšku** na hodnotu 350.

3. Nastavte název mřížky výběrem panelu **mřížky** v Návrháři (klikněte na pole uvnitř **MainWindow**) a nastavte vlastnost **název** v horní části okna **vlastností** na hodnotu "grid1".

4. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami ( **...** ) vedle vlastnosti `ColumnDefinitions`. tím otevřete dialogové okno **Editor kolekcí** .

5. V dialogovém okně **Editor kolekce** klikněte třikrát na tlačítko **Přidat** a vložte do rozložení tři sloupce. První sloupec bude obsahovat **sadu nástrojů**, druhý sloupec bude hostovat Návrhář postupu provádění a třetí sloupec bude použit pro inspektora vlastností.

6. Nastavte vlastnost `Width` prostředního sloupce na hodnotu "4 *".

7. Změny uložíte kliknutím na tlačítko **OK** . Do souboru *MainWindow. XAML* je přidán následující kód XAML:

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. V **Průzkumník řešení**klikněte pravým tlačítkem na *MainWindow. XAML* a vyberte **Zobrazit kód**. Upravte kód pomocí následujících kroků:

    1. Přidejte následující obory názvů:

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. Chcete-li deklarovat pole private member pro uložení instance <xref:System.Activities.Presentation.WorkflowDesigner>, přidejte následující kód do třídy `MainWindow`:

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

    3. Do `MainWindow` třídy přidejte následující metodu `AddDesigner`. Implementace vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner>, přidá do ní aktivitu <xref:System.Activities.Statements.Sequence> a umístí ji do prostřední sloupec grid1 **mřížky**.

        ```csharp
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
        ```

    4. Zaregistrujte metadata návrháře pro přidání podpory návrháře pro všechny předdefinované aktivity. To umožňuje vyřadit aktivity z panelu nástrojů na původní aktivitu <xref:System.Activities.Statements.Sequence> v Návrhář postupu provádění. Chcete-li to provést, přidejte metodu `RegisterMetadata` do `MainWindow` třídy:

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Další informace o registraci návrháře aktivit najdete v tématu [Postupy: Vytvoření vlastního návrháře aktivit](how-to-create-a-custom-activity-designer.md).

    5. V konstruktoru třídy `MainWindow` přidejte volání metod deklarovaných dříve pro registraci metadat pro podporu návrháře a vytvoření <xref:System.Activities.Presentation.WorkflowDesigner>.

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > Metoda `RegisterMetadata` zaregistruje metadata návrháře předdefinovaných aktivit, včetně aktivity <xref:System.Activities.Statements.Sequence>. Vzhledem k tomu, že metoda `AddDesigner` používá aktivitu <xref:System.Activities.Statements.Sequence>, musí být nejprve volána metoda `RegisterMetadata`.

9. Stisknutím klávesy <kbd>F5</kbd> Sestavte a spusťte řešení.

10. Viz [úloha 3: vytvoření podoken panelu nástrojů a PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) , kde se dozvíte, jak přidat podporu **nástrojů** a podpora aplikace **PropertyGrid** k vašemu Návrháři pracovního postupu, který je hostitelem.

## <a name="see-also"></a>Viz také:

- [Změna hostování Návrháře postupu provádění](rehosting-the-workflow-designer.md)
- [Úkol 1: Vytvoření nové aplikace Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Úkol 3: Vytvoření podoken pro sady nástrojů a mřížku vlastností](task-3-create-the-toolbox-and-propertygrid-panes.md)
