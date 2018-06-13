---
title: 'Postupy: Připojení dat k ovládacímu prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 4ef9e97745c1c5d7a240e4b07b753b72644c6c15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531128"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a>Postupy: Připojení dat k ovládacímu prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení podporuje standardní Windows Forms datový model vazby, tak ho vytvoří vazbu na celou řadu zdrojů dat. Ve většině situací, ale vytvoříte vazbu k <xref:System.Windows.Forms.BindingSource> komponenta, která bude spravovat podrobnosti o interakci se zdrojem dat. <xref:System.Windows.Forms.BindingSource> Součást může představovat libovolný zdroj dat Windows Forms a poskytuje flexibilitu při výběru nebo úpravách umístění vaše data. Další informace o zdrojích dat nepodporuje <xref:System.Windows.Forms.DataGridView> řízení najdete v tématu [– Přehled ovládacího prvku DataGridView](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md).  
  
 Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.  Viz také [postupy: vytvoření vazby dat na Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/33w255ac\(v=vs.110\)).  
  
## <a name="procedure"></a>Postup  
  
#### <a name="to-connect-a-datagridview-control-to-data"></a>DataGridView – ovládací prvek připojit k datům  
  
1.  Implementujte metodu pro zpracování podrobnosti načítání dat z databáze. Následující příklad kódu implementuje `GetData` metoda, která inicializuje <xref:System.Data.SqlClient.SqlDataAdapter> součásti a používá k naplnění <xref:System.Data.DataTable>. <xref:System.Data.DataTable> Pak je vázána <xref:System.Windows.Forms.BindingSource> součásti. Nastavte `connectionString` proměnné na hodnotu, která je vhodná pro vaši databázi. Budete potřebovat přístup k serveru s ukázková databáze Northwind SQL serveru nainstalován.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#20)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#20)]  
  
2.  V svého formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události, vazby <xref:System.Windows.Forms.DataGridView> řídit k <xref:System.Windows.Forms.BindingSource> součásti a volání `GetData` metoda pro načtení dat z databáze.  
  
     [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#10)]
     [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#10)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu dokončení obsahuje tlačítka pro opětovné načtení dat z databáze a odeslání změn do databáze.  
  
 [!code-cpp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/cpp/datagridviewboundeditable.cpp#00)]
 [!code-csharp[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewBoundEditable#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Windows.Forms, System.Data a System.XML sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivé informace, jako jsou hesla, v připojovacím řetězci může ovlivnit zabezpečení vaší aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Ochrana informací o připojení](../../../../docs/framework/data/adonet/protecting-connection-information.md)
