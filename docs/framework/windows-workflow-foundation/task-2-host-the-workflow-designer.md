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
# <a name="task-2-host-the-workflow-designer"></a>Úkol 2: Hostování Návrháře postupu provádění

Toto téma popisuje postup hostování instance [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] v aplikaci Windows Presentation Foundation (WPF).

Procedura nakonfiguruje ovládací prvek **mřížky** , který obsahuje návrháře, programově vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner> , která obsahuje výchozí <xref:System.Activities.Statements.Sequence> aktivitu, zaregistruje metadata návrháře pro zajištění podpory návrháře pro všechny vestavěné aktivity a hostují [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v aplikaci WPF.

### <a name="to-host-the-workflow-designer"></a>Hostování návrháře pracovních postupů

1. Otevřete projekt HostingApplication, který jste vytvořili [v úloze 1: Vytvořte novou Windows Presentation Foundation aplikaci](task-1-create-a-new-wpf-app.md).

2. Upravte velikost okna tak, aby bylo snazší používat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Provedete to tak, že v Návrháři vyberete **MainWindow** a stisknutím klávesy F4 zobrazíte okno **vlastnosti** , v části **rozložení** nastavíte **šířku** na hodnotu 600 a **výšku** na hodnotu 350.

3. Nastavte název mřížky výběrem panelu **mřížky** v Návrháři (klikněte na pole uvnitř **MainWindow**) a nastavte vlastnost **název** v horní části okna **vlastností** na hodnotu "grid1".

4. V okně **vlastnosti** klikněte na tlačítko se třemi tečkami ( **...** ) `ColumnDefinitions` vedle vlastnosti. tím otevřete dialogové okno **Editor kolekcí** .

5. V dialogovém okně **Editor kolekce** klikněte třikrát na tlačítko **Přidat** a vložte do rozložení tři sloupce. První sloupec bude obsahovat **sadu nástrojů**, druhý sloupec bude hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]a třetí sloupec bude použit pro inspektora vlastností.

6. `Width` Nastavte vlastnost prostřední sloupec na hodnotu "4 *".

7. Změny uložíte kliknutím na tlačítko **OK** . Do souboru MainWindow. XAML je přidán následující kód XAML:

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. V **Průzkumník řešení**klikněte pravým tlačítkem na MainWindow. XAML a vyberte **Zobrazit kód**. Upravte kód pomocí následujících kroků:

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

    2. Chcete-li deklarovat pole private member pro uložení instance <xref:System.Activities.Presentation.WorkflowDesigner>, přidejte `MainWindow` do třídy následující kód.

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

    3. Do třídy přidejte `AddDesigner`následujícímetodu `MainWindow` . Implementace vytvoří instanci instance <xref:System.Activities.Presentation.WorkflowDesigner>, <xref:System.Activities.Statements.Sequence> přidá do ní aktivitu a umístí ji do prostřední sloupec grid1 **mřížky**.

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

    4. Zaregistrujte metadata návrháře pro přidání podpory návrháře pro všechny předdefinované aktivity. To umožňuje vyřadit aktivity z panelu nástrojů na původní <xref:System.Activities.Statements.Sequence> aktivitu [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]v. Chcete-li to provést, `RegisterMetadata` přidejte metodu `MainWindow` do třídy.

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Další informace o registraci návrháře aktivit najdete v tématu [How to: Vytvořte vlastního návrháře](how-to-create-a-custom-activity-designer.md)aktivit.

    5. V konstruktoru <xref:System.Activities.Presentation.WorkflowDesigner>třídy přidejte volání metod deklarovaných dříve pro registraci metadat pro podporu návrháře a vytvoření. `MainWindow`

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
        > Metoda zaregistruje metadata návrháře vestavěných aktivit, <xref:System.Activities.Statements.Sequence> včetně aktivity. `RegisterMetadata` Vzhledem k tomu, že <xref:System.Activities.Statements.Sequence> `RegisterMetadata`Metodapoužívá aktivitu, musí být metoda volána jako první. `AddDesigner`

9. Stisknutím klávesy F5 Sestavte a spusťte řešení.

10. Viz [úloha 3: Vytvořte podokno nástrojů a podokna](task-3-create-the-toolbox-and-propertygrid-panes.md) PropertyGrid, abyste se seznámili s tím, jak přidat do návrháře pracovního postupu, který je hostitelem, a podpora **PropertyGrid** .

## <a name="see-also"></a>Viz také:

- [Změna hostování Návrháře postupu provádění](rehosting-the-workflow-designer.md)
- [Úloha 1: Vytvoření nové aplikace Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Úloha 3: Vytvoření podoken nástrojů a PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md)
