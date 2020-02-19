---
title: 'Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
ms.openlocfilehash: fc8b35c89e76a415529d76db687bc96767384e11
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452120"
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Návod: zobrazení dat z databáze SQL Server v ovládacím prvku DataGrid

V tomto návodu načtete data z databáze SQL Server a tato data zobrazíte v ovládacím prvku <xref:System.Windows.Controls.DataGrid>. Použijte Entity Framework ADO.NET k vytvoření tříd entit, které reprezentují data, a použijte LINQ k zápisu dotazu, který načte zadaná data z třídy entity.

## <a name="prerequisites"></a>Předpoklady

K dokončení tohoto návodu budete potřebovat následující komponenty:

- Visual Studio.

- Přístup ke spuštěné instanci SQL Server nebo SQL Server Express s připojenou ukázkovou databází AdventureWorks. Databázi AdventureWorks si můžete stáhnout z [GitHubu](https://github.com/Microsoft/sql-server-samples/releases).

## <a name="create-entity-classes"></a>Vytváření tříd entit

1. Vytvořte nový projekt aplikace WPF v Visual Basic nebo C#a pojmenujte ho `DataGridSQLExample`.

2. V Průzkumník řešení klikněte pravým tlačítkem myši na projekt, přejděte na **Přidat**a pak vyberte **Nová položka**.

     Zobrazí se dialogové okno Přidat novou položku.

3. V podokně nainstalované šablony vyberte **data** a v seznamu šablon vyberte **ADO.NET model EDM (Entity Data Model)** .

     ![Šablona položky model EDM (Entity Data Model) ADO.NET](../../wcf/feature-details/./media/ado-net-entity-data-model-item-template.png)

4. Pojmenujte soubor `AdventureWorksModel.edmx` a pak klikněte na tlačítko **Přidat**.

     Zobrazí se Průvodce modelem Entity Data Model.

5. Na obrazovce zvolit obsah modelu vyberte **z databáze EF Designer** a pak klikněte na **Další**.

6. Na obrazovce vybrat datové připojení zadejte připojení k databázi AdventureWorksLT2008. Další informace najdete v [dialogovém okně Výběr datového připojení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399244(v=vs.100)).

    Ujistěte se, že je název `AdventureWorksLT2008Entities` a že je zaškrtnuto políčko **Uložit nastavení připojení entity do souboru App. config** , a potom klikněte na tlačítko **Další**.

7. Na obrazovce zvolte vaše databázové objekty rozbalte uzel tabulky a vyberte tabulky **produkt** a **ProductCategory** .

     Třídy entit můžete vygenerovat pro všechny tabulky. v tomto příkladu se ale načítají jenom data z těchto dvou tabulek.

     ![Výběr produktu a ProductCategory z tabulek](./media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")

8. Klikněte na **Finish** (Dokončit).

     Entity produkt a ProductCategory se zobrazí v Entity Designer.

     ![Modely entit produktů a ProductCategory](./media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")

## <a name="retrieve-and-present-the-data"></a>Načtení a prezentace dat

1. Otevřete soubor MainWindow. XAML.

2. Nastavte vlastnost <xref:System.Windows.FrameworkElement.Width%2A> v <xref:System.Windows.Window> na 450.

3. V editoru XAML přidejte následující značku <xref:System.Windows.Controls.DataGrid> mezi značky `<Grid>` a `</Grid>` a přidejte <xref:System.Windows.Controls.DataGrid> s názvem `dataGrid1`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]

     ![Okno s ovládacím panelem DataGrid](./media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")

4. Vyberte <xref:System.Windows.Window>.

5. Pomocí editoru okno Vlastnosti nebo XAML vytvořte obslužnou rutinu události pro <xref:System.Windows.Window> s názvem `Window_Loaded` pro událost <xref:System.Windows.FrameworkElement.Loaded>. Další informace najdete v tématu [Postup: Vytvoření jednoduché obslužné rutiny události](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb675300(v=vs.100)).

     Následující příklad ukazuje XAML pro MainWindow. XAML.

    > [!NOTE]
    > Pokud používáte Visual Basic, v prvním řádku MainWindow. xaml nahraďte `x:Class="DataGridSQLExample.MainWindow"` `x:Class="MainWindow"`.

     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]

6. Otevřete soubor kódu na pozadí (MainWindow. XAML. vb nebo MainWindow.xaml.cs) pro <xref:System.Windows.Window>.

7. Přidejte následující kód, který načte pouze konkrétní hodnoty z připojených tabulek a nastaví vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.DataGrid> na výsledky dotazu.

     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]

8. Spusťte příklad.

     Měl by se zobrazit <xref:System.Windows.Controls.DataGrid> zobrazující data.

     ![Datová mřížka s daty z SQL Database](./media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.DataGrid>
