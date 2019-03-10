---
title: 'Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 57b4591dcca42ec1e864115239a6acc61e4de609
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723995"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Postupy: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView
Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.DataGridView> ovládací prvek pro hlášení chyb vstupní data pro uživatele.  
  
 Úplné vysvětlení tento příklad kódu naleznete v tématu [názorný postup: Zpracování chyb vzniklých při zadávání dat v Windows Forms DataGridView – ovládací prvek](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Data, System.Windows.Forms a System.XML.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Ukládání citlivých informací, jako jsou hesla, v rámci připojovací řetězec může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [chrání informace o připojení](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Návod: Zpracování chyb vzniklých při zadávání dat v ovládacím prvku Windows Forms DataGridView](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Zadávání dat v ovládacím prvku Windows Forms DataGridView](data-entry-in-the-windows-forms-datagridview-control.md)
- [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
