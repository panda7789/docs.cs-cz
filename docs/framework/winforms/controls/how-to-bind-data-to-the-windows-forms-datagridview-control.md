---
title: Vazba dat s ovládacím prvkem DataGridView
ms.date: 02/08/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 643dcd37cd1bb3f8b5938fedff66c67cd68278ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182266"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Postup: Vazba dat s ovládacím prvkem Windows Forms DataGridView

Ovládací <xref:System.Windows.Forms.DataGridView> prvek podporuje standardní model datové vazby Windows Forms, takže se může vázat na různé zdroje dat. Obvykle se vážete <xref:System.Windows.Forms.BindingSource> na který spravuje interakci se zdrojem dat. Může <xref:System.Windows.Forms.BindingSource> se nacházet jako libovolný zdroj dat z Windows Forms, což vám poskytuje velkou flexibilitu při výběru nebo úpravě umístění dat. Další informace o zdrojích dat, které <xref:System.Windows.Forms.DataGridView> ovládací prvek podporuje, naleznete v [přehledu ovládacího prvku DataGridView](datagridview-control-overview-windows-forms.md).  

Visual Studio má rozsáhlou podporu pro datové vazby na ovládací prvek DataGridView. Další informace naleznete v [tématu How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).  

Připojení ovládacího prvku DataGridView k datům:

1. Implementujte metodu pro zpracování podrobností načítání dat. Následující příklad kódu implementuje metodu, `GetData` <xref:System.Data.SqlClient.SqlDataAdapter>která inicializuje <xref:System.Data.DataTable>, a používá ji k naplnění . Potom váže <xref:System.Data.DataTable> na . <xref:System.Windows.Forms.BindingSource>

2. V <xref:System.Windows.Forms.Form.Load> obslužné rutině <xref:System.Windows.Forms.DataGridView> události <xref:System.Windows.Forms.BindingSource>formuláře spojte `GetData` ovládací prvek s , a volání metody k načtení dat.  

## <a name="example"></a>Příklad

Tento úplný příklad kódu načte data z databáze k naplnění ovládacího prvku DataGridView ve formuláři systému Windows. Formulář obsahuje také tlačítka pro opětovné načtení dat a odeslání změn do databáze.  

Tento příklad vyžaduje:

- Přístup k ukázkové databázi serveru Northwind SQL Server. Další informace o instalaci ukázkové databáze Northwind naleznete [v tématu Získání ukázkových databází pro ADO.NET ukázky kódu](../../data/adonet/sql/linq/downloading-sample-databases.md).

- Odkazy na sestavení System, System.Windows.Forms, System.Data a System.Xml.  

Chcete-li vytvořit a spustit tento příklad, vložte kód do souboru kódu *Form1* v novém projektu Windows Forms. Informace o vytváření z příkazového řádku jazyka C# nebo Visual Basic naleznete v [tématu Vytváření příkazového řádku s csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) nebo [Sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).  
  
Naplňte `connectionString` proměnnou v příkladu hodnotami pro připojení ukázkové databáze northwind SQL Server. Ověřování systému Windows, nazývané také integrované zabezpečení, je bezpečnější způsob připojení k databázi než ukládání hesla do připojovacího řetězce. Další informace o zabezpečení připojení naleznete v [tématu Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
