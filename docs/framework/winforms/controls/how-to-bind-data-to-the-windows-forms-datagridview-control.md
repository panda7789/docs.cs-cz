---
title: 'Postupy: Vytvoření vazby dat na ovládací prvek Windows Forms DataGridView'
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e147109a64687177f201ad1e312fab56ea61d604
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160067"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Postupy: Vytvoření vazby dat na ovládací prvek Windows Forms DataGridView

<xref:System.Windows.Forms.DataGridView> Ovládací prvek podporuje standardní Windows Forms datový model vazby, aby mohl vytvořit vazbu k řadě zdrojů dat. Obvykle můžete svázat <xref:System.Windows.Forms.BindingSource> , který spravuje interakci se zdroji dat. <xref:System.Windows.Forms.BindingSource> Může být libovolný zdroj dat Windows Forms, který dává velkou flexibilitu při výběru nebo úpravách umístění vašich dat. Další informace o zdrojích dat <xref:System.Windows.Forms.DataGridView> podporuje ovládací prvek, najdete v článku [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio poskytuje rozsáhlou podporu pro vytváření datových vazeb k ovládacím prvku DataGridView. Další informace najdete v tématu [jak: Vytvoření vazby dat na ovládací prvek Windows Forms DataGridView pomocí návrháře](bind-data-to-the-datagrid-using-the-designer.md).  

Ovládací prvek DataGridView připojení k datům:

1. Implementujte metodu ke zpracování detaily o načtení data. Následující příklad kódu implementuje `GetData` metodu, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter>a použije ho k vyplnění <xref:System.Data.DataTable>. Potom naváže <xref:System.Data.DataTable> k <xref:System.Windows.Forms.BindingSource>. 

2. Do formuláře <xref:System.Windows.Forms.Form.Load> obslužná rutina události, vazba <xref:System.Windows.Forms.DataGridView> ovládací prvek <xref:System.Windows.Forms.BindingSource>a volat `GetData` metody, aby se načetla data.  

## <a name="example"></a>Příklad

Tento příklad úplného kódu načte data z databáze k naplnění ovládacího prvku DataGridView ve formuláři Windows. Formulář obsahuje také tlačítek na hodnotu znovu načte data a odeslání změn do databáze.  

Tento příklad vyžaduje: 

- Přístup k ukázkové databázi Northwind SQL Server. Další informace o instalaci ukázkové databáze Northwind naleznete v tématu [získat ukázkových databází pro ukázky kódu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md). 

- Odkazy na sestavení systému, System.Windows.Forms, System.Data a System.Xml.  

Chcete-li sestavit a spustit tento příklad, vložte kód do *Form1* soubor kódu v novém projektu Windows Forms. Informace o vytváření z C# nebo příkazového řádku jazyka Visual Basic, naleznete v tématu [příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Naplnění `connectionString` proměnné v příkladu nahraďte hodnoty pro připojení ukázkové databáze Northwind SQL Server. Ověřování Windows, nazývané také integrovaného zabezpečení, je bezpečnější způsob, jak se připojit k databázi než uložení hesla v připojovacím řetězci. Další informace o zabezpečení připojení najdete v tématu [chránit informace o připojení](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Chránit informace o připojení](../../data/adonet/protecting-connection-information.md)
