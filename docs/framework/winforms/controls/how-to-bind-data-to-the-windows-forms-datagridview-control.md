---
title: Vázání dat k ovládacímu prvku DataGridView
ms.date: 02/08/2019
description: Přečtěte si, jak ovládací prvek DataGridView podporuje standardní model Windows Forms model vázání dat, aby se mohl navazovat na nejrůznější zdroje dat.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904413"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Postupy: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms

<xref:System.Windows.Forms.DataGridView>Ovládací prvek podporuje model standardní model Windows Forms datové vazby, takže může vytvořit vazbu na nejrůznější zdroje dat. Obvykle se svážete s objektem <xref:System.Windows.Forms.BindingSource> , který spravuje interakci se zdrojem dat. <xref:System.Windows.Forms.BindingSource>Může se jednat o libovolný model Windows Forms zdroj dat, který vám dává větší flexibilitu při volbě nebo úpravě umístění vašich dat. Další informace o zdrojích dat <xref:System.Windows.Forms.DataGridView> , které ovládací prvek podporuje, naleznete v tématu [Přehled ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio má rozsáhlou podporu pro datové vazby k ovládacímu prvku DataGridView. Další informace najdete v tématu [Postup: vytvoření vazby dat k ovládacímu prvku DataGridView model Windows Forms pomocí návrháře](bind-data-to-the-datagrid-using-the-designer.md).  

Připojení ovládacího prvku DataGridView k datům:

1. Implementujte metodu pro zpracování podrobností o načítání dat. Následující příklad kódu implementuje `GetData` metodu, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter> a použije ji k naplnění <xref:System.Data.DataTable> . Potom vytvoří vazby <xref:System.Data.DataTable> k <xref:System.Windows.Forms.BindingSource> .

2. V <xref:System.Windows.Forms.Form.Load> obslužné rutině události formuláře svažte <xref:System.Windows.Forms.DataGridView> ovládací prvek s <xref:System.Windows.Forms.BindingSource> a zavolejte `GetData` metodu pro načtení dat.  

## <a name="example"></a>Příklad

Tento úplný příklad kódu načte data z databáze k naplnění ovládacího prvku DataGridView ve formuláři Windows. Formulář obsahuje také tlačítka pro opětovné načtení dat a odeslání změn do databáze.  

Tento příklad vyžaduje:

- Přístup k ukázkové databázi Northwind SQL Server. Další informace o instalaci ukázkové databáze Northwind najdete v tématu [získání ukázkových databází pro ukázky kódu ADO.NET](../../data/adonet/sql/linq/downloading-sample-databases.md).

- Odkazy na sestavení System, System. Windows. Forms, System. data a System.Xml.  

Chcete-li sestavit a spustit tento příklad, vložte kód do souboru kódu *Form1* v novém model Windows Forms projektu. Informace o vytváření z příkazového řádku jazyka C# nebo Visual Basic naleznete v tématu [sestavování z příkazového řádku pomocí csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Naplňte `connectionString` proměnnou v příkladu hodnotami pro vaše připojení k ukázkové databázi Northwind SQL Server. Ověřování systému Windows, označované také jako integrované zabezpečení, je bezpečnější způsob, jak se připojit k databázi, než ukládat heslo v připojovacím řetězci. Další informace o zabezpečení připojení najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Zobrazení dat v ovládacím prvku DataGridView model Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Chránit informace o připojení](../../data/adonet/protecting-connection-information.md)
