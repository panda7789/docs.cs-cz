---
title: "Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], displaying data from SQL Server
- controls [WPF], DataGrid
ms.assetid: 6810b048-0a23-4f86-bfa5-97f92b3cfab4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3c8ed596706c8d656842191262c25301db595ee3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control"></a>Návod: Zobrazení dat z databáze serveru SQL Server v ovládacím prvku DataGrid
V tomto návodu načtení dat z databáze serveru SQL a zobrazit tato data v <xref:System.Windows.Controls.DataGrid> ovládacího prvku. Použijete k vytvoření tříd entit, které představují data a pomocí LINQ vytvořit dotaz, který načte zadaná data z třídu entity ADO.NET Entity Framework.  
  
## <a name="prerequisites"></a>Požadavky  
 K dokončení tohoto návodu budete potřebovat následující komponenty:  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)].  
  
-   Přístup k spuštěnou instanci systému SQL Server nebo SQL Server Express, která obsahuje ukázkovou databázi AdventureWorks k němu připojen. Si můžete stáhnout databázi AdventureWorks z [Githubu](https://github.com/Microsoft/sql-server-samples/releases).  
  
### <a name="to-create-entity-classes"></a>Chcete-li vytvořit tříd entit  
  
1.  Vytvořte nový projekt aplikace WPF v jazyce Visual Basic nebo C# a pojmenujte ji `DataGridSQLExample`.  
  
2.  V Průzkumníku řešení klikněte pravým tlačítkem na projekt, přejděte na **přidat**a potom vyberte **novou položku**.  
  
     Zobrazí se dialogové okno Přidat novou položku.  
  
3.  V podokně nainstalovaných šablonách vyberte **Data** a v seznamu šablon, vyberte **ADO.NET Entity Data režimu**l.  
  
     ![Vyberte model ADO.NET Entity Data Model](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step1.png "DataGrid_SQL_EF_Step1")  
  
4.  Název souboru `AdventureWorksModel.edmx` a pak klikněte na **přidat**.  
  
     Zobrazí se Průvodce modelem Entity Data Model.  
  
5.  V dialogovém okně Zvolte obsah modelu vyberte **generování z databáze** a pak klikněte na **Další**.  
  
     ![Vyberte možnost databáze generování](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step2.png "DataGrid_SQL_EF_Step2")  
  
6.  V dialogovém okně Vybrat datové připojení slouží k navázání připojení k vaší databázi AdventureWorksLT2008. Další informace najdete v tématu [zvolte vaše Data dialogové okno připojení](http://go.microsoft.com/fwlink/?LinkId=160190).  
  
     ![Zadejte připojení k databázi](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step3.png "DataGrid_SQL_EF_Step3")  
  
7.  Ujistěte se, zda je název `AdventureWorksLT2008Entities` a že **uložit nastavení připojení entity v souboru App.Config jako** zaškrtávací políčko je vybraná a pak klikněte na tlačítko **Další**.  
  
8.  V dialogovém okně zvolte si databázové objekty, rozbalte uzel tabulky a vyberte **produktu** a **ProductCategory** tabulky.  
  
     Můžete vygenerovat třídy entity pro všechny tabulky; ale v tomto příkladu pouze data načítat z těchto dvou tabulek.  
  
     ![Vyberte produktu a ProductCategory z tabulek](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step4.png "DataGrid_SQL_EF_Step4")  
  
9. Klikněte na tlačítko **Dokončit**.  
  
     Entity produktu a ProductCategory jsou zobrazeny v Entity designeru.  
  
     ![Modely entity produktu a ProductCategory](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step5.png "DataGrid_SQL_EF_Step5")  
  
### <a name="to-retrieve-and-present-the-data"></a>Načtení a prezentovat data  
  
1.  Otevřete soubor MainWindow.xaml.  
  
2.  Nastavte <xref:System.Windows.FrameworkElement.Width%2A> vlastnost <xref:System.Windows.Window> na 450.  
  
3.  V editoru XAML, přidejte následující <xref:System.Windows.Controls.DataGrid> značky mezi `<Grid>` a `</Grid>` značky se mají přidat <xref:System.Windows.Controls.DataGrid> s názvem `dataGrid1`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#3)]  
  
     ![Okno s DataGrid](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step6.png "DataGrid_SQL_EF_Step6")  
  
4.  Vyberte <xref:System.Windows.Window>.  
  
5.  Pomocí vlastnosti – okno nebo editoru XAML, vytvořte obslužnou rutinu události pro <xref:System.Windows.Window> s názvem `Window_Loaded` pro <xref:System.Windows.FrameworkElement.Loaded> událostí. Další informace najdete v tématu [postupy: vytvoření jednoduché obslužné rutiny události](http://msdn.microsoft.com/en-us/b1456e07-9dec-4354-99cf-18666b64f480).  
  
     Následující ukazuje XAML pro MainWindow.xaml.  
  
    > [!NOTE]
    >  Pokud používáte Visual Basic, v prvním řádku MainWindow.xaml, nahraďte `x:Class="DataGridSQLExample.MainWindow"` s `x:Class="MainWindow"`.  
  
     [!code-xaml[DataGrid_SQL_EF_Walkthrough#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml#1)]  
  
6.  Pro otevření souboru kódu na pozadí (MainWindow.xaml.vb nebo MainWindow.xaml.cs) <xref:System.Windows.Window>.  
  
7.  Přidejte následující kód k načtení jenom konkrétní hodnoty z spojené tabulky a nastavení <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost <xref:System.Windows.Controls.DataGrid> do výsledků dotazu.  
  
     [!code-csharp[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/CS/MainWindow.xaml.cs#2)]
     [!code-vb[DataGrid_SQL_EF_Walkthrough#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_SQL_EF_Walkthrough/VB/MainWindow.xaml.vb#2)]  
  
8.  Spusťte v příkladu.  
  
     Měli byste vidět <xref:System.Windows.Controls.DataGrid> , zobrazí data.  
  
     ![DataGrid – s daty z databáze SQL](../../../../docs/framework/wpf/controls/media/datagrid-sql-ef-step7.png "DataGrid_SQL_EF_Step7")  
  
## <a name="next-steps"></a>Další kroky  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DataGrid>  
 [Jak I: začít pracovat s platformou Entity Framework v aplikacích WPF?](http://go.microsoft.com/fwlink/?LinkId=159868)
