---
title: Vázání dat k ovládacímu prvku DataGridView
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: e2762bf363a469abf8c1e57b851d351c1cb41b62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745073"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Postupy: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms

Ovládací prvek <xref:System.Windows.Forms.DataGridView> podporuje model datové vazby Standard model Windows Forms, takže se může svázat s nejrůznějšími zdroji dat. Obvykle se vytváří vazba na <xref:System.Windows.Forms.BindingSource>, která spravuje interakci se zdrojem dat. <xref:System.Windows.Forms.BindingSource> může být jakýkoli model Windows Forms zdroj dat, který poskytuje skvělou flexibilitu při volbě nebo úpravě umístění vašich dat. Další informace o zdrojích dat, které podporuje ovládací prvek <xref:System.Windows.Forms.DataGridView>, naleznete v tématu [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio má rozsáhlou podporu pro datové vazby k ovládacímu prvku DataGridView. Další informace najdete v tématu [Postup: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms pomocí návrháře](bind-data-to-the-datagrid-using-the-designer.md).  

Připojení ovládacího prvku DataGridView k datům:

1. Implementujte metodu pro zpracování podrobností o načítání dat. Následující příklad kódu implementuje `GetData` metodu, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter>a používá ho k naplnění <xref:System.Data.DataTable>. Potom vytvoří vazby <xref:System.Data.DataTable> k <xref:System.Windows.Forms.BindingSource>. 

2. V obslužné rutině události <xref:System.Windows.Forms.Form.Load> formuláře navažte ovládací prvek <xref:System.Windows.Forms.DataGridView> na <xref:System.Windows.Forms.BindingSource>a zavolejte metodu `GetData` pro načtení dat.  

## <a name="example"></a>Příklad

Tento úplný příklad kódu načte data z databáze k naplnění ovládacího prvku DataGridView ve formuláři Windows. Formulář obsahuje také tlačítka pro opětovné načtení dat a odeslání změn do databáze.  

Tento příklad vyžaduje: 

- Přístup k ukázkové databázi Northwind SQL Server. Další informace o instalaci ukázkové databáze Northwind najdete v tématu [získání ukázkových databází pro ukázky kódu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Odkazy na sestavení System, System. Windows. Forms, System. data a System. XML.  

Chcete-li sestavit a spustit tento příklad, vložte kód do souboru kódu *Form1* v novém model Windows Forms projektu. Informace o sestavování z C# příkazového řádku nebo Visual Basic naleznete v tématu [sestavování z příkazového řádku pomocí CSc. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Naplňte `connectionString` proměnnou v příkladu hodnotami pro vaše ukázkové připojení databáze Northwind SQL Server. Ověřování systému Windows, označované také jako integrované zabezpečení, je bezpečnější způsob, jak se připojit k databázi, než ukládat heslo v připojovacím řetězci. Další informace o zabezpečení připojení najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Zobrazení dat v ovládacím prvku DataGridView model Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Chránit informace o připojení](../../data/adonet/protecting-connection-information.md)
