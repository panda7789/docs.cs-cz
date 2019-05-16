---
title: 'Návod: Zobrazení dat z databáze SQL Serveru v ovládacím prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: 30f3123a70e414e80842f726584623534994ab95
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645662"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Návod: Zobrazení dat z databáze systému SQL Server v ovládacím prvku DataGrid

V tomto podrobném návodu, načtení dat z databáze SQL serveru a zobrazit tato data v <xref:System.Windows.Controls.DataGrid> ovládacího prvku. Použijete k vytvoření tříd entit, které představují data a zprostředkovatel LINQ slouží pro napsat dotaz, který načte zadaná data z entity třídy rozhraní ADO.NET Entity Framework.

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio.

- Přístup ke spuštěné instanci systému SQL Server nebo SQL Server Express, která obsahuje ukázkovou databázi AdventureWorks, který se k němu připojená. Můžete stáhnout z databáze AdventureWorks [Githubu](https://github.com/Microsoft/sql-server-samples/releases).

## <a name="create-entity-classes"></a>Vytvoření tříd entit

1. Vytvoření nového projektu aplikace WPF v jazyce Visual Basic nebo C# a pojmenujte ho `DataGridSQLExample`.

2. V Průzkumníku řešení klikněte pravým tlačítkem na projekt, přejděte na **přidat**a pak vyberte **nová položka**.

     Zobrazí se dialogové okno Přidat novou položku.

3. V podokně nainstalované šablony vyberte **Data** a v seznamu šablon vyberte **datový Model Entity ADO.NET**.

     ![Šablona položky modelu Entity Data Model ADO.NET](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. Název souboru `AdventureWorksModel.edmx` a potom klikněte na tlačítko **přidat**.

     Zobrazí se Průvodce modelem Entity Data Model.

5. Na obrazovce výběr obsahu modelu vyberte **EF designeru z databáze** a potom klikněte na tlačítko **Další**.

6. V dialogovém okně vyberte datové připojení slouží k navázání připojení k databázi AdventureWorksLT2008. Další informace najdete v tématu [zvolte si Data Connection Dialog Box](https://go.microsoft.com/fwlink/?LinkId=160190).

    Ujistěte se, zda je název `AdventureWorksLT2008Entities` a že **uložit nastavení připojení v souboru App.Config jako entity** zaškrtávací políčko zaškrtnuto a pak klikněte na **Další**.

7. Na obrazovce Zvolte vaše databázové objekty, rozbalte uzel tabulky a vyberte **produktu** a **ProductCategory** tabulky.

     Můžete generovat třídy entity pro všechny tabulky; ale v tomto příkladu pouze načítáte data z těchto dvou tabulkách.

     ![Vyberte z tabulek Product a ProductCategory](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. Klikněte na tlačítko **Dokončit**.

     Product a ProductCategory entity se zobrazí v návrháři entit.

     ![Modely entity Product a ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>Načtení a zobrazení dat

1. Otevřete soubor MainWindow.xaml.

2. Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost <xref:System.Windows.Window> na 450.

3. V editoru XAML, přidejte následující <xref:System.Windows.Controls.DataGrid> označit mezi `<Grid>` a `</Grid>` značky se mají přidat <xref:System.Windows.Controls.DataGrid> s názvem `dataGrid1`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![Window with DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. Vyberte <xref:System.Windows.Window>.

5. Pomocí okna vlastnosti nebo editoru XAML, vytvořit obslužnou rutinu události pro <xref:System.Windows.Window> s názvem `Window_Loaded` pro <xref:System.Windows.FrameworkElement.Loaded> událostí. Další informace najdete v tématu [jak: Vytvořte obslužnou rutinu události jednoduché](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

     Následuje ukázka XAML souboru mainwindow.XAML.

    > [!NOTE]
    > Pokud používáte Visual Basic v prvním řádku souboru mainwindow.XAML, nahraďte `x:Class="DataGridSQLExample.MainWindow"` s `x:Class="MainWindow"`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. Otevřete soubor kódu na pozadí (soubor MainWindow.xaml.vb nebo MainWindow.xaml.cs) pro <xref:System.Windows.Window>.

7. Přidejte následující kód k načtení jenom konkrétní hodnoty z spojené tabulky a nastavit <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.DataGrid> do výsledků dotazu.

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. Spustíte v příkladu.

     Měli byste vidět <xref:System.Windows.Controls.DataGrid> , která zobrazí data.

     ![DataGrid – s daty z databáze SQL](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataGrid>
- [Postup: Začínáme s Entity Framework v aplikacích WPF?](https://go.microsoft.com/fwlink/?LinkId=159868)
