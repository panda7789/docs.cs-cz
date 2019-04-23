---
title: 'Úkol 2: Hostování Návrháře postupu provádění'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 3f7964e907fe513679e60c18292f07c84128590b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59299264"
---
# <a name="task-2-host-the-workflow-designer"></a>Úkol 2: Hostování Návrháře postupu provádění
Toto téma popisuje postup, pro který je hostitelem instance [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] v aplikaci Windows Presentation Foundation (WPF).  
  
 Postup konfiguruje **mřížky** ovládací prvek, který obsahuje Návrhář, prostřednictvím kódu programu vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner> , který obsahuje výchozí <xref:System.Activities.Statements.Sequence> aktivity, zaregistruje metadata návrháře k poskytování Podpora návrhářů pro všechny vestavěné aktivity a hostitele [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikace.  
  
### <a name="to-host-the-workflow-designer"></a>K hostování návrháře postupu provádění  
  
1. Otevřít HostingApplication projektu, kterou jste vytvořili v [úkol 1: Vytvoření nové aplikace Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).  
  
2. Úprava velikosti okna, které usnadňují použití [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Chcete-li to provést, vyberte **hlavního okna MainWindow** v návrháři, zobrazíte stisknutím klávesy F4 **vlastnosti** okna a v **rozložení** části existuje, nastavte **šířku** k hodnotě čítače 600 a **výška** na hodnotu 350.  
  
3. Nastavte název tabulky tak, že vyberete **mřížky** panelu v Návrháři (klikněte na pole uvnitř **hlavního okna MainWindow**) a nastavení **název** vlastnost v horní části  **Vlastnosti** okno "grid1".  
  
4. V **vlastnosti** okna, klikněte na tlačítko se třemi tečkami (**...** ) vedle položky `ColumnDefinitions` vlastnosti otevřít **Editor kolekce** dialogové okno.  
  
5. V **Editor kolekce** dialogové okno, klikněte na tlačítko **přidat** tlačítko třikrát pro vložení tři sloupce do požadovaného rozložení. První sloupec bude obsahovat **nástrojů**, druhý sloupec bude hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a třetí sloupec bude použit pro vlastnost inspector.  
  
6. Nastavte `Width` vlastnost v prostředním sloupci na hodnotu "4 *".  
  
7. Změny uložíte kliknutím na tlačítko **OK** . Do souboru MainWindow.xaml je přidána následující XAML:  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8. V **Průzkumníka řešení**, klikněte pravým tlačítkem na soubor MainWindow.xaml a vyberte **zobrazit kód**. Úprava kódu pomocí následujících kroků:  
  
    1.  Přidejte následující obory názvů:  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  Chcete-li deklarovat pole soukromý člen pro uložení instance <xref:System.Activities.Presentation.WorkflowDesigner>, přidejte následující kód, který `MainWindow` třídy.  
  
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
  
    3.  Přidejte následující `AddDesigner` metodu `MainWindow` třídy. Implementace vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner>, přidá <xref:System.Activities.Statements.Sequence> aktivitu a umístí ji v prostředním sloupci grid1 **mřížky**.  
  
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
  
    4.  Zaregistrujte metadata návrháře návrháře podporu pro všechny vestavěné aktivity. To umožňuje umístit aktivity z panelu nástrojů do původní <xref:System.Activities.Statements.Sequence> aktivity v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Chcete-li to provést, přidejte `RegisterMetadata` metodu `MainWindow` třídy.  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         Další informace o registraci návrháři aktivit najdete v tématu [jak: Vytvoření vlastního návrháře aktivit](how-to-create-a-custom-activity-designer.md).  
  
    5.  V `MainWindow` konstruktor třídy, přidejte volání metody deklarované dříve zaregistrovat metadata pro podporu návrháře a vytvořit <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
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
        >  `RegisterMetadata` Metoda registruje metadata návrháře integrovaných aktivit, včetně <xref:System.Activities.Statements.Sequence> aktivity. Protože `AddDesigner` metoda používá <xref:System.Activities.Statements.Sequence> aktivity, `RegisterMetadata` metoda musí být nejdříve volána.  
  
9. Stisknutím klávesy F5 sestavte a spusťte řešení.  
  
10. Zobrazit [úloha 3: Vytvořit panel nástrojů a podokna PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) Další informace o přidání **nástrojů** a **PropertyGrid** podporují do návrháře postupu provádění se změněným hostováním.  
  
## <a name="see-also"></a>Viz také:

- [Změna hostování Návrháře postupu provádění](rehosting-the-workflow-designer.md)
- [Úloha 1: Vytvoření nové aplikace Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Úloha 3: Vytvořit panel nástrojů a PropertyGrid podokna](task-3-create-the-toolbox-and-propertygrid-panes.md)
