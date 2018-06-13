---
title: 'Úloha 2: Hostování návrháře pracovních postupů'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8ac6b3590d146909c1cb9fd8cf9cae2352b0155b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519061"
---
# <a name="task-2-host-the-workflow-designer"></a>Úloha 2: Hostování návrháře pracovních postupů
Toto téma popisuje postup pro hostování instanci [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] v aplikaci Windows Presentation Foundation (WPF).  
  
 Postup konfiguruje **mřížky** ovládací prvek, který obsahuje návrháře, prostřednictvím kódu programu vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner> obsahující výchozí <xref:System.Activities.Statements.Sequence> aktivity, zaregistruje návrháře metadata zajistit Podpora návrháře pro všechny zabudované aktivity a hostitelé [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] v [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] aplikace.  
  
### <a name="to-host-the-workflow-designer"></a>K hostování návrháře pracovních postupů  
  
1.  Otevřete HostingApplication projektu, kterou jste vytvořili v [úloha 1: Vytvořte novou aplikaci Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md).  
  
2.  Upravit velikost okna, aby bylo snazší používat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Chcete-li to provést, vyberte **MainWindow** v návrháři, zobrazte stisknutím klávesy F4 **vlastnosti** okno a v **rozložení** části existuje, nastavte **šířka** na hodnotu 600 a **výška** na hodnotu 350.  
  
3.  Název mřížky nastavit tak, že vyberete **mřížky** panelu v Návrháři (klikněte na pole uvnitř **MainWindow**) a nastavení **název** vlastnost v horní části  **Vlastnosti** okno "grid1".  
  
4.  V **vlastnosti** okně klikněte na tlačítko se třemi tečkami (**...** ) vedle položky `ColumnDefinitions` vlastnost otevřete **Editor kolekce** dialogové okno.  
  
5.  V **Editor kolekce** dialogové okno, klikněte **přidat** tlačítko třikrát na tři sloupce k vložení do rozložení. První sloupec bude obsahovat **sada nástrojů**, druhý sloupec bude hostovat [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], a třetí sloupec se použije pro vlastnost inspector.  
  
6.  Nastavte `Width` vlastnost střední sloupce na hodnotu "4 *".  
  
7.  Klikněte na tlačítko **OK** a uložte změny. Následující XAML se přidá do souboru MainWindow.xaml:  
  
    ```xml  
    <Grid Name="grid1">  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition />  
            <ColumnDefinition Width="4*" />  
            <ColumnDefinition />  
        </Grid.ColumnDefinitions>  
    </Grid>  
    ```  
  
8.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na MainWindow.xaml a vyberte **kód zobrazení**. Upravte kód pomocí následujících kroků:  
  
    1.  Přidání následujících oborů názvů:  
  
        ```csharp  
        using System.Activities;  
        using System.Activities.Core.Presentation;  
        using System.Activities.Presentation;  
        using System.Activities.Presentation.Metadata;  
        using System.Activities.Presentation.Toolbox;  
        using System.Activities.Statements;  
        using System.ComponentModel;  
        ```  
  
    2.  Deklarovat privátního člena pole pro uložení instance <xref:System.Activities.Presentation.WorkflowDesigner>, přidejte následující kód, který `MainWindow` – třída.  
  
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
  
    3.  Přidejte následující `AddDesigner` metodu `MainWindow` třídy. Implementace vytvoří instanci <xref:System.Activities.Presentation.WorkflowDesigner>, přidá <xref:System.Activities.Statements.Sequence> aktivitu a umístí jej v prostředním sloupci grid1 **mřížky**.  
  
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
  
    4.  Zaregistrujte návrháře metadata o návrháře podporu zabudované aktivity. To umožňuje vyřadit aktivity z panelu nástrojů na původní <xref:System.Activities.Statements.Sequence> aktivity v [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Chcete-li to provést, přidejte `RegisterMetadata` metodu `MainWindow` – třída.  
  
        ```csharp  
        private void RegisterMetadata()  
        {               
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
        ```  
  
         Další informace o registraci návrháře aktivit najdete v tématu [postupy: vytvoření Návrháře vlastních aktivit](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-activity-designer.md).  
  
    5.  V `MainWindow` konstruktoru třídy, přidejte volání metody dříve deklarované registrujete metadata pro návrháře podporu a vytvářet <xref:System.Activities.Presentation.WorkflowDesigner>.  
  
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
        >  `RegisterMetadata` Metoda registruje návrháře metadata integrovaných aktivit, včetně <xref:System.Activities.Statements.Sequence> aktivity. Protože `AddDesigner` metoda používá <xref:System.Activities.Statements.Sequence> aktivity, `RegisterMetadata` metoda musí být volána nejprve.  
  
9. Stisknutím klávesy F5 sestavení a spuštění řešení.  
  
10. V tématu [úloha 3: vytvoření sady nástrojů a PropertyGrid podokna](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md) se dozvíte, jak přidat **sada nástrojů** a **PropertyGrid** podporu do vaší opětovné hostování nástroje pracovního postupu návrháře.  
  
## <a name="see-also"></a>Viz také  
 [Změna hostování Návrháře postupu provádění](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [Úkol 1: Vytvoření nové aplikace Windows Presentation Foundation](../../../docs/framework/windows-workflow-foundation/task-1-create-a-new-wpf-app.md)  
 [Úkol 3: Vytvoření podoken pro sady nástrojů a mřížku vlastností](../../../docs/framework/windows-workflow-foundation/task-3-create-the-toolbox-and-propertygrid-panes.md)
